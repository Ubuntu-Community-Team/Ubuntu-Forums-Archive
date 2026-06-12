---
title: "graphic card driver problems"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by mike martigin on 2009-07-10
hello all, so i recently downloaded ubuntu 9.04 and am now working on getting compiz on there as well. I found a tutourial at 
 
[http://linuxdesk.wordpress.com/2009/06/15/install-compiz-compiz-fusion-plugins-on-ubuntu-9-04/](http://linuxdesk.wordpress.com/2009/06/15/install-compiz-compiz-fusion-plugins-on-ubuntu-9-04/)
 
but where it says to download the drivers 
[COLOR=#000099]Nvidia binary X.org Driver version 173 or 177[/COLOR]
 
i'm not sure which one (if either) will support 
my graphics card which is a 
 
ATI Mobility RADEON 9000 AGP 4X video graphics at 32MB 
 
or whether i have to get an ATI specific driver 
any idea?

---

### Post by LewRockwell on 2009-07-10
[http://ubuntuforums.org/showpost.php?p=7361967&postcount=241](http://ubuntuforums.org/showpost.php?p=7361967&postcount=241)

not sure if anything in that thread will help but I thought I would mention it

.

---

### Post by csabo2 on 2009-07-10
Now this may have changed. but last I heard, the version of Xorg that ships with 9.04 does NOT have any ATI drivers to go with it (proper drivers at any rate)

---

### Post by QIII on 2009-07-10
You first have to keep in mind that drivers are the proprietary intellectual property of the OEMs, not something that is created by the developers of any particular OS.

The same is true for Windows.  Microsoft, however, has the muscle to force the OEMs to provide Windows compatible drivers.  ATI, for instance, does not dictate to Microsoft.

Until recently, most OEMs did not provide drivers compatible with Linux.  That is changing.

While Ubuntu does come with some support for ATI graphics, it is, as you say, not "proper".

I had to download ATI's Linux driver form their website and use Catalyst to manage it.

This situation is changing.

---

### Post by Mark Phelps on 2009-07-10
QIII:

That's all well and good ... but ... there are no AMD/ATI proprietary drivers for the op's card that will work with the Xserver included in Ubuntu 9.04. AMD/ATI dropped support for a lot of older cards (including the op's), so there is no point in going to their site for drivers -- there aren't any.  For the older cards, the open source driver, installed by default, is the only one that will work in Ubuntu 9.04.

---

### Post by QIII on 2009-07-10
Ah!

Hence:  While Ubuntu does come with some support for ATI graphics, it is, as you say, not "proper".

---

