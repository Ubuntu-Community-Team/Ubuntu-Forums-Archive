---
title: "Explosion"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by bgsteiner on 2009-06-03
After recently installing the newest update of ubuntu praise Linux I booted my computer and got an error 17 

I have 2 Hard Drives one with just XP and the other Linux and backups. 

On the Linux partition I installed ubuntu and it worked fine installing then when booting after installing i got an error 17 so I shutdown and checked everything booted again then herd a click and my extra hard drive sparked and died my power supply saved my computer and I have XP still. Could this be related to ubuntu of is it just a funny coincidence?

---

### Post by LewRockwell on 2009-06-03
no, it was just a coincidence

---

### Post by stalkier on 2009-06-03
> **bgsteiner said:**
> After recently installing the newest update of ubuntu praise Linux I booted my computer and got an error 17 

I have 2 Hard Drives one with just XP and the other Linux and backups. 

On the Linux partition I installed ubuntu and it worked fine installing then when booting after installing i got an error 17 so I shutdown and checked everything booted again then herd a click and my extra hard drive sparked and died my power supply saved my computer and I have XP still. Could this be related to ubuntu of is it just a funny coincidence?

Sorry to say but it is just a strange coincidence. As far as I know (and I could be wrong here) an OS cannot cause hardware to fail, as in destroying them like your hdd caught fire or whatever. It can, however, cause a CPU to go up in smoke if the fan is not running. I believe the same goes for RAM getting too hot etc.

---

### Post by bgsteiner on 2009-06-03
well now after letting my computer chill it wont load windows i only have my XP hard drive plugged in and i get an "GRUB Loading Please Wait...                         Error 21" i need Some help

---

### Post by LewRockwell on 2009-06-03
looks like you're going to need to use the live-run CD to do some investigating

---

### Post by mdawg414 on 2009-06-03
You mentioned you had two hard disks, GRUB probably detected both of them. Error 21 indicates that one of the disks doesn't exist which makes sense. Is there any way you can plug the other hard drive in or is it totally smoked?

---

### Post by bgsteiner on 2009-06-03
it is completely gone
 would inserting the old ubuntu disk work

---

### Post by mdawg414 on 2009-06-03
Yeah I would recommend using a Live CD and trying to fix grub. Depending on where grub is actually installed you sometimes can and sometimes cannot recover it but as far as I know, you cannot do it at all from Windows. There are tutorials scattered around Google but here is one that should be useful:
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

You basically need to remove one or more of the partitions from the old linux drive so that grub doesn't go looking where there's no disk

---

### Post by Bölvaður on 2009-06-03
> **stalkier said:**
> an OS cannot cause hardware to fail
it can. but most bugs like that have been fixed last century. one was a bug that made monitors explode.

but yeah this is a coincidence.

there might be a slight chance if.... umm... if you forgot your screwdriver inside the box and there came a very powerful earthquake and the computer fell down... 4 floors to the ground.

---

