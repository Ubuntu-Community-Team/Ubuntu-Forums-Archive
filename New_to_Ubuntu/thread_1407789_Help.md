---
title: "Help?"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by windsong on 2010-02-15
Hi I need some help. My Mom got this computer for free and it has Ubuntu installed, I've never used this operating system and would prefer just to have windows on it. I have a windows 98 floppy disk and an xp cd but neither have worked. The problem is that I cannot log on. I created a new user name and password and now it says that the GDM cannot write to my authorization file or something and then it takes me back to the log in screen... can anyone point me in the right direction here?

---

### Post by marshmallow1304 on 2010-02-15
Are you out of disk space?  Can you log onto the old account?  If so, log in to the old account and open a terminal (Applications->Accessories->Terminal).  Post the results of
```
df -h
```

---

### Post by bwhite82 on 2010-02-15
Would recommend downloading the latest Ubuntu release and reinstalling from scratch:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by tom.swartz07 on 2010-02-15
> **windsong said:**
> Hi I need some help. My Mom got this computer for free and it has Ubuntu installed, I've never used this operating system and would prefer just to have windows on it. I have a windows 98 floppy disk and an xp cd but neither have worked. The problem is that I cannot log on. I created a new user name and password and now it says that the GDM cannot write to my authorization file or something and then it takes me back to the log in screen... can anyone point me in the right direction here?

No bigs, its fairly easy to recover a lost (or in your case, unknown) password on Ubuntu.

During normal usage, a Linux OS runs under runlevels between 2 and 5 which corresponds to various multi-user modes. Booting Linux under runlevel 1 will allow one to enter into a specific mode, single user mode. Under such a level, you directly get a root prompt. From there, changing root password is a piece of cake.

Ubuntu offers a specific boot menu entry where it is stated "Recovery Mode" or "Single-User Mode". If this is your case, selecting this menu entry will boot your machine into single user mode, you can carry on with the next part. If not, you might want to read this part.
Using GRUB, you can manually edit the proposed menu entry at boot time. To do so, when GRUB is presenting the menu list (you might need to press ESC first), follow those instructions:

use the arrows to select the boot entry you want to modify.
press e to edit the entry
use the arrows to go to kernel line
press **e** to edit this entry
at the end of the line add the word ***single***
press **ESC** to go back to the parent menu
press **b** to boot this kernel
The kernel should be booting as usual (except for the graphical splash screen you might be used to), and you will finally get a root prompt (sh#).
Here we are, we have gained root access to the filesystem, let's finally change the password.


As root, changing password does not ask for your old password, therefore running the command:
```
passwd
```

will prompt you for your new password and will ask you to confirm it to make sure there is no typo.
That's it, you can now reboot your box and gain root access again. That should get you logged in to try it out.

---

### Post by no2498 on 2010-02-15
tom.swartz07

thank you for seeing the gist of problem
the first guy had no clue

now i hope he takes his moms new-used computer home puts it beside his an reads what you told him to do
i do hope he  does not put windows back on it an lets her enjoy linux-ubuntu

if he puts windows back on she will not find any anti-virus program for it on 98 and if he puts his xp disk in it they both need a new computer
this is her first computer she will NOT do any on line banking on it
let her enjoy some freedom
lol you just moved out yesterday

---

### Post by tom.swartz07 on 2010-02-15
> **no2498 said:**
> tom.swartz07

thank you for seeing the gist of problem
the first guy had no clue

now i hope he takes his moms new-used computer home puts it beside his an reads what you told him to do
i do hope he  does not put windows back on it an lets her enjoy linux-ubuntu

if he puts windows back on she will not find any anti-virus program for it on 98 and if he puts his xp disk in it they both need a new computer
this is her first computer she will NOT do any on line banking on it
let her enjoy some freedom
lol you just moved out yesterday

HAHA

Yeah, quite honestly, its not a good idea to put Windows 98 on a computer. I think they stopped supporting it last year.


Ive been thinking about this over the past few hours... The worst part about this whole scenario- the computer with Ubuntu originally installed on it is now completely compromised- all of the data is free to be read once the new password is in place. (not that it was a genius idea to give away a computer with a full hard drive in the first place)


To the OP- you could use the method I described to get access to the OS, but I would highly recommend that you dont try to access the old files on there. They were once someones private data, and although they were obviously dumb enough to give the data to you, you really shouldnt take advantage of that and sift through the data files there.



Perhaps SoldierBoy was on the right track when he said to re-install and start from scratch; this way the data is lost for good.

---

