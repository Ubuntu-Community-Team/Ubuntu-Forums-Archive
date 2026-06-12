---
title: "I have an Acer Aspire how do I get wireless?"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by friyia@hotmail.com on 2009-08-28
Hey guys I just put Kubuntu on My acer and I don't know how to get the wireless working can anyone help me out?

---

### Post by mgranet on 2009-08-28
What model # is your Acer?

---

### Post by mapes12 on 2009-08-29
> **friyia@hotmail.com said:**
> Hey guys I just put Kubuntu on My acer and I don't know how to get the wireless working can anyone help me out?
If it's a built in wifi adapter in Terminal ```
lspci
``` and post the output back here. If it's a usb wifi then ```
lsusb
```

---

### Post by k3lt01 on 2009-08-29
If its an Aspire 5100 your wireless should work without any problem immediately with Jaunty, it should work with a LiveCD. Hardy and Intrepid however need a little work and a madwifi module.

---

### Post by Paqman on 2009-08-29
Have you checked in Hardware drivers? There may be a driver sitting there waiting for you to give it the thumbs up. I've had a couple of Acer laptops and they both used Broadcomm wifi cards that need a little help from Hardware Drivers to get running.

---

### Post by friyia@hotmail.com on 2009-08-29
> **mapes12 said:**
> If it's a built in wifi adapter in Terminal ```
lspci
``` and post the output back here. If it's a usb wifi then ```
lsusb
```

I ended up getting 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)                                                                                      
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

does that tell us anything?

---

### Post by LewRockwell on 2009-08-29
> **friyia@hotmail.com said:**
> I ended up getting 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)                                                                                      
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

does that tell us anything?

what's the model number on that unit

should be something like aoa-110-1010

wheeeeeee, let's go on a fishin' expedition...

.

---

### Post by friyia@hotmail.com on 2009-08-29
> **LewRockwell said:**
> what's the model number on that unit

should be something like aoa-110-1010

wheeeeeee, let's go on a fishin' expedition...

.

how do I figure out the model number?

---

### Post by mgranet on 2009-08-29
There should be a sticker somewhere on it. Usually on the bottom. Nevertheless, it appears to be using the Atheros wifi card. IIRC, many of these cards should work out-of-box with Jaunty. Your profile shows you running Intrepid. Have you upgraded?

---

### Post by friyia@hotmail.com on 2009-08-29
> **mgranet said:**
> There should be a sticker somewhere on it. Usually on the bottom. Nevertheless, it appears to be using the Atheros wifi card. IIRC, many of these cards should work out-of-box with Jaunty. Your profile shows you running Intrepid. Have you upgraded?

ya I have I just never bothered to change the thing srry :P but ya it was almost working until my Mom started playing with it and now like it won't pick up any kind of signal 

BTW Model No.ZG5

---

### Post by mgranet on 2009-08-29
A bit of further research reveals some problems with this particular card. See here:

[http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu](http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu)

[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/ubuntu-9.04-atheros-ar242x-wireless-744555/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/ubuntu-9.04-atheros-ar242x-wireless-744555/)


Hopefully one of these sites can provide you with some insight. It appears that you can force the card to work with the madwifi drivers, but it seems others are getting the card to work without installing drivers. Seems there's some bugs in the kernel.

---

### Post by ugm6hr on 2009-08-29
> **friyia@hotmail.com said:**
> 03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

This is your wifi card.

It works fine with (K)ubuntu.

As for how to install the driver (and which driver), that depends which version of Kubuntu you have.

---

### Post by friyia@hotmail.com on 2009-08-29
> **ugm6hr said:**
> This is your wifi card.

It works fine with (K)ubuntu.

As for how to install the driver (and which driver), that depends which version of Kubuntu you have.

I have Jaunty I usually keep up with the upgrades

---

### Post by k3lt01 on 2009-08-29
Your model is on a label on the right hand side bottom of the screen.

If you have the LiveCD handy try it without changing anything, in other words just use the "Live" part. See if your wireless works with that. If it does you may be able to roll back your kernel to a previous version until your wireless is stable again.

Edit: I may be a bit premature, I assumed it was a laptop, is it?

---

