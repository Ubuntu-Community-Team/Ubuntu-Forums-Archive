---
title: "connect:Network is unreachable"
date: 2015-04-07
forum: Networking &amp; Wireless
---

### Post by kelly6 on 2015-04-07
Hi all, 

I am trying to set up a gateway router to allow internal networks to connect to the internet. The gateway server can ping both the internal network and external network fine, but the when I try to ping from the internal network to either the gateway server or internet I get the following error```
[INDENT=2]connect: Network is unreachable[/INDENT]

```[INDENT=2]
[/INDENT]
 I have tried searching for answers but don't seem to be getting anywhere.


On my gateway server I have 1 external and 2 internal NICS configured as:```
[INDENT=2]iface eth0 inet dhcp
[/INDENT]
[INDENT=3]address 172.168.30.16
netmask 255.255.255.240
[/INDENT]
[INDENT=3]gateway 172.168.30.254

[/INDENT]
[INDENT=2]iface eth1 inet static[INDENT]address 172.168.30.33
[/INDENT]
[INDENT]netmask 255.255.255.240
network 172.168.30.32
[/INDENT]
[INDENT]broadcast 172.168.30.47

[/INDENT]
iface eth2 inet static[INDENT]address 172.168.30.49
[/INDENT]
[INDENT]netmask 255.255.255.240
network 172.168.30.48
[/INDENT]
[INDENT]broadcast 172.168.30.63[/INDENT]

[/INDENT]

```[INDENT=2]
[/INDENT]
[INDENT]I am a complete noob to this and would really appreciate any help to get this up and running
[/INDENT]

---

### Post by michi1983 on 2015-04-08
Hi,

first, what version of Ubuntu are you running? 14.04 LTS?

Second, please answer the following questions:


[LIST]
[*]eth0 is connected to the ISP Modem/Router?
[*]eth1 is connected to what?
[*]eth2 is connected to what?
[/LIST]

What I can see is that you have set up eth0 for receiving an IP address from the DHCP server but you still set up a static IP address.
This might be the problem?!

And you don't have set up a gateway on either eth1 and eth2

Also the network address is always .0 and the broadcast is always .255

I would also leave the netmask at 255.255.255.0

And you have all 3 NICs in the same network, was that on purpose?
Are you running a DHCP Server on your Ubuntu server?

Please post the output of ```
cat /etc/resolv.conf
```

---

### Post by kelly6 on 2015-04-08
Thanks so much for the help. 
I reconfigured the network IP addresses by changing  eth0 to 172.168.20.0, eth1 to 172.168.30.0 and eth2 172.168.40.0 with a 255.255.2550 mask, so they are all on diferent networks
Removed the static IP from eth0.
Configured the gateway of eth2 and eth 3 to the router gateway and working like a charm now.

I'm very new to all of this, and very much appreciated the help!

---

