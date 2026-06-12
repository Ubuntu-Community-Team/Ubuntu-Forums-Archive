---
title: "Install doesn't recognize vista"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by snuggs on 2009-11-07
ok, I have a vista / 9.04 dual boot right now, and I went to perform a clean install of the new 9.10 distro and was just going to place it over my 9.04 when the partitions began. when i got to that part, i had 2 options, install 9.10 in the whole hard drive, or set up manually - which then led me to a screen to blindly set partitions. 

basically - during the install it said that it did not recognize any other OS. 

Help :)

thanks

---

### Post by 3l3vans on 2009-11-07
let me start by saying that i am not an expert but i have experience in dual booting linux and windows. what you will need to do after installing ubuntu is modify a file called menu.lst. basically when your grub bootloader runs (right as you turn on your machine) your pc looks at this file and goes "oh so these are the operating systems on this machine!".

menu.lst is located here /boot/grub (in a gui go up until you can't go up anymore and then click on the boot folder, and then the grub folder)

menu.lst is just a text file. open it with sudo privelidges and you will have to add some text under the "other operating systems". as long as you don't erase anything thats already there you won't screw up your system.

now you're probably asking what do i add to my menu.lst file?
well to get windows xp to work i had to add this:

title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

you'll have to search to find what your entry should look like and once you find the right entry you might have to modify the "rootnverify" line. (it tells the system where your windows is located)

hope that helps

---

### Post by Tahakki on 2009-11-07
PLEASE don't do what the above guy said. He meant for the old GRUB, but Karmic uses a new, more complicated version - 2.

Are you sure you didn't wipe all partitions?

---

### Post by snuggs on 2009-11-07
hmm. ok. i'm not sure that is the issue though. 

i've had ubuntu 9.04 and vista dual booting for a couple of months now and love it - actually am able to use it fully as a work computer (except for a couple hiccups in skype now and then), very happy. 

well 9.10 came out and i would like to clean install. 

I thought i could just install over top of 9.04 in the same partitioned area, 

am i confused? :confused:

---

### Post by 3l3vans on 2009-11-07
yea i could be wrong. i am using crunchbang 9.10. grub version is 0.97.

---

### Post by sukigenseki on 2009-11-07
When you manually choose partitions it will not tell you what os is installed on each one, but it will tell you what format each one is, so if you have a vista install then just don't overwrite the NTFS partition, and you will be fine with whatever you overwrite to install your new 9.10 os on. Windows can't use the ext3 or ext4 format, so if you have your 9.04 installation on ext3 or ext4 just overwrite those partitions.

---

### Post by snuggs on 2009-11-07
> **Tahakki said:**
> PLEASE don't do what the above guy said. He meant for the old GRUB, but Karmic uses a new, more complicated version - 2.

Are you sure you didn't wipe all partitions?

positive i canceled the install when it didn't recognize vista and i can still boot ubuntu/vista now. (on windoooze right now) 

can i, question1: use windows to manage partitions. clear the partitions ubuntu is using. and then install into the free space that i just created? 

question2: while i'm playing around (i really do enjoy doing all this - no headache at all - even when it's annoying its still kinda fun) is it possible with all of this uninstall, wiping hard drive, reinstall, dual install, upgrade, reinstall stuff... can i permantly damage my computer? if not, this will free up much of my worry everytime i play with this stuff and i'll feel more confident doing so - if it will i'll continue to have the heart poiunding excitement of not "really" knowing what i'm doing. i just don't want my "learn by experience" to = ruining something that i really need. haha.

---

### Post by snuggs on 2009-11-07
> **sukigenseki said:**
> When you manually choose partitions it will not tell you what os is installed on each one, but it will tell you what format each one is, so if you have a vista install then just don't overwrite the NTFS partition, and you will be fine with whatever you overwrite to install your new 9.10 os on. Windows can't use the ext3 or ext4 format, so if you have your 9.04 installation on ext3 or ext4 just overwrite those partitions.

gotcha... problem is i don't even get this option. i remember this step from when i originally dual booted, and saw the NTFS... it's like it doesn't even see that now.

---

### Post by snuggs on 2009-11-07
> **snuggs said:**
> question2: while i'm playing around (i really do enjoy doing all this - no headache at all - even when it's annoying its still kinda fun) is it possible with all of this uninstall, wiping hard drive, reinstall, dual install, upgrade, reinstall stuff... can i permantly damage my computer? if not, this will free up much of my worry everytime i play with this stuff and i'll feel more confident doing so - if it will i'll continue to have the heart poiunding excitement of not "really" knowing what i'm doing. i just don't want my "learn by experience" to = ruining something that i really need. haha.


bump for this... haha depending on this i might just make a day out of it and scratch both OS's and start all over  :)

---

### Post by snuggs on 2009-11-07
btw.. i didn't have too much time to mess with it so i updated my jaunty and upgraded. 

everything seems to be working flawlessly. 

Thanks for the replies.. sorry the newb urgency.

---

