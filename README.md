# Ansible Role for Caribou Peary

This role installs and deploys Peary through Ansible.

## Requirements

This role currently only supports Ubuntu/Debian systems.

## Role Variables

The following role variables can be used to configure this role. All variables are listed along with default values as defined in `defaults/main.yml`.

### Peary source and target
`peary_repository: "https://gitlab.cern.ch/Caribou/peary.git"` - Git repository to fetch Peary code from. Replace with your own repository if you have additional code which is not contained in the main Peary repository.
`peary_branch: master` - Peary version or Git branch to be deployed. The configured branch or tag has to exist in the selected repository.

`peary_build_folder: /tmp/peary`
`peary_install_folder: /usr/local`

### Peary features

`peary_interface_emulation: false` - Select whether interfaces such as I2C or SPI should be emulated or not. Normally, interface emulation should be switched off on production systems and switched on if only decoding libraries are required, e.g. for deployment on a reconstruction machine.
`peary_build_server: false` - Select whether to build the Peary server component or not.
`peary_install_headers: true` - Select whether to install the framework headers or not. Installation is required in order to compile other software such as EUDAQ2 against Peary.

## Dependencies

This role has no dependencies.

## Example Playbook

The following is an example playbook for installing Peary including the stand-alone Peary server:

```yml
  - hosts: runcontrols

    vars:
      peary_build_server: true

    roles:
      - role: ansible-role-peary
```

## License

MIT

## Author Information

Simon Spannagel (<simon.spannagel@desy.de>) DESY
