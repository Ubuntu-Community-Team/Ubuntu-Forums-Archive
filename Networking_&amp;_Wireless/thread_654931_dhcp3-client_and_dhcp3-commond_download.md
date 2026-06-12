---
title: "dhcp3-client and dhcp3-commond download"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by Apples123 on 2007-12-31
I was having problems with my dns not saving and i looked at a previous post ([http://ubuntuforums.org/showthread.php?t=334601](http://ubuntuforums.org/showthread.php?t=334601))

In which it said that i should remove these so i did

clearly a mistake, was wondering if there is any way to re install these (system restore or something similar) as i now have no internet on any of my home computers

---

### Post by Predator[23rd] on 2007-12-31
don't know if this can help, but have you tried "sudo apt-get install ubuntu-minimal" with the ubuntu CDROM inserted?

---

### Post by Apples123 on 2007-12-31
just tried that it searchs html links for it, not the cd

---

### Post by Predator[23rd] on 2007-12-31
ok. let's try something different: let DHCP go and configure your NIC by hand.

first check which NICs you have by typing **ifconfig**
reply should be something like this, but without all the configuration in eth0

[I]eth0      Link encap:Ethernet  HWaddr 00:0C:29:6F:C0:EF  
          inet addr:192.168.75.132  Bcast:192.168.75.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe6f:c0ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25551660 (24.3 MB)  TX bytes:2404064 (2.2 MB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
[/I]

check your mac's configuration with "ifconfig" too. darwin is sitting on BSD ...

try to figure out a configuration, based on your apple configuration, which should work for your ubuntu box too. then go to the */etc/network/interfaces* file and edit it. mine should look like this:exit

[I]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.75.132
netmask 255.255.255.0
network 192.168.75.0
broadcast 192.168.75.255
gateway 192.168.75.2[/I]

I think this should give you back internet connectivity. Then you can install the missing packages via apt-get. I hope ... ;)

---

