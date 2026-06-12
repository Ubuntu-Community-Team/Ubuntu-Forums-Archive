---
title: "I'm frustrated, wireless internet help?"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by a cup of tea on 2009-03-09
I decided to try Linux yesterday and I installed Ubuntu 8.10. I want to get wireless internet working. I tried typing "lspci -v | less" at the terminal and I think I broke the terminal. :confused:

screenshot of that:
[http://img12.imageshack.us/img12/7598/lspcivless.png](http://img12.imageshack.us/img12/7598/lspcivless.png)

I've been trying to search for info about how to get the wireless working and am just getting more confused. Maybe someone can point me in the right direction?

---

### Post by Svensk023 on 2009-03-09
you did not break terminal my friend haha. but here is a link to a how-to that helped me out when i got a new laptop a little while ago.
[http://ubuntuforums.org/showthread.php?t=885847]("http://ubuntuforums.org/showthread.php?t=885847")

you may also want to look around the networking & wirless threads for any further answers concerning your problem

---

### Post by Abu_Dayya on 2009-03-09
Don't be afraid from the terminal. There is nothing called "I broke the terminal". The colons you see at the end of the terminal is for navigation.

'Enter' to drop one line down
'Space' to drop one page down
'q' to quit

Or you can close the terminal and fire another one. You can even open more than one terminal at the same time

---

### Post by halovivek on 2009-03-09
can you post the output from terminal 
lspci

---

### Post by a cup of tea on 2009-03-09
Thanks. The output from lspci:

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:07.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 30)
00:0a.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:0a.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:0e.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5000 802.11a Wireless Adapter (rev 01)

```

I also took a look at the link Svensk023 gave, but I don't know if I have (or should have?) ndiswrapper.

---

### Post by Doug11 on 2009-03-09
> **a cup of tea said:**
> Thanks. The output from lspci:

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:07.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 30)
00:0a.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:0a.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:0e.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5000 802.11a Wireless Adapter (rev 01)

```

I also took a look at the link Svensk023 gave, but I don't know if I have (or should have?) ndiswrapper.

Have a look at this,,it may help

[http://ubuntuforums.org/showthread.php?t=800686&highlight=atheros+ar242x](http://ubuntuforums.org/showthread.php?t=800686&highlight=atheros+ar242x)

---

### Post by 3rdalbum on 2009-03-09
1. I believe you mean wireless network, not wireless internet (wireless internet is where you use the mobile phone network).

Your wireless network chipset is the Atheros AR5000. There is a capable driver for this chipset that does not require Ndiswrapper; it's not included in Ubuntu 8.10 but it is available easily.

First you need to connect your computer to your wireless router, via an Ethernet cable, so you can download the driver.

Second: Go to System > Administration > Software Sources and under the Updates tab, make sure that "intrepid-security", "intrepid-backports" and "intrepid-updates" are ticked and enabled. If they aren't, then tick them now. Click Close, and you'll be asked if you want to reload the package list. Do it.

After that has all finished, go into a terminal (Applications > Accessories > Terminal). Type the following or copy and paste it in:

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

You'll be asked for your password - type it in and be aware that it won't show the characters as you are typing them. The package management system will download the driver you want.

(Note, you could have also used Synaptic Package Manager to install this package).

After the package has been installed, open the modules (drivers) file by typing this into the terminal:

```
gksudo gedit /etc/modules
```

At the very bottom of the file, type this on a new line:

```
ath5k
```

Save your changes and close.

Now you need to open the Blacklist file - this allows you to stop the old driver from trying to take over the device. Type this into the terminal:

```
gksudo gedit /etc/modprobe.d/blacklist
```

At the end of this file, on a new line, type this:

```
ath_pci
```

Save changes and close. Restart the computer and your wireless network should work.

These steps will not be necessary for the next version of Ubuntu; unfortunately when Ubuntu 8.10 was released, there was a gap in support between the two drivers. This, I believe, has been fixed now, but the change will not come until the next version of Ubuntu (April 2009).

---

### Post by Miljet on 2009-03-09
3rdalbum, your answer should serve as a model for all replies in this forum. It includes step by step instructions and explanations for why each step is required. Thanks for taking the time to compose a real reply instead of just "See such-and-such post."

---

### Post by MrWES on 2009-03-09
> **Miljet said:**
> 3rdalbum, your answer should serve as a model for all replies in this forum. It includes step by step instructions and explanations for why each step is required. Thanks for taking the time to compose a real reply instead of just "See such-and-such post."

Amen! well said and nicely done.

---

### Post by 3rdalbum on 2009-03-09
You're welcome!

---

### Post by a cup of tea on 2009-03-09
> **3rdalbum said:**
> 1. I believe you mean wireless network, not wireless internet (wireless internet is where you use the mobile phone network).

You're right, I do mean wireless network.

I followed 3rdalbum instructions, which were great (thank you for taking the time to do all that!) I wish I could say it works now, but it still doesn't. I looked at Doug's link, and I could try that, but I don't have the Atheros 5007 (?) and I'm using 8.10 of Ubuntu rather than 8.04. How do I know if the instructions in that thread are applicable to my situation, and will I make things worse if I try that and it doesn't work?

---

### Post by a cup of tea on 2009-03-09
This is an update to say that my issue is now resolved. Thank you.

---

### Post by bodhi.zazen on 2009-03-09
Awesome

for the benefit of others , could you explain how you solved your problem ?

---

