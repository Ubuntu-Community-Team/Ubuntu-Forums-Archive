---
title: "change the login screen ubuntu/kubuntu"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by urbackdoor on 2009-11-29
hi^^
I run ubuntu 9.10 and kubuntu. I installed kubuntu before ubuntu. I would like to change the login screen from the kubuntu one to the ubuntu one. How would I do this? 
thanks!

---

### Post by zzHanks on 2009-11-29
Hi.

Go to System > Administration > Login window - Local tab.

You can download more [here]("http://gnome-look.org/index.php?xcontentmode=150").

---

### Post by scorp123 on 2009-11-29
> **zzHanks said:**
> Go to System > Administration > Login window - Local tab. In case you missed it: This doesn't work on Ubuntu 9.10 anymore because out of reasons I fail to understand they decided to ship Ubuntu 9.10 with a totally incomplete and castrated version of GDM.

With Ubuntu 9.10 you have three choices:

1.) Live with the castrated new GDM 2.28 and use the rather non-user-friendly ways to modify it ... If you want that, read here:
[http://ubuntuforums.org/showpost.php?p=8307472&postcount=2](http://ubuntuforums.org/showpost.php?p=8307472&postcount=2)
[http://wiki.archlinux.org/index.php/Gnome_2.28_Changes#Configuring_gdm_2.28](http://wiki.archlinux.org/index.php/Gnome_2.28_Changes#Configuring_gdm_2.28)


2.) Or: You do as I did and downgrade to the old version so it's all themable and customizable again as it was on Ubuntu 9.04 Jaunty. If you want that, read here:
[http://ubuntuforums.org/showpost.php?p=8350408&postcount=2](http://ubuntuforums.org/showpost.php?p=8350408&postcount=2)


3.) Forget about GDM and use Kubuntu's / KDE's "kdm" display manager. It's themable, customizable but e.g. it won't auto-launch the "GNOME Keyring Manager". If you want to give that a try, read here:
[http://ubuntuforums.org/showpost.php?p=8337723&postcount=1](http://ubuntuforums.org/showpost.php?p=8337723&postcount=1)


As I said, I downgraded GDM (suggestion No. #2) after having tried out KDM (suggestion No. #3) first.

---

### Post by zzHanks on 2009-11-29
Thanks.

I didn't think of that this might have changed between versions.

---

