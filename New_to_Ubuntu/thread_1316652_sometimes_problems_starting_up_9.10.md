---
title: "*sometimes* problems starting up 9.10"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by G_Alexander on 2009-11-06
Hi 

I have finished installing Ubuntu 9.10 on my Dell inspirion 1525 laptop and it works well (when it starts up!). I say that because sometimes (about 50%) when starting up it freezes on the ubuntu logo when loading (the white ubuntu logo thats appears for a minute whilst the system is loading in the background). I can tell straight away when it's going to be one of those no-no boots since when the logo appears there is no hard drive activity from the offset, whilst there is when its going to be a successful boot. 

When it does freeze like this during startup, I can normally restart properly by using CTRL+ALT+DEL, which restarts with boot options (like ubuntu normal boot, ubuntu recovery boot...) - I just choose normal boot and again, we have a 50/50 chance of booting.

Also, I have a windows 7 partition on the hard disk but since installing ubuntu I don't get the option to choose to boot in to windows. If windows is on /dev/sda2 and ubuntu on /dev/sda3 (according to gparted) how can I make it so I'm asked which one to boot in.


Hope you guys can help, thanks in advance :)

Grant

---

### Post by SunnyRabbiera on 2009-11-06
it might be doing a file system check, how many times have you booted

---

### Post by fancypiper on 2009-11-06
> **SunnyRabbiera said:**
> it might be doing a file system check, how many times have you bootedIf it is doing fsck, shouldn't there be disk activity? There is hard disk activity on my systems during fsck.

---

### Post by G_Alexander on 2009-11-06
I've probably managed to boot successfully about 4 times out of 8. Good point, that never crossed my mind, but then if it was doing some sort of filesystem check would there not be a message onscreen or some hard disk activity? (the HD light on the laptop doesn't even flash when it's in this state).

I also forgot to mention that after a few minutes of the ubuntu logo on screen, the screen just goes blank.

---

### Post by SunnyRabbiera on 2009-11-06
> **G_Alexander said:**
> I've probably managed to boot successfully about 4 times out of 8. Good point, that never crossed my mind, but then if it was doing some sort of filesystem check would there not be a message onscreen or some hard disk activity? (the HD light on the laptop doesn't even flash when it's in this state).

I also forgot to mention that after a few minutes of the ubuntu logo on screen, the screen just goes blank.

Its hard to rule out the possibility of a file system check as many people are having issues with Karmic.

---

### Post by Bunnybugs on 2009-11-06
For the dual-boot, you need to setup your BIOS to use this...

most of the time this is preset, but Dell is a little crappy with that kind of things, the have contracts with MS, etc, etc, so they don like that you use another OS...

just take a look on your BIOS settings...

and about the Ubuntu-boot... have you tried to do the recovery-mode?

had the same problem at start with 'karmic', but recovery solved the probs

---

### Post by G_Alexander on 2009-11-06
Thanks, I will try booting in recover mode later today to see if that solves anything.

---

### Post by G_Alexander on 2009-11-06
No joy I'm afraid. Switched on laptop this afteroon and the same thing happened (froze on logo). Booted in to recovery mode then at the prompt I restarted.

I then started up and shutdown three times successfully. On the forth time, same problem.

Is there any more info I can give to help such as a log file etc? 

Many thanks

---

### Post by G_Alexander on 2009-11-06
Hi 

I think I've managed to solve the problem by enabling SATA in the BIOS (SATA is enabled by default on this laptop model but I disabled it at one point so I could install WinXP). Since then, I've managed to boot successfully about ten times which is a record. I'll mark the thread solved and hopefully it won't happen again / hopefully I can open the thread again if the problem persists.

Thanks,

---

