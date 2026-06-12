---
title: "Why would Ubuntu sudenly start booting in low graphics mode?"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by Rossta on 2009-09-13
I was met with a brilliant response to my first set of questions yesterday and have sorted out a lot of problems already, this one however now has me stumped.

As of today when I boot up I am finding that I am met with a bunch of errors saying that ubuntu cannot recognize my graphics card and that there is no monitor present.  I am asked to boot in low graphics mode and cannot seem to rectify it.

Also after selecting to boot in low graphics I am met with a screen that tells me "there is already an X Server running and do I want to create a new instance?"

I am now completely flummoxed over this as it was reading my graphics card correctly yesterday.

Any help gratefully appreciated.

Thanks in advance.

Ross.

---

### Post by NoaHall on 2009-09-13
System -> Admin -> Hardware Drivers

If there's another version of the Driver in there, try enabling it.
Chances are is that you've updated and the new kernel conflicts with the driver.

---

### Post by Rossta on 2009-09-13
that program tells me that there are no propriety drivers for this system and I have no way to install any new ones.

I did recently have a power interrupt which means that the system did not shut down correctly.  Could this be something to do with it?

---

### Post by Sef on 2009-09-13
> I did recently have a power interrupt which means that the system did not shut down correctly. Could this be something to do with it?

Yes, possibly.   What graphics card do you have?

---

