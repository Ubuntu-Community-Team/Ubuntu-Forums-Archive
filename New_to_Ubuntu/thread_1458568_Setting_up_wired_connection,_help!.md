---
title: "Setting up wired connection, help!"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by lepel on 2010-04-20
Hi,
I was trying to set up a wireless connection, but since it didn't work I am trying first to set up a wired connection. This too seems to be very complicated.
I connected my modem with my laptop and typed in a terminal: sudo pppoeconf.
It starts very promising but at the end it says that my providers Access Concentrator did not respond.
When I looked in the log ( sudo tail -f /var/log/messages ), it seems that it has something to do with LCP: timeout sending Config-Requests.

How can I solve this?

Lepel

---

### Post by P4man on 2010-04-20
hang on. Are you sure you need PPOE ? What kind of internet connection do you have, and what router/modem? Are you connecting to the router or modem with USB or ethernet?

---

### Post by lepel on 2010-04-20
> **P4man said:**
> hang on. Are you sure you need PPOE ? What kind of internet connection do you have, and what router/modem? Are you connecting to the router or modem with USB or ethernet?

I'm not sure if I need ppoe. I'm connected via an ethernet-cable.
What exactly do you mean by what kind of internet connection?
I allready have 3 other laptops connected to that modem, wireless, but they all run on Windows XP, connecting my ubuntu-laptop didn't work out.
I was advised to set up a wired connection first, and than move on to wireless.

---

### Post by P4man on 2010-04-20
Okay, sounds like you dont need PPOE at all. Just plug in the ethernet cable in your router and you should be online. If you are not, then either the router needs some configuring (which is not very likely) or you have absolute terrible luck in having neither wireless nor wired network cards being recognized by ubuntu.

Can you open a terminal and type
```

ifconfig
```

and post the output here? Likewise for

```
lspci
```

---

### Post by lepel on 2010-04-20
ifconfig says:

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr e2:49:06:1d:51:b1  
          inet6 addr: fe80::e049:6ff:fe1d:51b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:804 (804.0 B)


lspci says:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by P4man on 2010-04-20
Eck. Indeed neither wired nor wireless are recognized. What version of ubuntu are you running? 9.10 should work with that wifi card at least.

---

### Post by lepel on 2010-04-20
9.04.
Could that be the problem?

---

### Post by P4man on 2010-04-20
Well, I could be wrong, but I believe from 9.10 onwards most atheros wifi cards should work out of the box. The wired network card Im less sure about, but you can grab a driver for that. See post 6 of this thread:
[http://ubuntuforums.org/showthread.php?t=1244898](http://ubuntuforums.org/showthread.php?t=1244898)

Might not be needed for 9.10, Im not sure.

Either way, I assume you only just got started with ubuntu and its probably a good idea to use the most recent stable release, which is 9.10. 10.04 is out as beta now, and will be released this month, but if you are new to linux or ubuntu, Id stay clear of beta's. Unless you dont mind experimenting.

**edit**: just realized, that driver needs to be compiled (as per instructions) and that may require packages you dont have, and cant easily install without any network connection. Id go for a newer ubuntu first and see what happens.

---

### Post by lepel on 2010-04-20
It WORKs with version 9.10!
Thank you very much for your help!

---

### Post by P4man on 2010-04-20
Good, glad to hear that. I assume wireless is working, or wired as well? Anyway, for googlers with a similar problem, perhaps mention your brand and type of notebook so people looking for it may find their answer here.

---

### Post by Iowan on 2010-04-20
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") :)
(Help others find your fix)

---

