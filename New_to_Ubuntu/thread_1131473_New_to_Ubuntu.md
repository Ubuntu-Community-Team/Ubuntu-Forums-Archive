---
title: "New to Ubuntu"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by spencerhdrew on 2009-04-20
I successfully installed Ubuntu 9.04 for the first time. I am using a dell E1505 laptop and have a dual boot the Ubuntu 9.04 and win xp home. The whole install ran beautifully. I go to log in and after I type in my password I get a black screen. I can see the cursor but nothing else.... What do I do to fix this...? Any help would be appreciated since I am new to Ubuntu Thanks

---

### Post by Bölvaður on 2009-04-20
in another thread I read

> **ghindo said:**
> Everything's great for me, other than:
[LIST]
[*]Horrible Intel graphic performance.
[*]Lack of PackageKit.
[/LIST]
Still, love Jaunty.  Best Ubuntu release in quite a while.2.6.28

You have integrated Intel Graphics Media Accelerator 950 according to notebookreview.com.

What puzzles me is that if the driver is not working well then you shouldn't be able to see the login screen at all. 
Try confirm that it is not the driver by pressing E in grub (the boot loader where you choose ubuntu) and write [B]xforcevesa
[/B]then press B to boot (probably after hitting the return button or esc)


Does this change anything? (except give you a little bit worse graphics)

---

### Post by LowSky on 2009-04-20
how did you install? LiveCD or Wubi?

How did you burn the LiveCD?

---

### Post by spencerhdrew on 2009-04-20
This Ubuntu guru at work gave me a cd.

I ran it with cd and it booted fine.  

Is my best bet to fix the problem or download 8.10 from ubuntu's website and "uninstall" Ubuntu 9.04?

[http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)  - (for uninstall)

---

### Post by anystupidname on 2009-04-20
Try:
CTRL-ALT-F1 to get to a terminal (if this fails, skip to 5)
1)sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.turd
2)sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
3)sudo /etc/init.d/gdm restart
4)figure out why your original xorg.conf is borked and fix it (post it here if you'd like)
[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

5)boot from liveCD
6)post output from "lshw -C video" and contents of /etc/X11/xorg.conf.turd in response
7)monitor thread for responses

Sorry, no guarantees...

---

### Post by Bölvaður on 2009-04-20
wait 
**[SIZE=2][Display freezes with Intel graphics cards]("http://www.ubuntu.com/getubuntu/releasenotes/904")[/SIZE]**

you can disable fancy graphical effects. I am not sure how to do it from the terminal but it might just be easier and safer to install compiz (the program responsible for the "cool effects").

CTRL-ALT-F1 to get to a terminal (borrowed from anystupidname)

type:
```
sudo apt-get remove compiz
```press enter
fill in your password blindly (you'll understand when I say blindly) and hit enter

either restart (foolish way) or type (smart way) *deleted* you are able to restart the graphics, but hey.. pushing the restart button is fool proof.


btw you do not uninstall operating systems... you just overwrite them or format their partitions... unless if you used wubi (google it), then you have to uninstall it. (the exception that breaks the rule)

---

