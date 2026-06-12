---
title: "[SOLVED] Network failure"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by Sterkarm on 2008-08-11
hi, after comfatbly running my dule boot desktop for what seems too long iv oncde again come accross yet more network problems.

The problem that im now left with is that none of the network cards in my machine is giving me an internet connection, on OS.

i currently have an onbord  via vt6102 [rhine-II] (rev 78) and a Realtek RTL-8139/8139C/8139C+ (rev 10) card


as i said - both resuse to connect to the tinterweb.

the network cable ect is all perfectly fine and dandy, and abel to conenct other devices using same cable, jsut not my desktop, on any of the two cards above


any one any idears on how i can try an get any of the two cards working. they bother show up, both lite up ect and connect via network manager - just no internet or network via them :(



thanks guys n galls

---

### Post by Sterkarm on 2008-08-11
Still stuggling to find any solutions.

been trawling though forums for any simmler situiations but crnt find anything :(


tried everything i can posabbily think of n starting to run out of solutions.

please somone sujest something - any little idears welcome on how to get my network cards working. they have previous worked perfectly. just not any more :(

---

### Post by Iowan on 2008-08-11
Post results of **ifconfig** and contents of **/etc/network/interfaces**.  If there is another machine on the network, can you **ping** this machine (via IP address from *ifconfig)*)?

---

### Post by Sterkarm on 2008-08-11
sertinatly. iv been looking tohugh them all day and not come up with anthything

ifconfig:

mat@mat-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:df:11:5a:c7  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:dfff:fe11:5ac7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31909 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3012401 (2.8 MB)  TX bytes:472611 (461.5 KB)
          Interrupt:16 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:11:09:eb:a9:e3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:270582 (264.2 KB)  TX bytes:24517 (23.9 KB)
          Interrupt:19 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60492 (59.0 KB)  TX bytes:60492 (59.0 KB)

contence of /etc/network/interfaces:

auto lo
iface lo inet loopback





as a note im currently concentrating my efforts on the realteck nic, witch displays as eth0
thanks

---

### Post by cariboo on 2008-08-11
You currently have a connection to your router as evidenced by the output of ifconfig for eth0. Could it be that your router is blocking the connection?

Jim

---

### Post by Sterkarm on 2008-08-11
My god i love you (but not in that way, thats just wrong :S)


lol, never thaught bout that. god i realy am a tard.

tralled through the wilderness that is our celler to reboot the rooter. thing work like a charm. wooo


thanks once more dood.

---

