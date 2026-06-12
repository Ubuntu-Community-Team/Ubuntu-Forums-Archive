---
title: "running Ubuntu 9.04 with no hdd"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by stalkier on 2009-07-16
I have a dilemma. I am trying to get another desktop going but right now I cannot get my other hdd out of my #1 desktop. Right now I am running Ubuntu 9.04 in Live session. The response is fast for me and everything is fine for now. What I am needing to know is:

Is there a way to install to external hdd via USB and use a bootloader CD?? I am unable to boot via USB. OR Is there a way I can write files (Bookmarks, temp files, etc) to a external and just use Live Session? 

I will not be able to buy a new hdd for two weeks. I do not care if I have to reinstall etc when I get a new hdd.

NOTES:
LiveCD version 9.04 desktop
CPU: AMD  Athlon X2 2.20GHrz
RAM: DDR 400 2.5GB
CDrom: DVDR DL
GPU: XFX GeForce 8500GT 512MB (PCIe)

---

### Post by starcraft.man on 2009-07-16
Ok, so as I see this is the setup. You have computer 1 functioning fine, and set up computer 2 but it has no HDD at all. You want to save files from computer 2. Well that's simple enough, ya you can just use a live session. The only note, is do not install any kernel updates that require you to restart the machine. You can install most others.

As for saving files, you have multiple possible solutions. If you have an external USB (or eSATA/firewire) hard drive just plug it in and it will be automounted. If you don't want to do that, assuming both machines are networked through a router/switch, you can share a folder on the first desktop and save files to that folder via the network from desktop 2.

To do that, just right click on a given folder (make one in home, call it Share) and click properties > share tab >share this folder. You'll be prompted to install samba services, do so. Once installed, tick all boxes, and name the share whatever you like. Go to desktop 2, and repeat by installing services, no need to share a folder on this one though. Once service installed, just open up Places > Network and you should be able to navigate to the share then just drop files on it.

Could also just use a multisession CD/DVD for saving absolutely important files. Just install gnomebaker or k3b and make sure you leave it open on burning.

---

### Post by Tman5293 on 2009-07-16
You could always create a casper rw file:

 **Step 1, create the casper file** 
1.1) panda@cyberspace:~$ mkdir project
1.2) panda@cyberspace:~$ cd project
1.3) panda@cyberspace:~/project$ mkdir casper
1.4) panda@cyberspace:~/project$ cd casper
1.5) panda@cyberspace:~/project/casper$ dd if=/dev/zero of=casper-rw bs=1M count=**512**


**Step 2, “format” the casper file** 
 
2.1) [email]panda@cyberspace:~/project/casper$mkfs.ext[/email]3 -F casper-rw


So... We've just created a 512MB EXT3 casper-rw file in *~/project/casper/*, that sweet!!!
Now I suppose you'd like to use it right??


**Step 3, mounting the casper-rw file** 
 
3.1) panda@cyberspace:~/project/casper$ sudo mkdir /media/casper
3.2) panda@cyberspace:~/project/casper$ sudo mount -o loop casper-rw /media/casper

---

### Post by stalkier on 2009-07-16
> **Tman5293 said:**
> You could always create a casper rw file:

 **Step 1, create the casper file** 
1.1) panda@cyberspace:~$ mkdir project
1.2) panda@cyberspace:~$ cd project
1.3) panda@cyberspace:~/project$ mkdir casper
1.4) panda@cyberspace:~/project$ cd casper
1.5) panda@cyberspace:~/project/casper$ dd if=/dev/zero of=casper-rw bs=1M count=**512**


**Step 2, “format” the casper file** 
 
2.1) [email]panda@cyberspace:~/project/casper$mkfs.ext[/email]3 -F casper-rw


So... We've just created a 512MB EXT3 casper-rw file in *~/project/casper/*, that sweet!!!
Now I suppose you'd like to use it right??


**Step 3, mounting the casper-rw file** 
 
3.1) panda@cyberspace:~/project/casper$ sudo mkdir /media/casper
3.2) panda@cyberspace:~/project/casper$ sudo mount -o loop casper-rw /media/casper

Now I know nothing of casper or what it does. Will this save my settings upon reboot of the machine? Thanks so much btw.

---

