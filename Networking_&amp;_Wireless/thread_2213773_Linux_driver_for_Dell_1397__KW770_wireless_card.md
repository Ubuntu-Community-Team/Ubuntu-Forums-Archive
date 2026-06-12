---
title: "Linux driver for Dell 1397 / KW770 wireless card?"
date: 2014-03-28
forum: Networking &amp; Wireless
---

### Post by riverguy99 on 2014-03-28
Is there a resource that lists what linux drivers are available for the most common wireless cards?  I've been trying to find a driver for my kids' Dell Studio 1535 (Ubuntu 12.04)and have had no luck.  The card is the Dell 1397 802.11 Half-Height.  The Dell number is KW770.

Any leads would be SO appreciated!

---

### Post by Hadaka on 2014-03-28
hi, please post the output of..
```
lspci -nn | grep 0280
```
thanks.

---

### Post by riverguy99 on 2014-03-28
Thanks!  I will have access to that laptop this afternoon and will post what I find there.  :)

---

### Post by riverguy99 on 2014-03-28
**Here's the output you requested.  I hope it helps!**

lilah@lilah-Studio-1535:~$ lspci nm | grep 0280
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
lilah@lilah-Studio-1535:~$ ^C
lilah@lilah-Studio-1535:~$ ^C
lilah@lilah-Studio-1535:~$

---

### Post by Hadaka on 2014-03-28
you have a typo in your command its not nm   its nn
2 n's.....please repost correctly..
```
lspci -nn | grep 0280
```
thanks

---

### Post by riverguy99 on 2014-03-28
**I am REALLY sorry about that . . .**

lilah@lilah-Studio-1535:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
lilah@lilah-Studio-1535:~$
-F <file>    Read PCI configuration dump from a given file
lilah@lilah-Studio-1535:~$

---

### Post by QIII on 2014-03-28
Hello!

Typo again.  There is a dash before nn.

Sometimes it is best to copy and paste.


Cheers.

---

### Post by riverguy99 on 2014-03-28
**OK, this time with cut-n-paste: (I had the dash before nn; maybe two spaces where there was only supposed to be one?  **

lilah@lilah-Studio-1535:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
lilah@lilah-Studio-1535:~$

---

### Post by Hadaka on 2014-03-28
from a wired connection to the internet please do..
```
sudo apt-get install firmware-b43-lpphy-installer
```

---

### Post by riverguy99 on 2014-03-28
**I ran it once and then lost the email back to the computer I'm working on,  I ran it the second time and got this:**

lilah@lilah-Studio-1535:~$ sudo apt-get install  firmware-b43-lpphy-installer 
[sudo] password for lilah: 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
firmware-b43-lpphy-installer is already the newest version. 
The following package was automatically installed and is no longer required: 
  thunderbird-globalmenu 
Use 'apt-get autoremove' to remove them. 
0 upgraded, 0 newly installed, 0 to remove and 284 not upgraded. 
lilah@lilah-Studio-1535:~$

---

### Post by Hadaka on 2014-03-28
ok, please post the output of..
```
lsmod
rfkill list
cat /etc/network/interfaces
```
thanks.

---

### Post by riverguy99 on 2014-03-29
I removed "thunderbird-globalmenu" and re-installed 
sudo apt-get install firmware-b43-lpphy-installer

This computer is now on our wired LAN so I unplugged it, rebooted, and nada.  No wireless shows up.

---

### Post by Hadaka on 2014-03-29
ok,, what does thunderbird-global menu have to do
with this? Please post the items i requested if you
want me to continue to help you.
thanks.

---

### Post by riverguy99 on 2014-03-29
I removed "thunderbird-globalmenu" and re-installed 
sudo apt-get install firmware-b43-lpphy-installer

This computer is now on our wired LAN so I unplugged it, rebooted, and nada.  No wireless shows up.

---

### Post by riverguy99 on 2014-03-29
Hadaka, my apologies.  I started this thread with you on a different computer.  When I was able to get the computer that this is all about online through a wired LAN, I continued on that one.  On that one, it went like this, and this is where the &#8220; thunderbird-globalmenu&#8221; came from.  I guess this doesn't work going back and forth between two computers?  If you would (please) continue to work with me on this, can you go back to the other thread (below), since then I will be on subject computer?

 **You:**
 from a wired connection to the internet please do..
 Code:
 sudo apt-get install firmware-b43-lpphy-installer[B] 

 Me:[/B]
 I ran it once and then lost the email back to the computer I'm working on, I ran it the second time and got this:

lilah@lilah-Studio-1535:~$ sudo apt-get install firmware-b43-lpphy-installer 
[sudo] password for lilah: 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
firmware-b43-lpphy-installer is already the newest version. 
The following package was automatically installed and is no longer required: 
thunderbird-globalmenu 
Use 'apt-get autoremove' to remove them. 
0 upgraded, 0 newly installed, 0 to remove and 284 not upgraded. 
lilah@lilah-Studio-1535:~$  
 

 **And that's the last I heard from you on that computer.**

---

### Post by mörgæs on 2014-03-29
> **riverguy99 said:**
> 
0 upgraded, 0 newly installed, 0 to remove and 284 not upgraded. 


Your computer is in a really bad shape. 
Before going further with wifi I suggest running
```
sudo apt-get update
sudo apt-get dist-upgrade
```
from a wired connection. After that a reboot.

---

### Post by robindebonnecoeur on 2014-11-16
> **Hadaka said:**
> from a wired connection to the internet please do..
```
sudo apt-get install firmware-b43-lpphy-installer
```

For the edification of others -- well, to help out those like me sitting here trying to get an older Dell Inspiron 11z with a Broadcom BCM4312 802.11 b/g LP.PHY wifi device to work -- just wanted to thank you, Hadaka, as I followed your advice after installing Linux Mint 64-bit 17 (Qiana) and not seeing wifi at all until I ran the above command.

Apparently the lpphy bit has been deprecated or something, but Terminal kindly gave me suggestions on how modify the command to:

```
sudo apt-get install firmware-b43-installer
```

and after a reboot the little Dell saw and connected to wifi, no dramas.

Thank you again!! :)

---

