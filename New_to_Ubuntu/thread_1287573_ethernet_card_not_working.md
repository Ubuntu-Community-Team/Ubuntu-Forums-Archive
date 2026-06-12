---
title: "ethernet card not working"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by Enkidux on 2009-10-10
hello 

I am trying to get a ethernet card running but I don't understand the messages I get, anyone can help please?

with lspci I get the following 

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
00:0a.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 43)
00:0c.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)

and with ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:e0:a6:66:41:e1  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:a6ff:fe66:41e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26793 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30522653 (29.1 MB)  TX bytes:2250645 (2.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14400 (14.0 KB)  TX bytes:14400 (14.0 KB)

It seems that is recognized, but doesn't let me access the internet.

I would appreciate any help

thanks

---

### Post by allenbradley on 2009-10-10
Are you behind a router?

---

### Post by Enkidux on 2009-10-10
I couldn't tell, is there any way to know it?

---

### Post by XDevHald on 2009-10-10
Remove the network from the connections list and then add it again. What's the name of your eth0 card? Also do you have one box or two that have blinking lights?

---

### Post by allenbradley on 2009-10-10
I'm guessing 'cause your IP address is 192.168.xx.xx, which is generally present in routers. Are you able to connect using Windows/any other OS? Finally, do you own this router?

---

### Post by Enkidux on 2009-10-10
I tried with Windows and it worked, but back to ubuntu it doesn't...

about the router I don't know if I have one let alone if I own it, any suggestions?

---

### Post by allenbradley on 2009-10-10
I can't seem to make out any real problem. If it's not too much, what are windows IP addresses like? Just to try again, try ```
sudo dhclient
```

---

### Post by Enkidux on 2009-10-10
I don't understand your question, what do you mean?

sorry but I don't have lots of knowledge in computers, I barely know what an IP is but I don't have a clue about the difference between IP in ubuntu and Win.

any suggestions?

---

### Post by Enkidux on 2009-10-10
i got this message:

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:e0:a6:66:41:e1
Sending on   LPF/eth0/00:e0:a6:66:41:e1
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.2.2 from 192.168.2.1
DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.2 from 192.168.2.1
bound to 192.168.2.2 -- renewal in 1563 seconds.

---

### Post by allenbradley on 2009-10-10
Sorry. Go to windows, Go to Run. Now, type in ```
cmd
```. Now, type ```
ipconfig/all
``` Loof for an address which looks like 192.168.xx.xx or some other combination ( should be called IP address )

---

### Post by allenbradley on 2009-10-10
> **XDevHald said:**
> Remove the network from the connections list and then add it again. What's the name of your eth0 card? Also do you have one box or two that have blinking lights?
@XDevHald : ```
00:0a.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 43)
``` seems to be the card. The computer is assigned an IP. Doesn't that mean there is no fault with eth0?

---

### Post by Enkidux on 2009-10-10
i got it, it says: 192.168.2.100

---

### Post by allenbradley on 2009-10-10
Ok. Are you able to ping 192.168.1.1 on linux? Fire up a terminal and ```
ping 192.168.1.1
``` and please post the output. ( 192.168.1.1 is usually the router )

---

### Post by XDevHald on 2009-10-10
You have an IP from the router as allenbradley stated, this is obvious as 192.168.x.x is from the router. This MAY sound crazy, but believe me it's not but goto your routers IP's address (192.168.254.254) and reboot the router. Once this is done, a new IP (dynamically) will be assigned to the computer (ubuntu) and should fix the preface of the networks connection login with the router.

If this continues, reset the router (there is a small reset button that can be done with a pen). This WILL reset your network key and passwords to wireless network you have connect to before, 9x's outta 10 this works.

---

### Post by allenbradley on 2009-10-10
XDaveHald : Seems to be a problem with the card : [https://bugs.launchpad.net/ubuntu/+bug/48263](https://bugs.launchpad.net/ubuntu/+bug/48263) , but the fix seems old.

---

### Post by Enkidux on 2009-10-10
I got a long list like this: 

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.2.1 icmp_seq=1 Destination Net Unreachable
From 192.168.2.1 icmp_seq=2 Destination Net Unreachable
From 192.168.2.1 icmp_seq=3 Destination Net Unreachable
From 192.168.2.1 icmp_seq=4 Destination Net Unreachable
From 192.168.2.1 icmp_seq=5 Destination Net Unreachable
From 192.168.2.1 icmp_seq=6 Destination Net Unreachable
From 192.168.2.1 icmp_seq=7 Destination Net Unreachable
From 192.168.2.1 icmp_seq=8 Destination Net Unreachable
From 192.168.2.1 icmp_seq=9 Destination Net Unreachable
From 192.168.2.1 icmp_seq=10 Destination Net Unreachable
...

then I stopped it and this message came:

From 192.168.2.1 icmp_seq=114 Destination Net Unreachable
From 192.168.2.1 icmp_seq=115 Destination Net Unreachable
From 192.168.2.1 icmp_seq=116 Destination Net Unreachable
From 192.168.2.1 icmp_seq=117 Destination Net Unreachable
^XFrom 192.168.2.1 icmp_seq=118 Destination Net Unreachable

--- 192.168.1.1 ping statistics ---
119 packets transmitted, 0 received, +118 errors, 100% packet loss, time 118008ms

---

### Post by XDevHald on 2009-10-10
> **allenbradley said:**
> XDaveHald : Seems to be a problem with the card : [https://bugs.launchpad.net/ubuntu/+bug/48263](https://bugs.launchpad.net/ubuntu/+bug/48263) , but the fix seems old.

Nice find allenbradley. Looks to be a new card is needing to be purchased as I do remember when I couldn't use my Linksys or D-link card wouldn't work for nothing even if I did extended research and fixing.

Enkidux: Take a look into another card if you can. Sorry to see this is not turning tables for you :-/

---

### Post by Enkidux on 2009-10-10
How can I go to an IP address to reboot the router?

I am now using two different adsl sets, one (old works) and the new one doesn't... 

If I use the old one to reset the router, will this help with the new one?

---

### Post by Enkidux on 2009-10-10
do you recommend me to go and buy a new one or try booting the router?

which one can I get that works with my pc? 

Grrrr..... is not really the money (about 4€) of the card, but the hassle of getting another one, installing it and hopefully getting it to work....

---

### Post by allenbradley on 2009-10-10
The "good" news is that your symptoms agree with [this]("https://bugs.launchpad.net/ubuntu/+bug/48263"): You are assigned an address, but are unable to ping the router. For a way to fix, please try following [this]("http://www.lockergnome.com/linux/2007/11/27/ubuntu-wired-networking-woes-read-this-closely/"). It should work for your case. Please let me know if you have difficulty in understanding the instructions.

---

### Post by Enkidux on 2009-10-10
hello again

and thank you for all the trouble, but indeed I do not understand the instructions.... where am I supposed to find all that...

I would appreciate your help once again

---

### Post by XDevHald on 2009-10-10
> **Enkidux said:**
> hello again

and thank you for all the trouble, but indeed I do not understand the instructions.... where am I supposed to find all that...

I would appreciate your help once again

As a result of the awareness in your level of understanding computer administration on the Unix (Linux) platform I/we would recommend you to read more into how to use linux and the commands before trying to take appropriate steps in making changes to your network/computer on your Ubuntu desktop.

1) **How to Use Ubuntu:** [http://www.easy-ubuntu-linux.com/how_to_use_ubuntu.html](http://www.easy-ubuntu-linux.com/how_to_use_ubuntu.html)

2) **Ubuntu Hardy Guide:** [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy) <-- You'll want to read this most importantly.

I hope these help, you may also see [http://help.ubuntu.com](http://help.ubuntu.com) and [http://wiki.ubuntu.com](http://wiki.ubuntu.com) for further support and the community forums here as well.

P.S The search option on the forum is like Google.com, (It's your BEST friend)

---

### Post by allenbradley on 2009-10-12
Enkidux, I have PM'ed you. Please check messages.

---

### Post by EnGorDiaz on 2009-10-12
do this  

```
sudo ifconfig eth0 up
```

---

### Post by simartem on 2009-10-21
are you trying to use Ubuntu on its own with installation on the partition, or are you running it from a vmware (or similar..) on windows ? This may be one of a problem source.

---

