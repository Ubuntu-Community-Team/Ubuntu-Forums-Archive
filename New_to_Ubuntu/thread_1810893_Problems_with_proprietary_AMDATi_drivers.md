---
title: "Problems with proprietary AMD/ATi drivers"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by jmans25 on 2011-07-23
Hi there, I am farly new to Ubuntu, only being using it for a month so far, and so far so good :)

Only problem I have is with the ATi proprietary graphics driver and (yes, REALLY:popcorn:) minecraft. Every time I use the proprietary ATi driver and run minecraft, it lets my play for a few seconds (i get no black screens), and then it just closes (crashes) by its self. I do not get that crash when I have the proprietary drivers uninstalled. Also, with the proprietary drivers, compiz is choppy (but it works and so do the window decorations with Emerald theme manager), and boot times are slow. 

But when the proprietary drivers are uninstalled minecraft works FULLY, and compiz works for a few seconds with no window borders (emerald is not working) REALLY FLUID (no lag) but then compiz just "crashes" or something like that, and all my icons on my system look like (gee:frown:) windows 95. With compiz disabled, everything is fine, but I really miss compiz :(.

Can someone help me, please ???

UPDATE:

Ok, I think the problem is with 2D excelleration. With my old, integrated card (Radeon 2100, no proprietary driver available, using open sorce driver), compiz worked fine (a bit of choppyness) and so did emerald theme manager, and I did not get the windows 95 icons! I DID get a warning on the proprietary drivers screen that "this driver is needed for 2D exceleration in newer cards".

---

### Post by wildmanne39 on 2011-07-23
Hi, the issue with compiz and choppiness can usually be fixed by this link.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

---

### Post by jmans25 on 2011-08-15
> **wildmanne39 said:**
> Hi, the issue with compiz and choppiness can usually be fixed by this link.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

Thanks but minecraft still crashes when on propritary drivers. Yes, I understand that this is the fault of ATi and not Ubuntu, as ATi wants everyone to have microcrap winblows. Ow well ;)

---

### Post by alphacrucis2 on 2011-08-15
> **jmans25 said:**
> Thanks but minecraft still crashes when on propritary drivers. Yes, I understand that this is the fault of ATi and not Ubuntu, as ATi wants everyone to have microcrap winblows. Ow well ;)

Try installing the latest version of the ATI driver from the AMD website. The one in the Ubuntu repos will be an older version and may be lacking bug fixes for your card. AMD release a Catalyst update every month. The best procedure for installing the AMD releases is the buildpkg method described in the Ubuntu AT binary driver howto. That ensure that the package management system keeps track of which version of Catalyst/fglrx is installed.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by jmans25 on 2011-08-16
> **alphacrucis2 said:**
> Try installing the latest version of the ATI driver from the AMD website. The one in the Ubuntu repos will be an older version and may be lacking bug fixes for your card. AMD release a Catalyst update every month. The best procedure for installing the AMD releases is the buildpkg method described in the Ubuntu AT binary driver howto. That ensure that the package management system keeps track of which version of Catalyst/fglrx is installed.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

I tried that same problem. But this helped me>>> [http://pastebin.com/EUgPvQ6r](http://pastebin.com/EUgPvQ6r) although thanks anyways ;)
I still don't understand why I need to go through all this BS to play minecraft on a pc with an ATi card. Just because Nvidia is supposedly more into the enterprise market and ATi is more into the consumer market doesn't mean... just forget it. ATi will not listen anyways. 

Ps: I will be making a YouTube tutorial about this "fix" as I am not the first one with this problem. I will give credit to you and all the links in the video.:p

---

### Post by kaldor on 2011-08-16
> **jmans25 said:**
> Thanks but minecraft still crashes when on propritary drivers. Yes, I understand that this is the fault of ATi and not Ubuntu, as ATi wants everyone to have microcrap winblows. Ow well ;)

Actually, AMD puts a lot of work behind open source and Linux. They also produce good quality open source drivers which happen to be the default in Ubuntu and many other distributions. 

As for their proprietary drivers, they frequently release new versions with more features. I think you should learn a bit more about it before slagging a company that does more work than most out there.

Try running Minecraft with the Oracle Java instead of openjdk.

---

### Post by jmans25 on 2011-08-16
> **kaldor said:**
> Actually, AMD puts a lot of work behind open source and Linux. They also produce good quality open source drivers which happen to be the default in Ubuntu and many other distributions. 

As for their proprietary drivers, they frequently release new versions with more features. I think you should learn a bit more about it before slagging a company that does more work than most out there.

Try running Minecraft with the Oracle Java instead of openjdk.
 
I tried both the oracle java and OpenJDK, both would not work, untill I turned on indirect rendering. AMD and ATi are helping the open source world A LOT, but they seem to be more focused on windows, probably because it is more popular. Im sorry for critisizing the company :'( .  Maybe if Linux and Ubuntu was more popular ([http://en.wikipedia.org/wiki/Usage_share_of_operating_systems](http://en.wikipedia.org/wiki/Usage_share_of_operating_systems), only about [median] 1.05% people use it to visit websites compared to Windows being at 85.54% and Mac at 7.25%) it would have better drivers, but the fix I found is acceptible for now. I am thinking of telling Markus Persson (Notch) to make the game default to indirect rendering if direct crashes the game, if that is even possible. But thanks anyways guys :)

BTW: I'm using Wubi, which is probably the cause of all this.

---

