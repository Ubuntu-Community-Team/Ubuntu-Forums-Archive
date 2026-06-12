---
title: "slow Boot"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by The Eight-Bit Link on 2010-05-11
After grub, I have a slow boot. How do I speed it up? It work fine after it finishes booting. For a short time, there is a blinking cursor. Then, it goes black. After a while, it displays text really fast, then goes to the xubuntu 9.10 'firefly' loading screen. I could tell you how long it takes to boot, but you wouldn't believe me.
Anyway, 256 mb ram, 816mhz celeron prossessor, dell inspiron 2500.

---

### Post by nhasian on 2010-05-11
has your boot always been this slow? or is it something recent?  some things you can do to make booting faster would be to switch to EXT4 filesystem and using Lubuntu 10.04.  also disable unused daemons

---

### Post by The Eight-Bit Link on 2010-05-11
Yes, it always has been slow.
Umm.. it takes a few hours to boot.
i will try the ext4 filesystem and turn off daemons
By the way, how does one go aout turning off the daemons?

---

### Post by k3lt01 on 2010-05-11
> **The Eight-Bit Link said:**
> Umm.. it takes a few hours to boot.Go into Synaptic, or whatever Xubuntu uses, and remove ureadahead, reboot and see if that improves things. Last time I let ureadahead on my laptop it took over 2 hours to boot (it never did actually finish) and I had to do a hard reboot because it was just wasting time waiting for the thing to work. Without ureadahead I have no problems and can boot in about 30 seconds from pressing the power button to usable laptop.

---

