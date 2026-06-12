---
title: "Beginner Printer"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by keats4 on 2010-10-28
Hello all

I am an absolute beginner to Ubuntu, was suggested by a friend. I have this computer installed on my office network.  Needless to say I've attached to the internet. I have a network printer located at 192.168.168.211 on my network. Its a Kyocera 3830N. How do I install the driver and make it see the location so I can print from Ubuntu. Not even sure IF there is a driver for this printer compatible with linux.

Misc info: I can see the status of the printer from Firefox if I type in the IP address.

Thanks in Advance 
Keats4

---

### Post by ArgusVision on 2010-10-28
Open firefox, and go 127.0.0.1:631.
This should open up the CUPS mangagement on your PC.
Select the "Adding Printers and Classes"
Click on Add Printer.
Follow steps.

---

### Post by garuda10 on 2010-10-28
The above reply might work, but recently I've added a network printer by clicking on System, then Administration and then on Printing. There is an option called network printer. Just enter the IP of the printer and it should find it... I use Ubuntu 10.10 BTW and have no idea about the rest of the versions...

---

### Post by ArgusVision on 2010-10-28
Either method should work. You might want to try garuda's first.
Mine just goes more directly to CUPS which is what should be managing your printers.

---

### Post by Boppa on 2011-12-16
I'm trying to add a printer to my computer, when I did this, I got this:

Firefox can't establish a connection to the server at 127.0.0.1:631.

Any suggestions?

---

