---
title: "SettingsPlugin-Ofono: file doesn't exist: /var/lib/ofono"
date: 2018-07-12
forum: Networking &amp; Wireless
---

### Post by rgrune on 2018-07-12
Hi,
 I use ubuntu 16.04 LTS, and I think I had a problem when the computer was installing some updatings, I'm not sure if I turned my computer off when they were being installed. Now the problem is that when I turned the computer on I can't get any wifi network. I´ve tried some solution that were suggested by some forums but any of those works :(
I thank in advance if someone could give me some help about this issue.
Anyway I can mention some of them:

iwconfig
> lo        no wireless extensions.

enp7s0    no wireless extensions.

ifconfig
> enp7s0    Link encap:Ethernet  HWaddr b8:2a:72:b5:8d:ce  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:19780 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19780 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1489296 (1.4 MB)  TX bytes:1489296 (1.4 MB)

netstat -r
> Kernel IP routing table
Destination      Gateway          Genmask          Flags    MSS  Window   irtt  Iface

route
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

systemctl status NetworkManager.service
> &#9679; NetworkManager.service - Network Manager
   Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
   Active: active (running) since jue 2018-07-12 10:28:17 -04; 5h 33min ago
     Docs: man:NetworkManager(8)
  Process: 3289 ExecReload=/bin/kill -HUP $MAINPID (code=exited, status=0/SUCCESS)
 Main PID: 3258 (NetworkManager)
   CGroup: /system.slice/NetworkManager.service
           &#9500;&#9472;3258 /usr/sbin/NetworkManager --no-daemon
           &#9492;&#9472;3290 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/NetworkManager/dnsmasq.pid 

jul 12 10:48:38 raul-Inspiron-3442 NetworkManager[3258]: <info>  [1531406918.6110] keyfile: update /etc/NetworkManager/system-connections/ARICA (
jul 12 10:48:38 raul-Inspiron-3442 NetworkManager[3258]: <info>  [1531406918.6117] audit: op="connection-update" uuid="78567526-99e9-42de-9768-b8
jul 12 11:25:17 raul-Inspiron-3442 NetworkManager[3258]: <info>  [1531409117.6809] manager: sleep requested (sleeping: no  enabled: yes)
jul 12 11:25:17 raul-Inspiron-3442 NetworkManager[3258]: <info>  [1531409117.6809] manager: sleeping...
jul 12 11:25:17 raul-Inspiron-3442 NetworkManager[3258]: <info>  [1531409117.6810] device (enp7s0): state change: unavailable -> unmanaged (reaso
jul 12 11:25:17 raul-Inspiron-3442 NetworkManager[3258]: <info>  [1531409117.7049] manager: NetworkManager state is now ASLEEP
jul 12 14:51:00 raul-Inspiron-3442 NetworkManager[3258]: <info>  [1531421460.3830] manager: wake requested (sleeping: yes  enabled: yes)
jul 12 14:51:00 raul-Inspiron-3442 NetworkManager[3258]: <info>  [1531421460.3830] manager: waking up...
jul 12 14:51:00 raul-Inspiron-3442 NetworkManager[3258]: <info>  [1531421460.3831] device (enp7s0): state change: unmanaged -> unavailable (reaso
jul 12 14:51:00 raul-Inspiron-3442 NetworkManager[3258]: <info>  [1531421460.5685] manager: NetworkManager state is now DISCONNECTED

journal ctl -xe
> jul 12 10:43:42 raul-Inspiron-3442 pkexec[3427]: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
jul 12 10:43:42 raul-Inspiron-3442 pkexec[3427]: pam_systemd(polkit-1:session): Cannot create session: Already running in a session
jul 12 10:43:42 raul-Inspiron-3442 pkexec[3427]: raul: Executing command [USER=root] [TTY=unknown] [CWD=/home/raul] [COMMAND=/usr/lib/unity-setti
jul 12 10:44:21 raul-Inspiron-3442 org.gnome.evolution.dataserver.Sources5[1408]: ** (evolution-source-registry:1698): WARNING **: secret_service
jul 12 10:48:05 raul-Inspiron-3442 dbus[861]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedeskto
jul 12 10:48:05 raul-Inspiron-3442 systemd[1]: Starting Hostname Service...
-- Subject: Unit systemd-hostnamed.service has begun start-up
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
-- 
-- Unit systemd-hostnamed.service has begun starting up.
jul 12 10:48:05 raul-Inspiron-3442 dbus[861]: [system] Successfully activated service 'org.freedesktop.hostname1'
jul 12 10:48:05 raul-Inspiron-3442 systemd[1]: Started Hostname Service.
-- Subject: Unit systemd-hostnamed.service has finished start-up
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
-- 
-- Unit systemd-hostnamed.service has finished starting up.
-- 
-- The start-up result is done.
jul 12 10:48:05 raul-Inspiron-3442 org.gtk.vfs.Daemon[1408]: ** (process:1846): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumera
jul 12 10:48:05 raul-Inspiron-3442 org.gtk.vfs.Daemon[1408]: ** (process:1846): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumera
jul 12 10:48:05 raul-Inspiron-3442 org.gtk.vfs.Daemon[1408]: ** (process:1846): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumera
jul 12 10:48:05 raul-Inspiron-3442 org.gtk.vfs.Daemon[1408]: ** (process:1846): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumera
jul 12 10:48:05 raul-Inspiron-3442 org.gtk.vfs.Daemon[1408]: ** (process:1846): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumera
jul 12 10:48:05 raul-Inspiron-3442 org.gtk.vfs.Daemon[1408]: ** (process:1846): WARNING **: send_done_cb: No such interface 'org.gtk.vfs.Enumerat
jul 12 10:48:10 raul-Inspiron-3442 NetworkManager[3258]: <info>  [1531406890.8139] keyfile: update /etc/NetworkManager/system-connections/ARICA (
jul 12 10:48:10 raul-Inspiron-3442 NetworkManager[3258]: <info>  [1531406890.8147] audit: op="connection-update" uuid="78567526-99e9-42de-9768-b8
jul 12 10:48:24 raul-Inspiron-3442 gnome-session[1559]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
jul 12 10:48:30 raul-Inspiron-3442 gnome-session[1559]: ** Message: Cannot save connection due to error: Editor initializing...
jul 12 10:48:30 raul-Inspiron-3442 gnome-session[1559]: ** Message: Connection validates and can be saved
jul 12 10:48:30 raul-Inspiron-3442 org.gtk.vfs.Daemon[1408]: ** (process:1846): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumera
jul 12 10:48:30 raul-Inspiron-3442 org.gtk.vfs.Daemon[1408]: ** (process:1846): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumera
jul 12 10:48:30 raul-Inspiron-3442 org.gtk.vfs.Daemon[1408]: ** (process:1846): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumera
jul 12 10:48:30 raul-Inspiron-3442 org.gtk.vfs.Daemon[1408]: ** (process:1846): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumera
jul 12 10:48:30 raul-Inspiron-3442 org.gtk.vfs.Daemon[1408]: ** (process:1846): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumera
jul 12 10:48:30 raul-Inspiron-3442 org.gtk.vfs.Daemon[1408]: ** (process:1846): WARNING **: send_done_cb: No such interface 'org.gtk.vfs.Enumerat
jul 12 10:48:38 raul-Inspiron-3442 NetworkManager[3258]: <info>  [1531406918.6110] keyfile: update /etc/NetworkManager/system-connections/ARICA (
jul 12 10:48:38 raul-Inspiron-3442 NetworkManager[3258]: <info>  [1531406918.6117] audit: op="connection-update" uuid="78567526-99e9-42de-9768-b8
jul 12 10:54:56 raul-Inspiron-3442 sudo[3560]:     raul : TTY=pts/4 ; PWD=/home/raul ; USER=root ; COMMAND=/bin/systemctl -l status NetworkManage
jul 12 10:54:56 raul-Inspiron-3442 sudo[3560]: pam_unix(sudo:session): session opened for user root by (uid=0)
jul 12 10:55:05 raul-Inspiron-3442 sudo[3560]: pam_unix(sudo:session): session closed for user root

journalctl -u NetworkManager
> jul 12 09:43:05 raul-Inspiron-3442 systemd[1]: Starting Network Manager...
jul 12 09:43:07 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402987.5515] NetworkManager (version 1.2.6) is starting...
jul 12 09:43:07 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402987.5517] Read config: /etc/NetworkManager/NetworkManager.conf (etc: defa
jul 12 09:43:07 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402987.7711] manager[0xcec1c0]: monitoring kernel firmware directory '/lib/f
jul 12 09:43:07 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402987.7712] monitoring ifupdown state file '/run/network/ifstate'.
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.0619] dns-mgr[0xccb950]: init: dns=dnsmasq, rc-manager=resolvconf, pl
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.1648] rfkill0: found WiFi radio killswitch (at /sys/devices/LNXSYSTM:
jul 12 09:43:08 raul-Inspiron-3442 systemd[1]: Started Network Manager.
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.6479] init!
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.6481]       interface-parser: parsing file /etc/network/interfaces
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.6481]       interface-parser: finished parsing file /etc/network/inte
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.6481] management mode: managed
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.6486] devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.6486] device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:0
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.6486] devices added (path: /sys/devices/virtual/net/lo, iface: lo)
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.6486] device added (path: /sys/devices/virtual/net/lo, iface: lo): no
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.6486] end _init.
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.6487] settings: loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To r
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.6487] settings: loaded plugin keyfile: (c) 2007 - 2015 Red Hat, Inc. 
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.6490] SettingsPlugin-Ofono: init!
**jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <warn>  [1531402988.6490] SettingsPlugin-Ofono: file doesn't exist: /var/lib/ofono (intentionally in bold)**
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.6490] SettingsPlugin-Ofono: end _init.
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.6490] settings: loaded plugin ofono: (C) 2013-2016 Canonical Ltd.  To
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.6491] (13747104) ... get_connections.
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.6491] (13747104) connections count: 0
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.7155] keyfile: new connection /etc/NetworkManager/system-connections/
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.7569] keyfile: new connection /etc/NetworkManager/system-connections/
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.7674] keyfile: new connection /etc/NetworkManager/system-connections/
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.7778] keyfile: new connection /etc/NetworkManager/system-connections/
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.7882] keyfile: new connection /etc/NetworkManager/system-connections/
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.7986] keyfile: new connection /etc/NetworkManager/system-connections/
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.8091] keyfile: new connection /etc/NetworkManager/system-connections/
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.8199] keyfile: new connection /etc/NetworkManager/system-connections/
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.8302] keyfile: new connection /etc/NetworkManager/system-connections/
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.8406] keyfile: new connection /etc/NetworkManager/system-connections/
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.8507] keyfile: new connection /etc/NetworkManager/system-connections/
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.8611] keyfile: new connection /etc/NetworkManager/system-connections/
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.8716] keyfile: new connection /etc/NetworkManager/system-connections/
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.8747] SettingsPlugin-Ofono: (13747328) ... get_connections.
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.8747] SettingsPlugin-Ofono: (13747328) connections count: 0
jul 12 09:43:08 raul-Inspiron-3442 NetworkManager[933]: <info>  [1531402988.8761] settings: hostname: using hostnamed

sudo lshw -class network
 > *-network UNCLAIMED     
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f7d00000-f7d07fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: enp7s0
       version: 07
       serial: b8:2a:72:b5:8d:ce
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:e000(size=256) memory:f7c00000-f7c00fff memory:f0000000-f0003fff

sudo /usr/sbin/NetworkManager -d
> NetworkManager[3956]: <info>  [1531408848.9363] NetworkManager (version 1.2.6) is starting...
NetworkManager[3956]: <info>  [1531408848.9364] Read config: /etc/NetworkManager/NetworkManager.conf (etc: default-wifi-powersave-on.conf)
NetworkManager[3956]: <info>  [1531408848.9391] manager[0x284f1c0]: monitoring kernel firmware directory '/lib/firmware'.
NetworkManager[3956]: <info>  [1531408848.9392] monitoring ifupdown state file '/run/network/ifstate'.
NetworkManager[3956]: <info>  [1531408848.9409] dns-mgr[0x284a160]: init: dns=dnsmasq, rc-manager=resolvconf, plugin=dnsmasq
NetworkManager[3956]: <info>  [1531408848.9422] rfkill0: found WiFi radio killswitch (at /sys/devices/LNXSYSTM:00/LNXSYBUS:00/DELLABCE:00/rfkill/rfkill0) (platform driver dell-rbtn)
NetworkManager[3956]: <error> [1531408848.9432] bus-manager: could not acquire the NetworkManager service as it is already taken
NetworkManager[3956]: <error> [1531408848.9432] failed to start the dbus service.
NetworkManager[3956]: <info>  [1531408848.9432] exiting (error)

---

### Post by chili555 on 2018-07-12
Until you solve this, there can never be any wireless connection, and trying to debug Network Manager is useless. NM has no wireless interface to work with.> *-network[COLOR="#FF0000"] UNCLAIMED [/COLOR]
description: Network controller
product: BCM43142 802.11b/g/n
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:06:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress cap_list
configuration: latency=0
resources: memory:f7d00000-f7d07fff'Unclaimed' means that there is no driver as there was previously. No driver means no wireless.

Working a hunch here. Please run and post:```
lsb_release -d
uname -r
```

---

