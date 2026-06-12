---
title: "Enable to locate package bcmwl-kernel-source"
date: 2014-09-28
forum: Networking &amp; Wireless
---

### Post by olivier10 on 2014-09-28
Hi, 

I installed ubuntu 14 on a vostro 1000 via usb stick. no problem.

Can you help to clear error I got see picture attached.
Enable to locate package bcmwl-kernel-source

via terminal option
with sudo apt-get install bcmwl-kernel-source 

via software center
Using the source on my usb drive /pool/restrited/b/bcmwl

Problem with Dependency is not satisfiable : dkms

I tried to activate internet via wifi in order to have internet working...seems to be a common issue and I am not familiar with linux..

thx for help

Oliver

---

### Post by ubfan1 on 2014-09-28
Did you plug in an ethernet cable to get an internet connection?  The first error seems to imply you don't have any internet connectivity.  What wireless chip do you have?  Maybe you can use the default b43 driver, after you add in the firmware from the linux-firmware-nonfree package.

---

### Post by varunendra on 2014-09-29
Welcome to the forums Oliver!

The 'dkms' package is available under "/pool/main/d/dkms/" directory of the installation media, but then it further depends on the headers, build-essential etc. There are ways to install them, but the easiest is to install it while being connected to internet via an Ethernet (cable) connection. Or, while installing Ubuntu (just check the "Install Updates" option during installation). This driver works in Live mode, so if it is a fresh installation, never updated, a live session can make things easy like a breeze, but only if your card is indeed supported by this driver.

Like ubfan1 pointed out, are you sure this is really the driver you need? If unsure, please show us the output of -
```
lspci -nnk | grep -iA2 net
```

> **ubfan1 said:**
> Maybe you can use the default b43 driver, after you add in the firmware from the **[COLOR="#FF0000"]linux-firmware-nonfree[/COLOR]** package.
Unfortunately, the 'linux-firmware-nonfree' package no longer installs firmware for b43 driver. Please see this bug : [https://bugs.launchpad.net/bugs/1367882](https://bugs.launchpad.net/bugs/1367882)

Fortunately, installing the firmware manually or with 'firmware-b43-installer' package is equally easy.

---

### Post by olivier10 on 2014-09-30
Yes, I don't have internet connectivity and I see on the web that is common problem .

I did not plug to an ethernet cable ? Do you have to this ? 

Wireless chip is Broadcom Corporation BCM4311 802.11b/g WLAN

Ethernet controller :Broadcom Corporation BCM4401-B0 100Base-TX

---

### Post by olivier10 on 2014-09-30
Hi, I did manage to get internet working from ethernet with my MAC address and it's work, Now i need to make the wifi but at least i can surg on my machine instead to jumb from 2 machine. 

However I happy because I spent hours to get internet working....so thank you for your tips with ethernet .

I did it before but I have DSL set up to and system was confused, I think with Ethernet of DSL .

I will continue my investigation for setting WIFI. thx again

---

### Post by Vladlenin5000 on 2014-09-30
Now it's time for you to read again post #3 and do the proposed troubleshooting.

---

### Post by varunendra on 2014-10-01
@Oliver,
Please just do as Vladlenin5000 hinted -
> **Vladlenin5000 said:**
> Now it's time for you to read again post #3 and do the proposed troubleshooting.

Which is to simply run the command -
```
sudo apt-get install --reinstall firmware-b43-installer
```
..while you are connected to internet via Ethernet cable. I added the "--reinstall" option in the above command just to be extra sure. Not necessary if you are going to install this package the first time.

---

