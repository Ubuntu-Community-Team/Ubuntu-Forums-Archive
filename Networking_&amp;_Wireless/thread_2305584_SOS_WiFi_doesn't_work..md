---
title: "SOS: WiFi doesn't work."
date: 2015-12-07
forum: Networking &amp; Wireless
---

### Post by rebelrobot on 2015-12-07
Hello everyone, 

First of all I'd like to apologise in advanced for my poor english. And I know this problem probably has been solved already but I'm not able to find a solution. I'm new in lubuntu.

 I instaled lubuntu in a Acer Aspire 7111WSMi laptop. Everything is working fine but the wifi. The problem is that I can't connect the laptop to the network. I think it's have to do with the drivers. I come from windows so pls I would appreciate if you can guide me.

my wireless device is a Broadcom BCM5318 [Air force one 54g] 802.11g (rev 02)

thanks in advanced.

---

### Post by Rex Bouwense on 2015-12-07
I think that you will find your answer here:  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) 
Broadcom cards were a pain until I found that page.

Did you say that your card was 5318 or is that a typo and should be a 4318?

---

### Post by Bucky Ball on 2015-12-07
Welcome. Please get online with a cable and do an update (Software Updater I think in Ubuntu) then check additional drivers. What do you see there?

---

### Post by chili555 on 2015-12-07
Please check here: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by Rex Bouwense on 2015-12-07
+1.  I saw your stickie after I edited.

---

### Post by rebelrobot on 2015-12-07
Hi there, thanks for your reply.
Yes it is a typo.. My device is a BCM 4318. I've followed the instructions in your link.
I executed:
lspci -vvnn | grep -A 9 Network 

and I got the following:


josemg@josemg-Aspire-7110:~$ lspci -vvnn | grep -A 9 Network
0a:05.0 Network controller [0280]: **Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)**
    Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at d0004000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use**: b43-pci-bridge**

0a:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]

---

### Post by rebelrobot on 2015-12-07
> **Bucky Ball said:**
> Welcome. Please get online with a cable and do an update (Software Updater I think in Ubuntu) then check additional drivers. What do you see there?

Hi there.

In fact I updated lubuntu right after installing. It's up to date.
Following your instructions, I've checked for additional drivers and this is what came out:

[ATTACH=CONFIG]266023[/ATTACH]

---

### Post by chili555 on 2015-12-07
Additional Drivers, which installs *bcmwl-kernel-source*, is incorrect for your device. Again, please see the link I gave above.

---

### Post by rebelrobot on 2015-12-08
> **chili555 said:**
> Additional Drivers, which installs *bcmwl-kernel-source*, is incorrect for your device. Again, please see the link I gave above.

Ok I got it working. I followed the instructions given in your link.  Now everything is working perfectly!

Thank you so much for your help.):P

---

### Post by Bucky Ball on 2015-12-08
Good news and thanks chili. Please see the first link in my signature and enjoy the forums and OS. :)

---

