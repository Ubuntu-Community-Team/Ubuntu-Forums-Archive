---
title: "Intel PRO Wireless Adapter 2200BG - which package for firmware?"
date: 2015-08-11
forum: Networking &amp; Wireless
---

### Post by alpage2 on 2015-08-11
I am attempting to install lubuntu 15.04 on a friend's (old Win XP) netbook (Dell Latitude D410) for them, in a location with no internet access.

Is there a .deb package that I can download and supply on a USB stick that would provide the necessary firmware?

Thanks in anticipation,
Alan

---

### Post by alpage2 on 2015-08-11
I should add that lubuntu loads the ipw2200 driver on boot.

Thanks
Alan

---

### Post by chili555 on 2015-08-11
Please see:```
modinfo ipw2200
```It says:```
filename:       /lib/modules/4.0.1-040001-generic/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
[COLOR="#FF0000"]firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw[/COLOR]
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2kmprq
<snip>
```However, as the firmware is included in all recent Ubuntu versions by default, I doubt this is your problem. Verify:```
ls /lib/firmware | grep ipw
```Does the message log complain about missing firmware?```
dmesg | grep ipw
```If not, then firmware is most certainly not your problem.

What* is* the underlying problem??

---

### Post by alpage2 on 2015-08-11
Thanks chili555 - it may be a while before I can get together with this friend + netbook to run those commands - but I'll do that as soon as is possible, and report back.

Yes - now you come to mention it, there may be hardware problems that are affecting this. When I ran dmesg after bootup, it reported scan results, repeated several times during bootup - something I have never seen during a boot, before. I'll provide the output from dmesg, as well, when I am able to get my hands on this netbook, again.

Thanks for your help,
Alan

---

### Post by chili555 on 2015-08-11
I had one of those a few years back. I replaced it with a 2915 because the particular version I owned didn't do WPA!!! Of course, since WPA2-AES is secure and prevalent, I didn't want a device that didn't do what the whole world requires. You can check the capabilities with:```
iw list
```We hope you see, among many other things:```
Supported Ciphers:
		* WEP40 (00-0f-ac:1)
		* WEP104 (00-0f-ac:5)
		* TKIP (00-0f-ac:2)
		* [COLOR="#FF0000"]CCMP[/COLOR] (00-0f-ac:4)
		* 00-0f-ac:10
		* GCMP (00-0f-ac:8)
		* 00-0f-ac:9

```If the nearby access point is set to use WPA2-AES (the same as CCMP), and the card is too old to do so, then you can't connect.

As well, some Linux wireless drivers are troubled by TKIP. If the nearby access point is set to use TKIP, I'd change it to AES, also known as CCMP.

---

### Post by alpage2 on 2015-08-11
Thanks, chili555 for those tips - I'll check that out, also.
Alan

---

