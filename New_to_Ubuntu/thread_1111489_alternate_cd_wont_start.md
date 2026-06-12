---
title: "alternate cd wont start"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by imaginashawn on 2009-03-30
My second machine needs an os (it has win2k now). I have Ubuntu 8.10 on my #1 machine. Since #2 is old, I can't install with graphics. I downloaded the alternate iso the only way I could find (using bit torrent). And then burned it to cd. Question: was there something I was supposed to do with the file I downloaded before burning to cd? 
I set up  my #2 bios to boot from cd first, floppy second and hd third (and saved). 
Problem = at boot, cdrom runs but still boots up windows. I even tried F8 and choosing boot from cd and it still boots windows.
PC #2 is AMD Duron, 1 meg ram, 6 gig HD
Thanks, Shawn

---

### Post by doctorbighands on 2009-03-30
1 meg RAM? I'm sure that's a typo. At least, I hope it is...

Anyway, you can try downloading the ISO directly from [here]("http://ubuntu.osuosl.org/releases/8.10/"). I've had extremely good luck and fast downloads from their mirrors.

It sounds like you got a bad download to begin with. Try downloading from the above link and burning that copy to a CD. If that doesn't help, let us know.

---

### Post by spiderbatdad on 2009-03-30
Hard to say. You should verify the iso before and after burning, and even that isn't 100% guaranteed...but close. It you have a cd you know is good, you can try to boot it and at the boot screen press F6. Escape any options if offered and then a boot prompt line should appear. Use the arrow key and move to the end of that line and delete "quiet splash --" and type in "vesa," or "vga=791" or "vga=792"

It may also be that your bios is misbehaving. I have an old machine as you described and was having the same problem. I gave up for over a month...decided to try again, replaced 2-256 ram modules with 1-new 256 and voila. Good luck. I also used Xubuntu by the way.

---

### Post by imaginashawn on 2009-03-30
Thank you both for your suggestions. I will go try them.
Shawn

---

### Post by imaginashawn on 2009-04-09
Finally got it. What I ended up doing is, I put in my old win2000 cd and opted to delete all partitions, Stopped it right there and put in my Ubuntu 8.10 Alt cd and it worked! When install was done I had no graphics so I installed a newer card that I had laying around. It's all working perfectly now. I'm downloading updates on it right now.
Thanks for all your support, Shawn
Now with two Ubuntu machines! :guitar:

---

