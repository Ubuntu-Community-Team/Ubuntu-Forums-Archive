---
title: "Dual Display Woes"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by angry_panda on 2009-08-01
Hi :)                           Please take pity on me and help, I am SUCH a noob with linux, basically if I can't do something from the synaptic package manager I have no idea. I had no problem sorting out this issue in windows, but I have just had enough of windows now, been screwed over by it too many times. So, without further ado...

I know this must be a common question, but I have tried to follow all the relevant guides and come out empty handed :( [B]I am trying to get a dual display setup working with my laptop (Advent 7111) and my Acer 22" lcd monitor (Acer P223w I think).
[/B]
I ran this in the terminal to find out what graphics chipset or whatever I have...

kieran@kieran-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

If anyone could help me, or at the very least point me in the direction of an easy-to-follow guide that is known to work specifically with this hardware, I would be ridiculously grateful.

Btw, sorry if there is some vital info I have left out or something; as I mentioned, I am pretty much clueless with linux (even ubuntu), but bill gates' shenanigans have finally driven me away and I need to get it sorted on here =D

Thanks in advance

Angry_Panda

---

### Post by angry_panda on 2009-08-01
badumpadump

PLEEEEAASSSE does anyone know how to do this?

---

### Post by PietreWitobi on 2009-08-01
Not really sure what the problem is here - You have a second monitor jacked into the VGA port on your computer, is it not appearing in System > Preferences > Display ?

---

### Post by LewRockwell on 2009-08-01
I've got an Acer Aspire One netbook with the Intel 945 chipset and I'm triple-booting XP, Jaunty, and Puppy

XP and Jaunty both work well with an auxillary CRT

you do need to fiddle in the display settings area a bit though

.

---

### Post by angry_panda on 2009-08-01
> **PietreWitobi said:**
> Not really sure what the problem is here - You have a second monitor jacked into the VGA port on your computer, is it not appearing in System > Preferences > Display ?

Pretty much :(

Any ideas?

---

### Post by angry_panda on 2009-08-02
It's weird, I looked in the display preferences before and nothing was there, but now it seems to work pretty much the same as the old windows setup... I'm stumped (certainly didn't change anything).

Anyway, thanks.

There is one more thing - I have it (mostly) working, but while the external 22" monitor is fully operational, my laptop screen is now in a different ratio or something (the image fills the vertical plane of the screen, but only about 80-90% of the horizontal plane :S

Anyone know how to remedy this?

edit: It's not really that much of a problem - I don't need an extended desktop, I just wanted to be able to use the monitor. I will probably have the laptop lid shut when the monitor is on anyway, and it is easy to change the aspect ratio back to full screen when it is disconnected. Still, perfection would be nice :)

---

### Post by LewRockwell on 2009-08-02
I had that problem also, and I just fooled around with all the different settings until I had it just like I wanted it

.

---

