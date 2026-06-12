---
title: "editing the master boot record"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by ubun_tut on 2010-08-28
hi,

i am using a dual-boot desktop that can either boot into windows xp or ubuntu hardy. usually, when the computer is booted up, the OS-selection screen comes up, and the default option is win xp, such that if i do not make any manual selection, win xp is automatically booted.

however, after doing some software updates in ubuntu some days back, many more options have appeared (i learnt from some other threads that these are various kernels that were installed by the updates), and the default selection has now been changed to a 'recovery mode' of one of these kernels. this makes things quite inconvenient as i have to manually make a selection for either win xp or ubuntu at each start-up.

i was told the master boot record is what i should edit to change the boot OS priority. can someone pls show me how to edit it? i would like to choose win xp as the default option. thanks!

---

### Post by Lightstar on 2010-08-28
> **ubun_tut said:**
> hi,

i am using a dual-boot desktop that can either boot into windows xp or ubuntu hardy. usually, when the computer is booted up, the OS-selection screen comes up, and the default option is win xp, such that if i do not make any manual selection, win xp is automatically booted.

however, after doing some software updates in ubuntu some days back, many more options have appeared (i learnt from some other threads that these are various kernels that were installed by the updates), and the default selection has now been changed to a 'recovery mode' of one of these kernels. this makes things quite inconvenient as i have to manually make a selection for either win xp or ubuntu at each start-up.

i was told the master boot record is what i should edit to change the boot OS priority. can someone pls show me how to edit it? i would like to choose win xp as the default option. thanks!

/etc/default/grub is what you'll want to edit, there you can change the default number to what you want, remember it starts at 0

In synaptic you can also remove old kernels.  I often keep an extra one just in case the most recent doesn't boot.  just search for linux-image or something like that (i usually just type "image") and remove/uninstall the older versions.
That will shorten up your boot list

---

### Post by cycling-rod on 2010-08-28
There may be a solution in these websites? [http://www.google.com/cse?cx=partner-pub-9300639326172081%3Ad9bbzbtli15&ie=UTF-8&sa=Search&q=Edit+the+master+boot+record+ubuntu&hl=en](http://www.google.com/cse?cx=partner-pub-9300639326172081%3Ad9bbzbtli15&ie=UTF-8&sa=Search&q=Edit+the+master+boot+record+ubuntu&hl=en)

---

### Post by srs5694 on 2010-08-28
Lightstar is correct. I just want to add that you should *not* attempt to edit the Master Boot Record (MBR)! That's the first sector of your hard disk, and it contains two things: stage 0 of the boot loader and the partition table. When using GRUB or GRUB 2, the boot loader's stage 0 does *not* control which of the options you see is the default, and of course you don't want to mess with the partition table. The MBR is encoded in binary, so editing it directly would require a binary editor. Going down that path is likely to get you into trouble, and quickly! Don't attempt it unless you're an expert. Whoever suggested you edit the MBR is one of four things: writing for experts, maliciously trying to get you into trouble, completely misinformed, or completely misunderstood your simple question. Any of those possibilities means you should probably ignore advice from this source.

---

### Post by ubun_tut on 2010-08-29
i managed to uninstall the older kernels through the synaptic manager, and edited the boot OS priority in /boot/grub/menu.lst.

thanks for all your help!

---

