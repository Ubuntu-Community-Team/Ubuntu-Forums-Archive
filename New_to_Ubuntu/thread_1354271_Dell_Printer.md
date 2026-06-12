---
title: "Dell Printer"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2009-12-13
One of the only devices that I haven't been able to set up on Ubuntu is my Dell A920 all-in-one printer. Has anyone else been able to set this up. Specifically, I'd like to be able to scan.

---

### Post by Janeleaper on 2009-12-13
Sorry, I think you'll find you cannot use the 920.  I'm not technically knowledgeable, but I think the problem is with this type of printer.  You need a "postscript" printer.

More bad news: this type of printer tends to be more expensive bought new than the ones that Dell practically give away with their computers.

Now the good news. There are plenty of secondhand printers around that are compatible and you can pick up for a few dollars.  I replaced my Dell printer with an HP that I got for $25 in a yard sale.

Have a look through the list of compatible hardware (in the hardware forum) and then go shopping. 

I don't have a scanner, so I can't advise about that.

---

### Post by Otto-C on 2009-12-13
Take a look at this post.

[http://ubuntuforums.org/showthread.php?t=29374](http://ubuntuforums.org/showthread.php?t=29374)

hth
otto-c

---

### Post by Janeleaper on 2009-12-14
Well, my apologies for giving you the wrong advice, and I'm now sorry I disposed of my 920.  Oh well, at least the HP I replaced it with works ok.

---

### Post by spiderbatdad on 2009-12-14
I have spent many hours trying to get the A940 to work with the Z600 and Z55 lexmark drivers, and it just never happened. Best of luck. I have had good experiences with HP printers and linux.

---

### Post by EnigmaticCoder on 2010-07-28
This post is for the benefit of googlers.

I'm just now getting my printer working. Months ago, I followed the advice given by people in this thread, but I couldn't get the printer to work. Today, I decided to try installing the printer again. And it works.

This page has been updated since my last attempt:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark) Z600 Series Printers

Follow the directions for the z600 series printers. Install the libstdc++5 package from the link they give you. Download and install the driver deb file. Then when you add a printer, the z600 model will show up at the bottom of the Lexmark list (when it searches before this step, it won't find a dell a920 driver but don't fret. Using the Lexmark z600 driver will work for your a920). Then you'll be set.

Moreover, scanning works natively in 10.04. Woo hoo!

---

