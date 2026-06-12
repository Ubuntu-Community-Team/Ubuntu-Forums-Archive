---
title: "eth0:avah? 169.254... what?"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by slink on 2007-10-15
I lost Internet connection during a lightning storm. Since then I can only get:

```
felix@ordinador:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xb400 

eth0:avah Link encap:Ethernet  HWaddr 
          inet addr:169.254.9.22  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6564 (6.4 KiB)  TX bytes:6564 (6.4 KiB)
```


You see? A eth0:avah interface has appeared but gives incorrect adresses.

It seems that I can't get a valid IP adress from DHCP.

How can I solve this ?

---

### Post by anubhavrocks on 2007-10-15
try doing 
```
sudo dhclient eth0 
```

---

### Post by slink on 2007-10-16
[FONT="Courier New"]sudo dhclient eth0[/FONT] has no effect on my machine :cry:

---

### Post by yangmi0313 on 2007-11-18
root@myang-desktop:/etc/apt# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:B9:5B:AE:EA  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738176 errors:310 dropped:788 overruns:24 frame:0
          TX packets:4688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:137859265 (131.4 MiB)  TX bytes:577183 (563.6 KiB)
          Interrupt:20 Base address:0x6000 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:B9:5B:AE:EA  
          inet addr:169.254.9.233  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7293 (7.1 KiB)  TX bytes:7293 (7.1 KiB)


yes,it is really a strange problem.
when i down and up the eth0, the "eth0:avah" disappeared.

---

### Post by kevdog on 2007-11-18
eth0:avah  -- its not an error, its just the avahi package.  It just basically means you have to LAN internet address or that your dhcp server did not assign you an address.

---

### Post by ranbo on 2008-03-18
I get the exact same thing on my machine: "eth0" with no real IP address, "eth0:avah" with a bogus 169... IP address, and I'm hosed.  In my case, it appears that we have a bad network switch in the building that I'm lucky enough to be connected to.  If I take my laptop and connect it to a long ethernet cable from the cube across the hall, I get a real IP address immediately.  But when I use the connection to the socket in my cube--or any any of the cubes along my wall and the one next to it--then I don't get an address, and I get the dorky "eth0:avah" thing eventually.  I only get the "eth0:avah" after my "sudo ifup eth0" fails several attempts at getting an IP address and says "sleeping."  Occasionally I do end up getting a real IP address from the flaky switch--once in a while I even get one immediately--but usually I'm hosed and it never comes up.

My old laptop (and a windows box nearby) would both eventually get an IP address, like after 2 or 3 minutes.  My new one is apparently configured to give up if it doesn't get one within a minute or so.

The people who are supposed to fix the switch still have trouble believing that the switch is bad.  "Every indication is that it's healthy," they say.  Except, I point out, that it doesn't, you know, work.

---

### Post by slink on 2008-03-18
In may case, the ethernet adaptor appeared to be not totally damaged but unable to connect with the DHCP server, then the avahi daemon assigns an IP adress valid for LAN area. 

I was forced to connect with the cable-modem via usb while the ethernet card is (still) disabled.

Guess I'm explaining it right....

---

### Post by vazir on 2008-04-08
I am having exact same problem on brand new desktop. I am not able to connect to the LAN over Ethernet at all. I am hosed. Please help. I am stuck and have no possible solution. 

Thanks in advance.

---

### Post by slink on 2008-04-08
vazir, since my ethernet adapter was damaged I fixed my problem connecting to the cable-modem via USB instead of ethernet, but I don't know if this can be of help to you because of your problem could be very different from mine :confused:

---

### Post by Dragonlaw on 2008-04-19
Try shutting down your computer modem and router (if you have any)

Leave it off for about a minute. Then turn on in this sequence. First your MODEM, then router (If you have. If not, just ignore this) then your computer and see if you can connect.

---

### Post by pepoweb on 2008-04-28
I have had the exect same problem as described in this thread. After I was done figuring it out on Ubuntu I tried Fedora, but it had the same problem, it would install fine but after the initial reboot it had no network. After fooling around for a few hours with two identical new machines, one with Ubuntu, one with Fedora, I decided to try yet another distro: Open SuSE. Popt in the CD, booted from it told and than there was the sollution. The screen asked me if I was sure to install a 32bit OS on 64bit hardware...

So I downloaded the 64 bit Ubuntu, installed it and it worked like a charme.

Hope this will help someone.

Greetz from Leeuwarden, The Netherlands ;-)

Pepo

---

