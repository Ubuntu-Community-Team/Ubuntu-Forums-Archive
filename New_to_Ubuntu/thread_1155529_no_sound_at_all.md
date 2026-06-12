---
title: "no sound at all"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by blackprince97 on 2009-05-10
I just installed Ubuntu 9.04 on my Gateway MX7515 laptop and I've been using it for a little while with almost no problems. However, recently I've been having quite a few issues with sound. At first it was just a restart and then the problem was solved. But now I'm getting absolutely nothing, restart or not. Using sudo alsa force-reload worked for awhile but now that has stopped and now I can't get sound working at all. Please help.

---

### Post by e_james on 2009-05-11
Where computers are concerned, I have found that almost anything is possible, but my first idea at this time is that your problem lies in hardware rather than software. Are you satisfied that there is no hardware fault? If you boot up from power-off using a live CD and have no sound, I would definitely put hardware at the top of the suspect list. Obviously this test is invalid if you need to install special sound drivers not available on the live CD. If the sound works properly with the live CD then my next suspect would be a recent update, in which case a bug report might be justified.

---

### Post by qjmoss on 2009-05-11
> **blackprince97 said:**
> I just installed Ubuntu 9.04 on my Gateway MX7515 laptop and I've been using it for a little while with almost no problems. However, recently I've been having quite a few issues with sound. At first it was just a restart and then the problem was solved. But now I'm getting absolutely nothing, restart or not. Using sudo alsa force-reload worked for awhile but now that has stopped and now I can't get sound working at all. Please help.

Alrighttt


What you need to do, is right click on your volume control, and open volume control.. or at least that's what I think it's called, im currently at school, and I can't remember what everything is called ; )


Make sure ALL the Sliders are turned up, this happens to me randomly and I just reset the volume options.


hope this helps

---

### Post by blackprince97 on 2009-05-11
> **e_james said:**
> Where computers are concerned, I have found that almost anything is possible, but my first idea at this time is that your problem lies in hardware rather than software. Are you satisfied that there is no hardware fault? If you boot up from power-off using a live CD and have no sound, I would definitely put hardware at the top of the suspect list. Obviously this test is invalid if you need to install special sound drivers not available on the live CD. If the sound works properly with the live CD then my next suspect would be a recent update, in which case a bug report might be justified.

Perfect sound when booting from the live CD.


> **qjmoss said:**
> Alrighttt


What you need to do, is right click on your volume control, and open volume control.. or at least that's what I think it's called, im currently at school, and I can't remember what everything is called ; )


Make sure ALL the Sliders are turned up, this happens to me randomly and I just reset the volume options.


hope this helps

okay tried that. Returned the sound until I rebooted and then got nothing. Tried it again and now I don't get sound back.

---

### Post by e_james on 2009-05-11
I am sure that you would be happy if someone reading this would make a suggestion along the lines of editing a configuration file or installing a new software package. Unfortunately that sort of knowledge is well beyond beyond my current level of linux expertise, but if I was in your situation, there are still things I could do to identify the cause of the problem and, hopefully, fix it.

1. A new thread in this forum or other forums is probably worth a try. You would want to provide as much information as possible about your hardware and the remedies you have tried so far. You should probably try to think of a title which would attract the attention of someone able to help. Maybe something like "Gateway MX7515, Ubuntu 9.04 - sound fails after updates - software bug?" Perhaps you have already done this.

2. While you are waiting for the replies, if you have the time and you are willing to do the testing, you could redo the installation in controlled steps. If the sound works well with the live CD, I would expect that it would also work well for an installation derived only from that CD. What I mean is - run the install without a connection to the internet so that no updates are downloaded. Assuming that works, then look for updates and install them in small batches with particular attention to any that seem to be relevant to the sound system. At each step you will want to be certain that the problem has or has not appeared, so several restarts are probably required.

If I was doing the above I might be tempted to make backup images of the root partition at each step forward so that when it breaks I could reload the most recent good image. You can't use the installed linux to backup itself so you would need to use the live CD (downloading partimage each time) or a specialist CD such as GParted or Parted Magic (which is clever at mounting and unmounting partitions). It would even be possible to install a second copy of ubuntu in a separate partition or an external hard drive or flash drive. This works best if the PC can boot from other partitions / drives without needing to install grub to the MBR of the main drive again. (Using the live CD there's an advanced options button at the grub install stage.)

All of the above represents several hours of work, but I can't offer anything better at this time.

---

