---
title: "Stuck on 10 mb/s after lightning strike"
date: 2015-05-22
forum: Networking &amp; Wireless
---

### Post by manny9 on 2015-05-22
I was getting mb/s but now none of the command work:
code:
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
sudo ethtool -s eth0 speed 100 duplex half autoneg off
```

The lightning strike disabled the port,so i had to manually set it back using
```
gksudo gedit /etc/rc.local
```

Now i cant play any game's cause alot of stuttering with 10 mb/s can anyone help me, i've heard unplugging the pc work's but it didn't for me, i know i was getting 100 mb/s before is there a way to completely restore my pc to all default setting's i can even do a fresh install the thing also is i dont get internet in my bios setting's like i could before seem's the ethernet port is disabled still without help from terminal

---

### Post by tgalati4 on 2015-05-22
Unfortunately, lighting strikes can send voltage spikes through the telephone and cable lines and damage your router and network card.  It's possible that your router is damaged.  Try a different port.  Try a new router.  Although better quality, business-grade routers and network cards use optical isolation, consumer-grade equipment does not and is subject to the 30-volt limitation that most electronic components can tolerate.

---

### Post by manny9 on 2015-05-23
I'm thinking it's the computer because the ethernet port stopped working completly it got disabled , i had to manually set it back,it still isnt enabled properly cause i dont get internet access in Bios so that means it's only enabled after booting up an operating system because i saved it in setting's i was wondering if anyone would recommend a complete reinstall of my system or reset like, cmos and everything to get it like a new computer again? maybe that will work?cause i reinstalled ubuntu twice and still had to manually  put in 
sudo ethtool -s eth0 speed 10 duplex half autoneg on
everytime,someone please recommend what i should do because i dont care about files im willing to fresh install just to get everything back to normal
so yeah i doubt it's the router

---

### Post by tgalati4 on 2015-05-23
Look for errors in /var/log/syslog during bootup.  Post any messages related to the network card.

```
more /var/log/syslog
```

Spacebar to page forward, "q" to quit.

---

### Post by manny9 on 2015-05-23
Sorry for the delay copied everything after a reboot, that has to do with network manager
```
[SIZE=1]May 23 16:42:00 manny NetworkManager[926]: <info> NetworkManager (version 0.9.8.8) is starting...
May 23 16:42:00 manny NetworkManager[926]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
May 23 16:42:00 manny NetworkManager[926]: <info> WEXT support is enabled
May 23 16:42:00 manny NetworkManager[926]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
May 23 16:42:00 manny NetworkManager[926]: <info> DNS: loaded plugin dnsmasq
May 23 16:42:00 manny polkitd[928]: started daemon version 0.105 using authority implementation `local' version `0.105'
May 23 16:42:01 manny dbus[730]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
May 23 16:42:01 manny NetworkManager[926]:    SCPlugin-Ifupdown: init!
May 23 16:42:01 manny NetworkManager[926]:    SCPlugin-Ifupdown: update_system_hostname
May 23 16:42:01 manny NetworkManager[926]:       interface-parser: parsing file /etc/network/interfaces
May 23 16:42:01 manny NetworkManager[926]:       interface-parser: finished parsing file /etc/network/interfaces
May 23 16:42:01 manny NetworkManager[926]:    SCPluginIfupdown: management mode: unmanaged
May 23 16:42:01 manny NetworkManager[926]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/
0000:02:00.0/net/eth0, iface: eth0)
May 23 16:42:01 manny NetworkManager[926]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0
000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
May 23 16:42:01 manny NetworkManager[926]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: l
o)
May 23 16:42:01 manny NetworkManager[926]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo
): no ifupdown configuration found.
May 23 16:42:01 manny NetworkManager[926]:    SCPlugin-Ifupdown: end _init.
May 23 16:42:01 manny NetworkManager[926]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please us
e the NetworkManager mailing list.
May 23 16:42:01 manny NetworkManager[926]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs plea
se use the NetworkManager mailing list.
May 23 16:42:01 manny NetworkManager[926]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
May 23 16:42:01 manny NetworkManager[926]:    SCPlugin-Ofono: init!
May 23 16:42:01 manny NetworkManager[926]:    SCPlugin-Ofono: end _init.
May 23 16:42:01 manny NetworkManager[926]: <info> Loaded plugin (null): (null)
May 23 16:42:01 manny NetworkManager[926]:    Ifupdown: get unmanaged devices count: 0
May 23 16:42:01 manny NetworkManager[926]:    SCPlugin-Ifupdown: (32260880) ... get_connections.
May 23 16:42:01 manny NetworkManager[926]:    SCPlugin-Ifupdown: (32260880) ... get_connections (managed=false): return emp
ty list.
May 23 16:42:01 manny NetworkManager[926]:    keyfile: parsing Wired connection 1 ... 
May 23 16:42:01 manny NetworkManager[926]:    keyfile:     read connection 'Wired connection 1'
May 23 16:42:01 manny NetworkManager[926]:    SCPlugin-Ofono: (-1342160528) ... get_connections.
May 23 16:42:01 manny NetworkManager[926]:    SCPlugin-Ofono: (-1342160528) connections count: 0
May 23 16:42:01 manny NetworkManager[926]:    Ifupdown: get unmanaged devices count: 0
May 23 16:42:01 manny cron[972]: (CRON) INFO (pidfile fd = 3)
May 23 16:42:01 manny dbus[730]: [system] Activating service name='org.freedesktop.login1' (using servicehelper)
May 23 16:42:01 manny anacron[1068]: Anacron 2.3 started on 2015-05-23
May 23 16:42:01 manny cron[1083]: (CRON) STARTUP (fork ok)
May 23 16:42:01 manny acpid: starting up with netlink and the input layer
May 23 16:42:01 manny cron[1083]: (CRON) INFO (Running @reboot jobs)
May 23 16:42:01 manny anacron[1068]: Normal exit (0 jobs run)
May 23 16:42:01 manny dbus[730]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
May 23 16:42:01 manny dbus[730]: [system] Successfully activated service 'org.freedesktop.systemd1'
May 23 16:42:01 manny dbus[730]: [system] Successfully activated service 'org.freedesktop.login1'
May 23 16:42:01 manny ntpdate[1134]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
May 23 16:42:01 manny ntpdate[1134]: no servers can be used, exiting
May 23 16:42:01 manny NetworkManager[926]: <info> monitoring kernel firmware directory '/lib/firmware'.
May 23 16:42:02 manny NetworkManager[926]: <info> WiFi enabled by radio killswitch; enabled by state file
May 23 16:42:02 manny NetworkManager[926]: <info> WWAN enabled by radio killswitch; enabled by state file
May 23 16:42:02 manny NetworkManager[926]: <info> WiMAX enabled by radio killswitch; enabled by state file
May 23 16:42:02 manny NetworkManager[926]: <info> Networking is enabled by state file
May 23 16:42:02 manny NetworkManager[926]: <warn> failed to allocate link cache: (-26) Protocol mismatch
May 23 16:42:02 manny NetworkManager[926]: <info> (eth0): carrier is OFF
May 23 16:42:02 manny NetworkManager[926]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
May 23 16:42:02 manny NetworkManager[926]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
May 23 16:42:02 manny NetworkManager[926]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') 
[10 20 2]
May 23 16:42:02 manny NetworkManager[926]: <info> (eth0): bringing up device.
May 23 16:42:02 manny acpid: 11 rules loaded
May 23 16:42:02 manny acpid: waiting for events: event logging is off
May 23 16:42:02 manny NetworkManager[926]: <info> (eth0): preparing device.
May 23 16:42:02 manny NetworkManager[926]: <info> (eth0): deactivating device (reason 'managed') [2]
May 23 16:42:02 manny NetworkManager[926]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring..
.
May 23 16:42:02 manny kernel: [   16.508337] r8169 0000:02:00.0 eth0: link down
May 23 16:42:02 manny kernel: [   16.508354] r8169 0000:02:00.0 eth0: link down
May 23 16:42:02 manny kernel: [   16.508392] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
May 23 16:42:02 manny NetworkManager[926]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring..
.
May 23 16:42:02 manny NetworkManager[926]: <info> urfkill disappeared from the bus
May 23 16:42:02 manny NetworkManager[926]: <info> ModemManager available in the bus
May 23 16:42:03 manny ModemManager[751]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:04.0/
0000:02:00.0': not supported by any plugin
May 23 16:42:03 manny atieventsd[1260]: ATI External Events Daemon started...
May 23 16:42:03 manny atieventsd[1260]: Event daemon control socket created
May 23 16:42:03 manny atieventsd[1260]: acpid connection established
May 23 16:42:03 manny acpid: client connected from 1260[0:0]
May 23 16:42:03 manny acpid: 1 client rule loaded
May 23 16:42:06 manny kernel: [   20.536622] r8169 0000:02:00.0 eth0: link up
May 23 16:42:06 manny kernel: [   20.536632] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May 23 16:42:06 manny NetworkManager[926]: <info> (eth0): carrier now ON (device state 20)
May 23 16:42:06 manny NetworkManager[926]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier
-changed') [20 30 40]
May 23 16:42:06 manny NetworkManager[926]: <info> Auto-activating connection 'Wired connection 1'.
May 23 16:42:06 manny NetworkManager[926]: <info> Activation (eth0) starting connection 'Wired connection 1'
May 23 16:42:06 manny NetworkManager[926]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 
40 0]
May 23 16:42:06 manny NetworkManager[926]: <info> NetworkManager state is now CONNECTING
May 23 16:42:06 manny NetworkManager[926]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
May 23 16:42:06 manny NetworkManager[926]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
May 23 16:42:06 manny NetworkManager[926]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
May 23 16:42:06 manny NetworkManager[926]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
May 23 16:42:06 manny NetworkManager[926]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
May 23 16:42:06 manny NetworkManager[926]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
May 23 16:42:06 manny NetworkManager[926]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
May 23 16:42:06 manny NetworkManager[926]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
May 23 16:42:06 manny NetworkManager[926]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
May 23 16:42:06 manny NetworkManager[926]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
May 23 16:42:06 manny NetworkManager[926]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0
]
May 23 16:42:06 manny NetworkManager[926]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 23 16:42:06 manny NetworkManager[926]: <info> dhclient started with pid 1375
May 23 16:42:06 manny NetworkManager[926]: <info> Activation (eth0) Beginning IP6 addrconf.
May 23 16:42:06 manny NetworkManager[926]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May 23 16:42:06 manny dhclient: Internet Systems Consortium DHCP Client 4.2.4
May 23 16:42:06 manny dhclient: Copyright 2004-2012 Internet Systems Consortium.
May 23 16:42:06 manny dhclient: All rights reserved.
May 23 16:42:06 manny dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
May 23 16:42:06 manny dhclient: 
May 23 16:42:06 manny NetworkManager[926]: <info> (eth0): DHCPv4 state changed nbi -> preinit
May 23 16:42:06 manny dhclient: Listening on LPF/eth0/bc:5f:f4:f1:0f:b7
May 23 16:42:06 manny dhclient: Sending on   LPF/eth0/bc:5f:f4:f1:0f:b7
May 23 16:42:06 manny dhclient: Sending on   Socket/fallback
May 23 16:42:06 manny dhclient: DHCPREQUEST of 192.168.0.103 on eth0 to 255.255.255.255 port 67 (xid=0x182e5b95)
May 23 16:42:06 manny dhclient: DHCPACK of 192.168.0.103 from 192.168.0.1
May 23 16:42:06 manny dhclient: bound to 192.168.0.103 -- renewal in 34561 seconds.
May 23 16:42:06 manny NetworkManager[926]: <info> (eth0): DHCPv4 state changed preinit -> reboot
May 23 16:42:06 manny NetworkManager[926]: <info>   address 192.168.0.103
May 23 16:42:06 manny NetworkManager[926]: <info>   prefix 24 (255.255.255.0)
May 23 16:42:06 manny NetworkManager[926]: <info>   gateway 192.168.0.1
May 23 16:42:06 manny NetworkManager[926]: <info>   nameserver '192.168.0.1'
May 23 16:42:06 manny NetworkManager[926]: <info>   domain name 'mami'
May 23 16:42:06 manny NetworkManager[926]: <info>   wins '192.168.0.1'
May 23 16:42:06 manny NetworkManager[926]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 23 16:42:06 manny NetworkManager[926]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
May 23 16:42:06 manny avahi-daemon[797]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.103.
May 23 16:42:06 manny avahi-daemon[797]: New relevant interface eth0.IPv4 for mDNS.
May 23 16:42:06 manny avahi-daemon[797]: Registering new address record for 192.168.0.103 on eth0.IPv4.
May 23 16:42:07 manny NetworkManager[926]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70
 90 0]
May 23 16:42:07 manny NetworkManager[926]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
May 23 16:42:07 manny NetworkManager[926]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90
 100 0]
May 23 16:42:07 manny NetworkManager[926]: <info> NetworkManager state is now CONNECTED_GLOBAL
May 23 16:42:07 manny NetworkManager[926]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DN
S.
May 23 16:42:07 manny NetworkManager[926]: <info> DNS: starting dnsmasq...
May 23 16:42:07 manny NetworkManager[926]: <warn> dnsmasq not available on the bus, can't update servers.
May 23 16:42:07 manny NetworkManager[926]: <error> [1432413727.904790] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not f
ound on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
May 23 16:42:07 manny NetworkManager[926]: <warn> DNS: plugin dnsmasq update failed
May 23 16:42:07 manny NetworkManager[926]: <info> Writing DNS information to /sbin/resolvconf[/SIZE]
```

---

### Post by tgalati4 on 2015-05-23
If your BIOS does not recognize your network card, then that could indicate damage to the card due to a lightning strike.  If your card still works at 10 mbits/sec, then you are lucky.  Typically lightning-induced voltage spikes kill the card completely.  A configuration file will not bring your card back to 100 mbits/sec.  If it is damaged, then your only recourse is to buy a network card that fits your computer slot.  If this is a laptop, then you might have to use a USB-to-ethernet adapter.

There is nothing helpful in your log file, other than it shows that the link is down (eth0) and then comes up in manual mode--probably after forcing 10 mbit/sec mode using /etc/rc.local script.

Try changing the cable and the router port to see if the behavior changes.

---

