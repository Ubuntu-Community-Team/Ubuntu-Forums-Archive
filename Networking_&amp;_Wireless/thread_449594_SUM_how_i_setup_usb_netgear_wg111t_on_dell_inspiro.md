---
title: "SUM: how i setup usb netgear wg111t on dell inspiron 8500"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by stu2004 on 2007-05-20
I thought I would sum this back. I have had some FUN trying to get  my old usb netgear wg111t working. I tried several times and read lots of posts which didn't help. So after many attempts, I hope this helps someone in my situation in the future.

I'm a noob, so there may be omissions/errors. 

The steps used:-

*    Uninstalled the synaptic version of ndiswrapper. 
*    Added build-essential from synaptic.
*    Went to sourceforge to get ndiswrapper 1.44. untarred it and read the install file. Then built it. This installed it for me.

*   I then added the two drivers in wg111t_1_2. i.e. by ndiswrapper -i *.inf and repeat. At this stage when i rebooted with the usb wireless beasty plugged in, wifi radar showed my network and the blue light came on.

*   To configure the network to use wpa looked hard from all the posts. In the end I avoided the manual config and just double clicked on the network icon and it was dead easy after that. i did have wpa supplicant already installed. No config was entered in a files by me ;-), all gui. 

From all the posts I read, I tried using wine to register stuff, looked at editing config all over the place. In the end, ndiswrapper came through for me.

I hope this helps someone.

Stu

---

### Post by mikesmith00 on 2007-05-20
Are you running Fiesty, Edgy, Dapper?  Or else just which kernel are you using?  Today I was considering dumping ubuntu, even though I really want to get it running so that I can put it on my cousins PC and be able to explain how to get them through things, because I have to reinstall windows every 2 to 3 months because of spyware problems, and I thought that linux wouldn't have that problem, but my laptop has no LAN port, just wireless, and it's on a wg111t, so as of now I've had no luck.  Thanks for figuring this out, I tried to get it, but I didn't have build-essential setup yet, I'm getting ready to try that.

---

### Post by mikesmith00 on 2007-05-20
Ok, I just tried it with Feisty, and I'm working on the laptop now through the wireless connection.

---

### Post by dawdler on 2007-05-23
Thanks stu2004!

I was having problems connecting to a WPA encrypted wireless network using network manager with my Netgear wg311v2.  I was using the synaptic ndiswrapper v. 1.38.  Once I installed the 1.44 version of ndiswrapper, I was able to connect to the WPA network.

Running fiesty...

---

