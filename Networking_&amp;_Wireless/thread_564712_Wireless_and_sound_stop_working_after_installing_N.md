---
title: "Wireless and sound stop working after installing Nvidia"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by 8oy on 2007-10-01
i hope i can get some help here, i installed ubuntu gutsy on my acer 5920,everything works fine,even the sound and the wireless works,but after i use envy to install nvidia,my wiress and sound disappear i noticed my kernal have change to kernel and i even try to fix the wirless thing with ndiswrapper,it will get to a stage that i get stock,when it time to find out if the driver works,ndiswrapper -l,it says "invalid driver" any  sugestions on what i could do to make all work without any problems now i was to do a fresh installation on ubuntu,since i cant get the wireless to work,then there is no use of leaving it that way,i will be glad if someone could help thanks in advance......

---

### Post by Elmer Fudd on 2008-01-15
> **8oy said:**
> i hope i can get some help here, i installed ubuntu gutsy on my acer 5920,everything works fine,even the sound and the wireless works,but after i use envy to install nvidia,my wiress and sound disappear i noticed my kernal have change to kernel and i even try to fix the wirless thing with ndiswrapper,it will get to a stage that i get stock,when it time to find out if the driver works,ndiswrapper -l,it says "invalid driver" any  sugestions on what i could do to make all work without any problems now i was to do a fresh installation on ubuntu,since i cant get the wireless to work,then there is no use of leaving it that way,i will be glad if someone could help thanks in advance......
Same with my hp dv9000t.  Everything was working fine then loaded latest nvidia restricted drivers. Sound (82801G (ICH7 Family) High Definition Audio Controller) and wireless (PRO/Wireless 3945ABG Network Connection) went away. lshw shows them  present but "unclaimed". I reset the driver in xorg.conf to "nv" and disabled the nvidia restricted drivers but no change.  Any ideas?

---

