---
title: "Creating a bonded connection in 20.04.4 LTS w/ kernel 5.4.0-100-lowlatency"
date: 2022-03-05
forum: Networking &amp; Wireless
---

### Post by robertwk on 2022-03-05
I'm having difficulty creating a bonded connection under 20.04.4 LTS w/ 5.4.0-100-lowlatency. 

So far I'm able to establish physical connections for both ethernet ports and get them assigned IP addresses, but in my attempt to bond the connections through the network connections gui hasn't resulted in a workable configuration.

Both of the connections show up under Network->Interfaces in System Information.

ifconfig shows them both having IP addresses, but despite setting them as both slaves under the bonding configuration, neither of them are listed as slaves in ifconfig under flags. 

I'm at a little bit of a loss. Any suggestions?

---

### Post by Tadaen_Sylvermane on 2022-03-05
Bonding is something usually reserved for server applications. The gui probably isn't entirely capable of doing it easily if at all. Just edit the netplan configuration directly. Much easier.

---

### Post by robertwk on 2022-03-06
> **Tadaen_Sylvermane said:**
> Bonding is something usually reserved for server applications. The gui probably isn't entirely capable of doing it easily if at all. Just edit the netplan configuration directly. Much easier.

I had something similar to this is /etc/network/interfaces and the configuration only lasted a day before it just stopped working and wouldn't reconnect at all. I had to go back and delete everything and reboot in order for it to just use one port again.

auto ens33
iface ens33 inet manual
auto ens36
iface ens36 inet manual
auto bond0
iface bond inet static
address 192.168.0.253
netmask 255.255.255.0
gateway 192.168.0.1
dns-search domain-name.local
slaves ens33 ens36
bond_mode 6
bond-miimon 100
bond-downdelay 0
bond-updelay 0

Is there a different way to make it happen?

---

### Post by robertwk on 2022-03-06
Also I just checked and I have both 01-netcfg.yaml and 01-network-manager-all.yaml in /etc/netplan. 

I've run other commands and it seems to indicate that I'm running a server config; should I just configure 01-netcfg.yaml and rename the 01-network-manager-all.yaml file? Or should I edit both?

---

### Post by robertwk on 2022-03-06
I edited the 01-netcfg.yaml file this:

[FONT=courier new]# This file describes the network interfaces available on your system[/FONT]
[FONT=courier new]# For more information, see netplan(5).[/FONT]
[FONT=courier new]network:[/FONT]
[FONT=courier new]  version: 2[/FONT]
[FONT=courier new]  renderer: networkd[/FONT]
[FONT=courier new]  bonds:[/FONT]
[FONT=courier new]    bond0:[/FONT]
[FONT=courier new]      addresses: [192.168.0.16/24][/FONT]
[FONT=courier new]      gateway4: 192.168.0.1[/FONT]
[FONT=courier new]      interfaces: [enp40s0, enp42s0][/FONT]
[FONT=courier new]      parameters:[/FONT]
[FONT=courier new]        mode: balance-alb[/FONT]
[FONT=courier new]        mii-monitor-interval: 100[/FONT]
[FONT=courier new]  ethernets:[/FONT]
[FONT=courier new]      enp40s0:[/FONT]
[FONT=courier new]        dhcp4: false[/FONT]
[FONT=courier new]        dhcp6: false[/FONT]
[FONT=courier new]      enp42s0:[/FONT]
[FONT=courier new]        dhcp4: false[/FONT]
[FONT=courier new]        dhcp6: false

(Note, spacing is correct, but it didn't paste that way)

However, ip link produces this:

[/FONT][FONT=courier new]: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000[/FONT]
[FONT=courier new]    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00[/FONT]
[FONT=courier new]2: enp42s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000[/FONT]
[FONT=courier new]    link/ether aa:aa:aa:aa:60:66 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]3: enp40s0: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc fq_codel master bond0 state UP mode DEFAULT group default qlen 1000[/FONT]
[FONT=courier new]    link/ether aa:aa:aa:aa:60:67 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]4: wlp35s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000[/FONT]
[FONT=courier new]    link/ether xx:xx:xx:xx:xx:xx brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]8: bond0: <BROADCAST,MULTICAST,MASTER,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default qlen 1000[/FONT]
[FONT=courier new]    link/ether aa:aa:aa:aa:60:67 brd ff:ff:ff:ff:ff:ff


[/FONT]
Clearly, enp40s0 is a slave, but enp42s0 isn't.  What's going on?

---

### Post by Tadaen_Sylvermane on 2022-03-07
Declare your ethernets before the bond. I think it works top to bottom.

---

### Post by robertwk on 2022-03-07
> **Tadaen_Sylvermane said:**
> Declare your ethernets before the bond. I think it works top to bottom.


I'll make that adjustment in the file, but I also found that there were definitions made by the NetworkManager service that were superseding the netplan configuration. I deleted the network connections that were made by it and then it instantly worked. I also stopped the NetworkManager, but didn't disable it and I'm wondering if that's going to fix the problem.

---

### Post by robertwk on 2022-03-09
I had to do a reboot, and for whatever reason, the network manager deleted the bond0 connection altogether. I had to recreate it to get networking working again. Should I disable it altogether?

---

