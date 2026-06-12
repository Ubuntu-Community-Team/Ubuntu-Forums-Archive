---
title: "root"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Duskao on 2009-04-17
Hey guys, I'm extremely new to Linux let alone Ubuntu and Kubuntu. Now here is the thing... I started with Ubuntu, but then I found out about kubuntu and then through psychocats I found how to have a dual startup with both Ubuntu and Kubuntu so I went and did it. All was fine. But then I decided that since I was using Kubuntu more and didn't want to have Ubuntu on my system anymroe I once agian used psychocats to remove Ubuntu and have a "pure KDE" system. Once again, working fine... mostly. The problem that I have noticed is that I don't seem to have root access. Is there any way I can fix this without having to reinstall the entire OS? BTW *buntu ROCKS!!!! Please help :)

---

### Post by overdrank on 2009-04-17
> **Duskao said:**
> Hey guys, I'm extremely new to Linux let alone Ubuntu and Kubuntu. Now here is the thing... I started with Ubuntu, but then I found out about kubuntu and then through psychocats I found how to have a dual startup with both Ubuntu and Kubuntu so I went and did it. All was fine. But then I decided that since I was using Kubuntu more and didn't want to have Ubuntu on my system anymroe I once agian used psychocats to remove Ubuntu and have a "pure KDE" system. Once again, working fine... mostly. The problem that I have noticed is that I don't seem to have root access. Is there any way I can fix this without having to reinstall the entire OS? BTW *buntu ROCKS!!!! Please help :)

Hi and welcome, this [link]("https://help.ubuntu.com/community/RootSudo") may help

---

### Post by Duskao on 2009-04-17
I'm still trying to find what I am looking for in the link that you gave me. (thanks by the way) but so far I'm having no luck. The problem is when I try to run "run adept" it tells me... "Could not obtain a write lock on the cache, falling back to read-only mode. You won't be able to install, remove or upgrade packages. However, you can still search in the package database and browse packages.
You apparently do not have sufficient permissions to install or remove programs. You may need to run this program as user root (or through kdesudo) to gain write access." 
I was trying to install the latest version of Amarok and failed miserably due to this hiccup with "run adept" perhaps this is normal to not be allowed to access "run adept" but it isn't even giving me an option to give a password or anything like when running add/remove software.

---

### Post by lykwydchykyn on 2009-04-17
Try typing alt-f2 and entering "kdesudo adept" into the box.  That should prompt you for a password.

Is "run adept" an icon or menu item?  If so, you may need to edit it and click the option to run as root.

---

### Post by Duskao on 2009-04-17
"run adept" comes up with Alt-F2 when you type adept.

Thanks it worked :D

---

