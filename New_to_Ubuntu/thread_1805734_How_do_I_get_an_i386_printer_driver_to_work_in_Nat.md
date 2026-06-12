---
title: "How do I get an i386 printer driver to work in Natty AMD64"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by bwallum on 2011-07-16
Hi

Just installed Natty 64bit on a Lenovo G560. I want to drive a Canon MP492 USB printer from it. I have a 32 bit driver in deb form. How do I put a wrapper on it to run in the 64 bit OS?

---

### Post by JC Cheloven on 2011-07-16
Hi, I see [here]("http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP490.aspx?type=download&page=1") Canon offers source code for the driver. You may try compiling yourself in your system. 

Note.- Your profile is not that of a newcomer, that's why I suggest that ;)

---

### Post by bwallum on 2011-07-17
> **JC Cheloven said:**
> Hi, I see [here]("http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP490.aspx?type=download&page=1") Canon offers source code for the driver. You may try compiling yourself in your system. 

Note.- Your profile is not that of a newcomer, that's why I suggest that ;)

Thanks JC, indeed my teeth are long (those that are left) and my mind forgetful. Also if my query appears that it might be of general interest to newcomers I post to the Absolute Beginner's forum.

Interestingly, I have found 
[http://theseekersquill.wordpress.com/2010/05/03/canon_mp610_ubuntu_1004_64bit/](http://theseekersquill.wordpress.com/2010/05/03/canon_mp610_ubuntu_1004_64bit/) 
which, although out of date, points in a similar direction to your suggestion. Also, there is a Debian version 
[http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP492.aspx?type=download&page=1 ]("http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP492.aspx?type=download&page=1")
that will make life a bit easier hopefully.

I'll return with an update soon to let you know how I got on.

UPDATE
I didn't find the .deb file useful because it was 32bit and the 'seeker quill' approach did not work for me.

Instead, as you kindly suggested, I downloaded the source file from 

[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP492.aspx?type=download&page=1](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP492.aspx?type=download&page=1)

I needed to select software downloads, then Linux and English (for me) and then chose 'Linux Source file for Print Drivers'. Instead of compiling a new driver I found a ppd directory. I made a folder on the Desktop called CanonDriver, put the IJ_Linux_Printer_Driver_Source_320.tar file in it (keeps the Desktop tidier) then 'Extract Here', open folder 'Extract Here' open folder and bless me there is the ppd folder. In my case I chose the canonmp490.ppd file and put it on the Desktop.

In System Settings (using Unity, System>Administration in Classic) I selected Printing and when the 'Choose Driver' appeared I chose 'Provide a PPD file' and navigated to it.

The PPD file is 32/64 bit neutral I think. CUPS takes care of the rest.

---

### Post by JC Cheloven on 2011-07-17
Awesome! I take a note myself of your solution. 

I'm also glad to see that companies with bad reputation regarding linux support (as canon) start to make our life easier.

Cheers

---

