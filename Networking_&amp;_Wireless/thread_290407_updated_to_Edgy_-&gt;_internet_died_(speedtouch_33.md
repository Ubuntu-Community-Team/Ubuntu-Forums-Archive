---
title: "updated to Edgy -&gt; internet died (speedtouch 330)"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by OXIj on 2006-11-01
I have Speedtouch 330 usb ADSL modem. I worked fine in Drapper but yesterday i've upgrated to Edgy.
Now while loading I have message:
usb1-1: device not accepting adress 2 error -71

I have searched forums and googled but all I found are problems with firmware.
I've created many -s links in /lib/firmware/
and in /lib/firmware/<kernel version>/
but it doesn't help.
System found firmware but it cant load it.....

I need Internet to fix other problems.
I need my files back!

Someone, please, help... :cry:

---

### Post by OXIj on 2006-11-01
I have plugged modem into other usb port and now there is no "usb1-1: device not accepting adress 2 error -71" message
but now I have:
"speedtch_upload_firmware: read BLOCK4 from modem failed (-110)!"
and
"speedtch_heavy_init: firmware upload failed (-110)!"
(it is 2.6.17-10 kernel)

if i load 2.6.15-27 kernel then there is no any of this error messages but configuring nas0 by (br26<TAB>) gives nothig.
so pppd cant call too...

any ideas?
i dont now there find answers.

---

