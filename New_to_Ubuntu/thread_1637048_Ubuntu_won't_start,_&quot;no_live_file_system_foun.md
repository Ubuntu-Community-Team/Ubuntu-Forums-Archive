---
title: "Ubuntu won't start, &quot;no live file system found&quot;"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by jking333 on 2010-12-03
I have fallen victim to the AVG disaster of two days ago, and I cannot start my computer. There were no restore points created, so could not just go with last good configuration. I cannot start in safe mode, I can't to anything, it's stuck in an endless startup loop. I created the AVG rescue disk, but when presented with the user agreement, my keyboard is not recognized, so nothing happens. I even pulled out an old ps2 keyboard, still nothing. The AVG forum manager told me to try a live cd and ubuntu was the first and best thing I found online, so I created an Ubuntu disk (3 tries actually, just to make sure), and every time I get this message when it starts up:

(initramfs) Unable to find a medium containing a live file system


Nothing can be entered, no buttons can be pushed, and if left long enough, the system just shuts down. I've been trying for 2 days to get my pc started up, and nothing is working. If I could just get it started and delete avg, the computer would start up fine. Any help would be greatly appreciated, the avg forums are all but useless, and they created this problem to begin with!

Thanks in advance,
Jessica

---

### Post by wilee-nilee on 2010-12-03
> **jking333 said:**
> I have fallen victim to the AVG disaster of two days ago, and I cannot start my computer. There were no restore points created, so could not just go with last good configuration. I cannot start in safe mode, I can't to anything, it's stuck in an endless startup loop. I created the AVG rescue disk, but when presented with the user agreement, my keyboard is not recognized, so nothing happens. I even pulled out an old ps2 keyboard, still nothing. The AVG forum manager told me to try a live cd and ubuntu was the first and best thing I found online, so I created an Ubuntu disk (3 tries actually, just to make sure), and every time I get this message when it starts up:

(initramfs) Unable to find a medium containing a live file system


Nothing can be entered, no buttons can be pushed, and if left long enough, the system just shuts down. I've been trying for 2 days to get my pc started up, and nothing is working. If I could just get it started and delete avg, the computer would start up fine. Any help would be greatly appreciated, the avg forums are all but useless, and they created this problem to begin with!

Thanks in advance,
Jessica

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

This will be probably quite helpful. A couple of days ago I saw thread suggesting that avg messes with the bootloader, can't confirm anything about avg though.

So to get a disc to boot you can use a per-session key prompt that brings up a menu from what you want to boot from. My prompt is f12 yours may be different or even the esc key, generally you can get the information on the key prompt from the manual or on the web if you search with the computer model, and boot, per-session.. etc you have to get creative here. 

This per-session boot is done like you would access the bios you hold down the correct key after hitting the power-up button immediately. Feel free to give the computer model I will look for this but try it yourself first please.

Also identify all the installed distros in other which windows. It sounds like you don't actually have a Linux install but if you do mention that as well.

So we want to get you booted into the live Ubuntu cd it is a powerful tool, you can get into windows through it. But most important to start is to post the bootscript.

---

### Post by jking333 on 2010-12-04
I am on a borrowed laptop, how do I get the bootscript from my defunct computer? It is completely nonfunctioning..cannot even bring up a command line.

My pc is a Gateway DX4720-03 running Windows Vista Home Premium 64-bit

---

### Post by wilee-nilee on 2010-12-04
> **jking333 said:**
> I am on a borrowed laptop, how do I get the bootscript from my defunct computer? It is completely nonfunctioning..cannot even bring up a command line.

Take a look at the per-session boot part I think other then getting a cd to boot from the bios by having the cd player first in that boot from menu, this method may be the only one off a forum.

---

### Post by jking333 on 2010-12-04
No go. Am I screwed? What if I got an old hdd with windows on it, made my current hdd slave to the old one and tried deleting avg from the current? Do you think that would work? Thanks for your time!

---

### Post by wilee-nilee on 2010-12-04
> **jking333 said:**
> No go. Am I screwed? What if I got an old hdd with windows on it, made my current hdd slave to the old one and tried deleting avg from the current? Do you think that would work? Thanks for your time!

Okay lets make sure we are on the same page. No go means you know this per-session prompt key and it isn't working?

Or what does no go mean?

As far as, are you screwed I wouldn't know, nor would I about just deleting a AVG file. If it is just a file deletion you could do it from a Ubuntu cd if the key prompt works.

This forum  and the support or helpers that try to help on rather messed up situations are rather methodical, as there are some straight forward ways to do this, but you never know maybe the 2nd hd would work but that is like hitting a hole in one from my point of view, but hey what do I really know.

---

### Post by Sef on 2010-12-04
> (initramfs) Unable to find a medium containing a live file system

Do you have a Live CD or a Live USB (or can you get one?)

If so, then boot into the live cd/usb, > Applications > Accessories > Terminal.

Then copy and paste this code into the terminal:

```
sudo fdisk -l
```

Then copy and paste the results here. That command will show us what your partitions are like.

---

### Post by jking333 on 2010-12-04
> **Sef said:**
> Do you have a Live CD or a Live USB (or can you get one?)

If so, then boot into the live cd/usb, > Applications > Accessories > Terminal.

Then copy and paste this code into the terminal:

```
sudo fdisk -l
```Then copy and paste the results here. That command will show us what your partitions are like.    


Yes, I made three different ubuntu live cds, trying to get it to work. But when that error message comes up, I cannot do anything. Nothing can be typed in or no buttons hit. And I tried all the fbuttons, other than f2, f8 and f10, which do something else, and nothing else happened, so I don't think my computer likes the live cd...

But with the avg thing, two drivers are in the boot process, and that is what is creating the problem. Apparently, it messed up the registry during the update and made it unstable. It happened to a LOT of people a couple days ago, but the avg rescue cd seems to have worked for most people, but for some reason, on my computer, it does not allow function of my peripherals. They have been little to no help on the avg forums, they told me to try a live cd. 

If I could just get into the program files, and delete the avg file, those two drivers would not load and the computer should start as normal, I think. I just have to borrow someone's unused hdd, which I can later on today.

Thanks again,
Jessica

---

### Post by jking333 on 2010-12-04
> **wilee-nilee said:**
> Okay lets make sure we are on the same page. No go means you know this per-session prompt key and it isn't working?

Or what does no go mean?

As far as, are you screwed I wouldn't know, nor would I about just deleting a AVG file. If it is just a file deletion you could do it from a Ubuntu cd if the key prompt works.

This forum  and the support or helpers that try to help on rather messed up situations are rather methodical, as there are some straight forward ways to do this, but you never know maybe the 2nd hd would work but that is like hitting a hole in one from my point of view, but hey what do I really know.


No keys worked, no change in anything.

---

### Post by wilee-nilee on 2010-12-04
> **jking333 said:**
> No keys worked, no change in anything.

Do you know the per session prompt key?

---

### Post by jking333 on 2010-12-04
> **wilee-nilee said:**
> Do you know the per session prompt key?

I googled it and nothing came up..I tried all the F keys and none of them change anything.

---

### Post by wilee-nilee on 2010-12-04
> **jking333 said:**
> I googled it and nothing came up..I tried all the F keys and none of them change anything.

Post the computer model the exact model. It may be any key lets see if we can find it.

---

