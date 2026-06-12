---
title: "Rready Boost"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by MrKlean on 2009-04-02
Windows has a feature called ready boost that lets you use a usb stick as ram.  Does Ubuntu have anything similar..as a quick fix for low memory.  It seems like a nice touch, but I'm sure there are hidden problems!
Thanks ; )

---

### Post by hovzio on 2009-04-02
Linux has a swap partition, this is used when ram runs low.

EDIT: you do need to manually set up this partition, best during installation.
:)

---

### Post by philinux on 2009-04-02
You can use a swap file too.

[http://www.linux.com/feature/113956](http://www.linux.com/feature/113956)

---

### Post by Hospadar on 2009-04-02
Not really - although it is possible to use a thumb drive as swap space.

They way a memory system works, in case you are not of the computer science persuasion, is that to each program, it appears that the entire memory space is available, the OS and hardware map memory addresses to where they are supposed to go.  If there isn't enough real memory, the OS puts some of that data onto the hard disk (which in linux is the swap partition, and in windows there are special swapfiles).
Really all ready boost does is put swap files on a usb stick, and I think it may prioritize that space for when it pre-loads programs.
In linux, you could just format (all or a portion of) your usb drive as swap (you can do this in gparted) and then mount it as swap with the "swapon" and "swapoff" commands.  You should probably google those commands and make sure you understand them.

All that said, it's probably unlikely you actually need to do that.  If you have an older machine that really doesn't have enough ram (512mb should be plenty to run ubuntu comfortably, especially xubuntu, I have systems with about 200mb running xubuntu acceptably), then you should have a fair sized swap partition (depending on the size of your ram, maybe .5 to 1 times the size of ram, smaller ram, bigger swap) on your hard disk.  If you notice that both your swap partition and main memory are consistantly filling up, and you can't increase the size of your swap partition (tiny old hard drive?) then I suppose you might want to try and use a thumb drive as extra swap space.

In short:
It's very unlikely you would need to do this, or that there wouldn't be a better option (a bigger hdd swap area)
In windows (vista) I think this is more of a red herring than anything.  Windows manages to squeeze some savings out of it because the jump drive may have slightly lower seek times then a hard disk (the time it takes to access a random piece of data), but overall a hard disk (connected with sata, ide, or whatever) is much faster than the usb interface, even if fast flash memory is on the other side.

---

### Post by MrKlean on 2009-04-03
Thanks all, I thot it was a nice feature till I read more about it ..lol

---

