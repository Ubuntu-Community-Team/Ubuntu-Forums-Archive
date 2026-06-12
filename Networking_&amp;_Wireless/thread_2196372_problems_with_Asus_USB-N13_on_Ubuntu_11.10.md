---
title: "problems with Asus USB-N13 on Ubuntu 11.10"
date: 2013-12-29
forum: Networking &amp; Wireless
---

### Post by gavin_bowlby on 2013-12-29
I got the Asus USB-n13 to work on my 10.4 installation by adding the command:

blacklist rt2800usb

to /etc/modprobe.d/blacklist.conf

in su mode.


I'm trying to upgrade my system to a more modern version of Ubuntu, so I went through the upgrade process from 10.4 to 11.10.

Now I see the same failure I saw with 10.4. The Wireless USB stick isn't powered up, and can't be used to connect to my wireless network.

lsmod doesn't show any rt2/rt3 devices.

lsusb shows an ID of 0b05:1784 for the ASUS Wireless adapter:

gavin@matango:~$ lsmod | grep -e rt2 -e rt3
gavin@matango:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter [Ralink RT2870]
Bus 005 Device 002: ID 0557:8021 ATEN International Co., Ltd 
Bus 005 Device 003: ID 0557:2213 ATEN International Co., Ltd CS682 2-Port USB 2.0 DVI KVM Switch


I tried adding additional devices to the blacklist:


gavin@matango:~$ tail /etc/modprobe.d/blacklist.conf

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2800usb


blacklist rt2x00lib
blacklist rt2x00usb
blacklist rt2870sta
gavin@matango:~$ 

and added rt3070sta to /etc/modules

but I still see the same problem after restarting the system.

Does anyone have any suggestions on what I could try?

Regards,
Gavin

---

### Post by chili555 on 2013-12-29
First of all, If you are upgrading, why not upgrade to the later long term support version 12.04 LTS or, even better, the latest version 13.10? There has been a lot of progress made in drivers in two years!

Second, you blacklisted any, every and all possible candidates for a driver for your device! We are not surprised that it doesn't work! Third, unless you compiled it yourself, rt3070sta doesn't exist in 11.10; check:```
modinfo rt3070sta
```It probably says:> chili@Think410:~$ modinfo rt3070sta
ERROR: Module rt3070sta not found.I suggest you upgrade and use rt2800usb.

---

### Post by gavin_bowlby on 2013-12-29
Chilli555:

Thanks so much for your quick response!

I blacklisted the set of drivers based on a response to a posting for a similar problem that someone else had.

I followed your good advice and upgraded Ubuntu from 11.10 to 13.10.

I can now see the Wireless USB stick get powered up, and join my home wireless network.

Thanks again!

Gavin

---

### Post by chili555 on 2013-12-29
Awesome! Glad it's working.

---

