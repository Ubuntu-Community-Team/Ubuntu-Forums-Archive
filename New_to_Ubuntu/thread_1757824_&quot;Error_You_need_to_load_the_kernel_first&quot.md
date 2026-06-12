---
title: "&quot;Error: You need to load the kernel first&quot;"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by Marcello511 on 2011-05-13
I got so excited when I found out that Natty has that cool windows 7 thing where you can snap a window to half of the screen that I threw a fit and smacked my netbook a couple times while it was running. Now at startup after the grub screen I get: 

[I]error: couldn't read file 
error: you need to load the kernel first

Press any key to continue...[/I]


What might the problem be?

---

### Post by Hedgehog1 on 2011-05-13
The shock/impact of your 'joyous outburst' may have forced the drive heads into contact with the spinning platter.

If you have a LiveCD/LiveUSB, please try booting from that, select 'TRY', and then fire up the 'Disk Utility'.  Please take a look at the SMART 'health' of your drive.

Post your findings...

***The Hedge***

:KS

---

### Post by loskiorama on 2011-09-17
hey!

same thing here 
i executed the disk utility on my brand new samsung hard drive and i got:

Bad Sectors: 24 

And in the Attribute assesment table i get
Attribute: Current Pending Sector count
Assesment : Warring

is it a hard drive failure? . I've got a new drive three weeks ago as my old one was constantly failing

:(

---

### Post by Mark Phelps on 2011-09-17
I'm not a fan of Disk Utility.  I would not trust it's claim as to disk health.

A more reliable approach (in my opinion) would be to find out the make and model of your hard drive, go to the manufacturer's website, and see if they have a drive health utility you can download.

If the drive has a warranty, they typically demand a report run from their own utilities before they will replace it.

---

