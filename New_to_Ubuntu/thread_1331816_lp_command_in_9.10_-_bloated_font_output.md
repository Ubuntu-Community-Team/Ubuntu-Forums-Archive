---
title: "lp command in 9.10 - bloated font output"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by bhold on 2009-11-19
The following command entered from a terminal window:

lp textfile

In Ubuntu 9.04, it works fine.

In Ubuntu 9.10, it prints but in a large, boated font.

I tried using lp -o cpi=12 -o lpi=8 - which made the output a little smaller but still not right.

I also tried modifying /etc/cups/printers.conf file to make the 9.10 file more like the 9.04 file. Result - no printing at all.

The printer is an HP OfficeJet 4215, served by a Windows XP system in my home office.

Suggestions how to trouble-shoot or fix this??     Thanks!!

---

### Post by zipcodeman on 2009-11-27
I am having the same problem.

When I use -o lpi, I have to specify a number much larger than what actually prints.

Spaces as well are not getting done correctly, I have a file that has words spaced out to a certain column, but it isn't in the right place.

It worked fine in Jaunty.

---

### Post by bhold on 2009-11-27
Printing a text file to the printer from gvim works fine. That is my work-around until I figure out how to make the lp command work for text files on 9.10, or until a patch comes out.

But in general if you have column spacing requirements you will probably get more reliable output using tabs instead of space characters.

---

### Post by zipcodeman on 2009-11-27
> **bhold said:**
> But in general if you have column spacing requirements you will probably get more reliable output using tabs instead of space characters.

I realize that, but my point is that using spaces worked when I was using Jaunty, but after the upgrade to Karmic, it stopped working correctly.

---

### Post by zipcodeman on 2009-12-11
bump.

---

### Post by bhold on 2009-12-15
I have no new information except - I thought maybe this was a problem with the printer's ppd file so I replaced the 9.10 file with the one from 9.04 (at /etc/cups/ppd/). Then re-started cupsd. This did not work. I print from Ubuntu to an HP OfficeJet 4210 remotely to an XP system.

---

### Post by zipcodeman on 2010-01-04
Does nobody have any answers here? How can this problem only affect two people?

---

### Post by bhold on 2010-02-18
Problem solved. Must be fixed due to patches as I have not changed anything. I noticed some cups patches the other day, maybe that is what fixed it.

---

