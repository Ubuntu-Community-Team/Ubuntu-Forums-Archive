---
title: "Getting excelerated graphics and uinput for my ThinkPad T42 (2373-L5U) - 8.10"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by Mortus Pryde on 2009-04-08
I am converting my IBM Thinkpad T42 over to Linux, Ubuntu 8.10 to be exact, however I am having a few issues.

First is successfully getting 3D excellerated graphics to work, the 2373-L5U uses the ATI Radeon Modility 9600 chipset graphics. I am very active in the virtual worlds of SecondLife and OpenLife, so 3D excelleration is a must for me. The proprietary drivers do not seem to install on the T42 (Not Surprising as they will not under Windows either.), and the XOrg driver results in only being able to start in Low-Res mode. I do not recall the error and I am not at home to try it. I have read just about everything I could in the forums and from google I could fing that seemed to relate to my situation, however many lead back to the above which to not work or restoring the the origional driver that is non-excellerated. Any suggestions on enabling 3D exceleration would be most appreciated, please try to be specific, though I am pretty savy computer wise I am not up to speed yet on Linux yet. 

The other is more a luxury then a nescessity, but would be nice. I am trying to get the built in fingerprint scanner to work with ThinkFinger, however I apparently need the uinput modules installed for it to work. I can't seem to find them in the package managers, do I need to download them seperately and from where?

---

### Post by iBurger on 2009-04-09
Please take a look at the this website;

[http://en.wikipedia.org/wiki/Fglrx](http://en.wikipedia.org/wiki/Fglrx)

> ATI fgrlx (proprietary drivers) are not currently supported out-of-the-box in 8.10.

---

### Post by Mortus Pryde on 2009-04-09
Thanks iBurger, I finally found instructions on how to install the ATI driver the long way. Having done that I am now looking for ways to tweak the driver settings for maximum performance. I an going to try the settings on ThinkWiki as it seems to have good information on this. If anyone has a T42 they use for 3D applications and would like to share there tweaks please do.

uinput is still an issue but one I can address later.

---

### Post by iBurger on 2009-04-09
I read many good users reports about nvidia's opensource drivers. ATI drivers
not so much ... A quote from the wiki;

" the fgrlx driver is not known for its speedy 2d or 3d performance " .

[unofficial ati wiki]("http://wiki.cchtml.com/index.php/Performance_Issues")


> perhaps check out these links;
[http://www.driverheaven.net/linux-radeon-display-drivers/](http://www.driverheaven.net/linux-radeon-display-drivers/)
[http://rage3d.com/board/forumdisplay.php?f=88](http://rage3d.com/board/forumdisplay.php?f=88)

---

### Post by Mortus Pryde on 2009-04-09
Understood, though the defualt driver is worse, and the Xorg driver provided in Add Remorve result in an EE no device error. I can at least milk a few extra frames out of the ATI driver at a higher graphics setting. I do hope support improves and/or the opensource driver? bug is fixed.

Once I am happy with the graphics I will revisit Thinkfinger and see where I can get with that.

---

### Post by iBurger on 2009-04-09
> **Mortus Pryde said:**
> Understood, though the defualt driver is worse, and the Xorg driver provided in Add Remorve result in an EE no device error. I can at least milk a few extra frames out of the ATI driver at a higher graphics setting. I do hope support improves and/or the opensource driver? bug is fixed.

Once I am happy with the graphics I will revisit Thinkfinger and see where I can get with that.


gl with the think finger :) I really like how it works. (Toshiba rocked backed in the day)

---

### Post by Mortus Pryde on 2009-04-09
Getting off topic, but hey it my thread and I don't care! LOL Yes have an OLD P3 Toshiba Sattelite packed away somewhere, still working! All I had to do was change the HSF assembly at one point after it was handed down to me. The battery it totally gone, will not hold a charge at all, but I will not complain as it lasted for 7 years of use.

---

