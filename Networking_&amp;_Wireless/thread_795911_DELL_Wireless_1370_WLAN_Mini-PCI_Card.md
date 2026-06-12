---
title: "DELL Wireless 1370 WLAN Mini-PCI Card"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by dec27george on 2008-05-15
I have a Dell B130 with a DELL Wireless 1370 WLAN Mini-PCI Card.

I have installed Ubuntu 8.04, but it cannot connect to the internet.  I installed Ubuntu through Wubi Installer, so I can connect to the interent through my xp sp3 home os.  Do I need to install a driver on Ubuntu?  Please help.  I'm a newbie on this stuff.

dec

thank you

---

### Post by Ayuthia on 2008-05-15
> **dec27george said:**
> I have a Dell B130 with a DELL Wireless 1370 WLAN Mini-PCI Card.

I have installed Ubuntu 8.04, but it cannot detect wireless.  How do I get a driver for this?

thank you
Can you go to the Terminal and post the results of lspci -nn?  It will help us see what the Dell Wireless 1370 really is.  If you do not have a working connection, please look for Network Controller or Ethernet Controller in the list of items and provide that information.  Thanks!

---

### Post by dec27george on 2008-05-16
I am a noob, so I'm not sure how to do that.

---

### Post by Ayuthia on 2008-05-16
If you go to Applications->Accessories->Terminal, a window will pop up that will look like the old DOS window.  Just type the following:
```
lspci -nn
```and press enter.
It will list out your PCI devices.  Look for anything that has Network Controller or Ethernet Controller.  One of them will be your wireless card.  Highlight it and copy it (control-shift-c) and paste it into your post (if you have a wired connection).  If you don't have a connection, please tell us what brand and model it is.

Here is what the information should look like:
```
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

```As you can see, there are two items that have either Ethernet Controller (nVidia MCP51) or Network Controller (Broadcom BCM94311MCG rev 01).  Just report back something like nVidia MCP51 or Broadcom BCM94311MCG rev 01.

---

### Post by glitter_cowgirl on 2010-04-08
Broadcom Corporation BMC4318 [AirForce One 54g]  802.11g Wireless LAN Controler

I have the same laptop and I am working on getting the wireless working on it.  I luckily have ethernet available but I am having a hard time finding a driver that I can get to work with the ndiswrapper.

---

### Post by PRC09 on 2010-04-08
Dont know if this will help but.....


[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by tator_tot2010 on 2010-05-05
I'm having a very similar issue on my Latitude D610.... I have a Dell Wireless 1370 WLAN Mini-PCI card, and naturally I can't get it to work right. When I run lspci in the terminal, it shows:

03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

That's just in regards to my wireless card, I didn't think anything else would need to be posted... If I missed something just say so. Pretty sure I'm running Ubuntu 10.04....

I have Internet access when I switch back to Windows - I have a dual-boot thing going on. That's the only way I can get wireless, and I don't have access to a wired connection. I'm also fairly new at dealing with Ubuntu, so please bear with me. XD

---

