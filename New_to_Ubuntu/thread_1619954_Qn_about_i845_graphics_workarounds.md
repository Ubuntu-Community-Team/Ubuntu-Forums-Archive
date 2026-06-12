---
title: "Qn about i845 graphics workarounds"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by Myrmidon83 on 2010-11-12
Greetings all. 

I've been trying the last few days to get a working linux on my old laptop which has the 'dreaded' 82845g/gl graphics card.  After NO luck with booting from live cd's, different distro's etc I was beginning to think this was a lost cause.

Then I came across the lucid i8xx freezes workarounds from [http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes), so I thought, what the hell.  Workaround A, I just tried adding the 'i915.modeset=1' after the quiet splash and whaddya know, i'm typing this from firefox, ubuntu 10.04 live cd. :P

So there's hope at least, i'll test this for a few reboots and if it's consistant then i'll install in a dual boot with win xp. (which i'm now an expert on).  My question is, when I install, the link says: > **From an installation:**

 1) Hold down Shift while booting to enter the GRUB menu. 
2) Press 'e' to edit. 
3) Add "i915.modeset=1" after "quiet splash". 
4) Ctrl+x to boot. 
If  adding "i915.modeset=1" to your boot parameters allows you to boot  successfully, you then need to enter the command above into a terminal  to make the changes permanent. 

What exactly would I type in the terminal to ensure this change stays applied?

Many thanks, maybe I'll get to join you all yet, so far I'm impressed.

:)

---

### Post by Myrmidon83 on 2010-11-19
Bu-bump

I've tried the grub update command but this setting doesn't want to stay applied.

:(

Apparently I didn't do it properly

> sudo update-grub

Sorted that out.

Next I have the random freezes to conquer.  I'm thinking of workaround D on the lucid freezes, booting with the other kernel.

Gonna play with compiz and see how long it takes before it breaks. :P

---

### Post by Myrmidon83 on 2010-11-19
Goddamit, it still didn't save the changes!

I booted up into grub, added ```
i915.modeset=1
``` after the 'quiet splash' line to boot up without problems. Then, opened a terminal and typed in: ```
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u
sudo update-grub
```

I must be doing something wrong here because grub isn't saving this new setting for boot up.

Any help appreciated.

---

