---
title: "What chipset?"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by NewWaves on 2006-09-24
Hi,
Curious as to what chipset exactly is in a Corega USB11 Mini 2?  I was thinking if I could find the same chipset in the ndiswrapper list ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)) I could just find the driver for that card and hopefully it would make this Corega one work?  It's worth a shot...

---

### Post by tturrisi on 2006-09-24
[http://linux-wless.passys.nl/query_part.php?brandname=Corega](http://linux-wless.passys.nl/query_part.php?brandname=Corega)
You should not need ndiswrapper for that device.  What version is it?

---

### Post by NewWaves on 2006-09-24
I already said the brand: Corega USB11 Mini 2

The closest on that page is: COR-USB-11-mini which is the model before mine.

In the comments box for that card it has: retail brand of Allied Telesys; [http://atmelwlandriver.sourceforge.net/news.html](http://atmelwlandriver.sourceforge.net/news.html)

Do you think that driver might work?

I'm going in circles! :confused:

---

### Post by zhangweiwu on 2008-04-13
Hi. I had the same device as you have and I had a discussion on other mailing lists about this device too. So far most promising solution comes from this patch:

[http://marc.info/?l=linux-wireless&m=119117771611554&w=2](http://marc.info/?l=linux-wireless&m=119117771611554&w=2)

When I find out which kernel version can support this device I'll post a follow-up. Looks Linux kernel is going to support that directly.

Currently Ubuntu kernel version is 2.6.22 (I am using 7.10) and that patch (which includes support for mini2) is later than this kernel, so probably you can expect after next time you upgrade kernel things work automatically.

---

