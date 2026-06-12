---
title: "Fritz WLAN USB disappears on cold start"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by SlayerMan on 2007-04-03
Hi all,

I've got a problem with my wireless setup using ndiswrapper and Fritz WLAN USB.

The problem is that when I cold start up my computer, the adapter doesn't get recognized by the kernel (doesn't even show up in lsusb). When I unplug the device and replug it a few seconds later, everything starts working again.

What could be the problem here?

Kind Regards
SlayerMan

---

### Post by SlayerMan on 2007-04-11
Does nobody have any suggestions on this?

---

### Post by hulluPeruna on 2007-04-14
check this
[http://ubuntuforums.org/showthread.php?t=301083]("http://ubuntuforums.org/showthread.php?t=301083")

:D

---

### Post by SlayerMan on 2007-04-15
Thanks for the link, but getting the stick to work is not the problem.

The problem is that the USB device per se does not get recognized by the kernel when the computer is powered on. It does get recognized, however, when I issue a reboot or when I unplug/replug the stick. The problem with this is that the stick is used on a desktop PC as its main internet connection, and is plugged into a USB slot at the back of the computer (so replugging the device is a real pain in the a...).

The problem does not occur with Windows, so it's not a hardware problem. I'll try to post dmesg output the next time the stick doesn't get recognized.

---

### Post by SlayerMan on 2007-04-21
Some news here. AVM seems to have released a new version of their native Linux driver for the stick.

Now, my problem has changed a bit :)

The native driver module loads fine, and the device is listed in iwconfig.
I can even associate to an access point manually. However, the interface is
not listed in ifconfig and NetworkManager doesn't see it, too.

Any suggestions?

---

### Post by Laryllan on 2007-05-03
I'm having exactly the same problem.

Building a new version of ndiswrapper (1.43) solved  the first issue -  the device is being recognized at cold start, but it still doesn't connect automatically.
I have to sudo ifdown/up to make it get a DHCP lease.

Using Xubuntu 7.04 64bit.

---

