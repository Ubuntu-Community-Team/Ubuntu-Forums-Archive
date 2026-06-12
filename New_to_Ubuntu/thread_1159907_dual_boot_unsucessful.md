---
title: "dual boot unsucessful"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by ettercap on 2009-05-15
hello every 1

i had windows 7 in a partition but the boot files were in an other 100MB drive.( yeah ! thats the way windows 7 installs)

When i installed 9.04 i selected the 100MB partition as /boot and an other partition as / 

after the installation was complete , i cant see windows 7 as an option in the grub list !

i need both windows & ubuntu !
Can any 1 plz help !?

---

### Post by bruno9779 on 2009-05-15
If I understand you right, you have installed /boot in the 100MB partition, thus overwriting the boot files of Windose.

---

### Post by ettercap on 2009-05-15
yes i did !

is there any way to get both of them working ?

---

### Post by hobo14 on 2009-05-15
You've killed windows with /boot ;)  Should have put /boot and / on the same partition.

Now you need to reinstall windows (or just that part of it, if possible), then reinstall ubuntu without putting anything where windows already is.

---

