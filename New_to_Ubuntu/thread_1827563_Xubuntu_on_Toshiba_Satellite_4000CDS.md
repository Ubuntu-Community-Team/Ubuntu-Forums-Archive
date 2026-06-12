---
title: "Xubuntu on Toshiba Satellite 4000CDS"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by Cameradude on 2011-08-18
hey all im having some trouble trying to do a minimal install of XUbuntu 10.04 on an old Toshiba Laptop, Specs Pentium II MMX, 32mb RAM, 6gig HDD, 24x CD Drive and Standard Floppy Drive. when i attempt to do a minimal install it gives me the error 
[   2.895226] Kernel Panic - not syncing: out of memory and no killable processes [    2.895249]
also the Caps Lock light blinks, ive tryed everything and have tested the disc on a Virtual Machine, the CD is working and have also done a Memory Test and says theres no errors, hope i can get this old system running again

---

### Post by papibe on 2011-08-18
I'm afraid that's not enough RAM. Check the [Installation System Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements").

Can you put more RAM on it?

Regards.

---

### Post by Brushstroke on 2011-08-18
Wow. That thing is old. I really don't even think Lubuntu, let alone Xubuntu, would run on it. Lubuntu is as light as any Ubuntu-based distro can get and it requires a minimum of 128MB of RAM. Grab a copy of the **Ubuntu Minimal CD image **and install that. You may be able to get a very low-requirement graphical environment running on a minimal install using the guide here: 

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Paqman on 2011-08-18
> **Brushstroke said:**
> Grab a copy of the **Ubuntu Minimal CD image **and install that.

He's already done that. 32MB is just going to be too small for Ubuntu.

A quick Google suggest the laptop has one RAM slot and a max memory of 160MB (?!?). So it might be possible to get a system installed if it was upgraded, but wouldn't be very usable. One of the distros designed for older hardware such as SliTaz might be a better choice than Ubuntu.

---

### Post by Cameradude on 2011-08-18
hey guys thanks for the info, though i did look further into the Computer running linux a while back[http://www.neilvandyke.org/linux-toshiba-satellite-4005cds/]("http://www.neilvandyke.org/linux-toshiba-satellite-4005cds/") , it said it should have been able to run a striped down version of Debian, but i guess that was with the Extended RAM put in, but i will defiantly try SliTaz or probably even DSL, and as for old computers the oldest i have fully running is an Atari STacy Version 1 from 1984, again thanks for the info and help, ill be sure to reply within the next few days on if it works or not

---

### Post by Cameradude on 2011-08-18
ok so ive been able to install DSL with CLI working :D, however XServer refuses to start, it gives the error

XIO:   fatal IO error 104 (Connection reset by peer) on X server ":0.0"
         after 0 requests (0 known processed) with 0 events remaining.

i currently have it set at Xfbdev through xsetup.sh

 to tell you the truth the goal im hoping to reach is to have an old laptop that can do Word Processing and play music and browse the web in all its 56k glory (yes the driver for the Modem works!)

---

