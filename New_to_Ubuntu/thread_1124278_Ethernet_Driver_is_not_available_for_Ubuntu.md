---
title: "Ethernet Driver is not available for Ubuntu"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by tkli on 2009-04-13
I just installed Ubuntu 8.10 yesterday but when I tried to install the driver for the onboard ethernet card, I couldn't found a suitable driver for ubuntu.

Here's the relevant hardware spec.:
Realtek RTL8110SC Ethernet Card (onboard)
Motherboard: ASUS P5SD2-VM

Ethernet drivers available from the asus support website:
- Mandriva2007
- sis19x_2.6.18_FC6_1.00.01
- sis19x_RHES4.4_2.6.9-42_1.01_x86
- suse10.1

I suppose I can only do the followings:
1. Somehow convert the above drivers to make it workable on ubuntu
2. Buy a new ethernet card

Any advice would be appreciated. Thanks!

---

### Post by spiderbatdad on 2009-04-13
[http://ubuntuforums.org/archive/index.php/t-629878.html](http://ubuntuforums.org/archive/index.php/t-629878.html)

another thread suggested the card should work and needs to be enabled in the bios.

---

### Post by lkraemer on 2009-04-13
You have two ways to proceed.
1. Install the Windows Drivers ??.inf & ??.sys with ndiswrapper,
assuming that ndiswrapper is installed, or that you want to use 
this method.
2. Download the specific software, or firmware (Broadcom), and
   use it to get your Wifi working.

Open a Terminal window and do the following:
```

ndiswrapper -l
iwconfig
lsmod
cat /etc/modprobe.d/blacklist

```
Then post all of the output from these commands.

Next, decide what method you want to use.

You should be able to search the forum for "HOWTO: & AR242x",
or for Broadcom use "HOWTO: & BCM4318" and find a guide for
installing your Wifi.

lkraemer

---

### Post by spiderbatdad on 2009-04-13
> **lkraemer said:**
> You have two ways to proceed.
1. Install the Windows Drivers ??.inf & ??.sys with ndiswrapper,
assuming that ndiswrapper is installed, or that you want to use 
this method.
2. Download the specific software, or firmware (Broadcom), and
   use it to get your Wifi working.

Open a Terminal window and do the following:
```

ndiswrapper -l
iwconfig
lsmod
cat /etc/modprobe.d/blacklist

```
Then post all of the output from these commands.

Next, decide what method you want to use.

You should be able to search the forum for "HOWTO: & AR242x",
or for Broadcom use "HOWTO: & BCM4318" and find a guide for
installing your Wifi.

lkraemer

ummm. no.

---

