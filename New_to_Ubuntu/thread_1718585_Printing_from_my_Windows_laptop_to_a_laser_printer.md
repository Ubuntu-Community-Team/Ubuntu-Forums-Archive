---
title: "Printing from my Windows laptop to a laser printer on my Ubuntu computer"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by peterfirth on 2011-03-31
Is there a way I can print from my laptop (running Windows XP) to my laserjet printer connected to my Ubuntu PC? The printer is shared in Ubuntu but the laptop can't see it.

---

### Post by wolfen69 on 2011-03-31
You need to network the computers with Samba.

---

### Post by JKyleOKC on 2011-03-31
> **peterfirth said:**
> Is there a way I can print from my laptop (running Windows XP) to my laserjet printer connected to my Ubuntu PC? The printer is shared in Ubuntu but the laptop can't see it.While wolfen69's suggestion will work, once you get Samba operational, there's a much simpler way that does not require Samba and works in Windows 2000 Pro and Win XP Pro, so ought to work with later versions of Windows as well. It involves configuring a printer, on the laptop, as a network printer. Here are the steps to do so:

First, on the Ubuntu machine, open your browser and go to [http://localhost:631](http://localhost:631) which will access the CUPS print server that's installed in Ubuntu by default. You can simply click the link in this message; "localhost" always refers to your own machine, at 127.0.0.1.

When the CUPS home page appears, click the "printers" tab, and from its list select the one you want to use. Now copy the address of the resulting page from the browser address bar, onto a flash drive. This is the critical part, to assure that there are no typos in the address when you use it in Windows. With the address saved, you can move over to the laptop for the rest of it.

From the start menu, select printers (the exact label may vary from one version to another), and click the icon for "add a printer" to start the "new printer wizard." When it asks whether to browse for the printer, locate the option that uses "http", and paste the saved address into its text box. Then use the "next" buttons to step through the wizard.

When it gets to the page asking what make and model of printer you have, you can select from its lists. However if your printer is not listed (mine isn't on these older versions) you can simply use the very first printer in the list. The Linux drivers in CUPS use postscript formatting and almost any printer driver on the list in Windows will provide postscript output!

To verify that it works, print a test page from the last screen of the wizard. It's worked every time, for me, but your mileage may vary...

---

### Post by I2k4 on 2011-03-31
These more experienced users probably have good mechanical solutions.  What I have done is install DropBox,.  When I'm running Ubuntu on one machine and XP on the other, I can "print" whatever document in whatever application I want to .PDF format in the DropBox.  It is then quickly synchronized to the DropBox folder on my main PC and can be printed to hardcopy that way.  

PDF format gives you an advance look at what the document will look like on paper, and overcomes any compatibility issues between documents on Windows and documents on Linux 

[www.dropbox.com](www.dropbox.com)

---

### Post by JKyleOKC on 2011-04-01
> **JKyleOKC said:**
> Now copy the address of the resulting page from the browser address bar, onto a flash drive. This is the critical part, to assure that there are no typos in the address when you use it in Windows. With the address saved, you can move over to the laptop for the rest of it.One very critical correction for you! Before you start, determine the IP address of your Ubuntu machine. You can do this from the Network Manager, or from a terminal window with the command "ifconfig -a" if you prefer. Note it down.

Then, after getting the full address of the printer and pasting it into a text file on the flash drive, open Notepad or a similar editor and replace "localhost" in the address with the IP address of the machine. This is what will let the laptop find it!

It slipped past me originally because I did almost the same thing, but my Ubuntu machine that I copied the address from already had the IP address of another box that actually had the printer.

If you're connecting the boxes through a router, you may need to verify that the Ubuntu box always gets the same IP address when you power up. Most routers allow you to modify settings to make sure this happens, but it's something to watch out for...

---

