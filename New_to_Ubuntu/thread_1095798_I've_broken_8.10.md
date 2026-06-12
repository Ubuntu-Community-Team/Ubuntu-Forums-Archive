---
title: "I've broken 8.10"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by mr-woof on 2009-03-14
lo all,

i rescued an old laptop with the purpose of installing loads of different distros on it, to play with the partition editors etc etc

So completely wiped it, installed 8.04 no problems. I left it doing the upgrade to 8.10, came back and power must of had gone off :)

I've ran the recovery mode, fixed the file system and tried to fix x. When i boot normally into ubuntu now, i can log in then it just sits on a peach screen and does nothing, no icons etc

This was the whole purpose of saving the laptop, to learn about the guts of linux and here i am lol :D, anyone got any tips/ideas?

---

### Post by Svensk023 on 2009-03-14
well if it shut-off during the upgrade then some key boot files may have not been upgraded. 
BUT it is possible that u had a dirty upgrade, which has happened to me so i stick to fresh installs.
To keep all of your personal files/settings be sure to set up your partitions as follows
ext3 /  (give about 7-10GB)
Linux-Swap (double your RAM)
Ext3 /home with the rest of your space.

so this way if u need to re-install your filesystem all you have to do is re-mount your /home partition but u wont have to re-format it during a re-install.

---

### Post by mr-woof on 2009-03-14
There are no personal files, as it's only my mess around laptop :)

At a root prompt if i try to remove the ubuntu desktop, it's asking me to run 

sudo dpkg --configure -a

i then run

sudo apt-get update

It's basically saying error, failed to fetch this, can't resolve that

Ethernet cable is connected

---

### Post by ex-wirecutter on 2009-03-14
Why not stick with 8.04 and just get the updates on that ?

---

### Post by mr-woof on 2009-03-14
I can't get into anything at the moment, i think this time i'll do a full reinstall lol

---

### Post by clive littlewood on 2009-03-14
Hi

+1 for 8.04     

For testing and "playing around" your better with the LTS version.

Clive

---

### Post by mr-woof on 2009-03-14
I want this laptop as a test bed, i dual boot at the moment on my main machine with xp and 8.10.

---

