---
title: "How to count the number of prints taken on printer?"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by Guruprasad on 2010-11-07
I have HP printer connected to Ubuntu. I want to count the number of printouts taken on the printer. How can I do this?

---

### Post by Cheesehead on 2010-11-07
The easiest way is usually to get the page count from the printer.
Many HP printers have a built-in webserver. Find the IP address, point a browesr at it, and the web page will tell you.

---

### Post by Guruprasad on 2010-11-07
My printer is connected via USB. How to check the print count in this case?

---

### Post by Verbeck on 2010-11-07
in the the print queue click view completed jobs. (the check-mark) should show every print job up to now

*not a count really, but might help ;)

---

### Post by Cheesehead on 2010-11-08
There are two answers for a USB printer.

In many cases, the printer does NOT tell your Ubuntu system how many pages it has printed in its lifetime. So you have two counts:

1) You have the printer's count. Most printer diagnositc pages include this number. You must consult your printer's manual to determine how to print the 'technical information' page, usually some combination of buttons on the printer.

2) Your system tracks how many jobs (not pages) it sends to each printer. Within each job is the number of pages for that job. Verbeck's instruction is appropriate for tracking job information.

---

