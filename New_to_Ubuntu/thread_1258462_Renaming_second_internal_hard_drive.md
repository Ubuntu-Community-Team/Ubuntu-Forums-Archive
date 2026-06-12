---
title: "Renaming second internal hard drive"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by hanzj on 2009-09-05
Hello, 
I've just installed a second SATA hard drive. It shows as "71.3 GB Media" in Nautilus. It is located in /media/disk.

Can I rename it to something else, such as "DriveB"?

---

### Post by Kristofer Van Orton on 2009-09-05
well if your dual booting with windows you can rename it there and the same changes will apply in ubuntu
thats how i did it anyway
if your not im sorry i can't help ive tried to rename them but it wont let you
im sure theres some way to do it though

---

### Post by Big_astur on 2009-09-05
I guess u can do it using gparted (partition editor).

U can find it under System - Preferences - Partition Editor (sorry mine is in Spanish)

If you don't have it you just go to Synaptic or Add/Remove from Applications and search for gparted.

Now launch it and you will have access to all your drives. On the top right u see you can select diff drives with a context menu.

Switch to the one u wanna "rename". If it's mounted you need to unmount it (right click on it and select unmount). Do it and now repeat the right click and you will see Label option. There you can give it a name.

---

