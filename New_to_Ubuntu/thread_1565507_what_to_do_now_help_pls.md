---
title: "what to do now? help pls"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by munna.cheyur on 2010-09-01
while installing ubuntu i have just allocated 10gb for linux file sysem now my file sysem showing full.. i cant install any softwares in it. im using windows also. now i have anoter 10gb spce. what to do now? is it possible to extend in this same area or can i go anoter ext3 partition if so it will be used by ubuntu without any prob? without getting any prob how to attach more space to my linux filesystem.. explain clearly thanks.

---

### Post by TNT1 on 2010-09-01
Use gparted to extend your current partition into the unused space.

---

### Post by Elaztic on 2010-09-01
If you install Ubuntu it does not take up 10 Gb of space.
You must have alot of data/files then.

If you need more storage for files you can either add a second hard drive (either internal or external) or repartition your drive.
As suggested this is very easy to do with Gparted but your drive cannot be mounted while you do this.
You can either run it from an Ubuntu live-cd or just download and burn Gparted onto a disc ([http://gparted.org/](http://gparted.org/)).

Hope this helps you out.

---

### Post by rocknrollmouse on 2010-09-01
> while installing ubuntu i have just allocated 10gb for linux file sysem now my file sysem showing full

> im using windows also. now i have anoter 10gb spce.

I think it would be useful if you could tell us what disks, partitions and usage you have.  GParted will show this information; as you're just running gparted for info (ie not making any changes) you can do this from within ubuntu (it's only when making changes you need to run it from a live disk.)

---

### Post by clhsharky on 2010-09-01
munna.cheyur

BleachBit in software center will clean files like ccleaner in windows. Pay attention to its popups, and I have never had a issue it.


Sharky

---

### Post by M93 on 2010-09-01
i've tried gparted to give some space from win7 to ubuntu
well i got that extra space...but when i tried opening win7 it didnt open and requested the installation cd to repair something >>keep that in mind<<
caz im not sure if the data is still ok caz today am lazy to try :)

---

### Post by M93 on 2010-09-01
whats better is log into windows reduce its size from(i dont remember the prog's name) then boot from a LiveCD, use gparted, add those extra gegs and ur done

---

### Post by Mark Phelps on 2010-09-01
> **M93 said:**
> i've tried gparted to give some space from win7 to ubuntu
well i got that extra space...but when i tried opening win7 it didnt open and requested the installation cd to repair something >>keep that in mind<<
caz im not sure if the data is still ok caz today am lazy to try :)

You should have checked here first!!  Using GParted to mess with Win7 partitions is asking for trouble -- as you have discovered.

You will need to repair Win7 in order to get it to boot again.  IF you don't have a Win7 installation DVD or a Win7 Repair CD, go to the link below, download and burn the appropriate Win7 CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by M93 on 2010-09-01
to me win7 didnt have much of important things
i was gonna give it up someday...i think this day has come :)
i guess i'll give all the disc space to ubuntu
and install XP in a virtual box or something
but thanks alot :)
and this link could be useful for u munna.cheyur in case u have any
trouble after partitioning (i hope not) :)

---

