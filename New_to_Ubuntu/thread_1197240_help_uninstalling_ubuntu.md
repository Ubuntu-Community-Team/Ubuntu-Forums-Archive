---
title: "help uninstalling ubuntu"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by zimmatic on 2009-06-25
i have ubuntu jauynty jackalope. i am pretty new to the linux. windows the bane of my computing existence anyways to make a long story short i installed ubunt a second time so now i have 2 ubuntu's that i can choose from... along with the stock windows vista loaders. i would like to uninstall the old 2 ubunts format the a partion while still keeping my windows(****) usable..

---

### Post by SunnyRabbiera on 2009-06-25
Well you could use the Ubuntu live disk to delete the two partitions and convert it to NTFS.
But Grub might remain though, but meh.
But if you need help using Ubuntu you really should just ask.

---

### Post by el.otro on 2009-06-25
I think we need more details to help you here, the set up of your hard drives (how many), partitions, etc...

you could probably try posting the output of this command:

```
sudo fdisk -l
```I'm pretty new here too, but I know it isn't necessarily difficult to delete an OS (sometimes you do it without knowing, :-?)....

Do you want to part with ubuntu, or just one of your ubuntus?  You did a fresh install or did you upgrade? you might have two kernel images, and that's different...

....

---

### Post by TheForumTroll on 2009-06-25
Boot from your Windows Vista DVD and enter a console. Then use the "bootrec" command to fix the MBR if needed.
([http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392))

Then in Vistas control panel you can delete the partitions.


Never thought I would give advice on Windows in here ;)

---

### Post by philcamlin on 2009-06-25
good luck

---

