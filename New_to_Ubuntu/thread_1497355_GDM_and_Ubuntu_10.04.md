---
title: "GDM and Ubuntu 10.04"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by fslezak on 2010-05-30
Hello. I recently installed a copy of Ubuntu 10.04 on my machine through Ubuntu 8.04's Update Manager.

Now, GDM will not load at standard boot. I have to use failsafe mode in the recovery to start X successfully (where I'm writing this.) 

Boot Process:

1. GRUB
2. Ubuntu Boot
3. Black screen where GDM is supposed to be.


Starting GDM by command line doesn't help either. WHAT CAN I DO???

---

### Post by cariboo on 2010-05-30
It sounds like the update didn't finish properly. Start in recovery mode by holding down the shift key and selecting recovery mode when the grub menu shows, at the menu select drop to root prompt with networking. Once at the prompt type:

```
sudo apt-get -f install
```

once the above command is finished at the same prompt type:

```
sudo aptitude update && sudo aptitude -y safe-upgrade
```

The above three commands should finish the update by installing any missing packages and dependencies.

---

### Post by Catharsis on 2010-05-31
What graphics card do you have?
```
lspci | grep VGA
```

---

### Post by fslezak on 2010-05-31
I uninstalled Ubuntu and I _attempted _to install with the Live CD of 10.04.  Just a blank screen after the progress bar disappears.

P.S. Before I uninstalled, I tried command line (via Ctrl+Alt+F1-F6). The only thing: NOTHING!!! The screen wouldn't change! X also has no mouse, but X might not be starting!

What is going on here?

Graphics card: Intel 82852/82855 GM/GME .

---

### Post by Catharsis on 2010-06-01
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
See Workaround A.

---

### Post by fslezak on 2010-06-06
Thanks. t worked perfectly.

---

