---
title: "ubuntu-&gt;debian"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by phanipalagummi on 2009-04-12
After a long use of ubuntu,i just switched to debian,after the installation procedure i fond the following problems

1.i could not fing the synaptic package manager any where.
2.i could not find the software sources any where
3.there is no pppoeconf package in the system.

when i tried to re-analyze the installation cd i could not find any clue ,please any one help me.
And sorry for asking this question here.

---

### Post by hyper_ch on 2009-04-12
(1) install it
(2) that's ubuntu specific
(3) no clue about that

---

### Post by drowner on 2009-04-12
Perhaps you should ask a debian forum?

---

### Post by Yashiro on 2009-04-13
If you don't have a working network connection during the install you will indeed encounter the problems you posted about.

---

### Post by kerry_s on 2009-04-13
> 1.i could not fing the synaptic package manager any where.
2.i could not find the software sources any where
3.there is no pppoeconf package in the system.


1) it was on my install
2) had that to
3) not sure

i used the net installer: [http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso)

in a couple of hours i can put pics, i'm waiting for a friend to bring me a hd, the 1 i had it on died.

alright it's installing, i'm at 595 of 838. :)

---

### Post by kerry_s on 2009-04-13
all right here it is, fresh install just booted,logged in and took the screenshoots.
i don't see no pppoeconf installed, but it is in the standard repo.

---

### Post by kerry_s on 2009-04-13
wow, debian gnome has got bloated.
tips: 
1) the stupid grey'd out parts, you need to install "policykit-gnome", log out and back in.

2) flash, add the multimedia repo, when you install flashplugin-mozilla mark swf-mozilla for reinstall, that will make the real flash the default without having to remove anything.

3) slow gui, save a session in sessions when you first log in. fix the host file. i turned on reduced resources, cause i prefer the wire frame.

i forget what else, had to fix so many things. :lolflag:

i think i'm going to try the xfce4 install, i saw in the installer you can now choose the 1 you want(kde,xfce4,lxde).
if i don't like that i'll probably go with a base build up. ;)

---

### Post by glotz on 2009-04-13
> **phanipalagummi said:**
> After a long use of ubuntu,i just switched to debian,after the installation procedure i fond the following problems

1.i could not fing the synaptic package manager any where.
2.i could not find the software sources any where
3.there is no pppoeconf package in the system.

when i tried to re-analyze the installation cd i could not find any clue ,please any one help me.
And sorry for asking this question here.What did you install exactly? I'm on Lenny and Synaptic definitely is there. Software sources are just like in Ubuntu if I remember correctly at /etc/apt/sources.list And pppoeconf is there too, just like with Synaptic, you'll need to install the package if you haven't got it.

---

### Post by halitech on 2009-04-13
I used the steps here:

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

to get my install done from the ground up. I don't think synaptic is installed by default but can be installed easily

2. once you have synaptic installed you can get to sources from there or gksu gedit /etc/apt/sources.list will open it.

3. pppoeconf needs to be installed as well - synaptic or sudo apt-get install pppoeconf

---

### Post by Yashiro on 2009-04-13
Synaptic is installed by default IF you choose the Desktop System AND you have a working net connection during the setup.

If not you get a semi working desktop and missing apps.

---

### Post by halitech on 2009-04-14
> **Yashiro said:**
> Synaptic is installed by default IF you choose the Desktop System AND you have a working net connection during the setup.

If not you get a semi working desktop and missing apps.

that depends on if you use the net install or a full download. the full download will give you a complete working install.

---

