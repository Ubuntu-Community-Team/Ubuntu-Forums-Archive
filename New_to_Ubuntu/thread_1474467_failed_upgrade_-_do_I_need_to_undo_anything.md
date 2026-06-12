---
title: "failed upgrade - do I need to undo anything?"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by noworldorder on 2010-05-06
I tried to upgrade and then (perhaps a stroke of luck) my internet connection failed and the upgrade was aborted. It said the files are still on my computer.


Did any of the installation steps do anything to my computer that I need to reverse?

---

### Post by muteXe on 2010-05-06
Not a lot to go on there to be honest.
Does your machine boot up?
If not, can you still "see" your files/drives if you boot up from a live CD?

---

### Post by noworldorder on 2010-05-06
oh that's right... you don't know what I'm thinking...

I think I am just being paranoid.  Everything woks perfectly fine.  Do I need to get rid of the files it put on my computer? Was any configurations or setting altered?

Thanks - Chris

---

### Post by muteXe on 2010-05-06
Ohhh right!  The way you worded that sounded like you may have completely messed up your system.
If it's all working I wouldnt worry about it.

p.s.  I'd get all your data backed up and do a completely clean install if you still wanted to go the latest version.

---

### Post by Charliemong on 2010-05-06
Same happened to me. If you do want to continue the upgrade then just go to the terminal and type update-manager -d. This will continue to upgrade. I managede to brick my upgrade so am now doing a fresh install. Oh well we live and learn.

---

### Post by GSF1200S on 2010-05-06
Nice line in your signature OP!

Did you complete the upgrade at a later time or are you still on 9.10? Post the results of:
```
cat /etc/lsb-release
```
and:
```
uname -a
```

Do you happen to remember if it was just downloading the packages or if it was installing them?

---

### Post by noworldorder on 2010-05-06
[FONT=monospace]DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

Linux chris-laptop 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux


So it was, I believe, in the downloading phase that it stopped due to an internet connection failure.

thanks ~
[/FONT]

---

