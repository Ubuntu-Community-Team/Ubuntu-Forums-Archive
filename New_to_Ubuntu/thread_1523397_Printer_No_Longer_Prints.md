---
title: "Printer No Longer Prints"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by skymera on 2010-07-03
I have an Epson E220

It was pritning fine, until I cancelled a print job..

Now it wont print a thing. I've deleted the printer in CUPS config, i purged all prints jobs and still, nothing!

What can fix this?

---

### Post by khelben1979 on 2010-07-03
Maybe the printer is "dead"? Have you tried to reboot?

---

### Post by skymera on 2010-07-03
Dead? It works fine in other PCs.

Rebooted several times.

If it helps:
```

scott@scott-desktop:~$ tail -f /var/log/cups/error_log
D [03/Jul/2010:20:29:26 +0100] [Job 3] Gutenprint: Reading 2975 634
D [03/Jul/2010:20:29:26 +0100] [Job 3] Gutenprint: Reading 2975 635
D [03/Jul/2010:20:29:26 +0100] [Job 3] Printer busy; will retry in 5 seconds...
D [03/Jul/2010:20:29:26 +0100] [Job 3] Job canceled by "scott"
D [03/Jul/2010:20:29:26 +0100] [Job 3] End of messages
D [03/Jul/2010:20:29:26 +0100] [Job 3] printer-state=3(idle)
D [03/Jul/2010:20:29:26 +0100] [Job 3] printer-state-message="Printer busy; will retry in 5 seconds..."
D [03/Jul/2010:20:29:26 +0100] [Job 3] printer-state-reasons=none
E [03/Jul/2010:20:29:55 +0100] cupsdReadClient: 16 IPP Read Error!
E [03/Jul/2010:20:30:00 +0100] PID 3544 (/usr/lib/cups/filter/rastertogutenprint.5.2) crashed on signal 13!
```

---

### Post by jmore9 on 2010-07-03
Try turning off the printer then turning off your machine.  Unplug the printer from the data connection you use ( lpt , usb, or what ever ).  Then turn on the machine , let it boot all the way to the desktop.  Then turn if off and hook up the printer as you had it before.  It should start working then.  Hope that helps you.  Know it is a little time comsuming but always works for me.

---

### Post by skymera on 2010-07-03
Tried that too, sadly that did not fix this.

---

### Post by cloyd on 2010-07-03
I don't know that Epsons do as my Lexmark does, but my x2600 will stop printing and not give a warning, and troubleshooting tool in karmic was useless. The problem? Ultimately, ink cartridge needed replacing. It would still work as a copier, but it had printed all the pages it was going to print. May not be your problem, but it got me twice. (Was really embarrassing the second time).  

As I said, diagnostics on 9.10 didn't solve the problem. Diagnostics on 10.4 did. (dual boot).

Another problem with an hp. Suddenly quit printing in evince. Printed in OpenOffice.  Solution was to install Adobe Reader. Never did get it to work on Evince again.

---

