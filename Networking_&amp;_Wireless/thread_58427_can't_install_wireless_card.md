---
title: "can't install wireless card"
date: 2005-08-20
forum: Networking &amp; Wireless
---

### Post by Atomic Ant on 2005-08-20
Dear Unbuntu users,

I installed Unbuntu on my laptop and everything works fine, except from my wireless network card :(
Can someone help me with a way to install a wireless network card from Sitecom WL-011 - Wireless Network PC Card ?

any help would be apreciated.....

many thanks


JR

---

### Post by amastronardi on 2005-08-20
Hi,
First get network card data:

```

root@cronopio:~ # lspci | grep -i lan
[COLOR=Red]0000:02:02.0[/COLOR] Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

root@cronopio:~ # lspci -n | grep [COLOR=Red]0000:02:02.0[/COLOR]
0000:02:02.0 0280: [COLOR=Green]14e4:4320[/COLOR] (rev 03)

```

Second, check if that card works with ndiswrapper [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) . If it works, read ndiswrapper installation documentation [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

Cheers, Adrian.

---

