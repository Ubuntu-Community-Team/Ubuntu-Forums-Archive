---
title: "print fine locally, as shared printer but not on router/server"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by wet_colored_arch on 2007-02-24
I am able to print to Konica Minolta 1350W on my Linux/Ubuntu machine when using PPD from this site and forums.  In addition I can treat the printer as a network printer and print from Mac OS x from different machine on my network IF my Linux box is turned on.  However, I have never been able to get the printer to work when connected to USRobotics 5461 router with built in server (using Linux/Ubuntu).

I can only print when the printer is directly connected to the Ubuntu machine via USB - not when connected directly to the server/router  The printer and router/server configuration worked fine when previously run from Windows.  I  understand the mechanics that I have to send to http:\.....\MyPrinter as recommended by USRobotics manual.

I am running Ubuntu 6.10 Edgy Eft on a PC platform that used to run Windows XP.  I had the same problem in 6.04.

I tried setting the printer up both in Ubuntu and also in CUPS with no success.  The job goes to printing but just seems to cycle indefinitely looking for localhost (I think - bottom status bar in cups flashes a quick message about localhost.)

Isn't there a log, or functionality I can check or enable to have the machine output to the network as it is properly working as a local install with shared printing?

Any suggestions... thanks

---

### Post by doncristobal on 2007-07-08
Maybe this can help: [http://ubuntuforums.org/showthread.php?t=369972](http://ubuntuforums.org/showthread.php?t=369972)
it's how i solved a very similar problem with my siemens router and hp printer

Good luck!

---

