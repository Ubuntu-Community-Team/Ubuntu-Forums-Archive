---
title: "Multi-function printer recommendation"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by jwaclawsky on 2009-04-22
I have Ubuntu 8.04. Printers are always changing. Has any one "recently" installed a multi-function printer (printer, copy, scan and fax) on Ubuntu they could recommend. I'd prefer one I could buy for $100 or less and simply works right out of the box (plug and play). Your guidance and suggestions are most appreciated. Thanks.

---

### Post by Sef on 2009-04-22
HP has Linux drivers for almost all their PSCes (Printers/Scanners/Copiers.)

---

### Post by jwaclawsky on 2009-04-22
I am looking for a specific make and model number that someone likes and would recommend to his friends. That installs without any fuss  :-)

---

### Post by Sef on 2009-04-22
With HP, you plug in and it works.  I have an PCS 1610, which is automatically detected once it is plugged in and turned on.

---

### Post by Malalo on 2009-04-22
I have a Brother DCP-7020, although this one does not do fax...
Works fine on Ubuntu

---

### Post by jwaclawsky on 2009-04-22
Anyone having any luck with Lexmark? I notice a couple with good prices at Costco and Sam's.

---

### Post by gj_clt on 2009-04-22
Lexmarks are mostly no no with Linux. My HP C4480 worked out of the box.

---

### Post by halitech on 2009-04-22
Lexmark is the devil when it comes to linux. I had a x2230 that I could not get to work so I gave it away. HP is generally the way to go

check openprinting.org for more info

---

### Post by riseringseeker on 2009-04-22
> **jwaclawsky said:**
> Anyone having any luck with Lexmark? I notice a couple with good prices at Costco and Sam's.

As a rule, home Lexmark printers do not work and play well with Linux, though I am sure there are exceptions.  I have heard Lexmarks more expensive office/production printers do much better, but I have no direct experience.

I use a HP 2175 All-In-One (Print, Scan, Copy) and it works perfectly.  You might want to look [[COLOR="Teal"]_here_[/COLOR]]("http://openprinting.org/printer_list.cgi"), that will give as good or better information than anywhere.

---

### Post by newbuntuxx on 2009-04-22
Not to high jack the thread, but I'd like to know if anyone here uses Canon all in one printers? Their photo printers? Are they also plug and play with Linux?

---

### Post by sydbat on 2009-04-22
Canon refuses to write drivers for Linux. You *might* get a Canon to work, but there's a 99% chance it won't.

---

### Post by Cammy on 2009-04-22
Since no one has mentioned it yet, there's a great app in the repositories called HPLIP that lets you do anything and everything on an HP all-in-one right from the desktop.  It also detects your printer if you have it installed via ethernet to your router.

I've been using an HP C5180 since 6.06, and never had a problem.  In fact, IMO the HPLIP app is better than HP's Windows drivers.

---

### Post by bear54 on 2009-04-22
I have a Pixma MP 500 printer - scanner combo and it works fine with Ubuntu 8.04. My only gripe is the quality of photo prints other than that it works great right out of the box. I just plugged it in and it worked.
Eric:)

---

### Post by Mortus Pryde on 2009-04-22
I have to say I am a great fan of HP Printers of all types and I find installing them on Ubuntu to be a dream! Far easer than Windows even. I am now to Linux and was floored when Ubuntu was able to just detect my HP Officejet Pro K5400dn and all its options over the network, just had to select its driver from the list and presto! Not to mention the print setup dialog is much more upfront with its options I don't have to go far in Linux to enable Tow Sided (Duplexed) printing.

I am half tempted to take out my older HP 2200 Business Inkjet that I upgraded with an internal print server and see how well that detects. ;)

Incase you have not noticed I am a huge fan of commercial class hardware, it just lasts soo much longer. Even the 2200 just needs a Megenta printhead and it would work near perfect.

---

### Post by jwaclawsky on 2009-04-23
I was looking at an HP Deskjet F4240 and checked to see if it was on the list at [http://openprinting.org/printer_list.cgi?make=HP](http://openprinting.org/printer_list.cgi?make=HP). It was but with an "*". Can I trust the information since the "*" seems to mean it is not verified?  ...Also will I need to get a driver or would I likely find what I need in my current Ubuntu distribution 8.04. Thanks for any advice.

---

### Post by sgosnell on 2009-04-23
IME any Brother or HP printer will work fine.  I can't say about other brands, but both these provide Linux drivers, and I haven't found one yet that didn't work.

---

### Post by halitech on 2009-04-24
> **jwaclawsky said:**
> I was looking at an HP Deskjet F4240 and checked to see if it was on the list at [http://openprinting.org/printer_list.cgi?make=HP](http://openprinting.org/printer_list.cgi?make=HP). It was but with an "*". Can I trust the information since the "*" seems to mean it is not verified?  ...Also will I need to get a driver or would I likely find what I need in my current Ubuntu distribution 8.04. Thanks for any advice.

according to here: [http://openprinting.org/show_printer.cgi?recnum=HP-Deskjet_F4240](http://openprinting.org/show_printer.cgi?recnum=HP-Deskjet_F4240)

the machine works perfectly. Basically they can't verify every machine because it would mean they would need to purchase every machine so they take the word on people that have the machine that say its working. If open printing says it works, chances are pretty good that it will work fine.

---

### Post by Sef on 2009-04-24
> Since no one has mentioned it yet, there's a great app in the repositories called HPLIP that lets you do anything and everything on an HP all-in-one right from the desktop. It also detects your printer if you have it installed via ethernet to your router.


HPLIP is very nice.  It is in Universe (All Open Source Software - in Add/Remove under Applications.)

---

### Post by Rowanmf on 2009-04-24
i have a hp officejet 5610 - all in one , plugged it in and never looked back ...

---

### Post by Kato4059 on 2009-05-01
> **Cammy said:**
> Since no one has mentioned it yet, there's a great app in the repositories called HPLIP that lets you do anything and everything on an HP all-in-one right from the desktop.  It also detects your printer if you have it installed via ethernet to your router.

I've been using an HP C5180 since 6.06, and never had a problem.  In fact, IMO the HPLIP app is better than HP's Windows drivers.
Let me get this clear;Do you mean to say that you connect the HP printer to the router instead of the tower or laptop ?. The reason that I am querying this is that I have an Epson Color Stylus 740 that I have been trying to 
have working with several Distros, but even though the CUPS finds the Epson, I still cannot print with it.I have tried on 2 different towers with different specs. but to no avail. Could this "router" solution possibly work with Epson ?
Thanking you.
kato4059:)

---

### Post by halitech on 2009-05-01
> **Kato4059 said:**
> Let me get this clear;Do you mean to say that you connect the HP printer to the router instead of the tower or laptop ?. The reason that I am querying this is that I have an Epson Color Stylus 740 that I have been trying to 
have working with several Distros, but even though the CUPS finds the Epson, I still cannot print with it.I have tried on 2 different towers with different specs. but to no avail. Could this "router" solution possibly work with Epson ?
Thanking you.
kato4059:)

the only way it would work is if the printer has an ethernet port to connect to the router.

According to Openprinting.org the printer should work properly if you install the proper driver. See here for more info:

[http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_740](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_740)

---

### Post by arapa on 2009-05-01
I also have an HP Printer Scanner Copier that had no problems at all getting it to work with Ubuntu.

[http://hplipopensource.com/hplip-web/index.html]("http://hplipopensource.com/hplip-web/index.html")

---

