---
title: "running gta:san andreas on wine"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by fremantle on 2010-08-18
i saw alot of youtube videos that show that gta san andreas is running smootly in later versions of wine. i wanted to do this on my ubuntu lucid lynx. i have a iso of the game and on xp i used to mount and install it from a  virtualdrive using magicdisk. i dunno how to do this on ubuntu. can anyone write me a step by step tutorial on how to accomplish this? i wud be extremely grateful. 
using wine 1.3

---

### Post by Vaphell on 2010-08-18
create a mountpoint, for example
**sudo mkdir /mnt/gta4sa**
mount iso using that mountpoint
**sudo mount gta4sa.iso /mnt/gta4sa -o loop**

now navigate to /mnt/gta4sa and run setup.exe or whatever

---

### Post by fremantle on 2010-08-18
can you explain in detail. like where to put the .iso file.

---

### Post by Calash on 2010-08-18
If you put the iso on your desktop and right click on it you may have the option to mount it from there.

I have it on mine but I don't remember if it was because I installed a utility or not.

---

### Post by achase79 on 2010-08-18
just place the .iso in your home directory

---

