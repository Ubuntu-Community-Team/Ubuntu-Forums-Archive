---
title: "Ubuntu crash after install BackTrack5 in vmware"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by nimdekvan on 2011-07-17
Hello, 

At first i install a dual boot XP and Ubuntu 11.04.

However i'm stupid enough to try installing Backtrack 5 in vmware (on winXP) 
because I want to try using backtrack.

And after that whenever I boot I cannot select ubuntu anymore 

it will say /ubuntu/disks/root.disk no such device 


also I checked in C:\ubuntu\disks in WinXP and it cannot access anymore 
"The file or directory is corrupted and unreadable"

What make it worse is at the time i installed ubuntu i chose 17 Gb.
and there was a file in this directory which is 17Gb.
However right now C:\ubuntu\disks is empty (and cannot access)

Help me pls. I have a lot of important file in ubuntu.

---

### Post by Sef on 2011-07-17
Boot into a live CD and open the terminal.

Copy and paste this command in the terminal and let us know the results here.

```
sudo fdisk -l
```

---

### Post by nimdekvan on 2011-07-18
Um so I need to install another ubuntu in live CD and boot from it right ?

because at first I use a dual boot ( XP and Ubuntu ) 

just ask to clarify.

---

### Post by Neoncamouflage on 2011-07-18
You need to put a LiveCD of Ubuntu into your disk drive, when you start up choose to boot off of the disc. Then when it comes up boot off of the CD instead of installing. This will run Ubuntu off of the CD, where you can then run that command.

---

### Post by nimdekvan on 2011-07-18
I've solved this already

I found a folder name "found.000" on C:\   (hidden folder)
inside I copied "boot" folder , root.disk , swap.disk

and paste to C:\ubuntu\disks\

and the problem is solved.

---

### Post by fractalman on 2011-07-18
I found it easier to just put bt5 on my hard drive instead of vmware. but you've fixed it now so no need to worry

---

