---
title: "Connect to internet- belkin wireless"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by harveyphillips on 2007-09-06
Beginner Here: Just installed Ubuntu 7.04. Can't figure out how to connect to the internet. I'm using a Belkin pcmcie card. Under host-program files, I see a folder named Belkin wireless utility; but from that point I have no idea how to activate the procedure. Step-by-step lesson please?

Harvey

---

### Post by Steve1961 on 2007-09-06
> **harveyphillips said:**
> Beginner Here: Just installed Ubuntu 7.04. Can't figure out how to connect to the internet. I'm using a Belkin pcmcie card. Under host-program files, I see a folder named Belkin wireless utility; but from that point I have no idea how to activate the procedure. Step-by-step lesson please?

Harvey


What's the model and version number of your card.  Also, plug in the card, open a terminal and type the command below:

lspci -v

post the output

---

### Post by harveyphillips on 2007-09-07
Thanks Steve

You Asked: "What's the model and version number of your card?"

      Version # not shown on card or manual, but model listed as Wireless Pre-N Notebook Network Card.

You requested I:  "... open a terminal and type the command below:

lspci -v"

     
     A little problem on this point Steve.  I don't know how to open a terminal!

Harvey

---

### Post by Steve1961 on 2007-09-07
> **harveyphillips said:**
> Thanks Steve

You Asked: "What's the model and version number of your card?"

      Version # not shown on card or manual, but model listed as Wireless Pre-N Notebook Network Card.

You requested I:  "... open a terminal and type the command below:

lspci -v"

     
     A little problem on this point Steve.  I don't know how to open a terminal!

Harvey


Hi again.  OK, is it this one:

[http://catalog.belkin.com/IWCatProductPage.process?Product_Id=184399](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=184399)

if so there's a few how tos on this forum that are worth reading through.  e.g.

[http://ubuntuforums.org/showthread.php?t=259037&highlight=F5D8010](http://ubuntuforums.org/showthread.php?t=259037&highlight=F5D8010)

However, as Belkin have a nasty habit of changing the chipsets on their cards whilst keeping the model number the same you should check the chipset by typing lspci -v  

The terminal application can be opened from Applications>accessories>terminal

After doing a quick search it looks like ndiswrapper is probably going to be your best bet - and again there's lots of how tos.  

Good luck :)

---

### Post by justinmiller87 on 2008-03-02
If you're having trouble getting the Belkin card installed, the Airgo link in my signature is a step-by-step guide to installing the F5D8010.

---

