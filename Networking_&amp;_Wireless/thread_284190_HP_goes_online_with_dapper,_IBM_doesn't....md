---
title: "HP goes online with dapper, IBM doesn't..."
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by mooscape on 2006-10-25
I have a HP compaq nx9110 running ubuntu dapper like a rocket. I have since bought an IBM R40 that is running well except that I cannot get onto the internet from home (works well from the office and from hotel). Both machines are running the same version of dapper and both installations should be identical...,but only the HP can get online. Is there any reason the one machine is being so obstreperous?

](*,)     I have posted this thread three days ago to no avail. Please help!

---

### Post by mooscape on 2006-10-25
Why do some threads get many replies and others none?   Some kind of code? (eg always use the word "wireless" and then some obscure card number to grab attention out there!) Must I seed this thread with a letter too self? = :twisted:  = bit twisted!

---

### Post by bswilson on 2006-10-25
Friend, you are not getting any responses because your problem description is _so vague_ nobody knows where to begin to help you.

Can you post here the output of **ifconfig -a** as well as the **/etc/resolv.conf** files for both your HP system and your new Thinkpad?  That's a good place to start...

---

### Post by mooscape on 2006-10-25
Hi bswilson

Thank you for your help, here are the files you requested.....

-----------------------
THIS IS HP compaq nx9110:

mel@mooscape-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:3F:21:A8:A4
          inet addr:222.125.47.143  Bcast:222.125.63.255  Mask:255.255.224.0
          inet6 addr: fe80::202:3fff:fe21:a8a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17769030 (16.9 MiB)  TX bytes:1928706 (1.8 MiB)
          Interrupt:201 Base address:0x4800

eth1      Link encap:Ethernet  HWaddr 00:90:4B:52:C1:B9
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:836 (836.0 b)  TX bytes:836 (836.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

and the contents of resov.conf =     nameserver 211.148.192.135     nameserver 221.4.66.66
----------------------------------


Will now get info from the IBM........

---

### Post by mooscape on 2006-10-25
This is the IBM ThinkPad R40 (but for this small hiccup it is a thing of beauty!):

mel@mel-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:06:1B: D0:0D:6C
          inet6 addr: fe80::206:1bff:fed0:d6c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:246464 (240.6 KiB)  TX bytes:3546 (3.4 KiB)

irda0     Link encap:IrLAP  HWaddr 00:00:00:00
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


and here is the resolv.conf:              nameserver 211.148.192.135
nameserver 221.4.66.66


Many thanks for your assistance - I cann't wait to go online :D

---

### Post by bswilson on 2006-10-27
**mooscape**, your problem is that the Thinkpad does not have an IPv4 address.  This line right here (from your other machine):

```
inet addr:222.125.47.143 Bcast:222.125.63.255 Mask:255.255.224.0
```

...does not appear in the Thinkpad's configuration.  To fix this, click on System > Administration > Networking and find **Wired connection (eth0)** in the list of **Connections**.  Make sure that it is enabled (see the check box)?  You need to open its properties and make sure the Configuration says **Automatic Configuration (DHCP)**.  Then click OK back to the desktop, and see if that fixes your problem.

---

### Post by mooscape on 2006-10-27
hi bswilson

I tried your suggestion. Everything looks right.  This setting connected easily at work today, but still no luck at home.

What else can we try?

---

### Post by Beaucephus on 2006-10-28
Is your HP network card configured via DHCP?  Check this in the network settings as above, instead of DHCP it should say "Static IP Address" for the configuration section.   If your is set IP is manually DHCP is probably not working at home.  This would explain why you did not have an IP address in the previous post, but it was able to connect at work.

If this is the case try this

In the network settings try changing from DHCP to "static IP address" and entering the info in manually. You can get the copy the subnet mask and gateway from your HP.  If your HP is xx.xx.xx.1 use xx.xx.xx.2 for the IP.


Cheers

---

### Post by mooscape on 2006-10-28
My IBM seems to be the problem....!

I tried firing up each computer in turn with the original Ubuntu Dapper CD.  The HP goes straight online from the CD, while the IBM is suffering from the same problem. :confused: :confused: 

For clarity here are the ifconfig -a details:

[COLOR="Red"]HP[/COLOR]:ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:3F:21:A8:A4
          inet addr:222.125.44.251  Bcast:222.125.63.255  Mask:255.255.224.0
          inet6 addr: fe80::202:3fff:fe21:a8a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12590 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1671210 (1.5 MiB)  TX bytes:186183 (181.8 KiB)
          Interrupt:201 Base address:0xe800

eth1      Link encap:Ethernet  HWaddr 00:90:4B:52:C1:B9
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
---------------------------------

[COLOR="Red"]I[/COLOR][COLOR="Lime"]B[/COLOR][COLOR="DeepSkyBlue"]M[/COLOR]

[COLOR="Black"][/COLOR]ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:06:1B:D0:0D:6C
          inet6 addr: fe80::206:1bff:fed0:d6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3612 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:228286 (222.9 KiB)  TX bytes:2178 (2.1 KiB)

irda0     Link encap:IrLAP  HWaddr 00:00:00:00
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11272 (11.0 KiB)  TX bytes:11272 (11.0 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

You will see the lines in eth0  matching
 inet addr:222.125.44.251  Bcast:222.125.63.255  Mask:255.255.224.0
are missing!

The CD is the same in each case so surely the problem must lie with the computer itself (ethernet card?)  :-k

---

### Post by mooscape on 2006-10-28
Beaucephus,

Thank you for suggestion.  However I do not have static address at the office. For some reason it just goes online there.

The DHCP goes off looking for settings at home, rather slow though.  I do get network activity, both from the the little lights on the physical connection as well as in "connection properties" on the screen. (like 20000 packets recieved, 33 packets sent)

If I try restarting networking i get:  

mel@mel-laptop:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:06:1b:d0:0d:6c
Sending on   LPF/eth0/00:06:1b:d0:0d:6c
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:06:1b:d0:0d:6c
Sending on   LPF/eth0/00:06:1b:d0:0d:6c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]
mel@mel-laptop:~$

---

### Post by Beaucephus on 2006-10-30
Sorry...I re-read my post above and it was not clear.:confused: 

Your HP may be functional at home because it is has a static IP.  Check both of your computers and make sure both are configured DHCP. This is the only thing I can think of that would make them behave differently.  

Have you tried a different network cable? (or did the same cable work at the office?)
Is there a router involved here?

---

### Post by mooscape on 2006-10-31
I think you may be onto something with regard to router question....:-k 

There is a _router _at work, but only a _cable modem_ at home.  Therefore I will get only one machine up and running at home (apparently = I will post the recent thread details I have been forumming lately, later) This has to do with ISP issuing a single Address, which is taken by the HP. I will probably need a router or server...

---

### Post by Beaucephus on 2006-11-01
That would explain it.  Are you plugging both computers directly into the modem?  Ive never seen one with more than one port.  

I use linksys routers and they provide lots of capability for the money.

---

### Post by mooscape on 2006-11-02
Ni hao Beaucephus

I am currently typing this on the IBM through the office router. It is purring away like a kitten. :D 

Here is the thread I spoke of:
[http://www.ubuntuforums.org/showthread.php?t=285055](http://www.ubuntuforums.org/showthread.php?t=285055)

I will be in Hong Kong next week and can look out for a linksys or a belkin router. Probably go the wireless route.  If you have any suggestions it would be much appreciated.  

I will update this thread when I get the system working.  I guess I should then make a "howto" as it appears many other people have a similar problem.

Thanks for your input.

---

### Post by mooscape on 2006-11-11
Have bought a new Linksys wrt54g (version 7) router. Now both machines are up and running beautifully on the internet. :D

---

### Post by Beaucephus on 2006-11-13
Cool.

---

### Post by mooscape on 2006-11-14
Hi Beaucephus and bswilson

Many thanks for your input and nudgeing me in the right direction.

mooscape

PS: How do I close this now that everythings resolved?  I should make a "howto" for others with the same problem... :-k

---

### Post by mips on 2006-11-14
> **mooscape said:**
> 
PS: How do I close this now that everythings resolved?  I should make a "howto" for others with the same problem... :-k

Edit your 1st post, go 'Advanced'. you should now see 2 tick boxes to select for resolved & unresolved.

---

