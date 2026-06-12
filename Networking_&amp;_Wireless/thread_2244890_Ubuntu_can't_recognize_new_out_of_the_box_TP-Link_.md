---
title: "Ubuntu can't recognize new out of the box TP-Link TL-WN851ND"
date: 2014-09-19
forum: Networking &amp; Wireless
---

### Post by roman20 on 2014-09-19
I'm new Ubuntu user, and it seems that I can't find answer to my specific problem.

Recently I bought TP-Link TL-WN851ND to install on an old pc.
I have just installed clean ubuntu on the machine.
After turning off the pc and inserting the network card in the PCI connector, I have turned the pc on.
It took him about half a minute longer to log on and he was really lagy at the beginning, but it seems that it found wireless networks.
On attempt to connect to one of the networks, it just froze and turnd off.
After that it seems it can't see the wireles network card.

```
Roman-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:cc:99:11  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fecc:9911/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16338 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:20955662 (20.9 MB)  TX bytes:1903048 (1.9 MB)

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:429237 (429.2 KB)  TX bytes:429237 (429.2 KB)

```

There is no wlan0

```
Roman-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
**03:00.0 Network controller: Device 0000:002d (rev ff)**
03:01.0 Multimedia audio controller: Ensoniq ES1371 / Creative Labs CT2518 [AudioPCI-97] (rev 08)

```

the network card seems unfomiliar to the the system- should be ```
Network controller [0280]: Atheros Communications Inc. Device [168c:002d] (rev 01)
```

Please help me. at this time any simmilar questions/articles already have any output of any sort that will identify this card.

I even tried  reinstalling Ubuntu from scrach after formating the pc again.
I have no idea what to do now.

---

### Post by praseodym on 2014-09-19
Please reboot and run
```

dmesg >> dmesg.txt
```
and upload that file.

---

### Post by roman20 on 2014-09-20
sorry for the delay. the file was to big for this attachment system, so i splited it into three.

---

### Post by praseodym on 2014-09-20
```
[    0.000000] DMI: System manufacturer System Product Name/P5KPL-CM, BIOS 0512    [COLOR="#FF0000"]05/19/2008[/COLOR]
```
Any chance to update the BIOS? I don't think the device is listed in the BIOS whitelist. It seems too new.

---

### Post by roman20 on 2014-09-20
just updated bios and reinstalled ubuntu. same lspci output as before.

---

### Post by praseodym on 2014-09-20
```
modprobe -c | grep -i "168c.*002d"
alias pci:v0000[COLOR="#FF0000"]168C[/COLOR]d0000[COLOR="#FF0000"]002D[/COLOR]sv*sd*bc*sc*i* ath9k
alias usb:v[COLOR="#FF0000"]168C[/COLOR]p[COLOR="#FF0000"]0002d[/COLOR]*dc*dsc*dp*ic*isc*ip*in* ar5523
```
Obviously, this device ID is part of ath9k (PCI) and ar5523 (USB) drivers. Strange. Please check
```
egrep -i 'net|eth|wlan|firm|reason|002d|03:00.0' /var/log/syslog 
lsmod
```

Can you try a Mainline kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.3-utopic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.3-utopic/)

---

### Post by roman20 on 2014-09-20
egrep output:
```
): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=455 comm="apparmor_parser"
Sep 20 13:31:13 hanna-PC kernel: [    7.074260] type=1400 audit(1411209072.915:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=454 comm="apparmor_parser"
Sep 20 13:31:13 hanna-PC kernel: [    7.074699] type=1400 audit(1411209072.915:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=454 comm="apparmor_parser"
Sep 20 13:31:14 hanna-PC kernel: [    8.591319] NET: Registered protocol family 31
Sep 20 13:31:14 hanna-PC avahi-daemon[710]: Network interface enumeration completed.
Sep 20 13:31:14 hanna-PC kernel: [    8.982150] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Sep 20 13:31:16 hanna-PC NetworkManager[727]: <info> NetworkManager (version 0.9.8.8) is starting...
Sep 20 13:31:16 hanna-PC NetworkManager[727]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Sep 20 13:31:16 hanna-PC NetworkManager[727]: <info> WEXT support is enabled
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> DNS: loaded plugin dnsmasq
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    SCPlugin-Ifupdown: init!
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    SCPlugin-Ifupdown: update_system_hostname
Sep 20 13:31:17 hanna-PC NetworkManager[727]:       interface-parser: parsing file /etc/network/interfaces
Sep 20 13:31:17 hanna-PC NetworkManager[727]:       interface-parser: finished parsing file /etc/network/interfaces
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    SCPluginIfupdown: management mode: unmanaged
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0)
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    SCPlugin-Ifupdown: end _init.
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    SCPlugin-Ofono: init!
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    SCPlugin-Ofono: end _init.
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> Loaded plugin (null): (null)
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    Ifupdown: get unmanaged devices count: 0
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    SCPlugin-Ifupdown: (38258208) ... get_connections.
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    SCPlugin-Ifupdown: (38258208) ... get_connections (managed=false): return empty list.
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    SCPlugin-Ofono: (38040080) ... get_connections.
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    SCPlugin-Ofono: (38040080) connections count: 0
Sep 20 13:31:17 hanna-PC NetworkManager[727]:    Ifupdown: get unmanaged devices count: 0
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> monitoring kernel firmware directory '/lib/firmware'.
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> WiFi enabled by radio killswitch; enabled by state file
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> WWAN enabled by radio killswitch; enabled by state file
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> WiMAX enabled by radio killswitch; enabled by state file
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> Networking is enabled by state file
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <warn> failed to allocate link cache: (-12) Object not found
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> (eth0): carrier is OFF
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> (eth0): new Ethernet device (driver: 'ATL1E' ifindex: 2)
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> (eth0): bringing up device.
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> (eth0): preparing device.
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> (eth0): deactivating device (reason 'managed') [2]
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> Added default wired connection '&#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1' for /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Sep 20 13:31:17 hanna-PC kernel: [   11.885485] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 20 13:31:17 hanna-PC kernel: [   11.885876] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> urfkill disappeared from the bus
Sep 20 13:31:17 hanna-PC NetworkManager[727]: <info> ModemManager available in the bus
Sep 20 13:31:17 hanna-PC acpid: starting up with netlink and the input layer
Sep 20 13:31:27 hanna-PC NetworkManager[727]: <info> WiFi hardware radio set enabled
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> (eth0): carrier now ON (device state 20)
Sep 20 13:33:00 hanna-PC kernel: [  114.480811] ATL1E 0000:01:00.0 eth0: NIC Link is Up <1000 Mbps Full Duplex>
Sep 20 13:33:00 hanna-PC kernel: [  114.480834] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> Auto-activating connection '&#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1'.
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> Activation (eth0) starting connection '&#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1'
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> NetworkManager state is now CONNECTING
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> dhclient started with pid 1906
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> Activation (eth0) Beginning IP6 addrconf.
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep 20 13:33:00 hanna-PC dhclient: Internet Systems Consortium DHCP Client 4.2.4
Sep 20 13:33:00 hanna-PC dhclient: Copyright 2004-2012 Internet Systems Consortium.
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Sep 20 13:33:00 hanna-PC dhclient: Listening on LPF/eth0/00:22:15:cc:99:11
Sep 20 13:33:00 hanna-PC dhclient: Sending on   LPF/eth0/00:22:15:cc:99:11
Sep 20 13:33:00 hanna-PC dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x6b71c2eb)
Sep 20 13:33:00 hanna-PC dhclient: DHCPREQUEST of 192.168.0.104 on eth0 to 255.255.255.255 port 67 (xid=0x6b71c2eb)
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> (eth0): DHCPv4 state changed preinit -> bound
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info>   address 192.168.0.104
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info>   prefix 24 (255.255.255.0)
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info>   gateway 192.168.0.1
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info>   nameserver '192.168.0.1'
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 20 13:33:00 hanna-PC NetworkManager[727]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Sep 20 13:33:00 hanna-PC avahi-daemon[710]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.104.
Sep 20 13:33:00 hanna-PC avahi-daemon[710]: New relevant interface eth0.IPv4 for mDNS.
Sep 20 13:33:00 hanna-PC avahi-daemon[710]: Registering new address record for 192.168.0.104 on eth0.IPv4.
Sep 20 13:33:01 hanna-PC NetworkManager[727]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Sep 20 13:33:01 hanna-PC NetworkManager[727]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 20 13:33:01 hanna-PC NetworkManager[727]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Sep 20 13:33:01 hanna-PC NetworkManager[727]: <info> NetworkManager state is now CONNECTED_GLOBAL
Sep 20 13:33:01 hanna-PC NetworkManager[727]: <info> Policy set '&#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1' (eth0) as default for IPv4 routing and DNS.
Sep 20 13:33:01 hanna-PC NetworkManager[727]: <info> DNS: starting dnsmasq...
Sep 20 13:33:01 hanna-PC NetworkManager[727]: <warn> dnsmasq not available on the bus, can't update servers.
Sep 20 13:33:01 hanna-PC NetworkManager[727]: <error> [1411209181.632530] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Sep 20 13:33:01 hanna-PC NetworkManager[727]: <warn> DNS: plugin dnsmasq update failed
Sep 20 13:33:01 hanna-PC NetworkManager[727]: <info> Writing DNS information to /sbin/resolvconf
Sep 20 13:33:02 hanna-PC NetworkManager[727]: <info> Activation (eth0) successful, device activated.
Sep 20 13:33:02 hanna-PC NetworkManager[727]: <warn> dnsmasq appeared on DBus: :1.61
Sep 20 13:33:02 hanna-PC NetworkManager[727]: <info> Writing DNS information to /sbin/resolvconf
Sep 20 13:33:02 hanna-PC avahi-daemon[710]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::222:15ff:fecc:9911.
Sep 20 13:33:02 hanna-PC avahi-daemon[710]: New relevant interface eth0.IPv6 for mDNS.
Sep 20 13:33:02 hanna-PC avahi-daemon[710]: Registering new address record for fe80::222:15ff:fecc:9911 on eth0.*.
Sep 20 13:33:20 hanna-PC NetworkManager[727]: <info> (eth0): IP6 addrconf timed out or failed.
Sep 20 13:33:20 hanna-PC NetworkManager[727]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 20 13:33:20 hanna-PC NetworkManager[727]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 20 13:33:20 hanna-PC NetworkManager[727]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Sep 20 16:33:23 hanna-PC kernel: [    0.093204] NET: Registered protocol family 16
Sep 20 16:33:23 hanna-PC kernel: [    0.107611] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
Sep 20 16:33:23 hanna-PC kernel: [    0.110123] pci 0000:03:00.0: [0000:002d] type 00 class 0x028000
Sep 20 16:33:23 hanna-PC kernel: [    0.110142] pci 0000:03:00.0: reg 0x10: [mem 0xfebf0000-0xfebfffff]
Sep 20 16:33:23 hanna-PC kernel: [    0.116594] NetLabel: Initializing
Sep 20 16:33:23 hanna-PC kernel: [    0.116596] NetLabel:  domain hash size = 128
Sep 20 16:33:23 hanna-PC kernel: [    0.116597] NetLabel:  protocols = UNLABELED CIPSOv4
Sep 20 16:33:23 hanna-PC kernel: [    0.116612] NetLabel:  unlabeled traffic allowed by default
Sep 20 16:33:23 hanna-PC kernel: [    0.132165] NET: Registered protocol family 2
Sep 20 16:33:23 hanna-PC kernel: [    0.133095] NET: Registered protocol family 1
Sep 20 16:33:23 hanna-PC kernel: [    0.472494] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Sep 20 16:33:23 hanna-PC kernel: [    0.472808] audit: initializing netlink socket (disabled)
Sep 20 16:33:23 hanna-PC kernel: [    0.653328] NET: Registered protocol family 10
Sep 20 16:33:23 hanna-PC kernel: [    0.653514] NET: Registered protocol family 17
Sep 20 16:33:23 hanna-PC kernel: [    4.800103] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 20 16:33:23 hanna-PC kernel: [    5.110328] type=1400 audit(1411219995.946:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=327 comm="apparmor_parser"
Sep 20 16:33:23 hanna-PC kernel: [    5.110778] type=1400 audit(1411219995.946:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=327 comm="apparmor_parser"
Sep 20 16:33:23 hanna-PC kernel: [   12.154965] type=1400 audit(1411220002.990:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=672 comm="apparmor_parser"
Sep 20 16:33:23 hanna-PC kernel: [   12.155406] type=1400 audit(1411220002.990:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=672 comm="apparmor_parser"
Sep 20 16:33:23 hanna-PC kernel: [   13.108568] NET: Registered protocol family 31
Sep 20 16:33:23 hanna-PC kernel: [   13.116055] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Sep 20 16:33:24 hanna-PC avahi-daemon[945]: Network interface enumeration completed.
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> NetworkManager (version 0.9.8.8) is starting...
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> WEXT support is enabled
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> DNS: loaded plugin dnsmasq
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    SCPlugin-Ifupdown: init!
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    SCPlugin-Ifupdown: update_system_hostname
Sep 20 16:33:25 hanna-PC NetworkManager[975]:       interface-parser: parsing file /etc/network/interfaces
Sep 20 16:33:25 hanna-PC NetworkManager[975]:       interface-parser: finished parsing file /etc/network/interfaces
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    SCPluginIfupdown: management mode: unmanaged
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0)
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    SCPlugin-Ifupdown: end _init.
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    SCPlugin-Ofono: init!
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    SCPlugin-Ofono: end _init.
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Loaded plugin (null): (null)
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    Ifupdown: get unmanaged devices count: 0
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    SCPlugin-Ifupdown: (34206480) ... get_connections.
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    SCPlugin-Ifupdown: (34206480) ... get_connections (managed=false): return empty list.
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    SCPlugin-Ofono: (33989056) ... get_connections.
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    SCPlugin-Ofono: (33989056) connections count: 0
Sep 20 16:33:25 hanna-PC NetworkManager[975]:    Ifupdown: get unmanaged devices count: 0
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> monitoring kernel firmware directory '/lib/firmware'.
Sep 20 16:33:25 hanna-PC whoopsie[987]: Could not get the Network Manager state:
Sep 20 16:33:25 hanna-PC whoopsie[987]: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> WiFi enabled by radio killswitch; enabled by state file
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> WWAN enabled by radio killswitch; enabled by state file
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> WiMAX enabled by radio killswitch; enabled by state file
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Networking is enabled by state file
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <warn> failed to allocate link cache: (-12) Object not found
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> (eth0): carrier is OFF
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> (eth0): new Ethernet device (driver: 'ATL1E' ifindex: 2)
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> (eth0): bringing up device.
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> (eth0): carrier now ON (device state 20)
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> (eth0): preparing device.
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> (eth0): deactivating device (reason 'managed') [2]
Sep 20 16:33:25 hanna-PC kernel: [   14.582711] ATL1E 0000:01:00.0 eth0: NIC Link is Up <1000 Mbps Full Duplex>
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Added default wired connection '&#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1' for /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> (eth0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> urfkill disappeared from the bus
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Auto-activating connection '&#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1'.
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Activation (eth0) starting connection '&#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1'
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> NetworkManager state is now CONNECTING
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> ModemManager available in the bus
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> dhclient started with pid 998
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Activation (eth0) Beginning IP6 addrconf.
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep 20 16:33:25 hanna-PC dhclient: Internet Systems Consortium DHCP Client 4.2.4
Sep 20 16:33:25 hanna-PC dhclient: Copyright 2004-2012 Internet Systems Consortium.
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Sep 20 16:33:25 hanna-PC dhclient: Listening on LPF/eth0/00:22:15:cc:99:11
Sep 20 16:33:25 hanna-PC dhclient: Sending on   LPF/eth0/00:22:15:cc:99:11
Sep 20 16:33:25 hanna-PC dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x31bfbb37)
Sep 20 16:33:25 hanna-PC dhclient: DHCPREQUEST of 192.168.0.104 on eth0 to 255.255.255.255 port 67 (xid=0x31bfbb37)
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> (eth0): DHCPv4 state changed preinit -> bound
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info>   address 192.168.0.104
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info>   prefix 24 (255.255.255.0)
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info>   gateway 192.168.0.1
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info>   nameserver '192.168.0.1'
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 20 16:33:25 hanna-PC NetworkManager[975]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Sep 20 16:33:25 hanna-PC avahi-daemon[945]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.104.
Sep 20 16:33:25 hanna-PC avahi-daemon[945]: New relevant interface eth0.IPv4 for mDNS.
Sep 20 16:33:25 hanna-PC avahi-daemon[945]: Registering new address record for 192.168.0.104 on eth0.IPv4.
Sep 20 16:33:26 hanna-PC NetworkManager[975]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Sep 20 16:33:26 hanna-PC NetworkManager[975]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 20 16:33:26 hanna-PC NetworkManager[975]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Sep 20 16:33:26 hanna-PC NetworkManager[975]: <info> NetworkManager state is now CONNECTED_GLOBAL
Sep 20 16:33:26 hanna-PC NetworkManager[975]: <info> Policy set '&#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1' (eth0) as default for IPv4 routing and DNS.
Sep 20 16:33:26 hanna-PC NetworkManager[975]: <info> DNS: starting dnsmasq...
Sep 20 16:33:26 hanna-PC NetworkManager[975]: <warn> dnsmasq not available on the bus, can't update servers.
Sep 20 16:33:26 hanna-PC NetworkManager[975]: <error> [1411220006.851378] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Sep 20 16:33:26 hanna-PC NetworkManager[975]: <warn> DNS: plugin dnsmasq update failed
Sep 20 16:33:26 hanna-PC NetworkManager[975]: <info> Writing DNS information to /sbin/resolvconf
Sep 20 16:33:27 hanna-PC avahi-daemon[945]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::222:15ff:fecc:9911.
Sep 20 16:33:27 hanna-PC avahi-daemon[945]: New relevant interface eth0.IPv6 for mDNS.
Sep 20 16:33:27 hanna-PC avahi-daemon[945]: Registering new address record for fe80::222:15ff:fecc:9911 on eth0.*.
Sep 20 16:33:29 hanna-PC NetworkManager[975]: <info> Activation (eth0) successful, device activated.
Sep 20 16:33:29 hanna-PC NetworkManager[975]: <warn> dnsmasq appeared on DBus: :1.20
Sep 20 16:33:29 hanna-PC NetworkManager[975]: <info> Writing DNS information to /sbin/resolvconf
Sep 20 16:33:35 hanna-PC NetworkManager[975]: <info> WiFi hardware radio set enabled
Sep 20 16:33:45 hanna-PC NetworkManager[975]: <info> (eth0): IP6 addrconf timed out or failed.
Sep 20 16:33:45 hanna-PC NetworkManager[975]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 20 16:33:45 hanna-PC NetworkManager[975]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 20 16:33:45 hanna-PC NetworkManager[975]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
```

lsmod output:
```
Module                  Size  Used by
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391136  10 bnep,rfcomm
joydev                 17381  0 
hid_generic            12548  0 
snd_hda_codec_via      27860  1 
snd_hda_intel          56451  3 
snd_hda_codec         192906  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
coretemp               13435  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
serio_raw              13462  0 
lpc_ich                21080  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69322  16 snd_hwdep,snd_timer,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
i915                  783805  3 
video                  19476  1 i915
drm_kms_helper         53081  1 i915
drm                   303102  4 i915,drm_kms_helper
soundcore              12680  1 snd
i2c_algo_bit           13413  1 i915
asus_atk0110           18657  0 
parport_pc             32701  1 
ppdev                  17671  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
psmouse               106678  0 
floppy                 69418  0 
atl1e                  42380  0 

```

what do I need to do with this: [http://kernel.ubuntu.com/~kernel-ppa...3.16.3-utopic/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.16.3-utopic/") ? How do I apply this?

---

