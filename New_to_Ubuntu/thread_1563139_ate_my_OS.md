---
title: "ate my OS"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by diosilva16 on 2010-08-28
i had ubuntu installed with wubi, i think i had version 9.10, and had it for a while, though i hadn't been using it. today i thought it would be a good idea to update it, and after finishing the update it restarted my pc and it gave me an error and a command line and never got to the os selection screen

the error is the following: no such device: a87ad0ba-9b3f-4d4a-bb22-1d6fcbfa081f.
grub rescue>


keep in mind that i'm an absolute noob, and i'm desperate

---

### Post by natman on 2010-08-28
If i had to guess i bet everything is still there, just a bit messed up. Have you tried using a Live Linux cd to boot from just to check if all your files are still on the hard disk? If everything is there i think the problem can be fixed by asking grub to ( not sure of the exact term ) "redo" the boot menu. Basically i had a similar problem once before and that fixed it bu ti cant remeber the solution - im sorry.

---

### Post by diosilva16 on 2010-08-28
i don't have a live cd, i'm downloading an iso to try and instal ubuntu on an usb stick right now

---

### Post by diosilva16 on 2010-08-28
ok, i'm on a live usb stick, now what?

---

### Post by natman on 2010-08-28
ok, so your on the live stick, try having a look for your files, open up the file browser and look for extra drives one should be your hard disk.

---

### Post by diosilva16 on 2010-08-28
yes, that's obvious enough, but it doesnt fix anything

---

### Post by mr clark25 on 2010-08-28
if all of your files are still there, you can do this (my website)-  [http://mrclark.ath.cx/linux/linux/grubfix.html](http://mrclark.ath.cx/linux/linux/grubfix.html)


all you really need to do is run these three comands (copy/paste them into the terminal and hit enter)-
```
[FONT=monospace]
[/FONT]cd ~/Desktop/[FONT=monospace]
wget http://[/FONT]207.68.218.64/linux/scripts/grubfix[FONT=monospace]
[/FONT]sudo bash ~/Desktop/grubfix

```now answer the questions on the screen. if you dont know the answers to the questions, (theres only 2 questions, so dont get worried) we can help you.

---

### Post by diosilva16 on 2010-08-28
ok, i fixed it using the advice on [this thread]("http://ubuntuforums.org/showthread.php?t=1547801"), but thank you guys anyway.

---

