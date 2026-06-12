---
title: "compaq laptop not able to run live ubuntu 10.04"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by myax on 2010-05-23
HI
i am new here, minutes ago i receive an ubuntu 10.04 cd and immediately set to boot it on my laptop whic is compaq cq 61 305ev.
the cd booted fine and came to the point where it asked me to select language ant i clicke to test it before install.however it got stuck on a black screen with an immobile cursor.

i tried the live cd on my desktop and it works perfect!!

hats off to UBUNTU for sending me the cd..

wish i can run it on my laptop.
PS: its an AMD processor and ati 4200 gfx.

---

### Post by Rubi1200 on 2010-05-23
I don't know if this will help, but it has worked for some people:

[http://ubuntuforums.org/showpost.php?p=9239795&postcount=19](http://ubuntuforums.org/showpost.php?p=9239795&postcount=19)

Alternatively, place i915.modeset=1 on the boot line.

Good luck!

---

### Post by lkraemer on 2010-05-23
There are a couple of things you can try with that LiveCD that may help.

First go here and read the information, especially about xforcevesa
at the bottom of the page.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

1.  Insert the LiveCD of 10.04 and do a RESTART of the booting OS.
2.  When the LiveCD starts to Spin up Hold down the Left Shift Key
    until you get the Question about Splash Screen.  Answer NO.
3.  Hit ENTER when you see Boot:
4.  As soon as the screen gets displayed about Booting hit the UP or DOWN
    arrow to let you have access to the menus, before it immediately
    boots.
5.  Add xforcevesa cheat code and see if it will boot using vesa versus
    trying to load the Nvidia drivers or whatever it tries.

Maybe this will get it booting, if not you probably need to download the
Alternate Install ISO.  I don't think any other cheat code will help,
but I could be wrong.
 
lk

---

### Post by myax on 2010-05-24
I tried Rubi1200 suggestion with xforcevesa option, but all i get is a black screen. :(

i actually am disspointed, puppy linux and kaspersky rescue disk(gentoo) have booted perfectly in the same laptop...

---

### Post by Rubi1200 on 2010-05-24
Hi,

there are 2 more options you could try that seemed to have worked for some people:

Change the boot line from this

[B]file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[/B]
to this

[B]file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz i915.modeset=1 --
[/B]
Alternatively,

from this

[B]file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[/B]
to this

[B]file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --
[/B]
See if either of these options works for you.

---

### Post by myax on 2010-05-25
thanks a lot !!!

nomodeset worked, i can run live ubuntu now.i did not try the i915.modeset option though.

Now could you please tell me if i have to set some special option prior installing or what?

---

### Post by Catharsis on 2010-05-25
After installing, your computer will boot into a black screen just like the LiveCD. To enable "nomodeset" here hold down Shift during your first boot to get to the grub menu. Then hit 'e' and then add "nomodeset" after "quiet splash". Ctrl+x to boot.

Once in the desktop, you can make this change permanent by editing /etc/default/grub
```
gksudo gedit /etc/default/grub
```
Add "nomodeset" to this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
so it reads
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
Save and exit, and then run
```
sudo update-grub
```

If you still get a black screen, then also remove "quiet splash".

---

### Post by myax on 2010-05-27
new problem here........

I tried the wubi installer, which worked fine, after booting i get the login screen and i noticed i am able to move my cursor for a sec then everything is just stuck, keyboard and mouse dont respond at all, had to remove my laptop battery and restart to windows.

is there a workaround to this now??

---

### Post by Catharsis on 2010-05-28
Wubi isn't designed as a stable system; it's for testing Ubuntu on Windows machines to see if you like it. If you want to install Ubuntu, create a new partition and install Ubuntu onto it using the LiveCD.

---

