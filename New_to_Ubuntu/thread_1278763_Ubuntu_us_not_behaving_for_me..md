---
title: "Ubuntu us not behaving for me."
date: 2009-09-29
forum: New to Ubuntu
---

### Post by zayka on 2009-09-29
I trying to do some data rescue, For that I need running Ubuntu. I tried running it in Live mode, Now I installed it with Wubi. The problem is almost right away it becomes unresponsive: I can't click close window, select something etc. I can move mouse pointer just fine, but Ubuntu doesn't seem to respond. Some keybord buttons work.
Please help. It is really frustrating.
I running it on XP machine, 3Gb RAM.

---

### Post by Saghaulor on 2009-09-29
Try to defragment your hard drive. 

I had many issues with a wubi install. One was due to a heavily fragmented drive.

It might help.

---

### Post by zayka on 2009-09-29
it doesn't matter. The same thing happens in Live CD session (without install)

---

### Post by QIII on 2009-09-29
Can you provide more complete specs on the machine?

Processor, GPU, etc...

---

### Post by zayka on 2009-09-29
Intel Pentium 4 3Ghz
Asus 478 motherboard
256 MB video card
several hard drives
3 Gb RAM

---

### Post by QIII on 2009-09-29
OEM of GPU?

---

### Post by zayka on 2009-09-30
I am sorry what is that?
Ok maybe it's a mouse...testing more

---

### Post by quinnten83 on 2009-09-30
Maybe it's just your CD. Try burning a new one.
You can also try other distributions, how about RescueCD or Knoppix? If none of them will work, than your system might be borked beyond function.

---

### Post by QIII on 2009-09-30
Is your graphics card or chipset an Intel-based piece?

---

### Post by Vignesh S on 2009-09-30
Zayka, what Quill meant when he said OEM of GPU is that he want to know who the manufacturer of the graphics card is. It would probably either be Nvidia or ATI, though it could be something else. The specific model would also be helpful.

In case you don't know:
OEM: Original Equipment Manufacturer, in this case, what brand the graphics card is

GPU: Graphics processing unit, aka graphics card, though it can also be a graphics chip.

Which version of Ubuntu are you using as the live CD? I know that 9.04, even with the live CD doesn't work on my computer, but 8.10 does. Judging by your processor, I presume that the LiveCD is 32 bits. Try going through 8.04, 8.10 and 9.04 live CD's. Might be some hardware incompatibilities in one version of Ubuntu that doesn't exist in the other. Finally, if none of them work, then try 9.10 (the beta's coming tomorrow). A tad unstable, but it might just do the trick, as a LiveCD.

---

### Post by DJonsson2008 on 2009-09-30
Just a hunch but you might try booting Live disk with the HDs
disconnected and see if one of the hard drives is in fact 
contributing to the problem.  Identifying your video card
is essential as different versions of Ubuntu have better
native support for various video cards, at least that's
been my experience.

A CD drive on the blink could also be problematic.

---

### Post by QIII on 2009-09-30
> **Vignesh S said:**
> Zayka, what Quill meant when he said OEM of GPU is that he want to know who the manufacturer of the graphics card is. It would probably either be Nvidia or ATI, though it could be something else. The specific model would also be helpful.

In case you don't know:
OEM: Original Equipment Manufacturer, in this case, what brand the graphics card is

GPU: Graphics processing unit, aka graphics card, though it can also be a graphics chip.

Which version of Ubuntu are you using as the live CD? I know that 9.04, even with the live CD doesn't work on my computer, but 8.10 does. Judging by your processor, I presume that the LiveCD is 32 bits. Try going through 8.04, 8.10 and 9.04 live CD's. Might be some hardware incompatibilities in one version of Ubuntu that doesn't exist in the other. Finally, if none of them work, then try 9.10 (the beta's coming tomorrow). A tad unstable, but it might just do the trick, as a LiveCD.

Man, Vignesh S, you rightly scolded me for something I don't like other people doing.  A fella just gets so used to using jargon that it is hard to break free of it even when one is trying to be helpful.

I'll go ask the wife to smack me around a bit for that...

---

### Post by JUDOHAWK on 2009-09-30
TC I noticed the same thing when I went to use my ubuntu live cd about 2 hours ago. It seemed it was horribly unresponsive, but the environment didn't freeze.  Exactly like you described. I ended up installing it anyway, and no more problems, but it seems to be a problem with something.  I also had issues with the install messing up my XP bootsector, which I used to use ubuntu 8 and never had any problems at all, however with 9 I've experienced some which is weird.

Anyway, got my bootsector fixed with testdisk.  I don't have the problem with the windows hanging on my fresh install though, so idk.

---

### Post by zayka on 2009-09-30
Thank you guys for all responses. I thought I should follow up on the issue.
Ok, so I have Nvidia graphics card. I guess I could've Google GPU. The main thing is that it seems to be working fine now. The culprit was the mouse I guess. What i did is unplugged it and plugged it back. So I am not sure what was the deal.
Now if I can get PhotoRec working correctly...
Thanks again.

---

