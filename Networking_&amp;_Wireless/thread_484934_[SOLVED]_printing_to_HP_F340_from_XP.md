---
title: "[SOLVED] printing to HP F340 from XP"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by buddagodfred on 2007-06-26
I am running Feisty, on which I have shared an HP Deskjet F340.  I am using the "Deskjet 300" driver, because that is the only one I can find (and I think it's appropriate).  I can print from the Feisty fine, no problems, etc.  However, when I print via the network from an XP machine, nothing prints out.  It goes thru the spooler on the XP machine with no errors.  I can see the CUPS webpage ([http://localhost:631/printers](http://localhost:631/printers)) and look at the printer jobs, and it shows that the job has completed sucessfully, but there's nothing to show for it that has physically printed.  I'm using the correct driver from the XP machine as well.  

I am fairly sure that the sharing settings are correct, because previously I had an HP Laserjet 1200 that was shared and worked fine via the network.  

I'm about to toss this thing thru the window.  Any help would be great!!

Also, one other oddity...   after deleting the HP Laserjet 1200, the option to "share printers" has gone gray in the printer options.  I can't get it turned on, but since i can see the printer via the network, i'm assuming that it's ok...?  It worked with the 1200, but not with the F340.  


-fred

---

### Post by pingvin on 2007-06-26
Have you tried adding it as a generic PostScript printer from Windows?
Mike

---

### Post by buddagodfred on 2007-06-26
Pingvin....

Excellent!!  That worked wonders.  Many most happy thanks!


-Fred



P.S. - as a side note (if anyone is bored and needs something to reply to), just curious why this behavior occurs?

---

### Post by pingvin on 2007-06-26
Hi,
Sorry I didn't reply earlier I've not been in all after noon.
Glad to have been of assistance, I've had my fair share of printing difficulties in Ubuntu, 'bout time I saved someone else the bother!
Fraid I don't know the 'why', but it does make setting up a Linux print server very easy, since none of the clients need the actual printer driver installed, just PostScript, which already comes with Windows. In my experience, this also works Linux -> Linux :)
Mike

---

