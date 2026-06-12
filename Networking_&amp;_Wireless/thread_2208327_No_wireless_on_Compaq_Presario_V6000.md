---
title: "No wireless on Compaq Presario V6000"
date: 2014-02-27
forum: Networking &amp; Wireless
---

### Post by A_ger21 on 2014-02-27
First of all, i am completely new to Ubuntu. I bought an old Compaq Presario V6000 just to try  it out, but my the wireless network doesnt seem to be working. I tried all sorts of commands that you all posted here, I don't think it's helping since I see that I dont exactly have the same results as anyone. I dont know what the problem is. So it would be very much appreciated if any one could help me out. Thanks!

---

### Post by westie457 on 2014-02-27
A_ger21 welcome to the Forum.

To give us more of a clue what hardware you have follow the directions posted by Wild Man earlier in this thread.

---

### Post by Iowan on 2014-02-27
Appending a post at the end of a solved thread about a different machine might not yield the best results. ;)
Moved to new thread

---

### Post by chili555 on 2014-02-27
How about telling us about your wireless device? Please run and post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by A_ger21 on 2014-02-27
here

---

### Post by varunendra on 2014-02-27
Welcome to the forums A_ger21 !

Your wireless_script report shows no wireless cards of any kind at all ! -
```
***** lspci *****

00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Kernel driver in use: forcedeth

***** lsusb *****

Bus 001 Device 002: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 64MB QDI U2 DISK
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****
```
Does the laptop even have one?

You mentioned you bought an old one, maybe the card was taken out before selling it? Maybe it's fried or just loose?

Or above all, does this model even have one? It seems that some of the models in this series come without a wireless card, e.g. V6310CA here : [http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06a/12139188-78299199-78308301-78308301-78308301-78867421.html?dnr=2](http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06a/12139188-78299199-78308301-78308301-78308301-78867421.html?dnr=2)

Yours appears to be a different model (V6000-RG287UA), but I couldn't find its specs on the net. Maybe it is too outdated?

**EDIT:** Okay, found a link which *may be* of the exact model you have : [http://h10025.www1.hp.com/ewfrf/wc/document?cc=ca&dlc=en&docname=c00762287&lc=en&jumpid=reg_r1002_caen_c-001_title_r0001](http://h10025.www1.hp.com/ewfrf/wc/document?cc=ca&dlc=en&docname=c00762287&lc=en&jumpid=reg_r1002_caen_c-001_title_r0001)
This one seems to have a wireless card, but it is not unusual for the same model to come with different specs at different times/places. Besides, I'm not sure if this one is indeed the same as yours.

---

### Post by A_ger21 on 2014-02-28
sorry for the late reply. 

Yes this is the model [COLOR=#000000](V6000-RG287UA)[/COLOR]
But I am not really sure if it has a wireless card. The guy said it has, but he probably wasnt telling me the truth. Is there any way for me to figure it out?

---

### Post by chili555 on 2014-02-28
> Is there any way for me to figure it out? Some laptops have a little door on the bottom for the wireless card. Does yours? What's in it?

You could also Google the maintenance manual and take it apart (!!) and look. You could also assume that either it doesn't have one or, if it does, it's defective and just get a USB wireless.

---

