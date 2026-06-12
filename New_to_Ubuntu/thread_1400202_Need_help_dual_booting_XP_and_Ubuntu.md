---
title: "Need help dual booting XP and Ubuntu"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by AsianInvasion on 2010-02-06
So I've got ubuntu installed and a windows XP disk. I want to dual boot. I know I have to do something with the Grub2 loader, but I'm not sure what to do. So please help me out! :)

---

### Post by cwalker1960 on 2010-02-06
if you are going to partition just a single drive and install Ubuntu as a second os  you really shouldn't encounter any major problems. grub-pc will almost configure itself. you should be aware that you will first need to shrink the windows partition to make room for ubu install unless your hard drive is already partitioned.. parted magic has some good utilities to help with resizing the windows partition.also has tools to make a partition image for backup .  as always you should back up any important files before continuing. download the latest ubuntu iso and burn it to a cd for the install. actually i had a better disk using a dvdr. set burn speed slow . 4 x is good . if you run into boot problems after the install , all is not lost, grub only rewrites the mbr of windows so it's still there. you don't have to re write the mbr for windows to reboot, just delete it and windows will rewrite it at startup. before you start it/s a good idea to have a boot disk for windows. your ubu disk used for install will get you back into ubu. just read some more in the forums and double check everything before you start. i would guess the biggest problem you should encounter would come from grub. here's a good place to learn more about it.[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by cwalker1960 on 2010-02-06
I guess i could pay better attention. you already have ubu installed .. after the windows install you should be able to run update-grub from ubu and it find the windows partition. if now you can always manually add it  ,, same link will explain

---

