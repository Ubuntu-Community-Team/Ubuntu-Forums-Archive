---
title: "dist-upgrade broke ndiswrapper"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by !Klams on 2007-07-17
Having spent a day getting ndiswrapper to work, I did a stupid thing and went and followed the tutorial stickied on this forum for getting my radeon X1900 to work. I say stupid, because I'm running dapper, not feisty (which the tutorial is intended for) and because after doing the dist-upgrade, my wireless no longer works. 

If I try and modprobe ndiswrapper, I get an error:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-28-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): invalid argument

I went to try re-installing ndiswrapper because I read somewhere that dist-upgrade on dapper can delete random .ko's, only to find that I had the same problem I'd had before, in that make and make install wouldnt work. The reason before was because I hadn't got the kernel headers, which I solved with

aptitude install linux-headers-`uname -r`

only now when I run that, I get the error, temporary failure resolving 'security.ubuntu.com' but of course its going to have that error, I cant get on the net! I guess before it was getting the headers off the CD but now it cant because I updated? 

I read about some issues with bcm43xx, so I blacklisted that, but trying to rmmod bcm43xx tells me that 'module bcm43xx does not exist in /proc/modules' so I dont think thats the issue here.

Any help would be much appreciated, sorry if I've left out any vital info. Its so very frustrating that connecting to the internet is the problem, because it seems every suggestion I come across involves having a connection in the first place!

Cheers.

---

### Post by reckless2k2 on 2007-07-17
yeah i came across this before going from kernel to kernel. you have to uninstall and reinstall all the way through ndiswrapper. then you'll be fine

---

### Post by !Klams on 2007-07-17
OH! Ok, well, thats fairly painless! Thanks!

---

### Post by !Klams on 2007-07-17
ok, well it turned out that without the internet, re-installing ndiswrapper would be fairly painful, since without the linux headers you cant use 'make', and trying to install the headers package from a cd insisted that the package was dependent on another package. (Confusingly, it claimed it was dependent on itself.)  So I ended up rebooting and hitting escape as grub loaded so that I could choose the old kernel to boot from instead of the new one, and then (after removing the bcm43xx blacklist, because that broke stuff) doing an update-manager -c to update to feisty instead. 

I hope this helps anyone else that might come across this. Getting wireless to work on dapper has been a pain for me, and I know a few other people. Obviously if you can get feisty to work from the cd then thats a much better way, but for me the feisty cd was freezing, so I figured I'd update an older version, and the only other CD I had knocking around was dapper. I guess in retrospect, I should have downloaded Edgy and done it from there.

---

### Post by kevdog on 2007-07-17
To install headers without an internet connection, you will need the ubuntu installation cd.  All commands are typed at command prompt:

1. After booting into Ubuntu, put installation cd into drive
2. sudo apt-cdrom add
3. sudo aptitude update
4. sudo aptitude install linux-headers-`uname -r

---

### Post by !Klams on 2007-07-18
doing that I still get the "temporary failure resolving 'security.ubuntu.com' problem.

---

### Post by kevdog on 2007-07-18
> doing that I still get the "temporary failure resolving 'security.ubuntu.com' problem

Thats a DNS issue, not a ndiswrapper or compilation issue.

---

