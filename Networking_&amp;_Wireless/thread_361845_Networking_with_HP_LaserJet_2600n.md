---
title: "Networking with HP LaserJet 2600n"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by ShirishAg75 on 2007-02-14
Hi all,
       I have installed ubuntu 6.06 at a friend's LAN. He just 3 machines with LaserJet 2600n (a network printer) being at 192.168.1.15 . Now I'm not able to set it up right. Can somebody help me?

Below is the extract of the output of the test page under Windows XP

Congratulations!

 If you can read this information, you have correctly installed your HP Color LaserJet 2600 on G1

The information below describes your printer driver and port settings.

Submitted Time: 8:09:50 PM 2/14/2007
Computer name: G1
Printer Name    : HP Color LaserJet 2600n
Printer Model    : HP Color LaserJet 2600n
Color Support   : Yes
Port Name(s)    : HPColorLaserJet2600n
Data format     : IMF
Share name     : HPColorL2600
Location:
Comment:
Driver Name     : IMFNT5.DLL
Data File         : SDhp2600.SDD
Config file        : SDMT5UI.DLL
Help File          :  SDhp2600.HLP
Driver version   : 6.00
Environment     : Windows NT x86
Monitor           :  HP CLJ2600n LM
Default datatype : RAW

   Then gives a list of additional files used by this driver. If something else is required please lemme know :(

   Now what settings should I give in Add printer dialog box, I did try some stuff but it didn't work out. So if somebody can point me in the right direction :)

After going to System > Administration > Printing

  One gets Add a printer >

      Then set up Printer 

       Printer Type :- Local  or  Network  .  Checking on Network gives  4 options  :-

a. CUPS Printer  (IPP)
b. Windows Printer (SMB)
c. Unix Printer        (LPD)
d. HP JetDirect    

    don't know any better hence used d. HP JetDirect. Invoking this I come up with another dialog box  :-

Host :- 
Port :- 1900 or 9100 (don't remember which but comes by default)

    Now don't know which hostname to put? Should it be HPColorLaserJet2600n or something else? Some clarity here guys, anyway putting something here something like G1 I get a list of companies through which I select HP  & the model Color LaserJet 2600n
       The driver which it selects if I select the above model is f002hp
Again it asks me for 
         Name :-
     Location :-

        Name is easy as anything can be given but location, tht one is hard one for me to crack. 

 A little bit of searching before revealed one can also look at [http://localhost:631/admin/](http://localhost:631/admin/) to know which printers it shows 2 printers in the network, one as Canon & the other as Epson, while the 2nd one is showing right, the 1st is being mis-read as Canon while he has HP. 

          Any help or pointer in the right direction would be helpful :) It has been very learning experience till now :)

---

### Post by jaripetteri on 2007-03-07
you probably already find the solution but anyway. Print network info sheet from printer control panel and use those details. I just installed my brand new 2605dn and use ip address found on that sheet.

---

### Post by Mr. C. on 2007-03-07
The Location and Comments are simply for users for identifying printers while searching for printers.  Consider that offices may have dozens or more printers, on various floors, so Location might be "4th floor, West", and Comments might be "Accounting Dept." or anything one finds useful.

Many network printers have various built-in printing and networking protocols.  There the UNIX LPD, HTTP, Jetdirect, FTP-based printing, old AppleTalk, etc.  To complicate things further, printers may have different printing languages (eg. Postscript, PCL).  You choose the type of network connection and printer language that suits your environment, and has the best output for your needs.

MrC

---

### Post by KernelKen on 2007-03-26
Printer Type :- Local  or  Network  .  Checking on Network gives  4 options  :-

a. CUPS Printer  (IPP)
b. Windows Printer (SMB)
c. Unix Printer        (LPD)
d. HP JetDirect    

    don't know any better hence used d. HP JetDirect. Invoking this I come up with another dialog box  :-

Host :- 
Port :- 1900 or 9100 (don't remember which but comes by default)


 d. HP jetDirect is correct.


Port is the 9100.

This should allow you to print.

---

### Post by ShirishAg75 on 2007-04-02
But this one is Laserjet , JetDirect & LaserJet are different are not they? and did you specifically use the LaserJet 2600n or some other printer?

---

### Post by NymDeVir on 2007-05-08
i can´t get my 2600n to print at all....

i have printed IP config from the printer and used the information there to fill in the blanks in the properties dialogue.  now when i go to print the printer pauses and has the message 

¨Paused:/usr/lib/cups/backend/socket failed¨

location is 192.168.0.103 just like the print-out
host name is NPIC21369 just like the print-out
port is 9100
used HP jetDirect, raw connection just like my other computers that print on the printer
usded the foo2hp driver

---

### Post by jeroen.straver on 2007-05-16
Hi there,

Just read this topic,
Used the printing dialog to add a my HP Laserjet 2600n.

Selected option d. (HP Jet direct) in network printing

Entered the IP address of my printer and used the default port (9100).
I then selected my printer and used the recommended driver. It works like a charm.

---

### Post by phishinphree on 2008-01-28
If its any help, Here is how I setup the 2600n in kubuntu 6.10 and cups 1.3.2 (default version)

1) goto [http://localhost:631/](http://localhost:631/) then the admin tab and new printer

2) Name, location, desc is anything you want.  name cannot have spaces and some other chars that the web interface tells you about; hit next.

3) Device: HP Printer HPLIP.  hit next.

4) Device URI: socket://192.168.1.200.  replace 192.168.1.200 with the ip address of your printer. (the test page that prints from the menu system on the front of the printer will tell you this.  I recommend using a static address or setting up a static DHCP address on your router so your printer's address won't change.) hit next

5) choose HP.  hit next.

6) choose HP Color LaserJet 2600n Foomatic/foo2hp hit add printer.

Print a test page from the interface.  Additionally, the printer status should show as "idle, accepting jobs"

This is what works for me.  Maybe it will work for you too.

---

### Post by Serpentus on 2008-02-03
@ phishinphree

Thanks a lot!!!!! It worked like a charm!!!!! =D

---

### Post by rockprincess on 2008-06-21
> **phishinphree said:**
> If its any help, Here is how I setup the 2600n in kubuntu 6.10 and cups 1.3.2 (default version)

1) goto [http://localhost:631/](http://localhost:631/) then the admin tab and new printer

2) Name, location, desc is anything you want.  name cannot have spaces and some other chars that the web interface tells you about; hit next.

3) Device: HP Printer HPLIP.  hit next.

4) Device URI: socket://192.168.1.200.  replace 192.168.1.200 with the ip address of your printer. (the test page that prints from the menu system on the front of the printer will tell you this.  I recommend using a static address or setting up a static DHCP address on your router so your printer's address won't change.) hit next

5) choose HP.  hit next.

6) choose HP Color LaserJet 2600n Foomatic/foo2hp hit add printer.

Print a test page from the interface.  Additionally, the printer status should show as "idle, accepting jobs"

This is what works for me.  Maybe it will work for you too.

you sir, are amazing :D 

works like a charm!

---

