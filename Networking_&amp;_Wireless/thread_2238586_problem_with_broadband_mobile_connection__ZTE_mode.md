---
title: "problem with broadband mobile connection / ZTE modem with tre.it"
date: 2014-08-08
forum: Networking &amp; Wireless
---

### Post by gosia2 on 2014-08-08
[FONT=arial]Hi all,

I'm asking for some help to make work a 3G USB modem on lubuntu 14.04.

I've a "tre.it" 3G USB modem with a SIM card. The modem is a ZTE model. 

In short I was able to perform the USB mode switch but the connection fails and I am unable to understand the reason. NetworkManager actually asks the PIN and unblock the modem.

I've configured the broadband configuration using the standard procedure. The APN is "tre.it".

This modem needed the usb_modeswitch trick. The usb id was 19d2:1232 and after some search on internet I was able to perform the USB modeswitch by installing the following packages from debian unstable:

libjim0.74_0.74-3_i386.deb
usb-modeswitch_2.2.0+repack0-1_i386.deb
usb-modeswitch-data_20140529-1_all.deb

since lubuntu 14.04 does not provide usb-modeswitch 2.2.0 needed to perform the USB modeswitch for my device.

Here the output of lsusb after the USB mode switch:

Bus 001 Device 004: ID 19d2:1268 ZTE WCDMA Technologies MSM 

Note that the product id changed from 1232 to 1268.
[/FONT]Now, I don't understand why the connection fails with NetworkManager and I don't have any clue about what is wrong.

In attachment the syslog, I hope a nice guy (or girl) will help me! Thank you in any case.

Gosia

---

### Post by gosia2 on 2014-08-09
Hi,

I didn't get any help up to now. This is ok, I guess this is a fairly technical and obscure problem. The point is that I really don't have any clue about what is going wrong and where to look to troubleshoot the problem.

Maybe someone can suggest me another place where to post my problem to get some help.

Gosia

---

### Post by gosia2 on 2014-08-09
Sorry for replying again to my post. Just for information, someone in the italian ubuntu forum pointed out sakis3g

[http://www.linuxmind-italia.org/index.php?topic=17178.0](http://www.linuxmind-italia.org/index.php?topic=17178.0)

and it actually works. Now I'm just wondering why NM fails to estabilish the connection but the main problem is solved for me.

---

