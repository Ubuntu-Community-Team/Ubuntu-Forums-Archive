---
title: "setting up network printer"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by Doby on 2008-06-17
I have a hp pavilion dv2000, with ubuntu 7.10 installed and xp running in virtualbox.  I need to be able to connect to a network printer at work.  The printer is a hp laserjet 2100tn.  Is there anyone out there that can help me?

---

### Post by rickyjones on 2008-06-17
> **Doby said:**
> I have a hp pavilion dv2000, with ubuntu 7.10 installed and xp running in virtualbox.  I need to be able to connect to a network printer at work.  The printer is a hp laserjet 2100tn.  Is there anyone out there that can help me?

I think you'll need to provide some more information here.

How is the printer connected to the network? Is it using JetDirect? Is it connected to another PC and then shared on the network? Is it directly connected so it has it's own IP address? Is it using RAW or LPR?

Thanks,
Richard

---

### Post by Doby on 2008-06-19
The printer is connect directly to the network with its own ip address, and i believe it is lpr.

---

### Post by rickyjones on 2008-06-19
Then I would think you should be able to use the printer administration link from the Admin menu (I think, don't have Ubuntu in front of me) to set up the network printer option. Should be able to just throw in the IP and select LPR and have it work.

Someone else may be able to give more exact directions. My original reply was mainly to get more information out that the gurus would need to see. :P

Thanks,
Richard

---

### Post by Doby on 2008-06-19
I figured it out.  I just had to use the hp laserjet 4 drivers instead of the drivers for the printer.  I hope this helps anyone who might have the same type of problem, just try different drivers till it works!!!!  Might suck but I still love ubuntu

---

