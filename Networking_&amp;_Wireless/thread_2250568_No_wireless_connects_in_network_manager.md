---
title: "No wireless connects in network manager"
date: 2014-10-29
forum: Networking &amp; Wireless
---

### Post by loren41 on 2014-10-29
Running Ubuntu 14.04 LTS on a Dell Inspiron 1520.  With Forum help, I activated an ethernet connection.  Now trying to add a wireless connection to my running router.  In Network Manager, I  see only my  ethernet connection.  
Ran the following:
loren41@loren41-Inspiron-1520:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Device [1028:01f1]
	Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: b43-pci-bridge

Don't know where to go from here.  Can you help?

---

### Post by jeremy31 on 2014-10-29
I believe the terminal command that finds wifi access points is ```
iwlist scan
```

---

### Post by loren41 on 2014-10-29
loren41@loren41-Inspiron-1520:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by jeremy31 on 2014-10-29
> **loren41 said:**
> loren41@loren41-Inspiron-1520:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Hopefully you are just missing firmware```
sudo apt-get install firmware-b43-installer
```
EDIT: I see you already did that in another post, please run the wireless script from http://ubuntuforums.org/showthread.php?t=370108

---

### Post by Hadaka on 2014-10-29
Hi loren41, I dont know if you remembered to run this command or not
if not..please do..
```
sudo apt-get update
```
this may take a little time, but its important you run it.
Then click your network mrg. (upper-right corner next to envelope)
and verify that Enable Networking and Enable Wireless are checked.
when you see your connecion, click network mgr >>edit your connection
make IPv4 and IPv6 look like the attached screen shots.
[ATTACH=CONFIG]257592[/ATTACH][ATTACH=CONFIG]257593[/ATTACH]
thanks

---

### Post by loren41 on 2014-10-30
Gentlemen,
Once again your help was excellent.  The diagnostics showed that my wireless driver was not found.  The suggested URL took me to the correct version and told me the Ubuntu code to use.  Worked like a charm!  My thanks.

---

### Post by Hadaka on 2014-10-30
GREAT !  glad you figured it out.
thanks.

---

