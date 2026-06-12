---
title: "Ubuntu 20.X - Replace Netplan problems with second NIC"
date: 2020-11-17
forum: Networking &amp; Wireless
---

### Post by guymandude2 on 2020-11-17
I want to run Suricata (network sniffer) on Ubuntu 20.X but Netplan does not support promiscuous mode on network adapters.  I replaced Netplan with the old Net Tools and have gotten the primary nic working fine but my second NIC does not start on boot up and when started manually it is does not run in promiscuous mode.  I have tried many variations with the /etc/network/interfaces config to no avail.  I need both nics to start on boot and the ens192 nic to start in promiscusous mode.  Any thoughts are appreciated.

Here's the latest /etc/network/interface configuration:

[COLOR=#000000][FONT=Arial]#loopback[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]auto lo[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]iface lo inet loopback[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# MGMT[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]iface ens160 inet static[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]address 10.1.1.9[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]gateway 10.1.1.250[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]netmask 255.255.255.0[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]broadcast 10.1.1.255[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]dns-nameservers 10.1.1.2[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# SNIFFER[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]iface ens192 inet static[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]address 172.16.21.9[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]netmask 255.255.255.0[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]broadcast 172.16.21.255[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]network 172.16.21.0[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]up ifconfig ens192 promisc up[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]down ifconfig ens192 promisc down

Thanks for reading and your thoughts.[/FONT][/COLOR]

---

