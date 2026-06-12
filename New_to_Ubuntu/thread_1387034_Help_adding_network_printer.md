---
title: "Help adding network printer"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by japhyr on 2010-01-21
Hello,

I am trying to add an HP 4050n laser printer, which is connected to a router, to an Ubuntu 8.04.3 desktop.  The desktop is connected to the same router.  The printer does not show up under System>Administration>Printing>New Printer, but I have the printer's ip address and I can telnet to the printer.

I have tried going to New Printer, and choosing "AppSocket/ HP JetDirect".  I enter the printer's ip address under host, and the port number is automatically listed as 9100.  On the next screen, "HP" is highlighted automatically, which makes me think the desktop is seeing the printer.  On the next screen it has "Laserjet 4200" highlighted; changing this to "Laserjet 4050" does not seem to work, nor does leaving it at Laserjet 4200.  When the printer is installed, the Device URI that shows is "hp:/net/hp_Laserjet_4200?ip=192.168.3.75".

Any suggestions about where I am getting off track?

---

### Post by bamim2 on 2010-01-21
For an HP printer you may want to use the HPLIP. Install & open that & it will walk you through setting up your printer. 

To manually setup your printer using what you already have, try clicking on "Network/Ethernet/Wireless network (direct connection or JetDirect)".

Click on "Show Advanced Options".

Check the "Manual Discovery" check box near the bottom. 

Enter the IP address of the printer (leave the port info) and click "Next". That should do it. 

If that doesn't do it, then you may want to go to the HP site & download the latest printer driver set. That will have to be installed from a terminal though.

---

### Post by japhyr on 2010-01-21
> To manually setup your printer using what you already have, try clicking on "Network/Ethernet/Wireless network (direct connection or JetDirect)".


I would like to try doing this manually if I can, rather than installing HPLIP.  Where do I find the Network/Ethernet/Wireless options?  Is that in a printer configuration menu?

---

### Post by japhyr on 2010-01-25
I found out that hplip was already installed on my computer.  Using hplip, I was able to enter the ip address of the printer.  The printer seems to install, except my desktop keeps thinking it's a 4200 instead of a 4050.  However, no pages are going to the printer when I try to print.

I tried installing the latest version of hplip, but after answering the questions at the hplip site it was about to install the same version I already have installed.

Any further suggestions?

---

### Post by matchett808 on 2010-01-25
It might be able to function through the ipp protocol or lpd protocol, try opening:
[http://127.0.0.1:631](http://127.0.0.1:631) in your browser (this is the cups adminitration panel)
when I tried to connect my laptop to a similar (4050, no idea what variant) printer (through a third party -not hp- paralell to lan device) it did not show up in administration --> printing but did through cups....

.....also try manually adding it like this:
lpd://192.168.1.6/lpt1 into add printer ---> lpd/lpr host or printer and enter lpt1 into the que (this is if it is shared through the parallel port of the printer - however check your routers manual as it may specify a printer que to use.......also is it directly connected to the router? or does it go through a server first???)

also check if an error message is associated with the no pages going to print.....(this can be the case when the incorrect paper size is used...like legal instead of a4)

---

