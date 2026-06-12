---
title: "Network printing with Gutsy"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by shanerdaner on 2007-10-22
Why is adding a network printer so difficult now????  Fiesty was so much easier...I cannot browse and auto detect anymore..... any ideas?

---

### Post by linuxwizard on 2007-10-22
Look at this it may or may not help 

[http://ubuntuforums.org/showthread.php?t=586981](http://ubuntuforums.org/showthread.php?t=586981)

---

### Post by shanerdaner on 2007-10-22
No Luck :-(

---

### Post by balbinny on 2007-10-24
try installing system-config-printer from synaptic.

---

### Post by shanerdaner on 2007-10-24
> **balbinny said:**
> try installing system-config-printer from synaptic.

still nooooooooooooooooo luck

---

### Post by the ber on 2007-10-25
try installing "gnome-cups-manager" from synaptic. afterwards go to "system-administration" and there should now be two "printing" icons. one of them should be the older version with the auto detect.

---

### Post by shanerdaner on 2007-10-25
> **the ber said:**
> try installing "gnome-cups-manager" from synaptic. afterwards go to "system-administration" and there should now be two "printing" icons. one of them should be the older version with the auto detect.
I think my router is blocking it I will add it and see how it does.  Thanks for your help.

---

### Post by shanerdaner on 2007-10-25
Nope still no luck must be this version of ubuntu the other worked perfectly. Any other ideas?

---

### Post by froy02 on 2007-10-25
have you installed the cups driver for your printer?  If so open your browser and type "http://localhost:631". A local site should open where you can configure your printer.

---

### Post by shanerdaner on 2007-10-25
Do I do it on the laptop or the desktop with the printer?  thanks

---

### Post by shanerdaner on 2007-10-25
ok I found the page but I am confused on what to do now...

---

### Post by shanerdaner on 2007-10-25
I clicked on the Administration tab and my V40 is not showing only the gen PDF

---

### Post by shanerdaner on 2007-10-27
Am i the only person having problems in the world with this???  lol

---

### Post by markbutler on 2007-10-29
No, I am experiencing exactly the same problem. Printing worked fine in the previous release, but now it does not, although things do sometimes print. Plus the tools for managing printers keep crashing.

---

### Post by markbutler on 2007-10-29
Here are the symptoms I am seeing: when I boot the machine, if I am lucky, I may be able to print a single page, although there is a considerable delay doing this. Then I get a message "Not connected? Pritner 'x' may not be connected".

If I try to use the new printer tool, then if I make any changes it just hangs, and any other program that has a printer dialogue also hangs if I open that dialogue. I installed the old printer tool as someone advised here, and that works better, but there is no way to get rid of the new printer tool, as ubuntu-desktop lists it as a dependency.

So no solution at the moment, apart from reboot to MS Windows if I want to do any printing. Printing worked fine in the previous version of Ubuntu, so this is very annoying. Any suggestions of a fix would be most appreciated?

---

