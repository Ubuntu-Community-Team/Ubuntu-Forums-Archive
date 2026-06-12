---
title: "Problem"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by reysol48 on 2009-09-11
I do not know source off the problem but if anyone know how to fix it please help, keep it simple new to Ubuntu (512ram, Pentium 3, 32 bit) , include 2 screen shot off the problem.

[ATTACH]128239[/ATTACH]

[ATTACH]128240[/ATTACH]

---

### Post by lisati on 2009-09-11
If you're referring to the area of the screen that appears to be blanked out on the second screen shot, I sometimes have a similar problem too with FF 3.0.13. Refreshing the page usually works for me. I suspect that it's possibly flash-related but haven't come up with a better solution yet.

---

### Post by RedRat on 2009-09-11
> **reysol48 said:**
> I do not know source off the problem but if anyone know how to fix it please help, keep it simple new to Ubuntu (512ram, Pentium 3, 32 bit) , include 2 screen shot off the problem.

[ATTACH]128239[/ATTACH]

[ATTACH]128240[/ATTACH]
I know you are new to Ubuntu and perhaps this forum but you give absolutely no details at what your problem is!! I am sorry but two pictures is just not enough. What version of Ubuntu are you running. Please be more descriptive.

---

### Post by cariboo on 2009-09-11
As lisati says, it looks like you don't have flash installed, go to System-->Administration-->Synaptic Package Manager and search for ubuntu-restricted-extras and install the meta package, it will install Flash, jave and most of the codecs you need to play most audio/video media.

---

### Post by reysol48 on 2009-09-11
Well I am runing Ubuntu 9.04, run update manager every 2 days, yes the problem is the white area in WOW page is alwayas there and on the other screen remains after an expanding advertaiment, I think all those packeges are install

---

### Post by dante00001 on 2009-09-16
I am also experencing this problem. I have searched launchpad for similar problems and found [this]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/342587") post. My problem is like this but the white space is in the advertisment and there is no residual effect when the add goes away. Any help would be greatly appreciated.

---

### Post by RedRat on 2009-09-16
Yesterday I had to re-install FF3.0 from scratch. I did a complete uninstall and then reinstalled FF from Synaptic. When I did this, I could not view YouTube video. I kept getting an error message that I either had Java script turned off (I did not) or I needed to download Adobe Flashplayer, which was already installed. Long story short, I did reinstall flashplayer from Synaptic and I "think" this might be the problem. I went to Launchpad and posted a query about this. One comment came back that Adobe FlashPlayer in the repos is borked. So I completely uninstalled FlashPlayer and re-installed the version from the Adobe Site. That seemed to make my system work once again. Now this just might be a coincidence, but today I noted that my update manager wants to install FlashPlayer from the repos. I think I will pass on this for the time being. You might trying doing what I did and install from Adobe directly.

---

