---
title: "NetworkManager and dhclient.conf"
date: 2018-12-28
forum: Networking &amp; Wireless
---

### Post by blalbrecht on 2018-12-28
Hello all,

I've been struggling with some configuration here and hope you could give me a hint.

Currently using 
[LIST]
[*]Ubuntu 18.04,
[*]kernel 4.15.0-43-generic,
[*]NetworkManager version 1.10.6,
[*]dhclient version isc-dhclient-4.3.5
[/LIST]

Installed it in a virtual machine (Virtual Box) and edited the network connections to have a Host only adapter, disabled the DHCP on VirtualBox.

My objective: to configure the DHCP client's fallback address and timeout.

What I did: edited the /etc/dhcp/dhclient.conf to contain a lease option for the mentioned network adapter with a specific IP address.

This is my dhclient.conf
```

# Configuration file for /sbin/dhclient.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#


option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;


send host-name = gethostname();
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    dhcp6.name-servers, dhcp6.domain-search, dhcp6.fqdn, dhcp6.sntp-servers,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;


#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
#require subnet-mask, domain-name-servers;
timeout 10;
retry 10;
reboot 10;
#timeout 300;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/sbin/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;


#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}


lease {
  interface "enp0s8";
  fixed-address 10.0.0.3;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  renew never;
#  rebind 2 2000/1/12 00:00:01;
#  rebind never;
#  expire 2 2000/1/12 00:00:01;
#  expire never;
}
```

The output of 
```

sudo journalctl -u NetworkManager

```

```

Dez 28 13:03:25 wattux NetworkManager[1367]: <info>  [1545998605.6267] caught SIGTERM, shutting down normally.
Dez 28 13:03:25 wattux systemd[1]: Stopping Network Manager...
Dez 28 13:03:25 wattux NetworkManager[1367]: <info>  [1545998605.6391] exiting (success)
Dez 28 13:03:25 wattux systemd[1]: Stopped Network Manager.
Dez 28 13:03:25 wattux systemd[1]: Starting Network Manager...
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.7115] NetworkManager (version 1.10.6) is starting... (after a restart)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.7117] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf, no-mac-addr-change.conf) (run: 10-globally-managed-devices.conf) (etc: default-wifi-po
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.7187] manager[0x55b315734060]: monitoring kernel firmware directory '/lib/firmware'.
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.7187] monitoring ifupdown state file '/run/network/ifstate'.
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.8950] hostname: hostname: using hostnamed
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.8950] hostname: hostname changed from (none) to "wattux"
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.8955] dns-mgr[0x55b315751160]: init: dns=systemd-resolved, rc-manager=symlink, plugin=systemd-resolved
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.8961] manager[0x55b315734060]: rfkill: WiFi hardware radio set enabled
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.8962] manager[0x55b315734060]: rfkill: WWAN hardware radio set enabled
Dez 28 13:03:25 wattux systemd[1]: Started Network Manager.
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9212] init!
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9214]       interface-parser: parsing file /etc/network/interfaces
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9215]       interface-parser: finished parsing file /etc/network/interfaces
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9215] management mode: unmanaged
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9223] devices added (path: /sys/devices/pci0000:00/0000:00:03.0/net/enp0s3, iface: enp0s3)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9224] device added (path: /sys/devices/pci0000:00/0000:00:03.0/net/enp0s3, iface: enp0s3): no ifupdown configuration found.
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9224] devices added (path: /sys/devices/pci0000:00/0000:00:08.0/net/enp0s8, iface: enp0s8)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9224] device added (path: /sys/devices/pci0000:00/0000:00:08.0/net/enp0s8, iface: enp0s8): no ifupdown configuration found.
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9225] devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9226] device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9226] end _init.
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9226] settings: loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list. (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-s
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9227] settings: loaded plugin keyfile: (c) 2007 - 2016 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9227] (360116480) ... get_connections.
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9227] (360116480) ... get_connections (managed=false): return empty list.
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9566] keyfile: new connection /run/NetworkManager/system-connections/netplan-enp0s8 (7ba7a298-c741-366c-a1ac-84ad05b0a814,"netplan-enp0s8")
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9571] get unmanaged devices count: 0
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9572] manager: rfkill: WiFi enabled by radio killswitch; enabled by state file
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9572] manager: rfkill: WWAN enabled by radio killswitch; enabled by state file
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9572] manager: Networking is enabled by state file
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9576] dhcp-init: Using DHCP client 'dhclient'
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9577] Loaded device plugin: NMBondDeviceFactory (internal)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9577] Loaded device plugin: NMBridgeDeviceFactory (internal)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9577] Loaded device plugin: NMDummyDeviceFactory (internal)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9578] Loaded device plugin: NMEthernetDeviceFactory (internal)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9578] Loaded device plugin: NMInfinibandDeviceFactory (internal)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9578] Loaded device plugin: NMIPTunnelDeviceFactory (internal)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9578] Loaded device plugin: NMMacsecDeviceFactory (internal)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9579] Loaded device plugin: NMMacvlanDeviceFactory (internal)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9579] Loaded device plugin: NMPppDeviceFactory (internal)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9579] Loaded device plugin: NMTunDeviceFactory (internal)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9579] Loaded device plugin: NMVethDeviceFactory (internal)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9580] Loaded device plugin: NMVlanDeviceFactory (internal)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9580] Loaded device plugin: NMVxlanDeviceFactory (internal)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9584] Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-adsl.so)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9594] Loaded device plugin: NMTeamFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-team.so)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9608] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wwan.so)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9612] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wifi.so)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9620] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9634] device (lo): carrier: link connected
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9651] manager: (lo): new Generic device (/org/freedesktop/NetworkManager/Devices/1)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9679] manager: (enp0s3): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9704] keyfile: add connection in-memory (7092d5a0-84ad-32c1-b6e2-75437516c57a,"Wired connection 1")
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9715] settings: (enp0s3): created default wired connection 'Wired connection 1'
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9734] device (enp0s3): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9767] device (enp0s8): carrier: link connected
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9782] manager: (enp0s8): new Ethernet device (/org/freedesktop/NetworkManager/Devices/3)
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9805] device (enp0s8): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Dez 28 13:03:25 wattux NetworkManager[1606]: <warn>  [1545998605.9858] Error: failed to open /run/network/ifstate
Dez 28 13:03:25 wattux NetworkManager[1606]: <info>  [1545998605.9989] device (enp0s8): state change: unavailable -> disconnected (reason 'none', sys-iface-state: 'managed')
Dez 28 13:03:26 wattux NetworkManager[1606]: <info>  [1545998606.0087] policy: auto-activating connection 'netplan-enp0s8'
Dez 28 13:03:26 wattux NetworkManager[1606]: <info>  [1545998606.0112] device (enp0s8): Activation: starting connection 'netplan-enp0s8' (7ba7a298-c741-366c-a1ac-84ad05b0a814)
Dez 28 13:03:26 wattux NetworkManager[1606]: <info>  [1545998606.0117] device (enp0s8): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Dez 28 13:03:26 wattux NetworkManager[1606]: <info>  [1545998606.0120] manager: NetworkManager state is now CONNECTING
Dez 28 13:03:26 wattux NetworkManager[1606]: <info>  [1545998606.0143] device (enp0s8): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Dez 28 13:03:26 wattux NetworkManager[1606]: <info>  [1545998606.0191] device (enp0s8): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Dez 28 13:03:26 wattux NetworkManager[1606]: <info>  [1545998606.0202] dhcp4 (enp0s8): activation: beginning transaction (timeout in 45 seconds)
Dez 28 13:03:26 wattux NetworkManager[1606]: <info>  [1545998606.0229] dhcp4 (enp0s8): dhclient started with pid 1617
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 49: expecting lease declaration.
Dez 28 13:03:26 wattux NetworkManager[1606]: <info>  [1545998606.0344] modem-manager: ModemManager available
Dez 28 13:03:26 wattux dhclient[1617]: send
Dez 28 13:03:26 wattux dhclient[1617]: ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 51: expecting semicolon.
Dez 28 13:03:26 wattux dhclient[1617]: option
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 52: no option named ms-classless-static-routes in space dhcp
Dez 28 13:03:26 wattux dhclient[1617]: option ms-classless-static-routes code
Dez 28 13:03:26 wattux dhclient[1617]:         ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 53: no option named wpad in space dhcp
Dez 28 13:03:26 wattux dhclient[1617]: option wpad code
Dez 28 13:03:26 wattux dhclient[1617]:         ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 55: expecting lease declaration.
Dez 28 13:03:26 wattux dhclient[1617]: request;
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 56: expecting semicolon.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]: ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 57: expecting lease declaration.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 58: expecting semicolon.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 59: expecting lease declaration.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 60: expecting semicolon.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 61: expecting lease declaration.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 62: expecting semicolon.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 63: expecting lease declaration.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 65: expecting lease declaration.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 66: expecting semicolon.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 67: expecting lease declaration.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 68: expecting semicolon.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 69: expecting lease declaration.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 70: expecting semicolon.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 71: expecting lease declaration.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 72: expecting semicolon.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 73: expecting lease declaration.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 74: expecting semicolon.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 75: expecting lease declaration.
Dez 28 13:03:26 wattux dhclient[1617]: also
Dez 28 13:03:26 wattux dhclient[1617]:  ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 75: expecting semicolon.
Dez 28 13:03:26 wattux dhclient[1617]: 
Dez 28 13:03:26 wattux dhclient[1617]: ^
Dez 28 13:03:26 wattux dhclient[1617]: /var/lib/NetworkManager/dhclient-enp0s8.conf line 75: unterminated lease declaration.
Dez 28 13:03:26 wattux dhclient[1617]: 
Dez 28 13:03:26 wattux dhclient[1617]: ^
Dez 28 13:03:26 wattux dhclient[1617]: DHCPDISCOVER on enp0s8 to 255.255.255.255 port 67 interval 3 (xid=0x6287e832)



```

The file /var/lib/NetworkManager/dhclient-enp0s8.conf is actually quite weird:
```

# Created by NetworkManager
# Merged from /etc/dhcp/dhclient.conf


# Configuration file for /sbin/dhclient.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
#require subnet-mask, domain-name-servers;
reboot 10;
#timeout 300;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/sbin/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;
#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}
lease {
fixed-address 10.0.0.3;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  renew never;
#  rebind 2 2000/1/12 00:00:01;
#  rebind never;
#  expire 2 2000/1/12 00:00:01;
#  expire never;
send host-name "wattux"; # added by NetworkManager


option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;
option ms-classless-static-routes code 249 = array of unsigned integer 8;
option wpad code 252 = string;


request; # override dhclient defaults
also request subnet-mask;
also request broadcast-address;
also request time-offset;
also request routers;
also request domain-name;
also request domain-name-servers;
also request domain-search;
also request host-name;
also request dhcp6.name-servers;
also request dhcp6.domain-search;
also request dhcp6.fqdn;
also request dhcp6.sntp-servers;
also request netbios-name-servers;
also request netbios-scope;
also request interface-mtu;
also request rfc3442-classless-static-routes;
also request ntp-servers;
also request ms-classless-static-routes;
also request static-routes;
also request wpad;

```

Looks like the NetworkManager is messing up when merging its built in options with the dhclient.conf file.

Any suggestions?

Cheers,
Bruno

---

### Post by blalbrecht on 2019-01-02
Really? no one has any suggestion? or at least I can find more info about it?

---

