---
title: "i'm stuck!"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by thepiratefish on 2009-07-24
I recently had to install windows to use my zune. i made a seperate partition while using ubuntu and my friend installed xp to the other partition. 
 
how do i swap back to ubuntu? and is there a way i can choose which one i want at startup?
 
i know this involves something called grub but i'm not entirely sure what to do

---

### Post by michy99 on 2009-07-24
Here is how to fix it:

[Recovering Ubuntu After Installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by LewRockwell on 2009-07-24
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by swoody on 2009-07-24
Well, the easiest way to get to where you want to be is to reinstall GRUB. It is the bootloader that tells your computer what to boot from. Since you installed XP, it wrote over GRUB with the Windows bootloader. When you restore GRUB, you will then be presented with the option of which OS you want to boot from when you start your computer. For a nice how-to check out this nice post:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
If you have any issues with that, or any questions, please let us know :D

---

### Post by thepiratefish on 2009-07-24
thanks for all the help! i just used the code from one of catlett's posts on another thread that was posted on this one....lets hope it works...

if not...i'm sure there's a plan B :p

---

### Post by thepiratefish on 2009-07-24
ok...so i'm back in my linux partition (it feels good to be home :p )

how would i switch back to the windows partition now? or preferably, how would i get a menu giving me the option to choose with OS to boot?

---

### Post by wojox on 2009-07-24
Good people:

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

---

### Post by mapes12 on 2009-07-25
...........and another one...........

[http://ubuntuforums.org/showthread.php?t=224351&highlight=backup](http://ubuntuforums.org/showthread.php?t=224351&highlight=backup)

:guitar:

---

### Post by swoody on 2009-07-25
> **thepiratefish said:**
> ok...so i'm back in my linux partition (it feels good to be home :p )

how would i switch back to the windows partition now? or preferably, how would i get a menu giving me the option to choose with OS to boot?

It doesn't give you the option during bootup? The Grub menu should appear early in the bootup process, and ask you if you'd like to boot into Ubuntu or Windows.

---

### Post by thepiratefish on 2009-07-26
it just gives me a bunch of ubuntu kernels as options...i'm not seeing one that looks like it would be the windows partition

---

### Post by philcamlin on 2009-07-26
thertes no option saying windows or anything??

---

### Post by thepiratefish on 2009-07-26
not at all...i just restarted to see if i had missed it. i get a 30 second period of time where i can choose what i want to boot with. they're all ubuntu :/

when i go into places-->computer i can see the windows partition labeled as 28.6gb media

---

### Post by philcamlin on 2009-07-26
check menu.lst and  see if theres any indication of windows

---

### Post by thepiratefish on 2009-07-26
how do i get to that?

---

### Post by thepiratefish on 2009-07-26
i'm going to try to restart again and see where that gets me...

---

### Post by rodh on 2009-07-26
Just in from another boot problem, but sounds to me like you need to hit any key to stop the timer, then scroll down to your windows line if you want to run windows.  The first line of Ubuntu is the newest and usually the one you want to boot to,  the others are fall backs in case an update fails to run because of driver or other issues.

---

### Post by rodh on 2009-07-26
Also you should learn a little about grub, here is a link

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0) 

And you should download and burn a copy of Super Grub Disk, I can't remember where but all I did was Google it.

Stick in there.  We are all here to help, or maybe to just point you in the right direction if we don't know how.

---

### Post by adempewolff on 2009-07-26
> **thepiratefish said:**
> how do i get to that?

open a terminal: applications > accessories > terminal

type:

```
gksudo gedit /boot/grub/menu.lst
```

enter your password, and then post here the entire contents of that file.

---

