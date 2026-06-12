---
title: "Backing up keyboard shortcuts/gconf-editor tweaks?"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by Cuddles McKitten on 2010-05-05
Is there any easy way to back up these changes so that you don't have to retype them when you reinstall to upgrade?  Alternately, is there any package which backs up and restores your entire setup so you don't have to go through each individual thing that needs restoration (Synaptic package ticks, keyboard shortcuts, networkmanager custom settings, etc.)?

---

### Post by mechro on 2010-05-05
Backing up and restoring... such a big subject... so many solutions.

Stuff like Keyboard settings and gconf tweaks are in your Home folder and the basic principle of replacing a newly installed folder with a back up of your previous "tweaked" folder will work. You can effectively do this for everything in your Home. There is another solution of keeping your Home on a separate partition and re-mounting it when you upgrade or reinstall Ubuntu.

Reinstalling the same packages is also possible.

To get you started...

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)

---

### Post by Cuddles McKitten on 2010-05-05
I set up a separate /home partition last time I reinstalled, so I'm already set.  I guess I can just make copies of said folders in case they're overwritten reinstalling; I was looking for the specific folders in which they're held, but I the "shotgun" approach works, too. :)

Thanks.

---

### Post by mechro on 2010-05-05
I'm not sure if there's a definitive list of what goes where but if your /root Home is pristine you could do...

```
sudo ls -a /root
```

This will give you a list of the basic configuration folders.

---

