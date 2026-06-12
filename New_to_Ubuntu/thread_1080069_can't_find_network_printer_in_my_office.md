---
title: "can't find network printer in my office"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by yanbianfan on 2009-02-25
I am running Intrepid on my laptop at work.  I'm connected to a wireless network in which the main computer in the office is sharing an hp laserjet 1020 plus.  I've tried to add this printer using "Windows Printer via Samba" under the new printer configuration menu.  It won't find the printer.  I can ping the computer that the printer is on, but this printer wizard won't find it.  I'd appreciate any help.
Thanks

---

### Post by stchman on 2009-02-25
> **yanbianfan said:**
> I am running Intrepid on my laptop at work.  I'm connected to a wireless network in which the main computer in the office is sharing an hp laserjet 1020 plus.  I've tried to add this printer using "Windows Printer via Samba" under the new printer configuration menu.  It won't find the printer.  I can ping the computer that the printer is on, but this printer wizard won't find it.  I'd appreciate any help.
Thanks

How is the printer hooked up in your office?

Is it attached to a Windows machine?  Is it attached to a print server?

---

### Post by yanbianfan on 2009-02-25
It's attached to a windows machine

---

### Post by superprash2003 on 2009-02-25
try this [http://ubuntuforums.org/showthread.php?t=1076545](http://ubuntuforums.org/showthread.php?t=1076545)

---

### Post by MrWES on 2009-02-25
Or try configuring with the CUPS GUI:

[http://localhost:631]("http://localhost:631")

When you add the printer, Ubuntu should see it from there.

Bill

---

### Post by yanbianfan on 2009-02-26
> **superprash2003 said:**
> try this [http://ubuntuforums.org/showthread.php?t=1076545](http://ubuntuforums.org/showthread.php?t=1076545)
Thanks so much.  Connecting directly with the IP address of the windows computer worked perfectly!! thanks

---

