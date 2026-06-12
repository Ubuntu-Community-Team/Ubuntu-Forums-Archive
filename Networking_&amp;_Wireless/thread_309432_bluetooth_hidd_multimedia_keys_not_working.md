---
title: "bluetooth hidd multimedia keys not working"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by sideshowb0b on 2006-11-29
I've recently moved to ubuntu edgy 6.10 from fc5. I've managed to get most of my system working as it did on fc5, but still have one or two problems. 

This problem is that although i can connect to and use my bluetooth keyboard / mouse (actually it's a Sony Ericsson k750 mobile that works as a mouse and keyboard), I don't seem to be able to use the multimedia keys (or extended keys). This worked in fc5 straight "out of the box". I've tried showkey -s and showkey and there is no response to these keys. However, if i run hcidump , the key presses are being sent. 

I've done some googling and found some vague references to the debian kernel not supporting multimedia keys through hidd. I'm not  sure if this is relevant. It talks about "boot mode" and "report mode" and a kernel patch. "hidd --show" reports:

xx:xx:xx:xx:xx:x Sony Ericsson Remote Control [0000:c028] connected

apparently it would show if the connection was in boot mode.

Any help greatly appreciated

---

