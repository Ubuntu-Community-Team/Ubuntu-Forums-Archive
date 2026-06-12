---
title: "Vpn stops after short time"
date: 2018-10-25
forum: Networking &amp; Wireless
---

### Post by marcingronowski on 2018-10-25
I have some problems with a VPN connection. I have set VPN connection by gnome network manager. It works fine some time ago (about 2-3 days). Today, I can connect, but after a short period of time, connection fails.

Some measeges from gnome logs
```
16:07:55 nm-dispatcher: req:2 'vpn-down' [tun0]: start running ordered scripts...
16:07:55 NetworkManager: <info>  [1540476475.7150] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",0]: VPN service disappeared
16:07:55 nm-dispatcher: req:1 'down' [tun0]: start running ordered scripts...
16:07:55 systemd: Started Network Manager Script Dispatcher Service.
16:07:55 dbus-daemon: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
16:07:55 gnome-shell: Removing a network device that was not added
16:07:55 systemd: Starting Network Manager Script Dispatcher Service...
16:07:55 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.346' (uid=0 pid=1769 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
16:07:55 NetworkManager: <info>  [1540476475.6729] devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
16:07:55 openvpn: Exiting due to fatal error
16:06:36 gdm-x-session: -2
16:04:05 systemd: Started Hostname Service.
16:04:05 dbus-daemon: [system] Successfully activated service 'org.freedesktop.hostname1'
16:04:05 systemd: Starting Hostname Service...
16:04:05 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.359' (uid=1000 pid=32506 comm="/usr/bin/gnome-logs --gapplication-service " label="unconfined")
16:03:51 sshd: Server listening on :: port 22.
16:03:51 systemd: Reloaded OpenBSD Secure Shell server.
16:03:51 sshd: Received SIGHUP; restarting.
16:03:51 systemd: Reloading OpenBSD Secure Shell server.
16:03:51 sshd: Server listening on :: port 22.
16:03:51 systemd: Reloaded OpenBSD Secure Shell server.
16:03:51 sshd: Received SIGHUP; restarting.
16:03:51 systemd: Reloading OpenBSD Secure Shell server.
16:03:51 sshd: Server listening on :: port 22.
16:03:51 systemd: Reloaded OpenBSD Secure Shell server.
16:03:51 sshd: Received SIGHUP; restarting.
16:03:51 nm-dispatcher: req:2 'up' [tun0]: start running ordered scripts...
16:03:51 systemd: Reloading OpenBSD Secure Shell server.
16:03:51 nm-dispatcher: req:2 'up' [tun0]: new request (1 scripts)
16:03:51 NetworkManager: <info>  [1540476231.3967] device (tun0): Activation: successful, device activated.
16:03:51 nm-dispatcher: req:1 'vpn-up' [tun0]: start running ordered scripts...
16:03:51 systemd: Started Network Manager Script Dispatcher Service.
16:03:51 dbus-daemon: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
16:03:51 NetworkManager: <info>  [1540476231.3858] device (tun0): Activation: starting connection 'tun0' (d02cc0d4-03eb-4571-85f0-c5f2774bee65)
16:03:51 systemd: Starting Network Manager Script Dispatcher Service...
16:03:51 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.346' (uid=0 pid=1769 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
16:03:51 NetworkManager: <info>  [1540476231.3766] device (tun0): state change: unmanaged -> unavailable (reason 'connection-assumed', sys-iface-state: 'external')
16:03:51 openvpn: Initialization Sequence Completed
16:03:51 NetworkManager: <info>  [1540476231.3718] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 213.135.39.84/31   Next Hop: 172.22.0.45
16:03:51 openvpn: UID set to nm-openvpn
16:03:51 NetworkManager: <info>  [1540476231.3718] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 213.135.39.80/30   Next Hop: 172.22.0.45
16:03:51 openvpn: GID set to nm-openvpn
16:03:51 NetworkManager: <info>  [1540476231.3717] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 213.135.39.64/28   Next Hop: 172.22.0.45
16:03:51 openvpn: chroot to '/var/lib/openvpn/chroot' and cd to '/' succeeded
16:03:51 NetworkManager: <info>  [1540476231.3717] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 213.135.39.0/26   Next Hop: 172.22.0.45
16:03:51 systemd-udevd: link_config: autonegotiation is unset or enabled, the speed and duplex are not writable.
16:03:51 openvpn: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper --debug 0 2921 --bus-name org.freedesktop.NetworkManager.openvpn.Connection_6 --tun -- tun0 1500 1542 172.22.0.46 172.22.0.45 init
16:03:49 NetworkManager: <info>  [1540476229.9563] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",0]: VPN connection: (ConnectInteractive) reply received
16:03:42 anacron: Normal exit (0 jobs run)
16:03:42 systemd: Started Run anacron jobs.
16:02:46 gdm-x-session: -2

```

Mesages from /var/log/syslog
```
Oct 25 16:02:46 Herzberg /usr/lib/gdm3/gdm-x-session[1395]: -2
Oct 25 16:03:42 Herzberg systemd[1]: Started Run anacron jobs.
Oct 25 16:03:42 Herzberg anacron[2914]: Anacron 2.3 started on 2018-10-25
Oct 25 16:03:42 Herzberg anacron[2914]: Normal exit (0 jobs run)
Oct 25 16:03:49 Herzberg NetworkManager[1769]: <info>  [1540476229.8077] audit: op="connection-activate" uuid="54da7c2c-717a-4682-a1ae-c9262f5e7e15" name="client" pid=1513 uid=1000 result="success"
Oct 25 16:03:49 Herzberg NetworkManager[1769]: <info>  [1540476229.8151] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",0]: Started the VPN service, PID 2921
Oct 25 16:03:49 Herzberg NetworkManager[1769]: <info>  [1540476229.8219] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",0]: Saw the service appear; activating connection
Oct 25 16:03:49 Herzberg NetworkManager[1769]: <info>  [1540476229.9562] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",0]: VPN plugin: state changed: starting (3)
Oct 25 16:03:49 Herzberg NetworkManager[1769]: <info>  [1540476229.9563] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",0]: VPN connection: (ConnectInteractive) reply received
Oct 25 16:03:49 Herzberg nm-openvpn[2927]: OpenVPN 2.4.4 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on Sep  5 2018
Oct 25 16:03:49 Herzberg nm-openvpn[2927]: library versions: OpenSSL 1.1.0g  2 Nov 2017, LZO 2.08
Oct 25 16:03:49 Herzberg nm-openvpn[2927]: WARNING: --ns-cert-type is DEPRECATED.  Use --remote-cert-tls instead.
Oct 25 16:03:49 Herzberg nm-openvpn[2927]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Oct 25 16:03:50 Herzberg nm-openvpn[2927]: TCP/UDP: Preserving recently used remote address: [AF_INET]213.135.39.86:1194
Oct 25 16:03:50 Herzberg nm-openvpn[2927]: UDP link local: (not bound)
Oct 25 16:03:50 Herzberg nm-openvpn[2927]: UDP link remote: [AF_INET]213.135.39.86:1194
Oct 25 16:03:50 Herzberg nm-openvpn[2927]: NOTE: chroot will be delayed because of --client, --pull, or --up-delay
Oct 25 16:03:50 Herzberg nm-openvpn[2927]: NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Oct 25 16:03:50 Herzberg nm-openvpn[2927]: [vpn] Peer Connection Initiated with [AF_INET]213.135.39.86:1194
Oct 25 16:03:51 Herzberg nm-openvpn[2927]: WARNING: INSECURE cipher with block size less than 128 bit (64 bit).  This allows attacks like SWEET32.  Mitigate by using a --cipher with a larger block size (e.g. AES-256-CBC).
Oct 25 16:03:51 Herzberg nm-openvpn[2927]: WARNING: INSECURE cipher with block size less than 128 bit (64 bit).  This allows attacks like SWEET32.  Mitigate by using a --cipher with a larger block size (e.g. AES-256-CBC).
Oct 25 16:03:51 Herzberg nm-openvpn[2927]: WARNING: cipher with small block size in use, reducing reneg-bytes to 64MB to mitigate SWEET32 attacks.
Oct 25 16:03:51 Herzberg nm-openvpn[2927]: TUN/TAP device tun0 opened
Oct 25 16:03:51 Herzberg nm-openvpn[2927]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper --debug 0 2921 --bus-name org.freedesktop.NetworkManager.openvpn.Connection_6 --tun -- tun0 1500 1542 172.22.0.46 172.22.0.45 init
Oct 25 16:03:51 Herzberg systemd-udevd[2929]: link_config: autonegotiation is unset or enabled, the speed and duplex are not writable.
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3558] manager: (tun0): new Tun device (/org/freedesktop/NetworkManager/Devices/5)
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3647] devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3647] device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3663] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",0]: VPN connection: (IP Config Get) reply received.
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3705] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: VPN connection: (IP4 Config Get) reply received
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3716] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data: VPN Gateway: 213.135.39.86
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3716] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data: Tunnel Device: "tun0"
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3716] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data: IPv4 configuration:
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3716] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Internal Gateway: 172.22.0.45
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3716] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Internal Address: 172.22.0.46
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3716] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Internal Prefix: 32
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3717] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Internal Point-to-Point Address: 172.22.0.45
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3717] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 213.135.37.0/24   Next Hop: 172.22.0.45
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3717] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 213.135.38.0/24   Next Hop: 172.22.0.45
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3717] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 213.135.40.0/24   Next Hop: 172.22.0.45
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3717] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 213.135.41.0/24   Next Hop: 172.22.0.45
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3717] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 213.135.39.0/26   Next Hop: 172.22.0.45
Oct 25 16:03:51 Herzberg nm-openvpn[2927]: chroot to '/var/lib/openvpn/chroot' and cd to '/' succeeded
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3717] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 213.135.39.64/28   Next Hop: 172.22.0.45
Oct 25 16:03:51 Herzberg nm-openvpn[2927]: GID set to nm-openvpn
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3718] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 213.135.39.80/30   Next Hop: 172.22.0.45
Oct 25 16:03:51 Herzberg nm-openvpn[2927]: UID set to nm-openvpn
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3718] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 213.135.39.84/31   Next Hop: 172.22.0.45
Oct 25 16:03:51 Herzberg nm-openvpn[2927]: Initialization Sequence Completed
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3718] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 213.135.39.87/32   Next Hop: 172.22.0.45
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3718] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 213.135.39.64/27   Next Hop: 172.22.0.45
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3718] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 213.135.39.120/29   Next Hop: 172.22.0.45
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3718] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 213.135.39.128/25   Next Hop: 172.22.0.45
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3719] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 172.22.0.1/32   Next Hop: 172.22.0.45
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3719] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Static Route: 172.22.0.45/32   Next Hop: 0.0.0.0
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3719] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   Internal DNS: 8.8.8.8
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3719] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data:   DNS Domain: '(none)'
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3719] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: Data: No IPv6 configuration
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3720] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: VPN plugin: state changed: started (4)
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3761] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: VPN connection: (IP Config Get) complete
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3766] device (tun0): state change: unmanaged -> unavailable (reason 'connection-assumed', sys-iface-state: 'external')
Oct 25 16:03:51 Herzberg dbus-daemon[838]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.346' (uid=0 pid=1769 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Oct 25 16:03:51 Herzberg systemd[1]: Starting Network Manager Script Dispatcher Service...
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3841] keyfile: add connection in-memory (d02cc0d4-03eb-4571-85f0-c5f2774bee65,"tun0")
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3847] device (tun0): state change: unavailable -> disconnected (reason 'connection-assumed', sys-iface-state: 'external')
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3858] device (tun0): Activation: starting connection 'tun0' (d02cc0d4-03eb-4571-85f0-c5f2774bee65)
Oct 25 16:03:51 Herzberg dbus-daemon[838]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 25 16:03:51 Herzberg systemd[1]: Started Network Manager Script Dispatcher Service.
Oct 25 16:03:51 Herzberg nm-dispatcher: req:1 'vpn-up' [tun0]: new request (1 scripts)
Oct 25 16:03:51 Herzberg nm-dispatcher: req:1 'vpn-up' [tun0]: start running ordered scripts...
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3931] device (tun0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'external')
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3934] device (tun0): state change: prepare -> config (reason 'none', sys-iface-state: 'external')
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3936] device (tun0): state change: config -> ip-config (reason 'none', sys-iface-state: 'external')
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3937] device (tun0): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'external')
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3941] device (tun0): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'external')
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3942] device (tun0): state change: secondaries -> activated (reason 'none', sys-iface-state: 'external')
Oct 25 16:03:51 Herzberg NetworkManager[1769]: <info>  [1540476231.3967] device (tun0): Activation: successful, device activated.
Oct 25 16:03:51 Herzberg nm-dispatcher: req:2 'up' [tun0]: new request (1 scripts)
Oct 25 16:03:51 Herzberg systemd[1]: Reloading OpenBSD Secure Shell server.
Oct 25 16:03:51 Herzberg nm-dispatcher: req:2 'up' [tun0]: start running ordered scripts...
Oct 25 16:03:51 Herzberg systemd[1]: Reloaded OpenBSD Secure Shell server.
Oct 25 16:03:51 Herzberg systemd[1]: Reloading OpenBSD Secure Shell server.
Oct 25 16:03:51 Herzberg systemd[1]: Reloaded OpenBSD Secure Shell server.
Oct 25 16:03:51 Herzberg systemd[1]: Reloading OpenBSD Secure Shell server.
Oct 25 16:03:51 Herzberg systemd[1]: Reloaded OpenBSD Secure Shell server.
Oct 25 16:04:05 Herzberg dbus-daemon[838]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.359' (uid=1000 pid=32506 comm="/usr/bin/gnome-logs --gapplication-service " label="unconfined")
Oct 25 16:04:05 Herzberg systemd[1]: Starting Hostname Service...
Oct 25 16:04:05 Herzberg dbus-daemon[838]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct 25 16:04:05 Herzberg systemd[1]: Started Hostname Service.
Oct 25 16:06:36 Herzberg /usr/lib/gdm3/gdm-x-session[1395]: -2
Oct 25 16:07:49 Herzberg nm-openvpn[2927]: [vpn] Inactivity timeout (--ping-restart), restarting
Oct 25 16:07:49 Herzberg nm-openvpn[2927]: SIGUSR1[soft,ping-restart] received, process restarting
Oct 25 16:07:54 Herzberg nm-openvpn[2927]: WARNING: --ns-cert-type is DEPRECATED.  Use --remote-cert-tls instead.
Oct 25 16:07:54 Herzberg nm-openvpn[2927]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Oct 25 16:07:54 Herzberg nm-openvpn[2927]: TCP/UDP: Preserving recently used remote address: [AF_INET]213.135.39.86:1194
Oct 25 16:07:54 Herzberg nm-openvpn[2927]: UDP link local: (not bound)
Oct 25 16:07:54 Herzberg nm-openvpn[2927]: UDP link remote: [AF_INET]213.135.39.86:1194
Oct 25 16:07:54 Herzberg nm-openvpn[2927]: [vpn] Peer Connection Initiated with [AF_INET]213.135.39.86:1194
Oct 25 16:07:55 Herzberg nm-openvpn[2927]: WARNING: INSECURE cipher with block size less than 128 bit (64 bit).  This allows attacks like SWEET32.  Mitigate by using a --cipher with a larger block size (e.g. AES-256-CBC).
Oct 25 16:07:55 Herzberg nm-openvpn[2927]: WARNING: INSECURE cipher with block size less than 128 bit (64 bit).  This allows attacks like SWEET32.  Mitigate by using a --cipher with a larger block size (e.g. AES-256-CBC).
Oct 25 16:07:55 Herzberg nm-openvpn[2927]: WARNING: cipher with small block size in use, reducing reneg-bytes to 64MB to mitigate SWEET32 attacks.
Oct 25 16:07:55 Herzberg nm-openvpn[2927]: Preserving previous TUN/TAP instance: tun0
Oct 25 16:07:55 Herzberg nm-openvpn[2927]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper --debug 0 2921 --bus-name org.freedesktop.NetworkManager.openvpn.Connection_6 --tun -- tun0 1500 1542 172.22.0.46 172.22.0.45 restart
Oct 25 16:07:55 Herzberg nm-openvpn[2927]: WARNING: Failed running command (--up/--down): could not execute external program
Oct 25 16:07:55 Herzberg nm-openvpn[2927]: Exiting due to fatal error
Oct 25 16:07:55 Herzberg NetworkManager[1769]: <info>  [1540476475.6683] device (tun0): state change: activated -> unmanaged (reason 'unmanaged', sys-iface-state: 'removed')
Oct 25 16:07:55 Herzberg NetworkManager[1769]: <info>  [1540476475.6729] devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Oct 25 16:07:55 Herzberg dbus-daemon[838]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.346' (uid=0 pid=1769 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Oct 25 16:07:55 Herzberg systemd[1]: Starting Network Manager Script Dispatcher Service...
Oct 25 16:07:55 Herzberg gnome-shell[1513]: Removing a network device that was not added
Oct 25 16:07:55 Herzberg gnome-shell[1064]: Removing a network device that was not added
Oct 25 16:07:55 Herzberg dbus-daemon[838]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 25 16:07:55 Herzberg systemd[1]: Started Network Manager Script Dispatcher Service.
Oct 25 16:07:55 Herzberg nm-dispatcher: req:1 'down' [tun0]: new request (1 scripts)
Oct 25 16:07:55 Herzberg nm-dispatcher: req:1 'down' [tun0]: start running ordered scripts...
Oct 25 16:07:55 Herzberg NetworkManager[1769]: <warn>  [1540476475.7067] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: VPN plugin: failed: connect-failed (1)
Oct 25 16:07:55 Herzberg NetworkManager[1769]: <info>  [1540476475.7068] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: VPN plugin: state changed: stopping (5)
Oct 25 16:07:55 Herzberg NetworkManager[1769]: <info>  [1540476475.7069] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",33:(tun0)]: VPN plugin: state changed: stopped (6)
Oct 25 16:07:55 Herzberg NetworkManager[1769]: <info>  [1540476475.7150] vpn-connection[0x563217b184d0,54da7c2c-717a-4682-a1ae-c9262f5e7e15,"client",0]: VPN service disappeared
Oct 25 16:07:55 Herzberg nm-dispatcher: req:2 'vpn-down' [tun0]: new request (1 scripts)
Oct 25 16:07:55 Herzberg nm-dispatcher: req:2 'vpn-down' [tun0]: start running ordered scripts...
Oct 25 16:08:17 Herzberg dbus-daemon[838]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.362' (uid=1000 pid=32506 comm="/usr/bin/gnome-logs --gapplication-service " label="unconfined")
Oct 25 16:08:17 Herzberg systemd[1]: Starting Hostname Service...
Oct 25 16:08:17 Herzberg dbus-daemon[838]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct 25 16:08:17 Herzberg systemd[1]: Started Hostname Service.
Oct 25 16:08:37 Herzberg org.gnome.Shell.desktop[1513]: Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4200084 (logmessage)
Oct 25 16:09:01 Herzberg CRON[3290]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
Oct 25 16:09:24 Herzberg systemd[1]: Starting Clean php session files...
Oct 25 16:09:24 Herzberg systemd[1]: Started Clean php session files.
```

ifconfig output
```
enp37s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.42.0.32  netmask 255.248.0.0  broadcast 10.47.255.255
        inet6 fe80::b38e:9845:fc81:c372  prefixlen 64  scopeid 0x20<link>
        ether 88:d7:f6:7c:29:bf  txqueuelen 1000  (Ethernet)
        RX packets 1322186  bytes 824719823 (824.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 466293  bytes 77241634 (77.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 59567  bytes 5509782 (5.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 59567  bytes 5509782 (5.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 172.22.0.46  netmask 255.255.255.255  destination 172.22.0.45
        inet6 fe80::d19c:3b6e:a144:a401  prefixlen 64  scopeid 0x20<link>
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (UNSPEC)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2  bytes 96 (96.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

---

### Post by TheFu on 2018-10-25
If your internet connection drops, then the VPN will drop too after the timeout period occurs.

Can you monitor the straight internet, without the VPN, to be notified of when it drops or not?

BTW, there is an important warning in the logs about using small keys.  I'd see to that ASAP.  Some VPN providers support different key sizes, but the defaults are usually not the strongest.  My provider has AES-256, but to use it requires some manual configuration.

---

