---
title: "xubuntu with edubuntu"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by hollowtd on 2009-03-04
Can I install the edubuntu cd if I have xubuntu on the laptop. (8.10)

---

### Post by jimi_hendrix on 2009-03-04
why not?

just overwrite your xubuntu partition (make sure you have stuff backed up!) or make a new partition and install there

---

### Post by Bölvaður on 2009-03-04
Yes... there are no EULAs stopping you.

But to be more precise what are you talking about?

1. Dual booting
2. edubuntu and xubuntu on different computers?
3. being able to log in under different desktop environment?

---

### Post by jimi_hendrix on 2009-03-04
> **Bölvaður said:**
> 
3. being able to log in under different desktop environment?

if i recall edubuntu uses gnome

this might work but i havnt tested

```
sudo apt-get install edubuntu-desktop
#aptitude might be better if you think you might uninstall 
#because it cleas up better

```

that will install gnome and the edubuntu apps

---

### Post by hollowtd on 2009-03-04
That is what I was thinking--Gnome. Well, actually I'm trying to put xubuntu on my older dell 2500 with over 300 meg of ram and it's now sitting with the bars about 1cm to finish. Im not sure if It will keep going to install or not (I'm actually trying it out first if it will ever load). 


No, I want xubuntu and edubuntu on the same computer.

---

### Post by hollowtd on 2009-03-04
What is the absolute lightest version of ubuntu distribution for a 300 meg computer (I collect computers as donation and take them to africa for schools.)

---

### Post by jimi_hendrix on 2009-03-04
ubuntu-minimal, but i believe that lacks xorg so you will need to get on the internet and download xorg and gnome from command line

(ask if you need help with that)

and to get them both on the same computer, make two partitions and install one to the first partition and the other to the second...or make three and mount one as /home so files can be shared between the two.

---

### Post by hollowtd on 2009-03-04
I'll check this out and tell you what I find and when I run into trouble, which I will.

---

### Post by hollowtd on 2009-03-04
What is xorg? I need that in additon to installing Gnome?

---

### Post by jimi_hendrix on 2009-03-05
> **hollowtd said:**
> What is xorg? I need that in additon to installing Gnome?

xorg is what runs gnome, kde, xfce4, xmonad, openbox, fluxbox, LXDE, and all the other WM's and DE's in linux

you will need it, yes

---

