---
title: "How do I find out the ink status on an Epson Stylus D92"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by bwallum on 2008-12-15
Hi

I have an Epson Stylus D92 Printer running under Intrepid on a 32bit machine. It connects through usb and works well. The driver is CUPS+Gutenprint v5.2.0 rc1 [en].

How do I find out the printer ink levels?

It's quite important because the printer has 4 separate ink cartridges. When one runs out the printer simply stops working and a warning light flashes...but it doesn't say which cartridge is empty! They are too expensive to buy a set of four each time one goes.

---

### Post by The Cog on 2008-12-15
Not that particular make of Epson printer, but I have monitored the ink status of Epson printers with the package **mtink** which is in the repositories.

---

### Post by ellgor on 2008-12-16
Hi,

You could try Qink, basic but works.

Regards, Ellgor.

---

### Post by philinux on 2008-12-16
As the cog says mtink works really well.

Only thing that it needs is gksudo to run it or, add your user name to the group lp in the file /etc/group

There is a warning to this effect when you install mtink.

---

### Post by Quasaur on 2009-03-23
To BWallum: I'm trying to get an Epson Stylus Photo 820 to work under amd64 Intrepid. Could you tell me how you got your Epson to work?

Right now lsusb doesn't even see the epson, even with usblp loaded.

---

### Post by bwallum on 2009-03-24
> **Quasaur said:**
> To BWallum: I'm trying to get an Epson Stylus Photo 820 to work under amd64 Intrepid. Could you tell me how you got your Epson to work?

Right now lsusb doesn't even see the epson, even with usblp loaded.

Sorry but I can't be of much help. I bought an HP Color Laserjet 3600n and haven't looked back. I find that HP printers are best supported in Linux along with minolta-qms and xerox. I looked at the cost per colour A4 sheet and got 17p per sheet for inkjet (using refilled cartridges) and 6.5p per sheet using the laserjet. You need to spend about £150 up front though. Look for new 'end of line' for a bargain.

Regards
Bob

---

### Post by F W Adams on 2009-06-08
Hi, I've got a problem with my D92, it's been working fine since I had it, many months. I've never changed ink cartridges since I had it. It may be out of ink now but which one ( if any )?

Some info.
lsusb gives:
Bus 007 Device 002: ID 04b8:0005 Seiko Epson Corp. Stylus D88+

Under printer properties
usb://EPSON/Stylus%20D92

Under make and model
Epson Stylus D68 - CUPS+Gutenprint v5.2.0-rc1 Simplified

Printer state
Idle

If I try to print something the printer state goes from Idle -> Processing - Printing page 1.20% ( and then hangs / waits )

The power light is on and the red light is on, it has paper and power.

------------

When I go into Mtink I get a choice of /dev/lp0, /dev/usb/lp0 or /dev/usblp0 ( they all do the same whichever I select ) and then I get "Problems with the printer communication, please check the printer for error. "Out of paper", "No ink" "printer not powered"

I think it may be out of ink but I thought it was meant to be telling me.

Help, I'm not sure what to do next?

---

### Post by bwallum on 2009-06-08
It may be a good time to consider an alternative. From what I have read this printer appears not to be the best thing Epson have produced.

[http://www.amazon.co.uk/product-reviews/B000QG3Q5O?pageNumber=3](http://www.amazon.co.uk/product-reviews/B000QG3Q5O?pageNumber=3)

I run HP with Ubuntu and have no problems. Check out which printer works best here:-

[http://www.openprinting.org/printer_list.cgi?make=HP](http://www.openprinting.org/printer_list.cgi?make=HP)

Regards
Bob

EDIT This might help too - 
[http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_D92](http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_D92)

---

### Post by ellgor on 2009-06-08
Hi,

Try using mtink from a terminal and simply put:

sudo mtink

this should get it to run properly

as an alternative you could try Qink, same again open it from a terminal and use the- sudo qink - to run it properly, hope this helps.

Regards, Ellgor

---

### Post by F W Adams on 2009-06-08
Ellgor, tried your ideas but made no difference. Mtink and Qink still gave same symptoms.

This guy seems to have had the same problem as me.
[http://ubuntuforums.org/showthread.php?t=812321](http://ubuntuforums.org/showthread.php?t=812321)

Solution:
Change the ink cartridge that you think is empty accessing by pressing the printer's red button twice. I guessed black and was right first time.

Once the printer is working again mtink can be used to check the ink levels and works fine. I reset my machine during all the messing about and you can certainly access mtlink as a normal user after that, see #4 above, lp group.

Still don't really know why mtink won't work once the printer has run out of ink and moved to red light.

---

