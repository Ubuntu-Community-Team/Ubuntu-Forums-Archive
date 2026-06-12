---
title: "Windows XP won't shut down with Grub 2"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by newbiewon on 2010-03-14
I have ubuntu, mint, and mint kde plus windows XP running with grub 2. Windows is on drive hdo and the linux distributions are on hd1.  When I ran the same configuration with grub legacy, I could get windows XP to shut the computer down.  Since I upgraded to grub 2, I can not get the Windows XP system to shut down the computer.  Instead I come back to the start up page of grub 2 and have to restart a linux distribution and then shut the computer down from that point. Why can't I get windows XP to shut the computer down?:o

---

### Post by Rey117 on 2010-03-14
Just get rid of windows...lol

---

### Post by oldfred on 2010-03-15
It sounds like a windows problem. Generally grub just passes the boot loading to XP and has no control once passed.

Do you have grub in sdb and windows boot loader in sda? If so try booting windows directly and see if the problem is still there.

---

### Post by Midnight Star on 2010-03-15
It sounds like, for some reason, Windows or some setting somewhere (maybe BIOS), is returning back to the "caller", so to speak. Like a RETURN in basic, (RTS, RTI in early assemblers). I have dual-boot computers here, and I haven't noticed that behaviour during shut downs. Though to be honest, I never really use the Windows partitions any more. It's mostly for my sons games.

---

### Post by lavinog on 2010-03-15
It could be that windows is crashing during shutdown.
A kernel panic in windows sometimes causes a reboot.  Check the event log for errors...try booting windows into safe mode and see if the problem persists.
Also do a virus scan, there are a lot of root kits going around lately.
Also scan the windows partition for errors

It is still likely that the this is a coincidence that it started happening after grub was updated.  There have been some windows updates that have caused system instability (especially if the system was infected with a root kit)

---

