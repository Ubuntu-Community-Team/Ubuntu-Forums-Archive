---
title: "Network printing problem(s)"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by Old *ix Geek on 2007-07-26
I didn't check any of the similar threads because I SERIOUSLY doubt anyone else has had this exact combination of printing problems!

Here's the setup:  There's an HP 3500 series printer connected via USB port to an XP box; the XP box is connected via wireless to the local network; the printer is shared; all other boxes on the network are Linux.

Okay, up until a week or so ago, EVERYTHING was fine and dandy.  The printer worked from its own computer and from any/all of the other computers on the network.  And then...being windoze...it inexplicably screwed up.

The first thing that happened was the printer stopped working from its OWN computer. In other words, anything sent to it--even a test page--from the local computer did not print.  However, it still worked fine from all of the REMOTE computers.  (Go figure!)

Next--after uninstalling and reinstalling the printer and its drivers on the XP box--it would print the HEADER only of a test page (where it shows the M$ logo and says "Windows XP" at the top of the page), but did NOT print any of the lines of text that are supposed to appear beneath it.  Simultaneously with this new development--after uninstalling and reinstalling the printer from various Ubuntu boxes--nothing sent to it from a Linux machine will print; instead, those documents end up in the printer's queue (which only shows on its own computer; checking its status from the Linux end shows that it was successfully sent to the printer).  And they stay in the print queue indefinitely...and stop windoze from being able to print anything ELSE sent to the printer.  I have to manually stop the print spooler from a 'doze prompt, delete the files in the queue, and restart the spooler in order to clear it.

Here's the clincher: Hooking the printer up DIRECTLY to a Linux machine...it works perfectly.  So the problem is NOT the printer itself!  And since I've already uninstalled/reinstalled the printer and its drivers on the XP box, I don't have a clue what else to try.

I realize this is more a 'doze problem than a Linux one, but I simply cannot fathom that anyone on a 'doze board would be able to help!

---

