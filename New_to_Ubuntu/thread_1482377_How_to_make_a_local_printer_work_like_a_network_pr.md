---
title: "How to make a local printer work like a network printer"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by RedOctober on 2010-05-13
[COLOR=Navy]***Environment:*  **[/COLOR]

10 Ubuntu 9.04 PCs, all latest updates, all using rdesktop to remote into one MS 2003 Server.  5 WinXP PCs remoted into the same server.  Several networked printers already installed via Cat5/RJ45 cables to their network port.

1 Ubuntu PC has a Dell Laser Printer 1110 connected directly to it using a USB cable. The printer doesn't have an RJ45 (Cat5) port.

[COLOR=Navy]***Situation:***[/COLOR]

Ubuntu recognized the printer immediately and connected and configured it correctly.  I can print locally.

[COLOR=Navy]***Goal:***[/COLOR]

I want to be able to print to this printer from other Ubuntu PCs and other Windows XP.  This means I'd like it to be listed in the list of printers available when people are in a remote session and try to print something.

***[COLOR=Navy]Question:[/COLOR]***

How do I achieve my Goal?  (Thanks in advance for any help you can provide)

---

### Post by oldsoundguy on 2010-05-13
Go into your printer set up utility and make the printer available to the network.  Works for me.
(some re-booting may be required)
I share 5 printers (including 2 parallel port printers) between 3 workstations and 6 computers (4 Linux and 2 XP), and ALL of the printers are plugged into computers, not a printer hub.

---

### Post by howefield on 2010-05-13
> **RedOctober said:**
> How do I achieve my Goal?

Go to System > Administration > Printing and then select Server > Settings and set as required,. 

Then set up the shared printer in the other networked computers.

---

### Post by RedOctober on 2010-05-13
Hi guys, I'm only part way there.  I went into the Ubuntu machine and clicked: System->Administration->Printing  Then I selected Server->Settings and shared the printer.

On the MS 2003 Server I went into Control Panel->Printers and Faxes->Add printer-> Internet printer-> URL [http://server_name:631/printers/PRINTER_NAME](http://server_name:631/printers/PRINTER_NAME), replaceing server_name with the IP address of the Ubuntu machine and PRINTER_NAME with the printer name.  Now comes the problem.  The next screen asks me to select the printer brand and model.  Dell Laser Printer 1110 is not listed, so I select "Have Disk" and point to the CD drive that contains the CD that has printed on it "Dell Printer Drivers", and, there is no .INF file on the CD so the process cannot continue.  Thinking that Dell may have a printer driver in .INF form, I downloaded the exact  correct printer driver from the Dell web site (it's an .exe). and guess what.. it's the same as whats on the CD. ... nothing usable from the point of view of installing the printer driver.

What is the next step?  My printer is not appearing in the printer choices list when I am remoted in.  (Simply sharing this printer, and allowing printing from Internet, did not make it appear in the printers list)  So I figured I have to install something.

Any help would be greatly appreciated.

---

### Post by cariboo on 2010-05-13
If you run the Dell software, it should ask you where the printed is connected. I'm not familiar with MS 2003 server, but it can't be all the different from XP/Vista/Win7.

---

### Post by RedOctober on 2010-05-14
Ok, problem solved.  I copied the contents of the printer driver CD to the network, then I connected the printer directly to the server.  I ran the install .exe file from the network drive and it did the install.  This enabled MS 2003 Server to "understand" what printer I was connecting to.  So, then I disconnected the printer from the MS 2003 Server box, back to the Ubuntu machine.   Then I did an Add printer, on the network server, and of course, this time when I picked "Dell".. .the Dell laser printer was listed.  So, now, the Dell Laser Printer 1110, connected directly to the Ubuntu box is listed as "http: .. etc".   I select it as the printer, and IT WORKS!

Yay Ubuntu!

---

