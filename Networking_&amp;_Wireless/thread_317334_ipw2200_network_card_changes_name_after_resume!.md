---
title: "ipw2200 network card changes name after resume!"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by alanfranz on 2006-12-12
Hello,
I'm experiencing a rather strange issue.

I've got two network cards in my system (Dell Latitude D810), a Broadcom Ethernet and an Intel IPW2200 wireless network card.

The cards kept switching their names, e.g. at one boot one was eth0, the other was eth1, and vice verse.

Somebody suggested I configure /etc/iftab matching the cards' addresses in order to make them permanent. It worked, but only partially.

The cards are fine at boot; eth0 is my ethernet card, and wlan0 is my wireless card.

Suspend-to-ram and Hibernate both work fine on my system, but this glitch occurs: whenever resuming, my wireless card is assigned the 'eth1' name.

I guess this has something to do with the way resuming works... probably the boot script which assigns the names does read /etc/iftab, but the resume doesn't. I guess it has something to do with udev, but I wouldn't know where to start looking!

---

### Post by zgornel on 2006-12-12
> **alanfranz said:**
> Hello,
I'm experiencing a rather strange issue.

I've got two network cards in my system (Dell Latitude D810), a Broadcom Ethernet and an Intel IPW2200 wireless network card.

The cards kept switching their names, e.g. at one boot one was eth0, the other was eth1, and vice verse.

Somebody suggested I configure /etc/iftab matching the cards' addresses in order to make them permanent. It worked, but only partially.

The cards are fine at boot; eth0 is my ethernet card, and wlan0 is my wireless card.

Suspend-to-ram and Hibernate both work fine on my system, but this glitch occurs: whenever resuming, my wireless card is assigned the 'eth1' name.

I guess this has something to do with the way resuming works... probably the boot script which assigns the names does read /etc/iftab, but the resume doesn't. I guess it has something to do with udev, but I wouldn't know where to start looking!
Try suspending with ```
sudo echo mem > /sys/power/state
```. If it works, do a script with the command.

---

### Post by alanfranz on 2006-12-13
that works for the card name, but leads to other problems. First, external usb drives are not disconnected properly and I get a "unsafe disconnect" alert when resuming. Also, I don't seem to be able to perform a proper reboot or shutdown after it (system hangs and I manually have to reset it via ctrl alt canc) and I don't know if I can bind any of these scripts to my power management system ( which is gnome-power-manager I suppose ) to let them be run automatically when the PC is idle.

---

### Post by zgornel on 2006-12-13
> **alanfranz said:**
> that works for the card name, but leads to other problems. First, external usb drives are not disconnected properly and I get a "unsafe disconnect" alert when resuming. Also, I don't seem to be able to perform a proper reboot or shutdown after it (system hangs and I manually have to reset it via ctrl alt canc) and I don't know if I can bind any of these scripts to my power management system ( which is gnome-power-manager I suppose ) to let them be run automatically when the PC is idle.
Hmm. I found some scripts in /etc/acpi. The interesting ones are: /etc/acpi/suspend.d/55-down-interfaces.sh and /etc/acpi/resume.d/ifup.sh. You coud replace the ifup.sh *for* section with manual commands: ifconfig eth0 up and ifconfig eth1 up. Try it, it might just work.

---

### Post by alanfranz on 2006-12-14
That's not the real problem. The problem is that my interface changes its name on resume.



If I just duplicate my wlan0 entry to eth1 in /etc/network/interfaces, everything works fine - but, as usual, it's a workaround; it's not the way it's supposed to work.

This is probably a problem related to the process that should read /etc/iftab to bind proper names to my interfaces: it works correctly on boot, but uncorrectly on resume.

According to iftab man page

> 
The  file /etc/iftab contains descriptive information about the various
       network interfaces and is used by udev(8) and  its  iftab_helper(8)  to
       assign consistent names to network interfaces.


so I guess it's an udev-related bug... udev seems to read iftab on boot, but not on resume. I'll try issuing a bug report for that package.

---

