---
title: "Samba stopped working after I inserted another network card"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2007-11-21
Good day, friends!
I have a problem that I have to solve as soon as possible! There's a company we work for and I ran into the following problem. I installed Ubuntu server, set up Samba everything worked great and as a breese until I installed a second ethernet card into it. Everything was smooth and device was recognised as eth1 but Samba refused to work after that on Ubuntu workstations. And I guess it's because of wins 'cause smb://192.168.0.1 shows me the folders on server and smb://server doesn't. :( I haven't changed the configuration in smb.conf or anything. preferred master=yes, wins support=yes.

Please help me! Any ideas would be appreciated!

---

### Post by cmnorton on 2007-11-21
Was the network restarted?

Was samba restarted?

It might help to post the output if ifconfig.

---

### Post by PryGuy on 2007-11-21
> **cmnorton said:**
> Was the network restarted?
Yes!> Was samba restarted?
Absolutely!!!> It might help to post the output if ifconfig.Will post it tomorrow! Thank you!!!

---

### Post by PryGuy on 2007-11-22
[HTML]eth0      Link encap:Ethernet  HWaddr 00:1A:4D:3A:80:DF  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe3a:80df/64 Range:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7165209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8254659 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1805617706 (1.6 GiB)  TX bytes:1994399723 (1.8 GiB)
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Range:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123270 (120.3 KiB)  TX bytes:123270 (120.3 KiB)
[/HTML]
I removed the eth1 card as you see... Everything's fine with it as far as I understand...

---

### Post by PryGuy on 2007-11-22
Well, there's one thing I just can't get, what WINS is? I just set up the path to the WINS server on all the clients and it started working, but I remember clearly that it worked without it!

---

