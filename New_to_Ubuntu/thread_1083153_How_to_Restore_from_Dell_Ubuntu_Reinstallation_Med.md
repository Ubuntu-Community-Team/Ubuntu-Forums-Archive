---
title: "How to Restore from Dell Ubuntu Reinstallation Media"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by bevsmith on 2009-02-28
Created a DVD with the "Create Dell Rescue DVD Image" app.

The DVD appears to be OK but how do I use it? I mean how do I restore from the DVD?

Thanks

---

### Post by dorkdork777 on 2009-02-28
Try booting from the DVD - you may need to change your BIOS settings (put the DVD drive first in the boot order).

Out of interest, why do you want to know?

---

### Post by bevsmith on 2009-02-28
> **dorkdork777 said:**
> 

Out of interest, why do you want to know?

Funny question. I want to know how to restore the system if I hose it.

I'd like to know the disk is good and how to go through the procedure to save the system. I want to know if it's going to wipe out my data files which it probably does without warning.

I did get to a bunch of F1, F2... help screens after booting up with the rescue disk once but they read like they were writtin by mad scientist from MIT that haven't seen the light of day in 20 years.


I can boot from the DVD but I just get to a [initranfs] prompt that I don't know how to do anything with. That couldn't be right anyway can it? If this thing is going to compete with Windows it's going to have to be a little friendlier than that.

Thanks for the help.

---

### Post by aikiwolfie on 2009-02-28
Do you have a recovery partition? With my M1330n I got a recovery partition on the hard drive, a CD image and an original Canonical shrinkwraped CD. The recovery partition worked like a charm. It's just like installing any OS. Boot up and select the options you want.

The standard Ubuntu install also works great with Dell systems sold with Ubuntu because Dell pushes all the drivers it writes for its' hardware upstream to the main Ubuntu project.

In the end I made a copy of the ISO image, deleted the recovery partition and installed the standard version of Ubuntu 8.10. I haven't had any problems at all.

---

### Post by dorkdork777 on 2009-02-28
Heh, I meant that in more of a "are you in need right now, or just wondering" sort of way. :) But I can't imagine that the restoration DVD would include much that the normal Ubuntu installation CD can't give you, besides DVD playback, [but that's a doddle with Medibuntu anyway]("https://help.ubuntu.com/community/Medibuntu").

---

### Post by aikiwolfie on 2009-02-28
Apparantly it does. The Dell images can be much larger than the standard Canonical editions.

---

