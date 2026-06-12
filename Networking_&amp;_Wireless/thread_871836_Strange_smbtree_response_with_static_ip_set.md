---
title: "Strange smbtree response with static ip set"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by cmatte on 2008-07-27
Hi,
I had the need to set my desktop ubuntu to have a static ip and not use dhcp,
so I followed all the advices out there and I have /etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface

iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

auto eth0
```
/etc/resolv.conf :
```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5578
#
### END INFO

nameserver 208.67.222.222 #opendns(public)
nameserver 62.211.69.170 #my isp
nameserver 208.67.220.220 #opendns
nameserver 212.48.4.30 #my isp

nameserver 192.168.1.1
search MSHOME
domain MSHOME
```
Ok, here we come to the strange problem...I were trying to share a directory and had the idea to have a look at smbtree response. Well, I get something strange:
```
smbtree
Password: 
MSHOME
	\\VMCE-U         		VMCE-U
timeout connecting to 208.69.34.132:445
timeout connecting to 208.69.34.132:139
Error connecting to 208.69.34.132 (Operazione già in corso)
cli_start_connection: failed to connect to VMCE-U<20> (208.69.34.132). Error NT_STATUS_ACCESS_DENIED
	\\PORTATILE-U    		PORTATILE-U
timeout connecting to 208.69.34.132:445
timeout connecting to 208.69.34.132:139
Error connecting to 208.69.34.132 (Operazione già in corso)
cli_start_connection: failed to connect to PORTATILE-U<20> (208.69.34.132). Error NT_STATUS_ACCESS_DENIED

```
VMCE-U is this pc, PORTATILE-U is my laptop(both with Samba and Ubuntu).
What's all the stuff with that ip 208.69.34.132 :confused:
Oh, forgot to mention, my laptop doesn't have all the 208... stuff (is set with dhcp)!

---

### Post by swells5 on 2008-11-12
did you get this sorted out?
check your /etc/hosts file and put the ip address of your LAN computers in there
computer name     ipaddress
computer2 name    ipaddress
etc

this solved the same problem for me.
Steve

---

