---
title: "Canon LBP-6000, not recognised by Ubuntu"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by etsah57 on 2011-03-07
I've just bought a Canon LBP-6000 printer. I have 2 PC's in our home. Ubuntu 10.10 on mine and Windows XP on the family PC. The new printer works great in the Windows PC but when I plug it into mine, Ubuntu does not have a driver for it. I get the new Printer window, I choose the brand, Canon, then it offers choices of models but mine does not come up. I tried installing a different model driver but the printer does not print. It places the file in the print que but does nothing. What do I do?

---

### Post by Newbie2910 on 2011-03-07
Did you go to Canon's website and try downloading a Linux driver for it?

---

### Post by etsah57 on 2011-03-07
They do not list drivers for linux for the 6000

---

### Post by Newbie2910 on 2011-03-07
Try here:

[http://downloadnew.org/drivers/printer/canon-monochrome-lbp6000-linux-printer-driver-516223.html](http://downloadnew.org/drivers/printer/canon-monochrome-lbp6000-linux-printer-driver-516223.html)

See if this works for you.

---

### Post by Old_Man_Unix on 2011-03-07
Please see here:

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

I believe the driver you need is the CAPT 2.2 so follow the instructions for installing that version.

I realize this is unsatisfying.  The procedure reminds me of UNIX sysadmin  instructions which were bad enough in the day but are not acceptable on a "consumer" desktop - however, you seem to have no choice at this time.

---

### Post by heavy metal on 2011-03-09
Did you check the Malaysia Canon Website???
I Think there's a driver for your canon printer! Check here:
[http://support-my.canon-asia.com/P/search?model=LBP6000&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-my.canon-asia.com/P/search?model=LBP6000&menu=download&filter=0&tagname=g_os&g_os=Linux)

or here:
[http://www.canon.com.my/](http://www.canon.com.my/)

---

### Post by etsah57 on 2011-03-09
Finally was able to download the file [CAPT_Printer_Driver_for_Linux_V220_uk_EN.tar.gz]("http://files.canon-europe.com/files/soft40567/software/CAPT_Printer_Driver_for_Linux_V220_uk_EN.tar.gz")
 from [http://software.canon-europe.com/download.asp](http://software.canon-europe.com/download.asp)
Opened a file to print and it is sitting in the 'document print status (my jobs)' and saying that it is processing, but not actually printing!
frustration is beginning to set in.

---

### Post by nomko on 2011-03-09
> **etsah57 said:**
> frustration is beginning to set in.
 
Canon is well known for their bad Linux support.
You were better off with a HP device or an Epson device.
 
Can you do this:
- open a terminal
- type in **lsusb**
- place the output here.

---

### Post by etsah57 on 2011-03-09
Sorry, I need a bit more explanation
- open a terminal
- type in **lsusb**
- place the output here (do I type this line in, or, what is the output?)

---

### Post by nomko on 2011-03-09
> **etsah57 said:**
> Sorry, I need a bit more explanation
- open a terminal
- type in **lsusb**
- place the output here (do I type this line in, or, what is the output?)
 
If you give that command in the terminal, then it comes with the output of that command. That output you have to copy (select the text and rigthclick > copy) and paste it here.

---

### Post by etsah57 on 2011-03-09
After I typed in lsusb a whole lot of lines followed, all beginning with bus. The one for the canon was:
Bus 001 Device 001: ID 04a9:271a Canon, Inc
I copied and pasted it at the end of all the other lines and then it said
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
etsah57@etsah57-KZ208AA-ABG-m9385a:~$

---

### Post by nomko on 2011-03-09
> **etsah57 said:**
> After I typed in lsusb a whole lot of lines followed, all beginning with bus. The one for the canon was:
Bus 001 Device 001: ID 04a9:271a Canon, Inc
I copied and pasted it at the end of all the other lines and then it said
No command 'Bus' found, did you mean:
Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
[EMAIL="etsah57@etsah57-KZ208AA-ABG-m9385a:~$"]etsah57@etsah57-KZ208AA-ABG-m9385a:~$[/EMAIL]
 
 
The output of the command **lsusb** is a list of USB devices connected **AND** turned/powered on which can be found by Ubuntu. None of the lines are either a command or executable link. It is just a listing. 
 
You copied the line for you Canon printer and pastes it in the terminal which gave you the error message.
 
You need to copy the list (=output of the command) and paste it here on the forum.
 
 
Anyway, there is a driver for your printer and it can be found here: [http://support-au.canon.com.au/P/search?model=LASERSHOT+LBP6000&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-au.canon.com.au/P/search?model=LASERSHOT+LBP6000&menu=download&filter=0&tagname=g_os&g_os=Linux)
 
Did you tried this driver?

---

### Post by etsah57 on 2011-03-09
etsah57@etsah57-KZ208AA-ABG-m9385a:~$ lsusb
Bus 002 Device 003: ID 046d:0a0c Logitech, Inc. Clear Chat Comfort USB Headset
Bus 002 Device 002: ID 05af:0809 Jing-Mold Enterprise Co., Ltd Wireless Keyboard and Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 04a9:271a Canon, Inc. 
Bus 001 Device 007: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 001 Device 006: ID 147a:e018 Formosa Industrial Computing, Inc. eHome Infrared Receiver
Bus 001 Device 005: ID 15a9:0004 Gemtek WUBR177G
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Yes this is the driver I down loaded

---

### Post by nomko on 2011-03-09
You're rigth about this line:
> Bus 001 Device 008: ID 04a9:271a Canon, Inc. 
 
My question for you is: how old is your printer?
Because Ubuntu recognizes it as a Canon, but not the model.

---

### Post by etsah57 on 2011-03-09
Brand new, bought it a week ago

---

### Post by nomko on 2011-03-10
> **etsah57 said:**
> Brand new, bought it a week ago
 
That might be the problem here. I think your printer is much too new for Ubuntu. That it works for Windows is understandable, the correct drivers for Windows are supplied with it. This is still the main rfeason for many Linux users not to buy hardware from Canon, poor support under Linux.
 
What you can try is install the Windows driver using Wine. I don't know exactly how to do it, but i've seen here on this forum that this migth work.

---

### Post by etsah57 on 2011-04-17
Problem solved! Got rid of Canon printer and went back to Samsung which was immediately recognised by Ubunu.:D

---

### Post by sikkinixx on 2011-04-30
hi people! i have the same problem... i also tried to follow the below links without any success... :confused:

[http://forums.linux-foundation.org/read.php?25,13053](http://forums.linux-foundation.org/read.php?25,13053)

[http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/](http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/)

is there anyone who could help me step by step to install this printer on my Ubuntu 11.04? 

many thanks!

---

### Post by albarrio85 on 2011-05-19
hi Ubuntu Forum:
i have the same problem with CANON- I-SENSYS LBP6000B
ON UBUNTU 10.10

---

### Post by Alekamos on 2011-11-25
me too,same problem on ubuntu 10.10.
I successeful inst[COLOR=black]alled the driver,(i converted the rpm file to a .deb using alien so i avoi[/COLOR]d all the dependences problem)..but now when i tried to print it doesn't!

---

### Post by flntobi on 2011-12-22
Hi,

there is a solution:

[http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/](http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/)

simply download script and execute as described. Worked for Ubuntu 11.4 - 64 bit.

Good luck!

---

