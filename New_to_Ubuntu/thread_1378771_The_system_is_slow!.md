---
title: "The system is slow!"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Aetixintro on 2010-01-11
I find the 9.10 Ubuntu system incredibly slow after the recent update of today, 12.10.2010. It's almost to the point where there's no use in it, but being a meager back-up system/OS storage system. This is rather poor!

I have no clue what's doing it. I very much like to support and recommend Ubuntu to other people, but I feel guilty if this is no better than this.

Anyone? :???:

---

### Post by DamenW on 2010-01-11
What is the hardware Ubuntu is running on?

When you using your computer when the updates were running?
try
sudo bash
aptitude update
aptitude full-upgrade

---

### Post by FreezWay on 2010-01-11
ummmm, what all was updated? also, press alt F2 and type "gnome-system-monitor" and tell us if any of the graphs are especially high.

---

### Post by Aetixintro on 2010-01-11
DamenW
Hardware: AMD Athlon 32 bit, 213,2 MiB in Memory
Using computer: No.

DamenW and FreezWay, I'm about to try out your recommendations! Thanks!

Alright. All rec. from DamenW carried out, 2 packages removed.

FreezWay: System Monitor: F.x. CPU appr. 27%... with the processes Xorg and SysMon running of that...

---

### Post by marshmallow1304 on 2010-01-11
> **Aetixintro said:**
> 213,2 MiB in Memory

That's why.

[QUOTE=https://help.ubuntu.com/community/Installation/SystemRequirements]
Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * **384 MB of system memory (RAM)**
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution
    * Sound card
    * A network or Internet connection[/QUOTE]

If you can upgrade to to 512 MB or even 1 GB that would be even better.  Otherwise, try a lighter DE like XFCE or LXDE or even a lighter distribution like Puppy.

---

### Post by daimaru on 2010-01-11
try xubuntu

---

### Post by DamenW on 2010-01-11
my old laptop had about the same specs, getting a more light weight os will help, i ran ubuntu and it could only handle firefox.  If your familiar with linux and willing to have an adventure you can try gentoo and design linux to your hardware.  But the recommendations above would be far easer and just as affective.

---

### Post by Aetixintro on 2010-01-11
Alright, [marshmallow1304]("http://ubuntuforums.org/member.php?u=663154"), thanks! I'll look for more RAM. Upgrade in the making...

(on the other hand, I've just installed Sysinfo: sudo aptitude install sysinfo and it's Good!

so more on the system: AMD Athlon 1102 MHz L2 Cache 256 KB f6m6s2 )

---

### Post by Aetixintro on 2010-01-11
Thanks, all!
I've been wondering if my trust in Ubuntu has been misplaced, but it turns out that it's just me running a too **old, limited** system with way too little RAM (1/2 of recommended).

marshmallow1304 is the winner of this thread with the notice!

No crap walks with Ubuntu 9.10 which is just beautiful! I'll see if I can get something worthy of it on the legs! So long, people! :D

---

