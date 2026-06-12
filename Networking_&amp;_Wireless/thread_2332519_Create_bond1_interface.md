---
title: "Create bond1 interface"
date: 2016-08-01
forum: Networking &amp; Wireless
---

### Post by les3453324 on 2016-08-01
Hello.
I install ubuntu 14.04.4.
In my system present 4 Ethernet adapters, 2 to local net, 2 to public.
I configured Cisco back-end an make 2 groups of lacp ports.
Now i need create bond0 and bond1.
I load module, install ifenslave, edit /etc/network/interfaces add bond0 and bond1 interfaces, reboot server, bond0 created success, bond1 not created. 

```
# The loopback network interfaceauto lo
iface lo inet loopback


auto eth0
iface eth0 inet manual


auto eth1
iface eth1 inet manual


auto bond0
iface bond0 inet static
post-up ifenslave bond0 eth0 eth1
post-down ifenslave -d bond1 eth0 eth1
bond-slave none
bond-mode 4
bond-lacp-rate fast
bond-miimon 100
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1
address 192.168.201.14
netmask 255.255.255.0






auto bond1
iface bond1 inet static
post-up ifenslave bond1 eth2 eth3
post-down ifenslave -d bond1 eth2 eth3
bond-slave none
bond-mode 4
bond-lacp-rate fast
bond-miimon 100
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1
address 38.x.x.x
netmask 255.255.255.0


auto eth2
iface eth2 inet manual


auto eth3
iface eth3 inet manual



```

---

