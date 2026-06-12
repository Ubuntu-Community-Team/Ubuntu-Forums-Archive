---
title: "Updating Ubuntu (new user)"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by Astel on 2010-09-22
Well, after having my XP installation fried one more time, i decided to try with an Ubuntu CD i had, since i have been hearing good things about it.

The process was flawless and i installed all the suggested updates, then proceeded to install some more apps and games. Then i realized the version was 8.04 and there is a new version to upgrade called 10.04... after a little research i found that a new version will be released in october.

So... should i upgrade now? Wait for the 10.10 version? Or just stick with 8.04?
There is a chance of the upgrade messing with the current installation?

I just want to be sure that i have a solid base before using the new OS.

---

### Post by lbrty on 2010-09-22
I would do a clean install of Lucid Lynx 10.04.1 LTS (Long Term Support). Download the .iso file, burn to a CD or use a USB flash drive (UNetbootin), boot into the live environment, test to make sure all the hardware is compatible with Lucid Lynx and go from there.

---

### Post by Paul820 on 2010-09-22
As linuxliberty said, just put the 10.04 lts version on. 10.10 will be out soon but that is not an lts (long term support) version and the first couple of months could still be a little unstable.

---

### Post by Jesus_Valdez on 2010-09-22
Also is important to notice that there's no way to direct upgrade from 8.04 to 10.04. You would need to upgrade step by step 8.04 -> 8.10 -> 9.04 -> 9.10 -> 10.04.

So, better reinstall.


EDIT. Yeah, except with LTS, wich I forgot 8.04 is one. Sorry for the incovenient.

---

### Post by cariboo on 2010-09-22
You can upgrade LTS versions from one to the next, you don't have to go through all the versions. To upgrade to the next LTS version, just press Alt-F2 and type:

```
update-manager -d
```

you will see a button to click on to do the upgrade. Make sure you are fully up to date before starting. The update process should also disable any third party repositories you have setup, that will have to be re-enabled after the upgrade is finished.

---

