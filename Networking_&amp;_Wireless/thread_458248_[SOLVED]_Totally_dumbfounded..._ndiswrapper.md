---
title: "[SOLVED] Totally dumbfounded... ndiswrapper"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by Korijn on 2007-05-29
Alright, I've had it. I can't figure it out on my own. I've been trying a gazillion different things, googling/searching my *** off on the internet and it just won't work.

I have a Speedtouch 121g wireless usb adapter which I use to connect my wireless router (usrobotics). I don't have a wired connection on that pc, I do however have the connection in windows since the driver works there.

If I look in the Documentation that comes with Feisty Fawn (normal Ubuntu, 7.04) I am told to install ndiswrapper-utils from the live cd through synaptic/software sources. So, I insert the cd. Then I start Synaptic packet manager and tell it to add the cd-rom's packages/repositories to the list. Afterwards I look in the list but there is no ndiswrapper-anything. So, that doesn't work. I decided to try it through the terminal. Doesn't work either.

After that I decided to download the .tar.gz file from their website in Windows. I unzipped it and then burned the entire folder (along with another folder with the speedtouch drivers) onto a cd, and rebooted into Ubuntu. I follow the instructions in the ndiswrapper INSTALL file and it gives me about 50 lines of errors/warnings and whatnot. So I decide to check if my kernel is recent enough (it is) and if the 'build list'-command (something like that) contains a .config file and the include folder. There is no .config file. Is this the problem? If so, where do I get this from? What do I need to do?

This is *really* getting on my nerves, so please, SOMEONE, help me out. I just need to know exactly what to do step by step in a way that it will work. Btw, I only recently switched from Windows to Ubuntu, if you hadn't noticed yet. :) THANKS for the help!

---

### Post by chili555 on 2007-05-29
When you tried to add the CDROM under Synaptic, did you press 'Reload' so Synaptic grabbed the package list from the CD? Please try and then install ndiswrapper from Synaptic.

---

### Post by Korijn on 2007-05-29
> **chili555 said:**
> When you tried to add the CDROM under Synaptic, did you press 'Reload' so Synaptic grabbed the package list from the CD? Please try and then install ndiswrapper from Synaptic.

I'm actually pretty sure I did, but I'll give it another shot.

---

### Post by Korijn on 2007-05-30
> **Korijn said:**
> I'm actually pretty sure I did, but I'll give it another shot.

Okay so I tried that but it won't Reload since I don't have a connection.

---

### Post by Korijn on 2007-05-30
Okay, well, I got it to work. I just got the two packages from packages.ubuntu.com and then installed them.

---

### Post by seshomaru samma on 2007-05-30
did you try ```
apt-cdrom add
```
also you should be able to browse the windows partition from ubuntu so you dont need to burn a CD with whatever you downloaded in windows


to install a tar.gz file you need a package called build-essential which in available in synaptic but I don't know if you can find it on the Live CD.......
after you get build-essential you should just go:
```
./configure
make
sudo make install
```

EDIT: I see you got it working so ...never mind...

---

