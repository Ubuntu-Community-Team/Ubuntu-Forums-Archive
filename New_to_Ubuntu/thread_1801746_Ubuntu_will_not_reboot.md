---
title: "Ubuntu will not reboot"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by YellowBronco on 2011-07-11
hi, im having issues with ubuntu loading, ive been runnung it for a couple of days now non stop and i thought i would try some of the downlaodable apps and chose the programing suite, then wile it was loading i went to firefox and tried to search on it, it opened ran for about a min , then shutdown, created a trouble report to firefox and would not reopen, so i did a hard boot and now umbuntu will not restart, its stuck on loading now.

os specs

ubuntu ver. 11.04
amd athlon 64x2 dual core pro 5000+ 2.59 gh
bios american megatrends v1.6
smbios 2.5
power thermaltake tr2-500pp psf450s
6 g ram crucial
nvidia gforce 7900 gt/gto grapics w/ dual 22 monitors

dr A zid citizen tuv
hd B seagate st340810a 40g 
hd C crucial ssd 64g
hd E western digital 1600aajs 160g

dr q memorex 16x double layer 5395 cd-r/rw drive
dr r sony optiarc dvd rw ad-7190s ata 1.02

---

### Post by jtarin on 2011-07-11
> its stuck on loading now.Loading what?

---

### Post by YellowBronco on 2011-07-11
ubuntu, , loaded some things and stoped with a flashing curser at 
*enabbling additional executable binary formats binfmt-support

---

### Post by YellowBronco on 2011-07-11
im still at the blinking curser

---

### Post by jtarin on 2011-07-11
Shift over to a virtual terminal by using the key combinations "Ctrl + Alt + F1-F6. Then login and issue the command startx. If you can reach the desktop you can try to run "apt-get --purge remove {package}" and remove the "programing suite".....use the real filename of course. Then when finished reboot and see if you can get logged in normally.

---

### Post by lovinglinux on 2011-07-11
I would advise to change the title to "Ubuntu will not reboot".

Looks to me that some of your system files got corrupted. Did you reboot while doing upgrades?

I am not good with system recovery. I usually just install Ubuntu again when that sort of thing happens, but I am sure someone will step in soon with a solution.

---

### Post by jtarin on 2011-07-11
> **lovinglinux said:**
> I would advise to change the title to "Ubuntu will not reboot".

Looks to me that some of your system files got corrupted. Did you reboot while doing upgrades?

I am not good with system recovery. I usually just install Ubuntu again when that sort of thing happens, but I am sure someone will step in soon with a solution.
And until they do, I thought I would fumble through.

---

### Post by YellowBronco on 2011-07-11
thanks guys, 
the startx brought me to the help section
build os : linux 2.6.24-29 server i686 umbuntufatal server error:
no screens found
cunsult x.org foundation support
at [http://wiki.x.org](http://wiki.x.org)
log file at "/var/log/xorg.o.log" for additional info
ddxsigGiveUp: closing log
conection refused
xinit: server error

---

### Post by Elfy on 2011-07-11
Title changed.

@YellowBronco - if you need something like a title change to a thread you can use the report abuse button to ask us.

---

### Post by jtarin on 2011-07-11
Ok proceed from the virtual screen and don't issue the startx command, but continue with the rest. If that fails try "Recovery Mode" from the Grub prompt.

---

### Post by YellowBronco on 2011-07-11
how do i get to the grub, i tried typing "grub" and it went back to the flashing curser

---

### Post by jtarin on 2011-07-11
You don't get a Grub **_boot_** screen?

---

### Post by YellowBronco on 2011-07-11
nothing it locks up

---

### Post by YellowBronco on 2011-07-11
now i get a "yellowbronco@sully:~$ "
after loging in

---

### Post by YellowBronco on 2011-07-11
im back up, finaly, 
i was able to get into the boot screen by shift+delete at startup, then choosing to fix the installed ubuntu and choosing to fix broken links, , then i let it restart on its own and its back up now, how do i file an error log?  dan

---

### Post by philinux on 2011-07-11
> **YellowBronco said:**
> im back up, finaly, 
i was able to get into the boot screen by shift+delete at startup, then choosing to fix the installed ubuntu and choosing to fix broken links, , then i let it restart on its own and its back up now, how do i file an error log?  dan

No need to file an error log. The system was damaged by the hard reboot. Your last actions let the system fix itself. Instead of hard reboot  try this next time.
 [http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by jtarin on 2011-07-11
Mark this thread as solved,please.

---

### Post by YellowBronco on 2011-07-13
well it was up for an hour then went down , i get to the selection screen and select fix ubuntu and it takes me to a blinking curser

---

### Post by YellowBronco on 2011-07-14
thanks

---

### Post by YellowBronco on 2011-07-22
well, its been almost 2 wks and im finaly to where i can reinstall   11.04, it was my own stupidity, i put a version 6 on top of 11.04. i   thought it was just info from the library , not a whole new install.   like i said^ i like ubuntu, ive been too enamored in the bill gates   world to fully get it all of ubuntu yet, i guess if u are starting out   fresh with it it is easier then having to relearn things 
alot of my problem is i think i know how it works, well it only works that way in windows,, lol
there is probably alot of ways to do this but i nuked the disks all hds ,   re-installed a new os , xp not the vista stuff, had to re-find all   drivers this way and reinstall from bios, in order to do that i had to   take the motherboard out and find the codes on the back side of it
please dont anyone else do what i did
dan

---

