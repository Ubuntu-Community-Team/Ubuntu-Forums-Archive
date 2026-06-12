---
title: "Bigpond nextG wireless broadband( Australia)"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by sunlover on 2008-09-28
I have Ubuntu 7.10 dual booted with Windows XP on my laptop.
I access the Net thru Windows XP using an OPTION GX 0202 pci wireless card.
I am keen to get into Ubuntu but am frustrated by lack of direct internet access.
In searching this and other forums I am getting close to a solution but need some clues on some basics(again).

CASE 1“oztules” on pharscape 3G forum has achieved successful connection on SUSE 10.2 with above card. Part of his method was to edit **/etc/modprobe.conf.local **with details of card vendor and product(ie. add: options usbserial vendor=0x0af0 product=0x6701). When I open this file with gedit(as root) this file is empty.
His next step was to edit **/etc/sysconfig/kernel** changing:
[B]# 
MODULES_LOADED_ON_BOOT="" 
to 
# 
MODULES_LOADED_ON_BOOT="usbserial"[/B] 
When I open this file with gedit(as root) this file is also empty.
He then goes on to configure wvdial(which I can follow).

CASE 2
“sharke” in these forums method to set up a different modem to mine is:
Quote:To set up modem set usbserial to modem:
In terminal- [B]sudo insmod /lib/modules/`uname -r`/kernel/\
drivers/usb/serial/usbserial.ko \
vendor=0x16d8 product=0x6280 [/B]
You now have your modem activated- Unquote.
If I run this command will the amended vendor and product no's I get output:
[B]insmod: error inserting '/lib/modules/2.6.22-14-generic/kernel/drivers/usb/serial/usbserial.ko': -1 File exists 
bruce@bruce-laptop:~$ CC[/B]He then goes on to configure ppp. 

It would seem both methods are inserting a module into kernel which is driver for appropriate card/modem.
I think the above module is the wrong one for my card and I guess I need a handle on inserting correct one.
I need a better understanding of what is trying to be achieved here before proceeding further.
Any advise/suggestions gratefully accepted.
sunlover

---

### Post by sharke on 2009-02-26
sunlover,
Have you succeeded in getting this working.
Regards
Sharke

---

