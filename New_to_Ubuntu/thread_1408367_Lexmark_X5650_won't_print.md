---
title: "Lexmark X5650 won't print"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by jennifermq on 2010-02-16
Ubuntu "sees" the printer, sends test pages to the printer, but no printed paper appears. The print queue says the jobs are complete but nothing ever prints. I tried installing the Linux driver from Lexmark, no dice there either. What am I missing?

---

### Post by arochester on 2010-02-16
According to this:[http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X5650es](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X5650es)

It won't work in Linux.

---

### Post by philinux on 2010-02-16
> **jennifermq said:**
> Ubuntu "sees" the printer, sends test pages to the printer, but no printed paper appears. The print queue says the jobs are complete but nothing ever prints. I tried installing the Linux driver from Lexmark, no dice there either. What am I missing?

Not good news.

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-X5650es](http://openprinting.org/show_printer.cgi?recnum=Lexmark-X5650es)

[http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

---

### Post by jennifermq on 2010-02-16
Well hell, back to Target it goes then. Knew I should have got the cheapie $30 printer, it likely would be up and running by now :-?

---

### Post by philinux on 2010-02-16
> **jennifermq said:**
> Well hell, back to Target it goes then. Knew I should have got the cheapie $30 printer, it likely would be up and running by now :-?

Hewlett Packard are one of the best supported. Lexmark are one of the the worst

Just got one for GF.

HP C4680, works a treat.

Again though, check the open printing database or the manufacturers website.

---

### Post by switch10 on 2010-02-16
Don't buy Lexmark junk.  I had an all in one Lexmark printer that I got a great deal on.  Never got it working in Linux.  I had the same problem that you are describing.  I gave it to my parents, and it only lasted them a few months and then it died.  

Lexmark is junk.

---

### Post by wbar2 on 2010-03-29
> **jennifermq said:**
> Ubuntu "sees" the printer, sends test pages to the printer, but no printed paper appears. The print queue says the jobs are complete but nothing ever prints. I tried installing the Linux driver from Lexmark, no dice there either. What am I missing?

I'm having a similar problem. I've had my printer for a few months before I installed Ubuntu, so I will not be replacing it. That said, I probably will go with an HP next time, especially when I see them on sale and less than the price of replacement ink.

[_This person_]("http://www.awakecoding.com/index.php?option=com_content&view=article&id=20:installing-lexmark-linux-drivers-in-64-bit-debian-based-distributions&catid=1:home") was able to get the x5650 running on Debian 64-bit. Something is different about Ubuntu 64 though. I've also read that some have gotten it working on 32 bit Ubuntu. [_The driver is located here._]("http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz")

---

### Post by wbar2 on 2010-03-30
Solved: [http://ubuntuforums.org/showthread.php?t=1441862](http://ubuntuforums.org/showthread.php?t=1441862)

---

### Post by Bob_G7 on 2010-04-04
After building a 2nd 9.10 server I ran into the same error, tried shutting down and restarting without any luck.

Finally went into CUPS and after the job failed I tried the RESTART button for the job and it started printing and has been working ever since.

Don't know why it happend on this server build it didn't on the first one or when I built a Desktop.

---

### Post by cwcthatsme on 2011-09-06
i am having the same problem with the lexmark x5650 said the print was done but no print

---

