---
title: "How much space to give Ubuntu 11.04?"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2011-08-05
Hi, planning on dual-booting Windows Vista and Natty sometime soon. I'm semi-experienced in Ubuntu, so I'm fine in that aspect. I'm just wondering how much space I should allocate on my harddrive for my Ubuntu partition? I'm going to be using the live CD method, where it lets you drag the slider to allocate however much space you want.

I have a 250gb harddisk, and at the moment Windows is using all of that space for it's partition. Out of that 250gb, I only have 144gb of free space left (not quite sure why, but I guess I have quite a bit of programs for vista installed). So, roughly 1/3rd of my harddrive space is already taken for windows. Now, In past experience, windows starts to malfunction a bit when it doesn't have much free space left, so I'm stuck here. I'd like to use Ubuntu as my main OS, but I don't want to allocate too much space to it, as that might make Windows unbearably slow. How much space  do you guys recommend that I allocate to Ubuntu, without messing up Windows?

Also, a few months ago I attempted to dual boot Windows vista and ubuntu 11.04, but the MBR didn't show Ubuntu as an option, and directly booted to Vista. I'm not sure what caused this, but can this be easily fixed using EasyBCD? 

PS: Ubuntu is awesome.

---

### Post by fuzzyworbles on 2011-08-05
normal use (e.g., no giant games): 15-ish gigs for / and 50gigs on up for /home. In the end, it depends on what you plan on using linux for.

installing windows *after* linux will overwrite the MBR.

---

### Post by Jouke S on 2011-08-05
50gb should be fine if you don't plan on gathering a ton of games and videos

---

### Post by Thrashrokz33 on 2011-08-05
> **fuzzyworbles said:**
> normal use (e.g., no giant games): 15-ish gigs for / and 50gigs on up for /home. In the end, it depends on what you plan on using linux for.

installing windows *after* linux will overwrite the MBR.

Ok, could you please explain how I set up the /home and / to be specific sizes?

---

### Post by SavageWolf on 2011-08-05
During the installer, select "Custom" or "Advanced" or the like when it asks you how you want to install. It should be fairly self explanatory, but if not you can just ask for help here.

---

### Post by oldfred on 2011-08-05
If you want lots of detail & explanation Herman has it, any differences in versions are minor and procedure is the same for all verisons:

Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by GoffyGoober on 2011-08-05
Depends on how often you use your Windows:
Often: 75% to ubuntu.
Half and half: 50%
Not verry: 25%
Hate it: all but 25 Gig

---

### Post by Thrashrokz33 on 2011-08-05
Ok, I've read through some of those guides...but is there really any advantage to partitioning it manually? I don't really plan on putting /home on a separate partition or anything. Wouldn't the non-manual option be easier?

---

### Post by Wim Sturkenboom on 2011-08-05
A seperate partition for /home has the advantage that a reinstall of Ubuntu does not wipe your data. Same applies for Windows with a seperate partition for 'My Documents'.

And yes, a non-manual partition is (slightly) easier to set up.

Note:
Fiddling with partitions and installing of another OS can result in data loss if it goes wrong. Make sure you make a backup of your important data before you start.

---

### Post by ubun2geek on 2011-09-04
80 GB is just right for me.

---

### Post by Vi3tHoneyX on 2011-09-04
I'll have to agree and say 80gb should be about right. :)

---

