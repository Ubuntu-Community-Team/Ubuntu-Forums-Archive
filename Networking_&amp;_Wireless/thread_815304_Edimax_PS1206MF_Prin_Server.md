---
title: "Edimax PS1206MF Prin Server"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by dave_didlydodo on 2008-06-01
I'm just experimenting with 8.04 at the moment and am very impressed so far (Linux newbie). But one thing I can't work out how to do is print via my Edimax PS1206MF print server. I know the following:

[LIST]
[*]That the Edimax supports LPR and IPP printing
[*]That I have the right printer drivers (HP PSC1210 All-in-One), as the printer works fine when connected via USB
[*]The print server's (fixed) IP address
[*]that my PC can 'see' the Edimax server as I can connect to its setup pages via Firefox 
[/LIST]

I've tried various of the 'add printer' options but none appear to work. Help!!

---

### Post by the4thamigo_uk on 2009-11-17
**Re: Edmax multifuctional printer manager under wine** 			
 			 			 		   		 		 		I had the same problem and I have found a solution without the need to install any drivers.

(1) Open System->Administration->Printing
(2) On the 'Printer Configuration' window click New->Printer
(3) On the 'New Printer' window expand Network Printer->LPD/LPR Host or Printer
(4) Type the ip address into the 'Host' field
(5) Type 'lpt1' into the 'Queue' field Click Forward and wait
(6) On the 'Choose drivers' page ensure 'Select printer from database' is selected and find your printer in the list and click Forward

hope this helps...

---

### Post by fubar65 on 2010-09-05
this helped me, I have my printers setup on an Edimax PS3205U print server and both printers would pause after a job was sent, the test page would print but there would be an error and the printer was paused, using this method works perfectly.

Thanks very much!

---

### Post by yanaek on 2011-12-10
I have PS1206U (usb, lan) edimax print server and when I try to add it with method mentioned above ubuntu just hangs on "Searching for drivers"

I can verify connected print server, Ubuntu finds AppSocket JetDirect, lpd/lpr and ipp connections.


EDIT: solved, I had to use LPD/LPR method with queue name "lp"
I did it through CUPS web interface and chose driver manually (gnome printer wizard was hanging up on Searching...)

lpd://192.168.2.101/lp

---

