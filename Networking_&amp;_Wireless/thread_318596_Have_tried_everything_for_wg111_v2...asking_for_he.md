---
title: "Have tried everything for wg111 v2...asking for help."
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by mattmueller on 2006-12-14
Ok, I hate to do this but I don't know what else to do.

I am running edgy, and cannot for the life of me get my wg111v2 usb adapter to work.  All I am trying to do is connect to my home network (no security).

I am worried at this point that perhaps I have tried too much stuff by following various how-tos, and that this may be effecting anything else I try.  I can't afford to do a clean install of Edgy right now.

Can anyone either help or point me to someplace that could help with getting this working?  I have tried the ndiswrapper method (it worked about 6 months ago when I was at home on Dapper) to no avail.  The only weird thing I have noticed when doing this is that it configs as eth2 instead of wlan0.  That and that although it says it is present, modprobe does not make the little light turn on.

Thanks in advance.

---

### Post by skinny on 2006-12-14
Which version of the wg111v2 do you have? Type "lsusb -v" at the console does it show  ID 0846:6a00?

$

---

### Post by FrodoB on 2006-12-14
Try 128bit WEP and see it that works.

Also do a forum seach for WG111v2, there is a list of my router setting that helped in at least one case.

---

