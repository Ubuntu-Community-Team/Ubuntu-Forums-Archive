---
title: "Need help installing Canon Pixma MX350"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by ROVDude on 2011-07-03
Hello all.

So I still consider myself new to Ubuntu, though I'm learning quite a bit and am in the process of working it into all my PCs and laptops at home.  What I am having an issue doing now is installing my printer/scanner/fax and having access to all the functions.

So, after searching the forums, I found [this]("http://ubuntuforums.org/showthread.php?t=1785003&highlight=canon+pixma")

I went [here]("http://software.canon-europe.com/products/0010836.asp") and downloaded the .tar and I'm all ready to do........something.

I can see the printer on the WLAN IP address, and Ubuntu found that (Running  with 10.10, by the way).  I open the system > admin > Printers  window, click "Add", then "Network Printer".  I typed in the IP address from the WLAN settings on the machine, and  found it right away.  Not sure what the "Queue" and "Connections" selections are supposed to be all about.  I just let it chose the default ones, and that's when it starts looking for the drivers.

Kind of at a loss at this point.  I have the file downloaded, but i can't figure out where to open it up to, and where to put the drivers so the printer will see them.

I'm still trying to figure out how to unpack the files, and where everything goes.  So, if someone could like, step by step me through this, I'd really appreciate it.

Thanks!

---

### Post by ROVDude on 2011-07-04
UPDATE:

I went online to [here]("http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html") and followed the directions.  Didn't work well, so I ended up following the link to the administrator page (at the bottom of the page).  I followed the directions there, and still couldn't get it to work or see or recognise my printer.

SO.....when all else fails, reboot.  I did, and went to System > Administration > Printing and started to add the printer.  When it came time to look for the drivers, low and behold, the MX350 was in the list now!  YAY!  Clicked on it, followed the instructions (I do that a lot), and there it was!

Worked beautifully, and now I can print....

so, how do I set up for scanning and faxing?  Haven't tried yet, but I'll work on that later.

---

### Post by ROVDude on 2011-07-04
UPDATE:

So I spent all day today downloading tarballs and trying to "compile and install" them.  Yeah, looked everywhere on the forums, and found virtually conflicting instructions.  For instance, found a tar.gz for a bundle that is supposed to allow my computer to work with and see the Canon Pixma MX350 that I have, so I can print and scan with it.  So the instructions say at one point to use the ./configure command in Terminal.  OK, so I got an error.  From then on it degenerated into one big confusing jumble.  At one point I had 4 different programs installed, and 3 more tarballs ready unpack.

Then came the epiphany:  Check Synaptic.

OK, so I searched "MX350" in Synaptic, and found this: scangearmp-mx350series.

Cool!  So I marked it for installation, installed it, and *POOF*, now I can scan!  sweet.

Dunno if anyone will be able to glean insight from this thread.  I hope it helps someone.

If there are any lessons to be learned, its this:  If you are a newbie like myself, and you are having a bear of a time finding a software program to do something.  Search for the name in Synaptic, or some variant of it.  Chances are you'll find something there.

---

