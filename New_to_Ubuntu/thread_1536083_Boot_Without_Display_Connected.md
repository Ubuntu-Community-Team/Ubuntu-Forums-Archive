---
title: "Boot Without Display Connected"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by Singlebbl on 2010-07-21
Will Ubuntu (and Linux in general) boot correctly without a display attached? I have tried several times and it acts like it's coming up but appears to be catatonic when I do connect the display. 
 
In my Windows experience, it flat don't care about the display. All it needs is a mouse & a keyboard.

---

### Post by endotherm on 2010-07-21
no you don't need a monitor, only really a keyboard, and you can probably ditch it as well if you config the bios to ignore no keyboard warnings.

ping is probably teh best way to confirm that a headless box is booted, so just ping it from another location until you start getting replies.

you can track your boot time using a tool like bootchart, or just checking the dmesg log, looking for a pair of events that are sequential but have widely differant timestamps. teh timesamp is the first collumn, and it indicates the number of seconds since boot.

---

### Post by gordintoronto on 2010-07-21
Yes, many, many people run systems with no monitor, keyboard or mouse.

---

