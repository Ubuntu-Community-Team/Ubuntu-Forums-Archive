---
title: "Hardy Wireless Issues"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by myattb on 2008-06-04
I have recently upgraded from 7.04 to Hardy and I am having real issues getting Wireless networking working again.

I have a Belkin wireless card (Broadcom bcm43xx).
I have followed the following two posts/guides

[http://ubuntuforums.org/showthread.php?t=766560&highlight=No-Fluff](http://ubuntuforums.org/showthread.php?t=766560&highlight=No-Fluff)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

and I have recompiled ndiswrapper from source.
I can get the card "working" in that I can see my network (although after rebooting I can't get the changes to stick as I dont fully understand the "Hardy bugfix" section from the community docs.

But when I can see the network and try to connect it keeps looping around the entering of the passkey and does not allow me to connect?
The network has WPA enabled and I beleive that this may be why I am unable to connect but I am not sure.

Can someone help me with making the Hardy bug fix permanent and what I need to do to connect?

Many thanks....

---

### Post by tonyk88 on 2008-06-04
I have a US Robotics Wireless MAXg PC Card and unable to get it to work with 8.4 LTS. In addition my Lexmark Printer, x3550 seems to be unsupported. What luck.
Any idea on the wireless card?

Tony
[email]tonk88@comcast.net[/email]

---

### Post by tonyk88 on 2008-06-04
SORRY THATS
[email]tonyk88@comcast.net[/email]

---

### Post by tonyk88 on 2008-06-04
Does anyone know what wireless card works well with ver 8.4 LTS for a Dell Inspiron 5100.

Thanks.
Tony
[email]tonyk88@comcast.net[/email]

---

### Post by vexingmodstwo on 2008-06-04
> **myattb said:**
> I have recently upgraded from 7.04 to Hardy and I am having real issues getting Wireless networking working again.

I have a Belkin wireless card (Broadcom bcm43xx).
I have followed the following two posts/guides

[http://ubuntuforums.org/showthread.php?t=766560&highlight=No-Fluff](http://ubuntuforums.org/showthread.php?t=766560&highlight=No-Fluff)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

and I have recompiled ndiswrapper from source.
I can get the card "working" in that I can see my network (although after rebooting I can't get the changes to stick as I dont fully understand the "Hardy bugfix" section from the community docs.

But when I can see the network and try to connect it keeps looping around the entering of the passkey and does not allow me to connect?
The network has WPA enabled and I beleive that this may be why I am unable to connect but I am not sure.

Can someone help me with making the Hardy bug fix permanent and what I need to do to connect?

Many thanks....

You might want to try another network manager.  If you've gone through Jamie Jackson's how to and still can't connect, it's worth a shot.  I installed wifiradar after going through that how to and it worked.

---

