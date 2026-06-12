---
title: "compiz fusion"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by dominic23 on 2009-05-19
hi im really new to linux. ive installed ununtu 9.04 and ive got the compiz fusion installed but cant see anything has changed. could someone explain what im to do. many thanx

---

### Post by taurus on 2009-05-19
Have you installed a driver for your graphic card?  Compiz needs 3D capability so look in System -> Administration -> Hardware Drivers to see if your graphic card is on the list.

---

### Post by billcat on 2009-05-19
You can try this link for the compiz fusion forums: [http://forum.compiz-fusion.org/]("http://forum.compiz-fusion.org/")

Also there&#347; a really good ap that will tell you about your card&#347; adaptability here:
[http://forlong.blogage.de/entries/pages/Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")

---

### Post by dominic23 on 2009-05-20
thanks for answering. the graphic card doesn't show up. do you know why that is?

---

### Post by dominic23 on 2009-05-20
thanks to you too billcat.great help

---

### Post by skymera on 2009-05-20
What is your graphics card?

Please post the output of 

```
 lspci 
```

---

### Post by alphacrucis2 on 2009-05-20
To find out what your graphics card is identified as, select Applications Accessories Terminal and then type:



```
lspci | grep VGA
```

---

### Post by bacardiandwatermelon on 2009-05-20
System->Preferences->Appearance->Visual Effects->Extra?

---

### Post by alphacrucis2 on 2009-05-20
> **bacardiandwatermelon said:**
> System->Preferences->Appearance->Visual Effects->Extra?

Good point. Has he actually activated compiz.

---

### Post by dominic23 on 2009-05-20
v 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
05:01.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
dominic@ubuntu:~$

---

### Post by skymera on 2009-05-20
You have a VIA graphics chip.

My laptop has VIA and i've never gotten 3D to work.
You can use the OpenChrome driver, but it has no 3D support.

---

### Post by DonThompson on 2009-05-21
Here's what bugs me about this VIA chipset...

I was running 8.something SERVER with a GUI added (despite the advice of the command line experts) and had good resolution - 1024 x 768.  It offered better, but I like using VNC 'cause I'm too lazy to walk over to the servers.  I replaced the machine with a better server and put on 9.04 desktop, and cannot get above 800x600 -  which I thought not enough for a server, so my opinion of a low-res desktop is not good.  I followed the instructions in the long post about movies, and they now work fine (better than fine!) BUT I can not get it to (a) recognize my chipset or monitor or b) give me decent graphics.  

In response to:
   lspci | grep VGA
I get: 
   01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

Don't know what it means other than lspci is able to read the name of the chipset.

---

