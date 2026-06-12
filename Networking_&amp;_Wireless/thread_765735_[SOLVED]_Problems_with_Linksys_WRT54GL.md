---
title: "[SOLVED] Problems with Linksys WRT54GL"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by devinWhalen on 2008-04-24
Hey, I just bought a Linksys WRT54GL wireless router but I am having problems setting it up.  It comes with an install cd but that only works with Windows.  I read that if you access the ip [http://192.168.1.1/](http://192.168.1.1/) in your browser then you can configure it that way.  Everytime I try I get the problem loading page error from firefox.  

Can anyone help?

This is my kernel:

2.6.22-14-generic

Thanks

---

### Post by ihavenoidea on 2008-04-24
Hmm, that should work. It worked with my wrt54gs router. Oh nvm, just remove the http:// part and just type 192.168.1.1 and that should do it.

---

### Post by fhantazm on 2008-04-24
Yea. That should work indeed. Lets start with the core and make sure your getting an IP from the router. Do an ifconfig and post the results please.

---

### Post by newruler on 2008-04-25
I have used Linksys WRT54GL's a lot.  The default setup is for DHCP to assign a network address to your computer as long as you are plugged into any of the 4 switch ports and not the WAN port.  If it isn't brand new perhaps someone has altered the configuration?  If so there is a small reset button that can be pressed with something like a paper clip, just hold it down for 10 seconds while powered on and the device will load back the factory default settings and reboot itself.  Going to either [http://192.168.1.1](http://192.168.1.1) or just typing 192.168.1.1 should indeed load the web interface of the router if it has it's default settings.  The username will be admin and the initial password I believe is just left blank.  I recommend once you get into the device to update the firmware from the default linksys to dd-wrt, [http://www.dd-wrt.com](http://www.dd-wrt.com)  It is a free alternative to Linksys' own firmware which adds many features, including increased power output for increased range.  They have a wiki that gives details on the process.  I highly recommend the upgrade I use these to sell to customers and always flash them first to this alternative firmware thanks to it's loads of additional options it gives you.  Anyway, best of luck.

---

### Post by devinWhalen on 2008-04-25
Thanks for your replies.

So here are the steps I performed.  I plug in the router, push the reset button on the router (I bought it new).  I turn off my current modem and then  I run poff -a to clear out my pppoe connection.  I plug my ethernet cable into the first slot in the modem and try to hit [http://192.168.1.1](http://192.168.1.1) and get a Problem loading page in firefox.

I then ran ifconfig with this output:

 eth0      Link encap:Ethernet  HWaddr 00:50:BA:50:56:67
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:288738 errors:3 dropped:0 overruns:0 frame:0
          TX packets:226985 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1361 txqueuelen:1000
          RX bytes:267477558 (255.0 MB)  TX bytes:35869968 (34.2 MB)
          Interrupt:12 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:E0:4C:C2:80:2F
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xec00

eth1:avah Link encap:Ethernet  HWaddr 00:E0:4C:C2:80:2F
          inet addr:169.254.6.170  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10849 (10.5 KB)  TX bytes:10849 (10.5 KB)

Seems like I still have my ip from my ISP.  Do I have to restart something to clear this out?

Thanks for the help, I really want to get this going to I can get my Wii to connect online.

Thanks.

---

### Post by devinWhalen on 2008-04-25
I figured it out, I just had to disable my network connection and then I was able to connect.

Thanks for all the help on this.  Really appreciate it.

---

### Post by Lynn Scott on 2008-05-13
I have a similar problem which may be the same.

I have installed Ubuntu 8.04 and am using the above mentioned router.  The problem is the system is not able to obtain a DHCP address.

I have other Windows systems that work fine, both wired and wireless.  I've tried several things but none seem to work.

At present I am not in front of my system, so if anyone has anything for me to try tonight, that would be great.

---

### Post by devinWhalen on 2008-05-13
Were you using a previous Internet connection setting and then changed to this router?  Because that was my problem.  I was using pppoe to connect to my IP and it was set to connect when the machine boots up so that would mess with my Internet connection.  Once I remove my old settings it was fine.  Are you able to connect to the router?

---

### Post by Lynn Scott on 2008-05-13
No, I am using Comcast broadband and I just connected the feed (ethernet cable) into the router and then have some machines connnected to the ports and other's using wireless.  Using Windows ipconfig everything looks and works great.  Ubuntu tries to get an address but never succedes.

---

### Post by tubbygweilo on 2008-06-11
Hi, 
I am using a Linksys WRT54GLv1.1 wireless router in conjunction with a Linksys AG241v2 wired router / gateway. 
I address the AG241v2 as **[http://192.168.2.1/](http://192.168.2.1/)** and the WRT54GLv1.1 as **[http://192.168.1.1/](http://192.168.1.1/)** 
I have also replaced the wireless router firmware with the open source code supplied by [Tomato]("http://www.polarcloud.com/tomato") and it all works rather well together.

[All you ever want to know about the WRT54G]("http://en.wikipedia.org/wiki/WRT54G")

---

