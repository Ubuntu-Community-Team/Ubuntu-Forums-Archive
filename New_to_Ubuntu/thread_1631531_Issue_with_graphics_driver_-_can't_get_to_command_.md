---
title: "Issue with graphics driver - can't get to command line on boot"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by Jerry123 on 2010-11-26
I'm having a problem with an nvidia driver and ubuntu 10.04, which seems to be a very common issue, but I can't get to a command line on boot to fix it. I think I can sort it out of I can just get to a command line, but all I get is a black screen after it boots with no options and no key combos seem to do anything. Even using recovery mode gives me a black screen.
 
I've tried the Ctrl-Alt-F1 that is supposed to bring up that boot type selector menu, but it doesn't work. I actually got to it once by jamming on some keys, but after trying to fix the problem (unsuccessfully) and rebooting, I can't get that menu back.
 
Pretty much the only think I can do is get to the grub selector screen, and can make it to the grub command prompt, or the grub editor using "e". Everything after that doesn't seem to work.
 
Please, if anyone can help I would really appreciate it. This problem is driving me crazy. I've found a lot of posts similar to this subject, but I haven't found a solution to the problem as it relates to not even being able to get to a command line.

---

### Post by bioterror on 2010-11-26
how about recovery mode from grub?
if that doesnt help, then LiveCD and chroot ;)

---

### Post by Jerry123 on 2010-11-26
> **bioterror said:**
> how about recovery mode from grub?
if that doesnt help, then LiveCD and chroot ;)
 
Recovery mode does the same thing. In both cases, I believe the graphics driver is fouled up and won't show any output. I think the OS is loading properly, it's just that I can't see anything.
 
It seems like I need to somehow interrupt the load of those drivers or disable them prior to the full boot. I had it working before with more generic drivers, but when I tried to load the nvidia ones, everything went black. I need to undo what I did, but without a screen for output, i'm sunk.

---

