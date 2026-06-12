---
title: "Display loses connection?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by lockalidiot on 2010-02-14
I've been having this issue for three days now. Usually involved with gaming. I play a while, say, Open Arena, and then my display goes black except for a blue notification that says "no signal detected". Whats whit that? My cp-specs can easily run all the games I have.

I ran this, so that you can see if there is anything that isn't supported or something.
```
me@here:~$ sudo lshw -C display

*-display               
       description: VGA compatible controller
       product: GT200 [GeForce GT 220]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:ce000000-cfffffff(prefetchable) ioport:d800(size=128) memory:fe980000-fe9fffff(prefetchable)

```

Any idea what is wrong?

---

### Post by lockalidiot on 2010-02-14
Could someone please help me with this!? Every time the display loses connection I'll have to reboot the machine the hard way and it is really annoying to have to do it more than three times a day, If I play something!

---

### Post by lockalidiot on 2010-02-14
Honestly guys, this has been here for over six hours, AND NOT ONE REPLY! Please help me with this!

---

### Post by col48 on 2010-12-22
It would be nice to know what the solution was......

I have this problem intermittently.  It can happen even if the computer has been idle for a while.

Usually Ctrl+Alt+F1 (don't panic at what you see) followed by Ctrl+Alt+F7 will get me back to the action.

---

