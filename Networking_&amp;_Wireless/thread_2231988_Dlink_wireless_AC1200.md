---
title: "Dlink wireless AC1200"
date: 2014-06-29
forum: Networking &amp; Wireless
---

### Post by granul on 2014-06-29
I am trying to make my usb wifi adapter to work. I tried with ndiswrapper and not working. Any drivers somerwhere for this.

I found instruction for D-Link DWA-182 Drivers for Linux so i download the file RTL8812AU_linux_v4.3.2_11100.20140411 and tried to install with no sucess I follow the instruction on this page: 
[http://www.rqna.net/qna/ryirhq-d-link-dwa-182-drivers-for-linux.html](http://www.rqna.net/qna/ryirhq-d-link-dwa-182-drivers-for-linux.html)

Thank you

---

### Post by Bucky Ball on 2014-06-29
Plug in the USB dongle and run this:

```
sudo lshw -C network
```

Post the output back here. With it plugged in, do an update and then check Additional Drivers. Anything there pertaining to the wireless card?

You say you had no success installing the driver on that link. What errors were you getting exactly? Had you extracted the driver, *_navigated to the correct directory_*, then run those commands? If you did all this right, what is the error you're getting?

---

### Post by Vladlenin5000 on 2014-06-29
Why would drivers made for a specific revision (rev. C only - rev. A is an entirely different hardware and D-Link doesn't provide drivers for that) of a specific model work for an entirely different hardware?  
And AC1200 seems to be a router: [http://www.dlink.com/us/en/home-solutions/connect_us/routers/dir-860l-wireless-ac1200-dual-band-gigabit-router](http://www.dlink.com/us/en/home-solutions/connect_us/routers/dir-860l-wireless-ac1200-dual-band-gigabit-router) ... As such I don't understand what are you trying to achieve here.:confused:

Also, as exemplified above, the brand/model is seldom useful. What really matter is the chipset inside and there's only a handful of wifi chipsets we have to account for. Fortunately most of them just work. Others like your need a little bit of love.
An easy way to determine what you really have is by issuing the following command in terminal (it lists all the USB devices): ```
lsusb
```

---

### Post by granul on 2014-06-29
There were no error when I install, but it still not working

[PHP]Bus 002 Device 002: ID 04f2:b3d6 Chicony Electronics Co., Ltd Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 004 Device 002: ID 04ca:300b Lite-On Technology Corp. Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubBus 001 Device 003: ID 2001:3315 D-Link Corp. Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying ReceiverBus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubBus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hubBus 005 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB StickBus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/PHP]

---

### Post by Bucky Ball on 2014-06-29
Bit of confusion here. You appear to have posted the output of 'sudo lshw -C network' on the wrong thread. I consequently jailed it. For the benefit of all, here is the relevant bit:

```
description: Interface réseau sans fil
produit: QCA9565 / AR9565 Wireless Network Adapter
fabriquant: Qualcomm Atheros
identifiant matériel: 0
information bus: pci@0000:05:00.0
nom logique: wlan0
version: 01
numéro de série: a4:db:30:80:4a:82
bits: 64 bits
horloge: 33MHz
fonctionnalités: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
configuration: broadcast=yes driver=ath9k driverversion=3.13.0-24-generic firmware=N/A ip=192.168.1.217 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
ressources: irq:32 mémoire:f0100000-f017ffff mémoire:f0300000-f030ffff  
```

Well, you seem to have the correct driver installed, but no firmware. Not sure if necessary with this card. Apart from that, all looks good. 

When you click on the network icon do you get a list of available networks? You say you are trying to get it working, but what is telling you that it is not, apart from the fact you are not automatically online? Error messages? Can't get on the web? Can't update?

BTW: ndiswrapper should be avoided at all costs unless there is absolutely no other alternative. Largely superseded and generally causes more issues than it fixes now.

---

### Post by Vladlenin5000 on 2014-06-29
Here it is: [http://www.linux-hardware-guide.com/uk/2013-11-16-d-link-dwa-182-ac1200-wifi-dual-band-usb](http://www.linux-hardware-guide.com/uk/2013-11-16-d-link-dwa-182-ac1200-wifi-dual-band-usb)

Broadcom BCM43526 chipset

> Currently no Linux driver is available for the DWA-182.
Not good...

---

### Post by granul on 2014-06-29
Yes i see the network but using the pci wifi from the laptop but I don't network for the usb wifi.

---

### Post by Bucky Ball on 2014-06-29
> **Vladlenin5000 said:**
> 
Broadcom BCM43526 chipset




Not what it tells us in the terminal output I posted in post #5: produit: QCA9565 / AR9565 Wireless Network Adapter.

That's an Atheros, the Ath9k driver is installed and the device has even been assigned an IP address. Unless, of course, this is referring to an internal card.

@OP: Do you have an internal card as well as the external dongle? The internal card appears to be up and running (ndiswrapper may be preventing it from connecting).

---

### Post by granul on 2014-06-29
Yes exactly, the Atheros is the wifi that comes with the laptop but the usb wifi is not working.

---

### Post by Bucky Ball on 2014-06-29
Okay, got you. Might be an idea to switch the other one off to avoid confusion. We don't want to create a 'dog's breakfast' and having one connected will probably prevent the other.

---

### Post by granul on 2014-06-29
> **Bucky Ball said:**
> Okay, got you. Might be an idea to switch the other one off to avoid confusion. We don't want to create a 'dog's breakfast' and having one connected will probably prevent the other.


So you mean to swich off the Atheros, if I do this I have no cennection

---

### Post by granul on 2014-06-29
I decided to return the Dlink AC1200 to the store to complicate for linux driver, I have a dw1-131 witch is working out of the box,

---

### Post by Bucky Ball on 2014-06-29
Excellent. Please mark the thread as solved to help others. Thanks.

---

### Post by El Bartolomew on 2015-01-31
Just to let you know:You can download latest linux driver at the website of D-linkinstall the folder and cd to the folder in terminal and sudo sh install.sh will do the tricksupports only kernel 2.6.18 - 3.10 so anything above is in trouble

---

### Post by Bucky Ball on 2015-01-31
> **El Bartolomew said:**
> Just to let you know:You can download latest linux driver at the website of D-linkinstall the folder and cd to the folder in terminal and sudo sh install.sh will do the tricksupports only kernel 2.6.18 - 3.10 so anything above is in trouble

Thanks for your input, and thanks for sharing, but the thread was solved six months ago. If your would like to provide a tutorial for future travelers, there is a sub-section for that. :)

Welcome to the forums and good luck.

---

