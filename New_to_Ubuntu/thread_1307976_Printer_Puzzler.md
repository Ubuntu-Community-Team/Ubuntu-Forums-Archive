---
title: "Printer Puzzler"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by catraeth on 2009-10-31
Hi all
Day two of my Ubuntu experience and all seems to be going well - I can now do most of the things I could with, you know, the other, ***old*** operating system... :p

I come to the point where I want to install my printer - HP Laserjet 1018 - I plug it in and I get a message saying there is no driver for that particular printer.  However, very helpfully it offers to download the driver for me.  I accept and it installs the driver.  Tickety boo. So I go to print a page, it appears in the print queue, then disappears just exactly as if it has been printed.  No error messages appear, but neither does anything appear from the printer!  I try another page.  Same thing happens.  I've checked the connections and everything seems okay, so I'm stumped.

Any ideas please?

p.s. Maybe I should have said that when I look at Printer Configuration the printer shows up okay, and says it's 'idle, ready to print'.

---

### Post by Bucky Ball on 2009-10-31
[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1018.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1018.html)

HP printers are very well supported. You shouldn't need to do much. Guides you through from a terminal setup. Real easy and should be up in 5.

I had a problem where the driver had been updated and I was attempting to use the old one which had become obsolete so I was getting similar problems. HPLip will compare what you have installed with what's available and get the right one for you.

The other thing is some of their printers need a plugin which is NOT part of the driver package and must be loaded separately. HPLip will detect and let you know if this is the case. Could be that.

One last thing; when using HPLip be careful to follow what it is instructing to do meticulously. There a couple of places where you can screw it up but you should be fine. Start with the printer UNPLUGGED from the machine then run HPLip. It will come to a section where it will ask you to plug it in.

* It does sound like the driver you have is working to a point - you might need to change something in the HP printer config GUI.

---

### Post by catraeth on 2009-10-31
> **Bucky Ball said:**
> [http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1018.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1018.html)

HP printers are very well supported. You shouldn't need to do much. Guides you through from a terminal setup. Real easy and should be up in 5.

I had a problem where the driver had been updated and I was attempting to use the old one which had become obsolete so I was getting similar problems. HPLip will compare what you have installed with what's available and get the right one for you.

The other thing is some of their printers need a plugin which is NOT part of the driver package and must be loaded separately. HPLip will detect and let you know if this is the case. Could be that.

One last thing; when using HPLip be careful to follow what it is instructing to do meticulously. There a couple of places where you can screw it up but you should be fine. Start with the printer UNPLUGGED from the machine then run HPLip. It will come to a section where it will ask you to plug it in.

* It does sound like the driver you have is working to a point - you might need to change something in the HP printer config GUI.

Bucky Ball - thank you!  That sorted it and I'm now able to print.  Great advice here!

---

### Post by Bucky Ball on 2009-10-31
No probs and welcome to the forums. Glad I could help. :)

I like it when a plan works out!

---

