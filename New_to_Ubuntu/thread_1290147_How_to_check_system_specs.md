---
title: "How to check system specs?"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by smileyguy on 2009-10-13
Can somebody remind me how to check system specs with 9.04?

The equivalent in XP was right-clicking on My Computer and selecting Properties.

I really only want to check the processor and memory installed.

GUI is preferred but if there is no other way than command then that will have to do . . .

---

### Post by dominiquec on 2009-10-13
For GUI, click on System->Administration->System Monitor.  System specs are in the leftmost tab.

On the command line, 'lshw' will give you everything you need.

If you just want to check your memory, 'cat /proc/meminfo'

If you just want to check your CPU, 'cat /proc/cpuinfo'

---

### Post by smileyguy on 2009-10-13
Thanks:)

---

### Post by laidback on 2009-10-13
Please mark as solved.

---

### Post by anaconda on 2009-10-13
And even more details from commandline:

more /proc/cpuinfo

more /proc/meminfo

EDIT:  Sorry. didn't notice that this was already on a previous post....

---

### Post by beastrace91 on 2009-10-13
> **smileyguy said:**
> Can somebody remind me how to check system specs with 9.04?

Install the package "sysinfo" from Add/Remove Programs, Terminal, or Synaptic. This will provide and GUI decently similar to WinXp right-click-mycomputer/properties.

~Jeff

---

