---
title: "D-Link AirPlusG DWL-G630 H/W C2 F/W 3.01"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by cqfast on 2008-05-17
I updated from Ubuntu 7.10 to 8.04 in the hopes of getting my D-Link wireless PCMCIA card working on my Dell Latitude C810 laptop.

According to the following websites, the chipset for my wireless DWL-G630 H/W: C2 F/W: 3.01 is the Atheros AR5005G and is supported by madwifi:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink")
[http://madwifi.org/wiki/Compatibility/D-Link]("http://madwifi.org/wiki/Compatibility/D-Link")

Up to this point, whenever my D-Link PCMCIA card was inserted, only the D-Link's "Act" LED blinked.

When I installed the 3 packages linux-restricted-modules-2.6.24-16-generic, linux-restricted-modules-common, and madwifi-tools and rebooted twice, then the System->Administration->Hardware Drivers indicated that I had restricted drivers available for my wireless card (it also indicated availability of a restricted driver for my nvidia display).

Happy to see my wireless card recognized by "Hardware Drivers", I followed the madwifi directions and gave the command ```
sudo modprobe ath_pci
```  As a result, the D-Link's "Link" LED also began to blink.  I thought this was good progress, but unfortunately the other result was that my keyboard/mouse no longer responded.  I could not switch to a text mode (ctrl-alt-f2) or restart X (ctrl-alt-backspace).  After a few minutes of fruitless waiting, I popped out the D-Link PCMCIA card and then my keyboard and mouse resumed as normal.

Unfortunately, after rebooting my laptop, the D-Link PCMCIA card was no longer recognized by "Hardware Drivers" (which listed only the nvidia restricted driver).  My further attempts to uninstall and reinstall the 3 packages mentioned earlier never did get the "Hardware Drivers" to list the wireless restricted drivers again.  It seems that I had only one chance and I blew it!

Now when I give the command "sudo modprobe ath_pci" the module is added, but the wireless card does not react.  The madwifi command ```
sudo wlanconfig ath0 create wlandev wifi0 wlanmode sta
``` always just complains: ```
wlanconfig: ioctl: No such device
```  I presume this will continue to be the case until my card is recognized again by Ubuntu.

Since I had read on several forums that I should try the latest madwifi drivers, I uninstalled the 3 packages mentioned earlier, downloaded the latest SVN snapshot of madwifi and successfully built and installed it.  "Hardware Drivers" still does not recognize my card, and the command "sudo modprobe ath_pci" does not affect the wireless card.  The "wlanconfig" command still complains about "no such device".

So, I appear to have 2 different issues:

1. Getting Ubuntu "Hardware Drivers" to recognize my D-Link PCMCIA wireless card again.

2. Once the wireless card is recognized, how to correctly configure it for use such that my keyboard/mouse do not freeze up

To provide some additional history, I had attempted to get this card to work with Ubuntu 7.10 with almost identical results.  The card was recognized during a bootup and presumably the drivers were activated because I saw the D-Link's "Link" LED blinking during bootup.  At that point, the bootup was frozen until I popped out the D-Link PCMCIA card.  After that, the bootup continued but the card was never recognized again.

I had even tried the ndiswrapper approach using a Windows XP driver from dwlg630_driver_300.zip, but the System->Administration->Windows Wireless Drivers claimed that the hardware was not present (probably related the same issue as in my #1 above).

Here's what I currently see from "lspci" when the wireless PCMCIA card is inserted (and only the D-Link's "Act" LED is blinking):

```
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
02:06.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
02:06.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller

```

Any thoughts on my #1 and #2 issues?

---

### Post by cqfast on 2008-05-22
BUMP

I'm hoping someone can at least tell me what files to edit to convince Ubuntu/Linux that it has never seen my wireless PCMCIA card before.  Then perhaps I could at least reproduce my issue #2.

---

### Post by Ai1dRo0kNotBot on 2008-05-31
1. Try using search on this forum.
2. Your D-Link (as well as mine) has rt61 chip inside, which means you can use _working_ driver.
Here [http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)
There is a minor disadvantage: you should compile it.

---

### Post by cqfast on 2008-06-03
> **Ai1dRo0kNotBot said:**
> 1. Try using search on this forum.
2. Your D-Link (as well as mine) has rt61 chip inside, which means you can use _working_ driver.
Here [http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)
There is a minor disadvantage: you should compile it.

I had hoped that my detailed first posting would be evidence for the significant forum searches I had already performed!  The forums (and the other links I provided) indicate that my chipset is the Atheros.  You apparently have a different chipset in your D-Link.  In any case, thanks for responding.

---

### Post by buddycraigg on 2008-07-06
I'm hoping you get this figured out.
i've got the same setup except i'm using a Dell C600

---

### Post by cqfast on 2008-07-07
> **buddycraigg said:**
> I'm hoping you get this figured out.
i've got the same setup except i'm using a Dell C600

Sorry, I have not gotten any further with this problem, and have not wanted to reinstall Ubuntu just to give Linux another chance to recognize the wireless card.  Perhaps I'll have success upgading to the next version of Ubuntu when it is released.

---

