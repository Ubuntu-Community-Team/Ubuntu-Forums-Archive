---
title: "Feisty Killed my Internet!"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by Aithnea on 2007-04-20
Last night I installed Feisty over my Dapper partion on my laptop.  Everything worked fine in Dapper so I figured it would be all good in Feisty as well.  I installed the 64bit version of Feisty and found that I had no internet as well.  I was able to ping my router but I cannot seem to get past my router.  This morning I switched back to Dapper to see if switching to the 32bit version of Feisty would be better, but imagin my suprise when I couldn't get past my router in Dapper 64bit as well!  I never had this problem before.

Please help.  I'm at my wits ends and would really like to be able to go online on my laptop again.  Thank you everyone.

EDIT:  I'm not sure if this is important or not, but this is my wired internet on my laptop that I'm having issues with.  I don't care about getting the wireless to work.  My wireless card isn't supported and I've lasted over a year without it so it's not a big deal.

---

### Post by Kobalt on 2007-04-20
What does the *ifconfig* command return ?

---

### Post by Aithnea on 2007-04-20
eth0 Link encap:Ethernet HWaddr 00:C0:9F:BF:EF:F5
         inet addr: 192.168.1.8 Bcasr: 192.168.1.255
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
         RX packets:31 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes 4948 (4.8 KiB) TX bytes 0 (0.0KiB)
         interrupt: 169 Base address:0X1800

lo      Link encap:Local Loopback
         inet addr:127.0.0.1 Mask: 255.0.0.0
         UP LOOPBACK RUNNING MTU:16436 Metric: 1
         RX packets:35 errors:0 dropped:0 overruns:0 frame:0
         TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RXtytes:2540 (2.4KiB) TX bytes:2540 (2.4KiB)

---

### Post by smartboyathome on 2007-04-20
I had this problem a while ago, too. What type of internet do you have? If it is comcast, follow these steps:

Turn off your router
Reset your Comcast box
Turn on your router
Do a Release and Renew on the router

It should work now (tested on Linksys router with comcast).

---

### Post by Aithnea on 2007-04-20
I'm using ADSL through Telus.  I'm not sure if it's my router as I'm on my husbands window's machine right now and am able to get online.  I can even get online on my windows partion on my laptop.  It's just in Ubuntu that it's not working.  We did try releasing and renewing the IP on the router last night and it didn't work.  But thank you for the help.  I really do appreshate everyone trying to help.

---

### Post by Aithnea on 2007-04-20
Okay, I tried releasing and renewing my router ip address but it didn't do anything.  The problem appears to be that I can't ping my DNS server.

---

### Post by elmerfud on 2007-04-20
I think I have the same problem.
See [http://ubuntuforums.org/showthread.php?t=415692](http://ubuntuforums.org/showthread.php?t=415692)

If I do a /etc/init.d/networking stop and then start or do some ifdowns and ifups, it works.  Give it a try and report back.  If you have the same problem, I'll report it as a bug.

---

### Post by Aithnea on 2007-04-20
Hi elmerfud thanks for trying to help me

I tried /etc/init.d/networking and got this back:
Usage: /etc/init.d/networking {start|stop|restart|force-reload}

Next I tried: sudo /etc/init.d/networking start and got this back:
* Configuring network interface...
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDF: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systms Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systms Consortium.
All rights reserved.
For infor, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0

Following this I tried the sudo /etc/init.d/networking stop and recieved this message:
*Deconfiguring network interface...
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/productis/DHCP](http://www.isc.org/productis/DHCP)

Listening on LPF/eth1/00:14:a4:24:e8:24
Sending on  LPF/eth1/00:14:a4:24:e8:24
Sendign on Socket/fallback

---

### Post by elmerfud on 2007-04-20
When I was running Edgy, my wireless card was eth0.  For some reason, when I run Feisty, my wireless card is wlan0.

It doesn't look like its finding your hardware.

You might want to check /etc/network/interfaces.  You might also need to modprobe the driver for your Ethernet device.  I'm guessing here.

---

### Post by Aithnea on 2007-04-20
This is going to sound really dumb, but I think my brain is fried.  When I type in "sudo /etc/network/interfaces" I get this reply: sudo: /etc/network/interfaces: command not found

Yet if I try it without the sudo I get the reply bash: /etc/network/interfaces: Permission denied

Also how do I do a modprobe for my driver?  I've never had to do that before.  Sorry about being such a bother.

---

