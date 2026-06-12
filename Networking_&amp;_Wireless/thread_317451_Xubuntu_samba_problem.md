---
title: "Xubuntu samba problem"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by ducamie on 2006-12-12
Hi, I'm a *complete* noob at linux. I have a microsoft pc and a xubuntu pc on a network through a hub.

I've managed to get samba half working, I can dump files onto the linux machine from the xp machine, and I can mount the C drive of the xp machine on linux I can see the files, (upto a certain point) and then the folders appear empty even though they're not (I can get as far as 'documents and settings', then the user folders appear empty). Also when I restart the linux machine, the mount I had made disappears and I have to mount it again. Alls I really want to be able to do is listen to my music off the microsoft computer on the xubuntu machine. :) 

Which rasies another problem, because once I manage to get the mount to stick, and the folders to not appear empty anymore, my folder I want to get to is private and passworded on the microsoft computer, so will I be able to get around this without removing the password? If not, its not a huge problem. :-k 

Thanks for reading. :p

---

### Post by ducamie on 2006-12-12
I have also tried installing fusesmb following the instructions in this thread, but that didnt do anything it doesnt seem. ](*,) 

[http://ubuntuforums.org/showthread.php?t=300310]("http://ubuntuforums.org/showthread.php?t=300310")

---

### Post by ducamie on 2006-12-12
anyone know what i'd write to mount to a certain folder to the windows pc?

% smbmount //winbox/c /mnt/win 

what would i add to 'c' to get me to my documents?

anyone?

---

### Post by maxamillion on 2006-12-12
it depends on the path to "my documents" i haven't touched windows in many years so i can't say i completely remember but it should be something like "//winmachine/c/documents\\and\\settings/my\\documents/"

/me

---

### Post by ducamie on 2006-12-12
awesome i got it working :) 

ive got to the music, i just cant get it to stick with fstab.

it disappears when i restart.

does anyone know what i have to type in that file. ive tried a million times. :-k

---

