---
title: "KpackageKit issue"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by vivek40 on 2010-04-12
Hi! 
There is a quite peculiar issue which I am facing.I can use synaptic and software center perfectly ,but whenever I use kPack after the upgrade to kde4.4, it opens , I go ahead selecting the package in kpack , and after that it says "you dont have sufficient privileges to do that operation."

(I use Kubuntu Karmic and upgraded to KDE 4.4 recently.. I guess this issue started after that.. but I am not very sure)

---

### Post by vivek40 on 2010-04-12
bump!!!

(someone please help.. )

---

### Post by WinterRain on 2010-04-12
Try running it with:
```
gksudo kpackagekit
```

---

### Post by cespinal on 2010-04-12
I stopped using kpackage kit for removing software, too. Somehow it does not open with root privileges, which is nonsense considera how critical this application might be...

---

### Post by agnes on 2010-04-12
It does in 10.04; so it might be the upgrade to KDE 4.4 in 9.10 that broke this.
Right click the menu button, go to menu-editor, and insert *kdesu -nc kpackagekit *as the command for KPackagekit.

---

### Post by vivek40 on 2010-04-13
Hii thanks for all the replies ...but agnes: after using that command in the command editor.. kpackage does not open at all...

---

### Post by vivek40 on 2010-04-13
hii i tried using "kdesudo kpackagekit" by pressing "alt +f2"..and yes it worked  but i tried using the menu editor and inserting kdesudo in the command .. so that it looked something like this "kdesudo kpackagekit"... However after doing that when i click on Kpack in the menu I get an additional pop up saying KDEINT could not launch 'usr/bin/kdesudo'.. is that not strange.

---

### Post by vivek40 on 2010-04-13
bump!!!!

---

### Post by kellemes on 2010-04-13
> **vivek40 said:**
> hii i tried using "kdesudo kpackagekit" by pressing "alt +f2"..and yes it worked  but i tried using the menu editor and inserting kdesudo in the command .. so that it looked something like this "kdesudo kpackagekit"... However after doing that when i click on Kpack in the menu I get an additional pop up saying KDEINT could not launch 'usr/bin/kdesudo'.. is that not strange.

Use "kdesu" instead.
Afair "sudo" may work too..
Or.. upgrade to 4.4.2 (as i did), where "the kdesudo issue" (lost link to bugreport) is fixed.
But with 4.4.2 "the kdesudo issue" isn't needed anymore.. KpackageKit is fixed too.. ;-)

---

### Post by vivek40 on 2010-04-13
Thanks Kellemes .. but am using KDE 4.4.2 only...In fact Kpack was working fine before I upgraded from 4.3 to 4.4.2... and yes Kdesu gives me the same issue as below:-

""However after doing that when i click on Kpack in the menu I get an additional pop up saying KDEINT could not launch 'usr/bin/kdesudo'.. is that not strange.""

---

### Post by vivek40 on 2010-04-14
bump! someone please help

---

