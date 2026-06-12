---
title: "Wireless adapter is Unknown Device"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by czaleski on 2006-08-26
Greetings. I'm hoping someone can offer some advice. I have a new Dell Inspiron e1405 with a "Dell Wireless 1390" adapter. I've found that this is a Broadcom adapter, but not positive what chipset it is (4311?)
As most folks, I've spent a lot of time reading these forums and scouring Google results. I've found what I believe is a way to get it up and running, but all the info I've found seems to assume that the adapter is recognized in the first place. Thus using ndiswrapper fails because (I think) it doesn't even know what *device* to apply the driver to.

For instance, I followed the instructions here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
However after using the GUI tool to install the driver, it simply reports: "Hardware present: No"

"lspci | grep Broadcom" reports the following:
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:0c:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)

I am hoping to learn...
Am I correct in assuming I need to get the "unknown device" to be "known" first before I can do anything else?
If so how do I resolve this problem?
If not, what should I do?

Any help or advice is appreciated.
Thanks very much

---

### Post by czaleski on 2006-08-26
shameless bump

---

### Post by NetworkGuy on 2006-08-26
There have been several threads in the last hour or two on how to get broadcom cards working.  Click on new posts and go back several pages.

---

### Post by Melcar on 2006-08-26
People have been having more success (if you can call it success:roll: ) using the fwcutter method 
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174).
Be aware that you may not get your wireless device working 100%, so don't get too frustrated; most Broadcom users are in the same boat as you.

---

### Post by Sh8kR on 2006-09-09
> **NetworkGuy said:**
> There have been several threads in the last hour or two on how to get broadcom cards working.  Click on new posts and go back several pages.


But there is a special issue with the Broadcom 4311 this card cannot use the bcm43xx driver does not currently work on this bcm4311 chip. So the only option is the Ndiswrapper.

---

