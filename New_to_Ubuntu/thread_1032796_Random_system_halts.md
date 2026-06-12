---
title: "Random system halts"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by AZoMBiE on 2009-01-06
I'm new to Linux and decided to go with Ubuntu for my transition,
been putting it off for a long time but now that I have I don't want to
go back to Windows.
I've gotten pretty much everything I wanted to working but there's one
problem I just can't solve.

I'm well versed in Google-fu and pretty knowledgeable when it comes to
troubleshooting PC problems but being new to Linux is really hurting.


[B]My problem is a seemingly random complete system halt.
(sound loops, mouse and keyboard unresponsive, have to do a cold boot)[/B]


I've tried everything I can think of to resolve this but it's continuing
to happen and is the only problem I'm having.



_**So what do I need to provide to help?**_
Looking at the system log right after a crash it's always something
different it was doing at the last second.

[INDENT]
Ubuntu 8.10
3 HDD (1 sata, 1 ide, 1 usb - Ubuntu installed on SATA
  with Vista in dual boot) (All Western Digital)
Athlon X2 64 3800+
2GB DDR2 Dual Channel
Foxconn 939 mobo using onboard eth
nV 8800gt
audigy 1[/INDENT]


_Things I've tried:_
- Install the gui for ntfs-3g and enable read/write on all drives
- Uninstall all non-essential applications
- Using the 2nd kernel option @ boot (not the safe mode thing,
    the other x.x.x one)
- Using different applications (Transmission instead of Ktorrent, etc)
- Burn-in tests using Hiren's boot disc, all clear
- Removing non-essential hardware
- Disabled services (powernowd, acpid)
- Not doing anything (just leaving it be, nothing running, still crashes)

[I]
Example of randomness:[/I]
Ran for 2 days, no crash.
Wake up this morning and it was locked up, cold booted, went to go
make some coffee, came back was locked up again.

---

### Post by donkyhotay on 2009-01-06
When it locks up on you if you press ctrl-alt-f2 what happens?

---

### Post by AZoMBiE on 2009-01-06
Nothing, Tried CTRL ALT F1-F6, CTRL ALT Backspace,
Unresponsive.

only thing I haven't tried is ALT SysRq + R S E I U B

---

### Post by AZoMBiE on 2009-01-07
bump, don't know where to look for help with this if
anyone could share some light on what logs to check etc
would be very helpful.

---

