---
title: "Install problem hang Busybox/initramfs"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by kahoona on 2010-01-27
Hello
I am new to linux and I am trying to install Ubuntu or Xubuntu from CD on an old Compaq Presario 5190. It has 186m of ram and I have connected a newer Seagate Barracuda 40g hard drive. I wish to do a complete new install including formatting the HD.T have tried 9.10 which shows the menu screen and when I select install it hangs with a black screen and a blinking cursor.
I suspect not enough RAM so I tried Xubunto 8.04 hardy desktop then 8.04 alternate both for i386. I get the menu screen with the logo and choose install and, after the bar with the moving dot ic on for 20 seconds or so I get
BuisyBox v 1. 1.3 (Debian 1:1.1.3-5 ubunto12) Built-in hell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) with a blinking cursor
It does not react to any input. Help, Exit. This is the same with or ALT. I have no coding experience and am lost . Anything you can suggest would help. Thanks

---

### Post by 4Orbs on 2010-01-27
Even if you manage to get Xubuntu installed somehow, I think your desktop would be unpleasant to use. Considering the amount of ram available you could be much happier using one of the super-lightweight or micro-distros. I suggest visiting this website: [DistroWatch]("http://distrowatch.com") and check out Puppy Linux, MacPup, Slitaz, DamnSmallLinux or some of the other systems made specifically for older, low-ram computers. You might also consider trying an Ubuntu Minimal install and add a window manager rather than a full desktop environment. Openbox is a great window-manager with a quick learning curve.

---

### Post by kahoona on 2010-01-28
Thankyou
I will do exactly that and will post the results when I do.
Kahoona
Wow! 
That was easy.I truly cannot believe that you fit all that in a 50m environment. And this old doorstop of a PC runs great!
A little more help please. I need to format the Hard drive to remove its other content and create the 50m partition to do the frugal install. It says to use  cfdisck. I have looked for it but cannot find. cfdiskcf

---

### Post by 4Orbs on 2010-01-28
cfdisk runs in a terminal instead of a clickable interface. So you need to first open a terminal and make yourself the super user by entering:
```
su
```
Then enter your password (which might be confusing because entering a password in the terminal shows no indication that it is being entered). Then, when you are root user (super user), enter in the terminal:
```
cfdisk /dev/sda
```
And cfdisk should appear in the terminal. I am assuming that your hard drive is /dev/sda, but it might be /dev/sdb or /dev/hda depending on which distro you are using and which hard drive you are installing the system into.

---

### Post by kahoona on 2010-01-28
OK
This could be fun. "Toto..I don't think were in windows (Kansas)anymore"
I have a lot to learn but if I can get the hang if it I might keep Linux on a PC. 
Kahoona

---

### Post by 4Orbs on 2010-01-28
It would probably be prudent to go to the main website for whichever distro you are planning to install. There, you should find the proper installation instructions and user documentation. Check out their forums to get an idea of what to expect after install.

---

