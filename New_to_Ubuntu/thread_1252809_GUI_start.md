---
title: "GUI start??"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by broncot on 2009-08-29
I am trying to setup xubuntu on a Sony Vaio laptop for my son to use, it installed, but it boots to the terminal prompt. I did the below because the select and install software failed during the installation, but it still boots to terminal. When I type 'startx' which I saw in another post, my screen goes blank and I have to press & hold the power key to shut down, and then restart.
I'm clueless, help!!
sudo apt-get install gdm ubuntu-desktop

---

### Post by halitech on 2009-08-29
if you want Xubuntu you should install
```
sudo apt-get install xubuntu-desktop
```
what model Vaio are you trying to install on?

---

### Post by LewRockwell on 2009-08-29
it is possible that your difficulties have been identically experienced previously by someone reading your thread and trouble-call

of course, they could not be sure of this without your specific equipment information

IIRC, Sony produced more than one Vaio laptop...

.

---

### Post by broncot on 2009-08-29
Sorry. I copied and pasted, I entered xubuntu. It's a PCG-9401
sudo apt-get install xubuntu-desktop

---

### Post by halitech on 2009-08-29
could you post the specs of the machine, can't find much online but from what I can find, Xubuntu may be too heavy for it and you may want to install LXDE to get a little better performance out of it.

---

### Post by broncot on 2009-08-29
It has 188mb of memory, an AMD K-6 processor 550mhz, 12GB hard drive. It had Windows ME on it, which was useless.

Where do I get LXDE? I went to lxde.org, but the download links seem broken.

I just want a basic system with a web browser and Open Office (or something similar) for my 9th grade son to do school work on.

---

### Post by halitech on 2009-08-29
almost identical to a system I just gave away, except mine only had a 6gig drive. Once you have the base install done, run
```
sudo apt-get install lxde
```
you'll probably want to go with Abiword and gnumeric instead of open office, it will be a bear on those specs

---

### Post by halitech on 2009-08-29
another option, if you want something similiar is to go with Debian with LXDE with a full install from the Debian cd

[http://cdimage.debian.org/debian-cd/5.0.2a/i386/iso-cd/debian-502a-i386-xfce+lxde-CD-1.iso](http://cdimage.debian.org/debian-cd/5.0.2a/i386/iso-cd/debian-502a-i386-xfce+lxde-CD-1.iso)

---

### Post by broncot on 2009-08-29
> **halitech said:**
> almost identical to a system I just gave away, except mine only had a 6gig drive. Once you have the base install done, run
```
sudo apt-get install lxde
```you'll probably want to go with Abiword and gnumeric instead of open office, it will be a bear on those specs

I get 'e: couldn't find package lxde'

---

### Post by halitech on 2009-08-29
were you trying to install 9.04 or another version? 9.04 should have lxde available to download but 8.10 or older doesn't

---

### Post by broncot on 2009-08-29
> **halitech said:**
> were you trying to install 9.04 or another version? 9.04 should have lxde available to download but 8.10 or older doesn't

It's 9.04. I will try debian

---

### Post by halitech on 2009-08-29
there is info here on installing LXDE

[http://ubuntuforums.org/showthread.php?t=707008](http://ubuntuforums.org/showthread.php?t=707008)

---

### Post by broncot on 2009-08-29
I installed debian, now how do I get that to work?? If I just let it boot, same result black screen. If I choose single user mode, I get the terminal prompt, startx gets me a black screen. sudo apt-get install lxde gets 'lxde is already the newest version. Grrr

---

### Post by halitech on 2009-08-29
I'm thinking issue with the video card drivers. go into single user mode and run```
lspci
``` and look for a line that starts with VGA and post that line back here

---

### Post by broncot on 2009-08-29
VGA compatible controller: Trident Microsystems CyberBlade/i7d (rev 5d0

---

### Post by halitech on 2009-08-29
just what I thought, trident video card. look at this post and if you can, use a thumbdrive to copy the xorg.conf file to the Sony and replace the current xorg file

[http://ubuntuforums.org/showpost.php?p=6135903&postcount=48](http://ubuntuforums.org/showpost.php?p=6135903&postcount=48)

if you can't use a thumb drive, do it manually
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_old
```
```
sudo nano /etc/X11/xorg.conf
```
save and reboot and hopefully it will be working

---

### Post by broncot on 2009-08-29
That did the trick! I've got a gui!!

---

### Post by halitech on 2009-08-29
sweet, it was probably the same issue with Xubuntu but I think you'll find Debian with LXDE will run a little quicker on that machine then a full Xubuntu install.

---

### Post by XubuRoxMySox on 2009-08-29
Make sure your repositories are up-to-date and try installing it from Synaptic.

Open Synaptic, then find the Reload button (up top). It will update the repositories for you, and when it's done, lxde should be listed there. Click on it, select "Mark for installation" and then "Apply."

I can vouch for the superb lightweightness and speed of LXDE on low-spec hardware like yours (and mine). It's super-simple, too, for newbies.

Let us know how it goes for you!

-Robin

---

### Post by broncot on 2009-08-30
Ok, now moving on to other topics, not sure if I should start a new thread or not. I'm wanting to get internet connectivity now, I've got a Linksys USB10T ethernet adapter (no ethernet built in), and a 802.11b Dlink pc card. How do I install them, if possible? Direct me to the proper forum if this isn't it.
Thanks

---

### Post by halitech on 2009-08-30
I would start a new thread and include the relevent details on what is going on. I guess which one to install would depend on you. I would suggest trying both and seeing if they happen to work out of the box before going any farther though.

ps. If you are running the Debian install I would go to their forum and look and post if needed. I have the same username there if you want to hit me with a pm to your thread.

---

