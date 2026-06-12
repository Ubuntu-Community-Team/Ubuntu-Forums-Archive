---
title: "network printer ubuntu / xubuntu"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by kb2tfa on 2009-07-11
Desktop pc = ubuntu latest version 9.04 I think
Laptop is same but running XFCE for performance issues.
printer=brother mfc 4800
network is comcast internet, both pcs connected via comcast router.
------------------

I have a desktop pc with Ubuntu installed, and this pc is connected to a brother mfc-4800 printer via printer cable, not wireless, not router, not usb.

I can print from this pc, however, I want to print from my laptop which is on the same network.

I choose printer config from the laptop and my options are:

[LIST]
[*]app socket/hp jetdirect
[*]internet printing protocol
[*]lpd/lpr host or printer
[*]windows printer via samba
[*]other
[/LIST]
The only two I can think apply to me are "other" or "lpd/lpr"
LPD/LPR wants the host / queue, and 
Other wants "Enter Device URL"

How do I find what the url of the other computer printer?

---

### Post by schwascore on 2009-07-20
You need to enable sharing on the host computer first.  Here are some guides.

[https://help.ubuntu.com/community/Printers#Sharing%20Printers]("https://help.ubuntu.com/community/Printers#Sharing%20Printers")

[http://productivelinux.com/2009/02/10/how-share-printers-on-your-local-network-in-ubuntu-810-intrepid/]("http://productivelinux.com/2009/02/10/how-share-printers-on-your-local-network-in-ubuntu-810-intrepid/")

---

