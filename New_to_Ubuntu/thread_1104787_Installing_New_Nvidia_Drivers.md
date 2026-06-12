---
title: "Installing New Nvidia Drivers"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by Tumpster on 2009-03-23
Hey there, I just downloaded the most recent drivers from Nvidia's site and was wondering how I can install them. I remember the commands briefly but I always get the "X server is running" talk and then it tells me to try again when it's not running. My issue is I've forgotten the commands on how to safely close x and run the driver package to update to the most recent drivers. I'm currently running 173 and want to have the newest ( I know it may break, thats the risk I'm willing to take.) Thanks everyone!

---

### Post by dwasifar on 2009-03-24
> **Tumpster said:**
> Hey there, I just downloaded the most recent drivers from Nvidia's site and was wondering how I can install them. I remember the commands briefly but I always get the "X server is running" talk and then it tells me to try again when it's not running. My issue is I've forgotten the commands on how to safely close x and run the driver package to update to the most recent drivers. I'm currently running 173 and want to have the newest ( I know it may break, thats the risk I'm willing to take.) Thanks everyone!

Why not just use Envy?  That'll take care of it all for you automatically.  It's in the repos:

```
sudo apt-get install envyng-core envyng-qt envyng-gtk
```

---

### Post by James_Lochhead on 2009-03-24
/etc/init.d/gdm stop

cd to/directory/with/run/script

chmod +x *.run

sudo ./*.run

/etc/init.d/gdm start

---

### Post by The-IRS on 2009-03-24
the newest drivers WILL kill your pc ](*,)

DON'T DO IT!!!! wait till they are supported by ubuntu too.

the latest version supported by ubuntu is 177 by the way. it should find it just with the hardware drivers program.

---

### Post by manilaph on 2009-03-24
i agree do not install the nvidia drivers yet.

when i got a notice that proprietary drivers are available for my system and i activated/downloaded these drivers... the system told me that i needed to restart.

after the re-start... i just got a black screen and no gui no gdm. i did some work-arounds found in this forum but none was a permanent fix for it. after re-starting... other things happened like the fonts became microscopic etc... then after the fix,... back to the black screen.

i just re-installed ubuntu and did not anymore activate the nvidia drivers. and it has been problem-free ever since.

if the drivers were ubuntu-supported... then i would be more confident.

---

### Post by tread29 on 2009-03-25
I know 177 is the latest supported by Ubuntu, but are there any cases where one might need to use an older one. The reason I'm asking is because I have an older Dell that I'm running ubuntu on and the 177 version doesn't work as well as the older one.

---

### Post by MavisCruet on 2009-03-28
I just installed the newest NVidia drivers recommended by the system, 177.  On restart rather than the Gnome I just got input not supported.  Am I going to have to do the manual config thing again?  If so won't this reset the drivers and leave me where I was before?

Should I be adding to this thread or starting my own, sorry if I have breached protocol?

---

