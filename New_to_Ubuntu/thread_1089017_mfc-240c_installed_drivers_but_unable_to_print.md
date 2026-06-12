---
title: "mfc-240c installed drivers but unable to print"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by jumpingjaxs on 2009-03-06
hi, im new to forums and ubuntu/linux - please redirect me if im in the wrong spot, not posting correctly or something. thx

i need to set up all-in-one brother printer(mfc240) on ubuntu 8.10.

i reviewed instructions from various sources, but especially the brother website, [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html), and also this forum tutorial: [http://ubuntuforums.org/showthread.php?t=486675](http://ubuntuforums.org/showthread.php?t=486675).

i followed the steps to download and install the drivers including the preparation procedures, added my printer, and everything seemed to go fine (no obvious errors or glitches and whatnot). 

however, attempts to print a test page are unsuccessful (status stays on processing, and printer never receives the job). 
when i go to [http://localhost:631/printers](http://localhost:631/printers) it shows my printer as existing there but says 'Printer not connected; will retry in 30 seconds'.

what have i missed or done wrong?
do i need to uninstall the drivers and start over -if so please guide me how to do this (uninstall is on the brother troubleshooting webpage but i dont understand the exact commands for terminal)? 

really appreciate some guidance - have some projects due soon and having a functional printer would help so much
thx

---

### Post by avtolle on 2009-03-06
You may install the proper driver for the printer through Synaptics; search for Brother.

Yes, you will need to remove the drivers you installed via the Brother web-site. What is giving you trouble?

---

### Post by jumpingjaxs on 2009-03-07
thx..

the brother website says to 'Uninstall the cupswrapper driver' use 
'Command : sudo dpkg -P (driver name)'.

how do i identify the actual driver name, and do i type it in the parentheses or without?

---

### Post by plucky on 2009-03-08
> **jumpingjaxs said:**
> thx..

the brother website says to 'Uninstall the cupswrapper driver' use 
'Command : sudo dpkg -P (driver name)'.

how do i identify the actual driver name, and do i type it in the parentheses or without?

From a terminal ```
dpkg  -l  |  grep  Brother
``` and see what that gives.

> do i type it in the parentheses or without?

Without

Good Luck

---

### Post by jumpingjaxs on 2009-03-09
here is the output from that command:

jaxs@jaxs-desktop:~$ dpkg -l |grep Brother
ii  mfc240ccupswrapper                         1.0.1-1                                 Brother CUPS Inkjet Printer Definitions
ii  mfc240clpr                                 1.0.1-1                                 Brother lpr Inkjet Printer Definitions


doesnt this output show they are installed correctly? 
( please see step 4-5 at [http://solutions.brother.com/linux/en_us/instruction_prn1a.html](http://solutions.brother.com/linux/en_us/instruction_prn1a.html) )

i just realized the brother troubleshooter suggests to reinstall driver only if 'installation failed with a message about it' 
.. i didnt get any error msgs and things seemed to go smoothly when i installed. 

if my drivers are installed correctly, what other circumstances could cause my problem?


pls and thx for your continued guidance

---

### Post by plucky on 2009-03-09
> ii mfc240ccupswrapper 1.0.1-1 Brother CUPS Inkjet Printer Definitions
ii mfc240clpr 1.0.1-1 Brother lpr Inkjet Printer Definitions



The drivers are installed.Plug in the printer using the USB port and power on.Go to **System > Administration > Printing** and delete the printer it previously found,then select new printer.

It should then search and find your printer.It will then search for drivers,make sure you select the correct driver.

Also check the correct paper size is selected as that can cause it not to print.


Good Luck

---

### Post by jumpingjaxs on 2009-03-09
i deleted the printer and added it again. it still says 'printer may not be connected' when i try a test page.
can you help me figure out what im missing or have incorrect? this is what i did:

i searched for new printers, chose 'lpd/lpr host printer' as the device. selected 'local host' for location, chose 'Brother' from the database, chose model mfc240c and then selected the driver. the uri address in the settings says lpd://localhost
the printer is definately plugged to the usb port and powered on. i have rebooted everything more than once.

---

### Post by plucky on 2009-03-10
Is it plugged into a USB hub?

I am pretty sure the URI should be USB://Brother/MFC-240C . Perhaps you could delete the printer and add again,but try IPP instead of LPR/LPD and see what that does.

I think LPD/LPR is for a Network printer.


Good luck

---

