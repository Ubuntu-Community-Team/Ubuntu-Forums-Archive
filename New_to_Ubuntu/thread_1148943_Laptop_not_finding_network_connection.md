---
title: "Laptop not finding network connection"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Neon612 on 2009-05-04
Laptop not finding Network Connection
I just did a clean install of Ubuntu 8.04, and so far have had no luck getting connected to our home network (wired). What do I do to get it connected? Its a Toshiba Satellite P305-8900, if that is of any help.

Or how do I find out if I have the correct drivers needed for the network card?

Thank you

---

### Post by cmnorton on 2009-05-04
Is Network Manager running? It's an icon that is probably on the upper toolbar to the right.

---

### Post by lisati on 2009-05-04
Some of us on the forums have Toshiba laptops as well, so there's a chance someone with one similar to yours might be able to help. Please post the output from the following command: ```
lspci
```

---

### Post by Neon612 on 2009-05-04
> **cmnorton said:**
> Is Network Manager running? It's an icon that is probably on the upper toolbar to the right.

Yes that icon is present, with a large red "X" infront of the two computer screens.

> **lisati said:**
> Some of us on the forums have Toshiba laptops as well, so there's a chance someone with one similar to yours might be able to help. Please post the output from the following command: ```
lspci
```

lspci output
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Unknown device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
02:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4355 (rev 12)
09:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
09:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```

---

### Post by lisati on 2009-05-05
Apologies for the delay responding.
What the output from lspci tells me is that Ubuntu isn't recognising your network card(s). Because your machine is a different model to the Toshiba laptops I use (both of which connect to my home network "out of the box"), I'm not sure what it should be showing, and would welcome suggestions from other Toshiba users.

---

### Post by Neon612 on 2009-05-05
One quick question. Is it the Network controller (Atheros) or the Ethernet controller (Marvell) that runs the wired network port?

---

### Post by anewguy on 2009-05-05
The Atheros will be the wireless.  Does your model show anything other than P305-8900?  According to Toshiba's support site, they would be P305-Sxxxx, and they don't show just an 8900, they show things like S8904, S8910, S8915 and S8920.  They appear to have sub-models of the S8904 as S89041 and the S8915 as S89151.

On the support site, they have a link for the wireless driver for Vista, available as 32 or 64 bit for a large series of these laptops at:

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2234099&rpn=PSPCCU&modelFilter=P305-S8906&selCategory=3&selFamily=1073768663]("http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2234099&rpn=PSPCCU&modelFilter=P305-S8906&selCategory=3&selFamily=1073768663")

I'm not sure what Atheros chipset is being used yet.  I'll see if I can extract anything from the driver download and then see if there is something compatible for Linux.

Toshiba also has a link on their support site to another site that provides Linux support.  It looks like they are away until May 6, but I may be worth checking there as well to see which wireless driver they are using in Linux.

My suspicion is that you are going to need the madwifi drivers - perhaps someone else with experience with those can also post to you here.

dave :)

---

### Post by Neon612 on 2009-05-05
Oops. Sorry about that the number is P305***D***-***S***8900.

The wireless, I assume works fine, but I am not sure seeing as the nearest WiFi access point only gives me a reading of 10-20%. I'm trying to get the wired port setup to work with my home network at the moment. And, if I'm reading the lspci output right then the wired netwqork connection will be the Marvell Ehternet Controller. Am I correct?

---

### Post by tmos22 on 2009-05-05
Try this guide it work for me

[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)

---

### Post by Neon612 on 2009-05-05
I'm not sure if I'm making myself clear here, but I DO NOT need drivers for wireless. I NEED drivers for wired.

---

### Post by unrealfighter on 2009-05-05
There seems to be a bug in ubuntu 8.04 
[https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/239852](https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/239852)
If somehow you can not get this fixed, why not try ubuntu 9.04? I had a wireless card on my pc that didn't work with 8.04, but works perfectly with 9.04.

---

### Post by unrealfighter on 2009-05-05
On another thread, it seems that they have a very simple solution for this to work.

 Re: Ubuntu 8.04 with Marvell Yukon 88E8040T
OK, I hope the following instructions should help. All you need to do is to open a terminal and copy-paste the following commands.

Code:

$ sudo su -
[type your password]
# rmmod sky2
# cd /lib/modules/`uname -r`/kernel/drivers/net
# cp -p sky2.ko{,.orig}
# perl -pe 's/\0\0\x6c\x43/\0\0\x55\x43/g' sky2.ko.orig > sky2.ko
# echo sky2 >> /etc/modules
# modprobe sky2

The last command loads the fixed driver and you should see it detect your network card like this:
$ dmesg | grep sky2
[ 30.364735] sky2 0000:07:00.0: v1.20 addr 0x88000000 irq 17 Yukon-FE+ (0xb8) rev 0
[ 30.365174] sky2 eth0: addr 00:1e:68:46:d3:34
[ 33.962661] sky2 eth0: enabling interface

On next reboot, the driver should load automatically, so all you need to do is to configure the network parameters then.

Obviously, when you upgrade your kernel (e.g. via Synaptic) you should repeat all the commands up to the "perl" line.

HTH.
Last edited by wanted; June 29th, 2008 at 05:26 PM.

I hope this works for you!

---

### Post by Neon612 on 2009-05-06
THanks for all the help guys. I figured it woul dbe easier if I just upgraded. My laptop is now the proud owner of Jaunty Jackalope.

Thank everyone for all the help.

---

### Post by unrealfighter on 2009-05-07
Well done :) Faster and more compatible! Ubuntu seems to always get better and better!

---

### Post by anewguy on 2009-05-07
Sorry I missed that you were looking for help on your wired connection, not the wireless.  In addition, anyone else who may read this, I messed up in thinking the madwifi drivers in addition, as I think those would have been for a different chipset anyway.

Again, sorry!

Dave :)

---

