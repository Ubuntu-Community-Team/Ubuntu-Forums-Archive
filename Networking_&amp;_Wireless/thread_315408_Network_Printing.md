---
title: "Network Printing"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by Nhatz on 2006-12-09
can someone teach me how to print via network... ubutu-ubuntu and windows-ubuntu... thanks!:confused:

---

### Post by DWright on 2006-12-09
How is the printer connected to the Network? HP JetDirect? lpr?

---

### Post by bscbrit on 2006-12-09
We will need a bit more information.  Have you got a printer with a network interface, or do you want to share a printer that is connected to an existing computer on your network?


EDIT: DWright beat me to it - but the same question!

---

### Post by wireddad on 2006-12-10
I am trying to do the same.  I have a HP PSC 750 share through another PC that I would like to configure this Kbuntu laptop to print.  Simple as possible steps would be great.

---

### Post by Malakia on 2006-12-10
Well if you just want to share a printer and its hooked up to one of your ubuntu boxes than you can use CUPS if you want to share files also than I would recommend using Samba with CUPS.

---

### Post by wireddad on 2006-12-10
Apparently I did not include important info, the HP PSC 750 printer is shared out on a winxp pc, connected via usb.  I want to see if I can print to it.

---

### Post by FrodoB on 2006-12-10
Use the Printing Configuration Tool:

System -> Administration -> Printing


Double Click on the "New Printer" Icon to create a Print Queue:

For printers that are attached to the local machine take the "Local Printer" path and select the "Printer Port" for the printer. Complete the path.

For "Network Printer" select the radio button and the in the drop down menu select the type of printer that you need to use.

Configure the printer(s) with the desired options.


Use the Global Settings menu to Detect and Share printers:

Global -> Settings -> Detect Lan Printers

Global -> Settings -> Share Printers

If you have a printer shared on another Ubuntu machine and wish to use it go to that printer and check "Share Printers" in its "Global Settings". Printers that are shared from one Ubuntu machine will automatically become available if they are on the same network segment and you have selected the "Share Printers" and "Detect Lan Printers" on the respective machines.


The Windows side, How to print to a Ubuntu Linux Queue:

[http://solutions.brother.com/Library/pdf/ipp_W2K.pdf](http://solutions.brother.com/Library/pdf/ipp_W2K.pdf)

Debian Administration - Sharing a printer to Windows XP Clients:

[http://www.debian-administration.org/articles/425](http://www.debian-administration.org/articles/425)

Also note the Web Based Tools for configuring CUPS seems to allow printing to Windows XP clients:

[http://localhost:631](http://localhost:631)

---

### Post by wireddad on 2006-12-10
Thank you.  I will have to try your suggestions.

---

### Post by wireddad on 2006-12-11
I have attempted to install cups-pdf.  Is this what I need to print to pdf?  I do not see it in the printer choices.
 
Also, I have a printer connected to a WindowsXP machine shared out.  I would like to be able to print to this using Ubuntu.  Possible?
 
I will search the web also.

---

### Post by FrodoB on 2006-12-11
For printing to the Windows XP machine open your browser and go to:

[http://localhost:631]("http://localhost:631/")

For PDF:

Install  cups-pdf:

sudo apt-get update

sudo apt-get install  cups-pdf


Create a new printer.

Add a new printer:

System->Administration->Printing

select the &#8220;Local Printer&#8221; &#8220;PDF Printer&#8221; option

In the next step choose &#8220;raw&#8221; and then click on Queue and press forward

Do not try to change the printer name, fill in Description and location and click apply.

The printouts go into your home directory in the PDF directory.

---

### Post by wireddad on 2006-12-11
Thank you.  I will try it tonight.

---

### Post by gigaferz on 2006-12-22
hello!! im ve been looking for 3 days now about share a printer and  use printers in windows..

My question is to you wireddad, Did any of that work?

---

### Post by wireddad on 2006-12-30
> **gigaferz said:**
> hello!! im ve been looking for 3 days now about share a printer and  use printers in windows..

My question is to you wireddad, Did any of that work?


I am sorry.  I have not had the time to mess with it yet.  :(

---

### Post by wireddad on 2006-12-31
Ok, was able to install the pdf printer but not the printer connected to the winxp machine.  I am not sure I understand the options in [http://localhost:631](http://localhost:631) either.  :(

Just for clarification, I have a HP PSC 750 connected via usb on a winxp machine that is shared out.  I can print to it through winxp on other machines.  It is not setup for IP printing directly.

---

### Post by wireddad on 2007-01-02
It works!!

Followed the directions here: [http://www.idevelopment.info/data/Unix/Linux/LINUX_PrintingWindows2000FromRedHatLinuxSMB.shtml](http://www.idevelopment.info/data/Unix/Linux/LINUX_PrintingWindows2000FromRedHatLinuxSMB.shtml)

I was able to print to a printer shared off of a winxp machine through Ubuntu.  :-D

---

