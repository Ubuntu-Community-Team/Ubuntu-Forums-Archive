---
title: "Boot Directly to Ubuntu over Vista"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by Don Ju4n on 2010-10-10
Hi guys

Sorry if this has been posted before im a complete newbie to ubuntu... (i just finished installing about 15 minutes ago)

I know theres something called the GRUB that lets me choose whether to boot to Vista or Ubuntu, but since Ubuntu is way awesome i always boot right into it (unless i gotta change something on vista). The question is if i can skip the GRUB menu and boot right into ubuntu. Thanks

---

### Post by mikeyphi on 2010-10-11
> **Don Ju4n said:**
> Hi guys

Sorry if this has been posted before im a complete newbie to ubuntu... (i just finished installing about 15 minutes ago)

I know there's something called the GRUB that lets me choose whether to boot to Vista or Ubuntu, but since Ubuntu is way awesome i always boot right into it (unless i gotta change something on vista). The question is if i can skip the GRUB menu and boot right into ubuntu. Thanks

If you've got the 2 OS's on different HD's - just disconnect Vista before installing Ubuntu. However if they're on the same HD - you need Grub to be able to boot into vista; you can reduce the delay time before the system automatically boots into Ubuntu.

---

### Post by Mark Phelps on 2010-10-11
Install startup-manager.

Then, open it and use the pull-down to select your default OS.

When you reboot, that will launch if you don't select anything else.

If you want to see NO menu, experiment with reducing the wait time.  Also can be done using startup-manager.

---

### Post by BingHeZhouKe on 2010-10-11
there is a file named "grub.cfg"  in /boot/grub ,you can edit it to make it.
there are  several  lines  like this :
[COLOR="Red"][B]if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi[/B][/COLOR]

you just need  change "timeout=10" to "timeout=0",then svae the file .
the file is readonly,you must run as root to change its attribution before edit it.
wish you  good luck

---

### Post by Rubi1200 on 2010-10-11
> **BingHeZhouKe said:**
> there is a file named "grub.cfg"  in /boot/grub ,you can edit it to make it.
there are  several  lines  like this :
[COLOR=Red][B]if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi[/B][/COLOR]

you just need  change "timeout=10" to "timeout=0",then svae the file .
the file is readonly,you must run as root to change its attribution before edit it.
wish you  good luck
grub.cfg should NOT be edited directly! And, this can be done in other ways.
See here for more information:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by BingHeZhouKe on 2010-10-11
> **Rubi1200 said:**
> grub.cfg should NOT be edited directly! And, this can be done in other ways.
See here for more information:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

in my opinion,it is a easy way.the grub.cfg is just a config file,it is also easy to be recoveried:)

---

### Post by cariboo on 2010-10-11
You have to change the permissions of /boot/grub/boot.cfg before you can edit it, then change it back after you are done. 

The preferred method is to edit /etc/default/grub as root, then run update-grub after you have finished the edit.

---

### Post by Rubi1200 on 2010-10-11
> **BingHeZhouKe said:**
> in my opinion,it is a easy way.the grub.cfg is just a config file,it is also easy to be recoveried:)
As cariboo907 already pointed out, > The preferred method is to edit /etc/default/grub as root, then run update-grub after you have finished the edit. 	

There is a good reason that grub.cfg is not meant to be edited directly:

> [SIZE=3]**[COLOR=DarkRed]Manual Editing of grub.cfg[/COLOR]** (Not encouraged)[/SIZE]
Manual editing of /boot/grub/grub.cfg is not encouraged. Think of *grub.cfg* as a result, not as an initiator. The files that should be edited are contained in the */etc/grub.d* folders and the */etc/default/grub* file.

In order to discourage its editing, *grub.cfg* is read-only. Even  attempting to open, edit and save this file using root privileges cannot  be done until the 'read-only' status is changed.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Don Ju4n on 2010-10-13
> **Mark Phelps said:**
> Install startup-manager.

Then, open it and use the pull-down to select your default OS.

When you reboot, that will launch if you don't select anything else.

If you want to see NO menu, experiment with reducing the wait time.  Also can be done using startup-manager.

I'll try that, but for now I guess ill have to stay content with my GRUB... and im not talking about jail grub :D

---

