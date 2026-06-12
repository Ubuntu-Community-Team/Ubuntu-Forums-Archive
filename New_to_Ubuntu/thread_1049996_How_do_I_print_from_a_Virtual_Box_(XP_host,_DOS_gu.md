---
title: "How do I print from a Virtual Box (XP host, DOS guest)"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Heleen Tammes on 2009-01-25
I have a Virtual Box running under XP Home. 
I have DOS running in the Virtual Machine. 
But how do I print? 
I don't see a parallel port connection I can capture.
I don't think the DOS OS can print to a USB port. 
Thanks in advance, Heleen

---

### Post by kestrel1 on 2009-01-25
Not sure if this will work, but have you tried the old DOS comand:```
**print c:\file.txt /c /d:lpt1**
```

---

### Post by diablo75 on 2009-01-25
You're probably going to have to call MacGyver.  He might see if there's any way to print via a serial port (I don't know that there is).  Or perhaps you can attach an old floppy drive and move whatever data you're trying to print out of the VM.  Who knows what else might work?  I'm pretty sure Virtualbox does not support LPT ports.

---

