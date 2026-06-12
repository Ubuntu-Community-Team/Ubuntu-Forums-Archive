---
title: "Install problem Xbunto"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by wabe on 2009-08-13
I'm an absolute beginner trying to replace Win 98SE with xbunto on an old compaq armada (Intel P3 I think)  Everything goes well until the following message is received

[   0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    4.136470] OI APIC resources could not be allocated.

What do I do now? Do I need a different version of Xbunto - if so which one.

The problem I'm trying to solve is Win98's failure to connect properly thru USB ports

---

### Post by kerry_s on 2009-08-13
list the specs please, sounds like its to old.

---

### Post by QIII on 2009-08-13
In addition to the system specs requested above, could you tell us what you mean by "all goes well until..."

Does this mean the installation goes properly, but when you try to run Xubuntu you are getting the message?

If that is the case, then it used to be the case that one only had to add the words "acpi=force" to one of the lines in a file known as menu.lst.  It's been a while since I ran into the problem on a very old machine, but I might be able to find some notes.  Not sure if it would even work with a more recent kernel, though.

Don't worry about the file name or how to modify it just now.  Someone can talk you through it if you come to that bridge.  The big thing to understand is that there is likely a simple solution, but we need more information to figure out where to look.

So please post your system specs and let us know exactly when you are encountering the message.

We're here to help, and we'll do all we can!

---

### Post by Clorow on 2009-08-13
You might want to use the Alternate Install CD if your hardware is too old to run the Live CD. It's text-based, so it might not look pretty, but the end result will be the same: Xubuntu on your old computer.

---

### Post by Paqman on 2009-08-13
> **wabe said:**
> 
The problem I'm trying to solve is Win98's failure to connect properly thru USB ports

Win98 didn't include support for USB by default, you'll need to install USB drivers to get it to work.

---

### Post by wabe on 2009-08-14
PROBLEM SOLVED

Thanks for your input guys.  I passed the problem to a kid I know.  Its all fixed - tho' I have no idea what the problem was or how he fixed it  ... Its all magic to me

---

