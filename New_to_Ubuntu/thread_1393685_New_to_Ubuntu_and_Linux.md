---
title: "New to Ubuntu and Linux"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by Lakota on 2010-01-29
Hi folks.  Yeah, I'm new..  I'm sitting here with my newly arrived Ubuntu 8.10 Desktop Edition still in the box.  Here's what I'm working with:

Gigabit Motherboard w/AMD Dual Core Processor
NVIDIA GeForce 9500 GT Video Card
Sprint Sierra Wireless Compass 597 USB modem w/instructions from Sprint for Linux

Here's my options:

1) Yank out the HD with Micro-Cah Cah Windows XP, replace it with an empty HD and do a clean install.
2) Add the empty HD as a second drive and do a clean install.
3) Leave XP as is and just load Ubuntu on the same drive.
4) Replace the Vid card with one that doesn't need programming.

I'm open for suggestions here folks.  

Note:  No sense in throwing a rock at Windows, it already has enough holes in it!!!

---

### Post by MichealH on 2010-01-29
Dual Boot! Just install Linux on a separate Partition GRUB will take over

---

### Post by themusicalduck on 2010-01-29
For the first three options either would work. Although installing Ubuntu onto a clean separate HD is easiest and most reliable/safe. You can install it on one of the HDs with both in if you like or swap them out to be extra safe.

Also one thing to note, 8.10 is about a year old. 9.10 is the latest version which you can download off ubuntu.com if you want it. 8.10 should work find if you prefer though.

Owning an Nvidia card requires no programming expertise :p Its really a case of point, click, card works.

---

### Post by Lakota on 2010-01-29
Sounds easy.  But I'm not sure if I know the proper procedure for creating a separate partition.  I think that I'll begin by installing it to a clean HD.  If anything goes wrong, I can always use XP to get back up and running.  Can you download an upgrade from 8.10 to 9.10?

BTW, thanks for responding so quickly.

---

### Post by halitech on 2010-01-29
you would have to upgrade from 8.04 to 8.10 to 9.04 to 9.10. There is no reason not to go with 8.04 if it works as it is a LTS and is supported until April 2011. The non LTS versions are supported for 18 months on the desktop.

---

### Post by themusicalduck on 2010-01-29
Installing to a separate HD is sensible as partitioning drives always has some kind of risk of data loss associated with it, even if it's a small risk.

It is possible to upgrade from 8.10 to 9.10, but you would have to update it to 9.04 and then to 9.10 by downloading all of the files once 8.10 has been installed, using up a lot of time and bandwidth. And there's more potential for something funny to happen inbetween causing problems.

Best thing to do is download the 9.10 iso from [www.ubuntu.com](www.ubuntu.com) and write it to a CD. Then just install it from that CD instead.

---

### Post by Shpongle on 2010-01-29
if your new to linux i would duel boot just to be safe!, its better to be safe than sorry , also you should try a later version for better performance .  karmic 9.10 is the latest and its a great improvement over previous releases . Best of luck:-)

---

### Post by Lakota on 2010-01-30
Well folks, heres the update.  I tried everything I could.  Every time I got to the kppp part it would come to a screeching halt.  No connection!  I tried a Catholic prayer, a Baptist prayer, a Hebrew prayer, even a Native American prayer....nothing!  Finally I laid on the floor, kicked my feet, and threw a hissy fit...Then got up and clicked the Mobile Broadband Connector on the top right of my screen...BANG...Instant web access to the internet.  Yup, a hissy fit works every time.
Now I have to work on the sound.  The windows verson used the Realtech drivers.  The drivers I have now are the HDA Ati SB (Alsa mixer) from Ubuntu, and they don't work.  Any advice?

---

### Post by themusicalduck on 2010-01-30
Did you install 8.10 or 9.10 in the end?

First thing to do is open a terminal (Applications > Accessories > Terminal) and type in ```
alsamixer
``` hit enter, and check that all the volume levels in there are turned up.

Also right click on the volume icon at the top right and check the mute button isn't checked.

If none of that helps, then type ```
lspci
``` into a terminal and copy the contents here. Then we know exactly what sound hardware you have.

---

