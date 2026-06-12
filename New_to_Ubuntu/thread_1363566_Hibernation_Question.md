---
title: "Hibernation Question"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by fleamour on 2009-12-24
I regularly hibernate both Windows 2000 & Xubuntu on the same disk/laptop.  It seems to work, other than Xubuntu throwing up a error, something about indirect registry access?  Not sure really, must jot it down next time it happens...  But does Xubuntu hibernate to the swap partition as opposed to RAM?

If not, I imagine this could be causing some kinda problem if both operating systems were fighting for RAM space?

It definitely causes problems between Ubuntu & XP on my tower, where I only leave XP hibernated & just boot to Ubuntu when needed (Windows tends to have a horrifically long start up time.)

---

### Post by JKyleOKC on 2009-12-24
Yes, Xubuntu hibernates to disk. I've never gotten WinXP's hibernation to work at all so I don't know whether it goes to RAM or to disk, but from your report I suspect it goes to RAM. In that case, bringing Xubuntu back from hibernation would work just fine but would destroy any hibernated XP session...

---

### Post by oldfred on 2009-12-24
WinXP saves to hiberfil.sys.

The risk you take with hibernation and booting another system is if you modify something in the hibernated system that the hibernation is using or linked to then you have corrupted the system. As long as you do not delete or change anything in windows while in ubuntu it may work.

---

