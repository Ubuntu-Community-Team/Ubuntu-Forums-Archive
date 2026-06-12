---
title: "No wireless signal"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by Grimnir512 on 2008-04-10
Hello all,

I can't seem to connect to my wireless network; when set to roaming mode it seems to find it and the bar next to the essid is about one segment full; but when I click it it asks for the WEP kep, which I enter. It then proceeds to say that it has a 0% signal and then about 30 seconds later, the WEP key entry appears again. The WEP key is definetly correct.

The wireless card is a Belkin F5D6020 version 2, which does seem to pick up the network but not connect.

I have tried the troubleshooting in the FAQ but it didn't seem to help, and I couldn't get step one:

> Check for device recognition

   1.

      Open Device Manager (System &#8594; Administration &#8594; Device Manager).
   2.

      Check to see the hardware is recognised if it is then the section called &#8220;Check for driver&#8221;
   3.

      If your device is not displayed then there ma be a hardware problem. Ensure if it is PCMCIA or PCI that it is inserted correctly.



Device manager isn't there.

Thanks for your help :)

EDIT: I am running Ubuntu Version 7.10

---

### Post by Sam Lars on 2008-04-10
Could you post the output of
```
lspci
```
and
```
iwconfig
```
from a terminal?

---

### Post by Grimnir512 on 2008-04-10
lspci:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller (rev 01)

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 14)

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller

00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]

00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)

00:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)

```


iwconfig:

```
lo        no wireless extensions.



eth0      no wireless extensions.



eth1      IEEE 802.11-DS  ESSID:"DownieNet"  

          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:17:3F:15:D0:9D   

          Bit Rate:11 Mb/s   

          Retry short limit:7   RTS thr:off   Fragment thr:off

          Power Management:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Hope that helps :)

---

### Post by Sam Lars on 2008-04-10
Try right clicking on the menu on the panel and selecting Edit.  See if you can enable the Device Manager you're looking for.
Nothing seems to look like a wireless device in what you posted; can you see it in the device manager?

---

### Post by brian_p on 2008-04-10
> **Grimnir512 said:**
> lspci:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller (rev 01)

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 14)

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller

00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]

00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)

00:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)

```

This tells you your card wasn't detected. The F5D6020 is in my /usr/share/misc/pci.ids. You can check yours with

```
less /usr/share/misc/pci.ids
```

Not there? Do

```
sudo update-pciids
```

---

### Post by Grimnir512 on 2008-04-10
> **Sam Lars said:**
> Try right clicking on the menu on the panel and selecting Edit.  See if you can enable the Device Manager you're looking for.
Nothing seems to look like a wireless device in what you posted; can you see it in the device manager?

I'll try that.

OK, I tried finding the device manager, but no luck.

> **brian_p said:**
> This tells you your card wasn't detected. The F5D6020 is in my /usr/share/misc/pci.ids. You can check yours with

```
less /usr/share/misc/pci.ids
```

Not there? Do

```
sudo update-pciids
```

What am I looking for when I enter the first one? I just get a bit that tells me about vendors.

After trying the second one, it didn't work, since I have no internet on the computer I am running Ubuntu on. I'm trying to set it up at the moment with a modem though :)

---

### Post by brian_p on 2008-04-10
> **Grimnir512 said:**
> What am I looking for when I enter the first one? I just get a bit that tells me about vendors.

Whether your card is listed there. Use the / key to search.

> After trying the second one, it didn't work, since I have no internet on the computer I am running Ubuntu on. I'm trying to set it up at the moment with a modem though :)

An up-to-date list is at

[http://pciids.sourceforge.net](http://pciids.sourceforge.net)

---

### Post by Grimnir512 on 2008-04-15
> **brian_p said:**
> Whether your card is listed there. Use the / key to search.



An up-to-date list is at

[http://pciids.sourceforge.net](http://pciids.sourceforge.net)

Sorry I haven't replied for a while, I was on holiday.

I'll have another look.

One other thing. While on holiday I managed to get it to connect to an unencrypted hotspot (which required payment to use, so all I got was a splash), but not the free, encrypred one provided by the hotel. Suggests to me the card works.

---

