# Kiosk Ansible role

This role installs and configures a kiosk environment on a Linux system. It sets up a user session that automatically launches a web browser in kiosk mode, displaying a specified URL.

It is designed for Raspberry Pi OS 64-bit, but it may work on other Linux distributions as well.

## Requirements

- Ansible 2.2 or newer
- A target system running Linux and systemd (e.g., Raspberry Pi OS 64-bit)
- A user account for the kiosk session
- A display server

## Role variables

The role exposes the following variables through defaults/main.yml:

- `kiosk_url`: The URL to display in kiosk mode (default: `https://www.example.com`)
- `kiosk_user`: The user account for the kiosk session (default: `pi`)
- `kiosk_group`: The group for the kiosk user (default: `pi`)
- `kiosk_display`: The display to use for the kiosk session (default: `:0`)
- `kiosk_chrome_window_position`: The position of the Chrome window (default: `0,0`)
- `kiosk_chrome_window_size`: The size of the Chrome window (default: `1920,1080`)
- `kiosk_kernel_video`: The kernel video mode (default: `HDMI-A-1:1920x1080@60`)

## Dependencies

This role has no external dependencies.

## Example playbook

```yaml
---
- hosts: servers
  become: true
  roles:
    - name: ansible-role-kiosk
      src: https://github.com/supcik/ansible-role-kiosk.git
      scm: git
```

You can override variables if needed:

```yaml
---
- hosts: servers
  become: true
  vars:
    kiosk_url: "https://example.com"
    kiosk_user: "pi"
  roles:
    - name: ansible-role-kiosk
      src: https://github.com/supcik/ansible-role-kiosk.git
      scm: git
```

## Notes

This role installs Chromium, X11 utilities, and configures a systemd service that starts a kiosk session on boot. It is primarily intended for Raspberry Pi-style Linux systems with a graphical display and systemd.

## License

MIT

## Author information

Jacques Supcik <mailto:jacques@supcik.net>
