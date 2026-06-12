---
title: "Dual boot with two harddrives ubuntu &amp; Mythbuntu"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by Peterfc on 2009-11-29
I have on my Computer Ubuntu 9.10 running nice and i am happy with it. I have installed a second drive 500GB that i would like to install Mythbuntu. 

I would like to install Mythbunu on my second drive but still boot to my normal Ubuntu but when i wish to use Ubuntu change drive. The reason is i have tried Mubuntu before and did not get it to work the way it should the best i could get was to watch Dvd's but not to upload Dvd's that where mine. So i would like to try now there is a later version. 

I know in Ubuntu Linux anything can be done but some of use need some help.

Peter

---

### Post by oldfred on 2009-11-29
I have always liked the idea of at least one operating system on each drive and in that drive have the MBR with boot for that drive. That way if any drive fails I can still change BIOS and boot another drive.

I do not know if mythbuntu will give you a choice where to install its boot loader like Ubuntu does. The advance button in Karmic near the end of the install lets you choose where to install grub. Karmic with grub2 is really good at finding other operating systems so once you have myth installed, you can run the update-grub command and it should find it and add your myth install to the grub menu. 

I would just go ahead and install it and see if you can redirect the default grub install to the new 500GB drive not your current one . Just be prepared to reinstall grub for your standard install if myth overwrites your boot grub. If you are real concerned you can unplug your first drive and install to the second. After your plug in the ubuntu drive you then can run the update-grub.

---

