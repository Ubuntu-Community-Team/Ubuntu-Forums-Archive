---
title: "Jaunty Upgrade Problems"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by mpl34 on 2009-05-06
Hey,

I've just updated to Jaunty Jackalope, after the restart my kubuntu (KDE) interface no longer seemed present. Is there any quick and easy fix to this?? I've got some important file there that i do not want to be overwritten so i am holding off reinstalling from my kubuntu cd.

If any more information is needed plz ask.

Cheers,

---

### Post by abn91c on 2009-05-06
can you log in at all or just command prompt? if the upgrade went bad do a **sudo dpkg --configure -a** then sudo apt-get update. you may also have to do sudo aptitude reinstall kubuntu-desktop

---

### Post by mpl34 on 2009-05-06
For the update i will need a connection to the internet won't I? 
Which i am unsure how to do in the command prompt
Yer i can only log into the command prompt mode

---

### Post by abn91c on 2009-05-06
> **mpl34 said:**
> For the update i will need a connection to the internet won't I? 
Yer i can only log into the command prompt mode
better if you do a wired connection, is possible to do with cdrom(the alt cd) but slower. the directions are in the kubuntu website for cdrom upgrade
run the first command it probably tell you whats going on

---

### Post by triunenature on 2009-05-06
Dual boot or just Kubuntu?

Either way really, just use command line to transfer said file to somewhere safe, if your dual booting, move the file to the windows partion, if its a single boot, plug a flash drive in there, mount it and place said file in there, unmount flash, take it out of the computer, and then reformat.

Simple enough.

If you need the codes to do what i just said, i can give you some of them.. but google is your friend

---

### Post by modmadmike on 2009-05-06
type this ```
sudo -i
ifconfig eth0
ifconfig eth1
ifconfig eth2
ifconfig eth3
ifconfig eth4
```
and tell us the output.

---

