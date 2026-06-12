---
title: "wireless installation problem"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by zezito555 on 2008-07-23
hi to all, i got my head all messed up because of this:

**-» lspci**
...
02:02.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
...
**(so i guess it recognizes wifi card!)**

**-» ndiswrapper -l**
neti2220 : driver installed
	device (17FE:2220) present
**(i think it means driver correctly installed and the wifi device is there!)**

**-» dmesg**
...
[   38.859085] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   38.958858] ndiswrapper (check_nt_hdr:156): kernel is 32-bit, but Windows driver is not 32-bit;bad magic: 020B
[   38.958867] ndiswrapper (load_sys_files:206): couldn't prepare driver 'neti2220'
[   38.959492] ndiswrapper (load_wrap_driver:108): couldn't load driver neti2220; check system log for messages from 'loadndisdriver'
[   38.959584] usbcore: registered new interface driver ndiswrapper
**(is this the reason i dont have wifi card working??)**

i already edited the /etc/modules and added the ndiswrapper line, to load at startup, and still nothing!!!

Any Ubuntu user can help plz???
dont know what moro to do

---

