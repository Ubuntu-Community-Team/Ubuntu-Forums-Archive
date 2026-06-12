---
title: "Ubuntu 19.10: Intel 1217-V wired network not connecting"
date: 2019-12-02
forum: Networking &amp; Wireless
---

### Post by Dean Powell on 2019-12-02
Hi:

Dual booting Win10/Ubuntu 19.10
Intel 1217-V NIC
Fresh install of 19.10 last night

WoL (Wake On LAN) is DISABLED at the BIOS level

Wireless connection works, but is unacceptably slow. Wired connection consistently fails, with error popping up about connectivity failing

syslog shows the following:

cat /var/log/syslog | grep -e etwork -e eno1 | tail -n20
Dec  2 17:06:03 dean-K30AD-M31AD-M51AD NetworkManager[4104]: <info>  [1575331563.5980] device (wlp3s0): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Dec  2 17:06:03 dean-K30AD-M31AD-M51AD NetworkManager[4104]: <info>  [1575331563.5982] device (wlp3s0): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Dec  2 17:06:03 dean-K30AD-M31AD-M51AD NetworkManager[4104]: <info>  [1575331563.5986] manager: NetworkManager state is now CONNECTED_LOCAL
Dec  2 17:06:03 dean-K30AD-M31AD-M51AD NetworkManager[4104]: <info>  [1575331563.6000] manager: NetworkManager state is now CONNECTED_SITE
Dec  2 17:06:03 dean-K30AD-M31AD-M51AD NetworkManager[4104]: <info>  [1575331563.6001] policy: set 'ZyXEL38935' (wlp3s0) as default for IPv4 routing and DNS
Dec  2 17:06:03 dean-K30AD-M31AD-M51AD NetworkManager[4104]: <info>  [1575331563.6006] device (wlp3s0): Activation: successful, device activated.
Dec  2 17:06:04 dean-K30AD-M31AD-M51AD NetworkManager[4104]: <info>  [1575331564.2753] manager: NetworkManager state is now CONNECTED_GLOBAL
Dec  2 17:06:04 dean-K30AD-M31AD-M51AD whoopsie[1813]: [17:06:04] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/2
Dec  2 17:06:04 dean-K30AD-M31AD-M51AD whoopsie[1813]: [17:06:04] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/2
Dec  2 17:06:04 dean-K30AD-M31AD-M51AD whoopsie[1813]: [17:06:04] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/2
Dec  2 17:06:14 dean-K30AD-M31AD-M51AD systemd[1]: NetworkManager-dispatcher.service: Succeeded.
Dec  2 17:13:45 dean-K30AD-M31AD-M51AD NetworkManager[4104]: <info>  [1575332025.1263] device (eno1): DHCPv4: grace period expired
Dec  2 17:13:45 dean-K30AD-M31AD-M51AD NetworkManager[4104]: <info>  [1575332025.1266] device (eno1): state change: ip-config -> ip-check (reason 'ip-config-unavailable', sys-iface-state: 'assume')
Dec  2 17:13:45 dean-K30AD-M31AD-M51AD dbus-daemon[903]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.497' (uid=0 pid=4104 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Dec  2 17:13:45 dean-K30AD-M31AD-M51AD systemd[1]: Starting Network Manager Script Dispatcher Service...
Dec  2 17:13:45 dean-K30AD-M31AD-M51AD systemd[1]: Started Network Manager Script Dispatcher Service.
Dec  2 17:13:45 dean-K30AD-M31AD-M51AD NetworkManager[4104]: <info>  [1575332025.1469] device (eno1): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'assume')
Dec  2 17:13:45 dean-K30AD-M31AD-M51AD NetworkManager[4104]: <info>  [1575332025.1472] device (eno1): state change: secondaries -> activated (reason 'none', sys-iface-state: 'assume')
Dec  2 17:13:45 dean-K30AD-M31AD-M51AD NetworkManager[4104]: <info>  [1575332025.1484] device (eno1): Activation: successful, device activated.
Dec  2 17:13:56 dean-K30AD-M31AD-M51AD systemd[1]: NetworkManager-dispatcher.service: Succeeded.


I believe the network interface is eno1. "ifconfig eno1" shows:eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::3a2c:4aff:fec6:5779  prefixlen 64  scopeid 0x20<link>
        ether 38:2c:4a:c6:57:79  txqueuelen 1000  (Ethernet)
        RX packets 4037  bytes 631628 (631.6 KB)
        RX errors 0  dropped 18  overruns 0  frame 0
        TX packets 968  bytes 173703 (173.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf7200000-f7220000

My Network Manager confirms I have disabled IPv6. Wired connection simply will not connect.

Any suggestions?

---

