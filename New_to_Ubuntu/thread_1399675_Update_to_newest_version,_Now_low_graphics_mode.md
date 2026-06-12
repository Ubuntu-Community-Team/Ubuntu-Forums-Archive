---
title: "Update to newest version, Now low graphics mode"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by SumthingWicked5 on 2010-02-06
I've looked up quite a few instances of this happening, but the answers have confused me, as I'm a lot newer than the other people I've seen. 

I was running Intrepid Ibex for a while, and got the urge to upgrade to the newest one. Which I believe is Jaunty? Anyways, everything went well, except now, when I boot, it goes into the usual alert saying that Ubuntu has to start in low graphics mode, because it's failed to load the NVIDIA kernel module. I tell it okay, that it should give me low graphics mode so I can try to figure it out, but it just gives me a blank screen, where the format is "not supported"

I get 3 other options;
Reconfigure graphics,
Troubleshoot the error,
and Exit to console. 

However, I don't really know what I'm doing in any of these, so it's not much help. Selecting "reconfigure" gives me three options that don't seem to have any effect, and I'm put back into my same blank screen.

Any help is appreciated in advance.

-Tad

---

### Post by Thomas Garman on 2010-02-06
I had a similar issue when I upgraded to 9.10.  So I started in low graphics mode and then went to System ---->  Adminstration ---->  hardward drivers and from there installed the nvidia drivers...  and rebooted.

It all came on just fine.

If I remember correctly, though, when I went to change the display settings I used Alt F2 and then gksudo nvidia-settings-manager so that I could save my changes to the display configuration.

---

### Post by SumthingWicked5 on 2010-02-06
I would love to try that! I feel like even I could manage that one. However, I can't even get to a GUI. Just the blank screen. Once I click to the low graphics mode, I have to restart because it's useless.

---

### Post by SumthingWicked5 on 2010-02-06
Well, I found what may have been the cause. I went to download the Live CD to see if I could do anything with that, but when I read it, it tells me I can't update from as far back as my old setup was without damaging my system. Wonderful.

Now that the damage is done, is there anything I can do, short of trying to use the Live CD to get into my drives, back everything up, then simply format to the newest version? If there is, is it really worth the effort?

---

