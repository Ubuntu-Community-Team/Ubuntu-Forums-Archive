---
title: "upgrading crashes my computer"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by tiarna on 2011-01-03
I have a problem with upgrading ubuntu if I except a down load from the net it looks ok but after re start it will not load ubuntu I have to reinstall again Geoff

---

### Post by bludgard on 2011-01-03
edit:Make sure Ubuntu Install Media is selected to boot first in BIOS.
 
What is the source of the install media?
 
Maybe it is corrupt?

---

### Post by ninjafighter123 on 2011-01-03
Boot problem?
Try getting grub from a live CD?

Try
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Couldn't find  exact site.

I accidently installed my grub on my hard disk partition once so it wouldn't boot.

---

### Post by ninjafighter123 on 2011-01-03
> **bludgard said:**
> edit:Make sure Ubuntu Install Media is selected to boot first in BIOS.
 
What is the source of the install media?
 
Maybe it is corrupt?

Upgrade happens on the OS

---

### Post by tiarna on 2011-01-03
I install from CD but when I get upgrades and I click on them to install it looks OK tells me to restart computer all I get is something about grub?? and that's it I have to reinstall  from disk I have 1010 in windows XP Geoff

---

### Post by bludgard on 2011-01-03
> **tiarna said:**
> I install from CD but when I get upgrades and I click on them to install it looks OK tells me to restart computer all I get is something about grub?? and that's it I have to reinstall from disk I have 1010 in windows XP Geoff
 
Can you boot into Windows and post a screenshot of Disk Management?All partitions with status?
 
Please note which partitons are marked active.

---

### Post by bludgard on 2011-01-03
> **ninjafighter123 said:**
> Upgrade happens on the OS
 
Thanks.I was/am a little lost.:p

---

### Post by tiarna on 2011-01-04
the system is ok if I do not except Internet upgrades but as soon as I let ubuntu down load any files that's it it will not load the system it gets stuck at something about grub something or other so I have to delete it and then reload back into windows Geoff

---

### Post by tiarna on 2011-01-04
I down load files from the Internet and the computer will not start something about grub?? but if I refuse upgrades it gives me no t rubble at all so am I doing wrong by letting any upgrades   or not  geoff

---

### Post by bludgard on 2011-01-04
> **tiarna said:**
> 
...the computer will not start something about grub??

 
Maybe this helpful post by Bucky Ball will help get you sorted.[http://ubuntuforums.org/showpost.php?p=10310010&postcount=2](http://ubuntuforums.org/showpost.php?p=10310010&postcount=2)

---

### Post by mastablasta on 2011-01-04
how did you install ubuntu? through wubi? please post the result of bootscript (follow the instructions here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)) in the code tags (use the # icon before pasting).

---

### Post by bludgard on 2011-01-05
> **tiarna said:**
> I have a problem with upgrading ubuntu if I except a down load from the net it looks ok but after re start it will not load ubuntu I have to reinstall again Geoff
 
I'm sorry tiarna,I am at a loss.
 
I hope you get this sorted and would be interested in knowing how you do.
 
My apologies.
 
One

---

### Post by bcbc on 2011-01-05
It sounds like a wubi install. There are two package updates you need to avoid - grub-pc and grub-common (find them under "Recommended" in Update Manager and uncheck them). Let the rest run.

It's a known issue affecting wubi since November 20th update to grub. [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

