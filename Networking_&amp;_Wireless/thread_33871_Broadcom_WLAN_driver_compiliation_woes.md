---
title: "Broadcom WLAN driver compiliation woes"
date: 2005-05-12
forum: Networking &amp; Wireless
---

### Post by THEspacemonkey on 2005-05-12
There is a thread about installing ndiswrapper drivers for Broadcom WLAN cards, but it only applies to one or two out of many models. I have the BCM5788 card, and have gone to broadcom.com to download their linux drivers.

Unfortunately, the first step after unpacking is running *make*, which of course errors out thusly:

```

make -C  SUBDIRS=/software/broadcom/linux/bcm5700-8.1.55/src modules
make: *** SUBDIRS=/software/broadcom/linux/bcm5700-8.1.55/src: No such file or directory.  Stop.
make: *** [default] Error 2

``` 

I've taken a look around, but my build skills have withered on the vine as I dedicate myself wholly to PHP...

Anyone willing to help me work through this?

---

### Post by Alexander Kirillov on 2005-05-12
Broadcom provides Linux drivers for their wireless cards? This would be great news if it were true. From reading their website, it seems that they only provide drivers for Ethernet NICs - wired, not wireless.

---

### Post by THEspacemonkey on 2005-05-12
Hard to tell, either they do (and call them all ethernet cards) or they mix their model numbers (57xx has both WLAN and Ethernet NICs)...

As long as the build fails I suppose it is a moot point :???:

---

### Post by Alexander Kirillov on 2005-05-12
[QUOTE=THEspacemonkey]Hard to tell, either they do (and call them all ethernet cards) or they mix their model numbers (57xx has both WLAN and Ethernet NICs)...
[/QUOTE]
I beleive they mix the model numbers :(

> 
As long as the build fails I suppose it is a moot point :???:

Agreed...

---

