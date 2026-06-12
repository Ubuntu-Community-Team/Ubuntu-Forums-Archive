---
title: "Karmic won't boot"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by Old and Rusty on 2010-04-14
Karmic 64 has run flawlessly since it's release date.  It fails to boot now and the recovery mode does not work either.  

I did a fresh install on another partition on the one drive I am connected to now.  It is just fine.  I need to be able to repair the old install or import everything to the new install.  I would prefer to repair. 

On boot-up grub starts the old install. The normal start-up commences but at the point where the desk-top would normally appear, a blizzard of text appears.  "init: failed to spawn networking   mainprocess: unable to execute: Permission denied.

init: job-process.c.529 unhandled error"

This goes on and on with references to rc-sysinit and many other similarly named things.

I am pretty sure this is not a grub problem.



I examined the sys folder in the old install and compared it to the new one.  The old folder is empty while the new one has a number of files in it.

Can somebody help me get the old install going?   Is there something I should copy?    I have a huge amount things in the old one which I would hate to lose.  I can't even figure out how to get my email stuff from the old system.:confused:

---

### Post by mikewhatever on 2010-04-14
I've no idea how to fix the old installation, however, it should be fairly easy to pull out all of the files and settings. From the live cd, or the new installation, open Nautilus, click on the relevant partition in the left panel to mount it, and make a copy of your home folder. All the emails, for example, should be in .evolution, a hidden folder in the home directory.

---

### Post by Old and Rusty on 2010-04-14
Thanks.  It is a start and email is one of the more important things to revive properly.


It worked.  Thanks a lot!

---

