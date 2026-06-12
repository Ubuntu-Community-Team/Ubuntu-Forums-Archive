---
title: "installing a printer"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by shasocastris on 2009-01-18
Hi. I recently moved from Windows XP to Ubuntu 8.04, and I've had trouble installing my printer.

I have a Brother DCP-7020, and, while my computer recognizes it, the printer doesn't seem to receive any commands to print. I've been following the instructions in _Beginning Ubuntu Linux Third Edition_, Chapter 8, but it hasn't been helping. 

Here's a quick overview of what's going on:
1. I go to System > Administration > Printing and select new printer.

2. Here, I'm asked which Device to use, and I select Brother DCP-7020 USB #1. This makes sense, as it's attached to my laptop via a USB cord.

3. Then it searches for drivers, and I press the 'Select printer from database' radio button. I've tried using the CD that came with the printer, but Ubuntu won't run any of the .exe files on the CD.

4. After going to the next screen is where I run into problems. It asks for the model, and gives me the options for:
DCP-1200
DCP-7025 BR-Script3
DCP-8020 BR-Script3
DCP-8025D BR-Script3
DCP-8040 BR-Script3
DCP-8045D
DCP-8045D BR-Script3

The one Ubuntu selects by default is the second option. This has one driver option:
DCP-7025 BR-Script3[en](recommended)

Could someone please help me understand what's going on, and how to install my printer. Thanks a lot!

Cheers!

---

### Post by jimmy the saint on 2009-01-18
As far as I can tell go to this page
[http://www.linuxprinting.org/show_driver.cgi?driver=hl1250&fromprinter=Brother-DCP-7020](http://www.linuxprinting.org/show_driver.cgi?driver=hl1250&fromprinter=Brother-DCP-7020)

And press the Generate PPD button (make sure download box is checked)

Go back to the "printing" app (where you installed the printer) and delete the one you installed so you can start over.

When it asks you what driver to use slecet "provide PPD file" and locate the file you downloaded.  Finish the installation as normal and you should be good to go.

Good Luck

---

### Post by mac71 on 2009-01-18
Have you installed the drivers through synaptic? (its in there- i just checked) There seems to be support for just about everything brother in there now. I had my DCP-135 up and running in no time.

---

### Post by shasocastris on 2009-01-18
Thanks guys. I was able to make my printer work.

Cheers!

---

