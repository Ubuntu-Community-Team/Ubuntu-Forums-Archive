---
title: "Low Graphics Mode"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by WileyGaia on 2008-12-07
Hi - everything was all good (first 3 weeks of Ubuntu 8.10 under the belt!) - then yesterday got an error on starting up "Ubuntu has to run in Low Graphics Mode". Tried all the options presented, nothing seems to resolve the problem, can barely see anything on the screen...

Tested the screen on my Windows machine and its fine (LG LCD). I have a Windows machine so I can still get to this forum. Any assistance would be greatly appreciated
PS. I am a total beginner, this is my first venture into the world of Linux

---

### Post by taurus on 2008-12-07
What kind of graphic card does it have?  Try booting into recovery mode and use the fix Xserver option to see if that helps.  Otherwise, boot straight into recovery mode and run

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by WileyGaia on 2008-12-08
Thanks for the input. This is a bit embarassing - but the problem is I am such a beginner I don't know how to start in recovery mode...  (sorry, I also don't know what graphics card I have either, but I will find out from the shop I bought it and let you know)

---

### Post by nhasian on 2008-12-08
when you first begin to boot your pc, when the grub menu is showing, choose the recovery option.  when the menu appears, select the xfix option and see if that fixes your graphics.

---

### Post by WileyGaia on 2008-12-08
Thanks, will try tonight when I get home and let you know

---

### Post by WileyGaia on 2008-12-11
Got a break from studies last night and attempted both fixes above, but neither of them worked...:confused:
Any other suggestions?

---

### Post by WileyGaia on 2008-12-11
It doesn't look like this problem is solv-able. 
SO: I think I will try re-installing from scratch...
is this just a matter of booting from my boot cd?
and before I do that, is there any way I can save my files on my hard drive to cd or memory stick before I do that? I cannot see anything on the normal desktop so would have to use the "Back-End" console for that... 

My DSL router also died, luckily it was under warrantee, so now I have a brand new (NETGEAR wired) router, but has not been plugged back in yet - can't view the screen so don't want to do anything with it yet

---

### Post by WileyGaia on 2008-12-11
To answer your question regarding the graphics card - it does not have a graphics card, it is "onboard" the motherboard. The notherboard is an Intel 945

---

### Post by WileyGaia on 2008-12-11
In fact the motherboard has the following video:
"Intel® GMA 950 onboard graphics subsystem"

Anyone have any clue on how I can sort this out?:confused:

---

### Post by WileyGaia on 2008-12-11
And the screen is an LG W1934S (1440x900)

---

