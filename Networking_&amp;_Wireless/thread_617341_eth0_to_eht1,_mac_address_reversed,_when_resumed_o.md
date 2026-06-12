---
title: "eth0 to eht1, mac address reversed, when resumed on desktop"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by marutter on 2007-11-19
Just built a brand new system with Kubuntu 7.10 (64 bit).  Works great and as quiet as a SATA drive:

AMD BE-2400: Chip
ASUS M2NPV-VM: Motherboad (nforce 430)

Out of the box, suspend works fine.  When it resumes, all appears to work.  However, when playing with wake-on-lan, I discovered eth0 is now eth1 and the mac address has switched, the original in reverse.  I have only onboard ethernet, so no card conflict issues.

I have searched and tried udev rules and some other things (should have kept track) but could not fix this issue.  There are lots of bug reports, but they have not been helpful in resolving the issue.

Any suggestions?

---

### Post by kevdog on 2007-11-19
I take it that you tried editing:

/etc/udev/rules.d/70-persistent-net.rules (if using Gutsy)

Can you tell us specifically what you did??

---

### Post by pebo on 2007-11-19
Taken from the Archlinux wiki udev article:
> Another method for network card ordering is to use the udev-sanctified method of statically-naming each interface. Create a file called /etc/udev/rules.d/10-network.rules and bind the MAC address of each of your cards to a certain interface name:

SUBSYSTEM=="net", ATTRS{address}=="aa:bb:cc:dd:ee:ff", NAME="lan0"
SUBSYSTEM=="net", ATTRS{address}=="ff:ee:dd:cc:bb:aa", NAME="wlan0"

A couple things to note:

    * To get the MAC address of each card, use this command: udevinfo -a -p /sys/class/net/<yourdevice>
    * Make sure to use the lower-case hex values in your udev rules. It doesn't like upper-case.
    * Some people have problems naming their interfaces after the old style: eth0, eth1, etc. Try something like "lan" or "wlan" if you experience this problem. 
 

HTH

---

### Post by marutter on 2007-11-19
> **kevdog said:**
> I take it that you tried editing:

/etc/udev/rules.d/70-persistent-net.rules (if using Gutsy)

Can you tell us specifically what you did??

I Tried:

# PCI device 0x10de:0x0269 (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1d:60:18:c2:3c", NAME="eth0"

# PCI device 0x10de:0x0269 (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="3c:c2:18:60:1d:00", NAME="eth1"

Also changed the the mac address on "eth1" to the 00:1d....  That just ended up creating eth2.

---

### Post by marutter on 2007-11-19
Pebo,

Only one of the devices exists at one time.  For example, if ifconfig returns eth1, then I can't find the mac for eth0, as it does not exist.  Not sure if this helps.

Also, I tried renaming things.  Now it switches between lan0 and wlan0.  But I still have access to the internet.

---

