---
title: "Network UNCLAIMED for built in Dell Latitude C Port 2 ethernet (3com 3c920)"
date: 2014-08-27
forum: Networking &amp; Wireless
---

### Post by arivee on 2014-08-27
I have an ancient computer - a PIII based Dell Latitude CPxJ attached to a C Port 2 docking station.  I believe I installed Dapper on it and upgraded it up to Intrepid.  I  tried learning Linux on the machine but also used it as file and print  server.  It has a Xircom ethernet/modem card in the PCMCIA slot but I  connected it to my network using the built in ethernet port on the  docking station (3COM 3C920 10/100 ethernet NIC).

  
In the course of my messing around with Ubuntu - I was ambitious  enough to try setting up a fax service on the machine - and messed up  the whole shebang so much so that my update manager would never pop up  and anything I minimized never went to the taskbar.  Never having upgraded from Ibex, my system was in stasis until a  couple of weeks ago.  I tried manually starting update manager and  succeeded.  Updated some files and after reboot, I lost my ethernet  connection.  Not even the Xircom was firing up.


  I chalked it up as the system was so compromised, I probably needed  to reinstall the OS - I went back to my archives and found my old Dapper  CDs and tried to reinstall.  Nothing - hopefully it was just the media -  but since I was going to reinstall might as well use one that is apt  for such an old machine.  I installed Puppy - initially, I was working  off the built in NIC but for some reason, that connection got lost.   Puppy recognized the Xircom card at least and I was able to work from  there. 

  
I was willing to live with the Xircom until I discovered that the  connection was not persistent.  I tried transferring a 10gB file and it  stopped before it reached 1gB and appeared that it was disconnected.

  I said - maybe it's Puppy - let me try Ubuntu again - after a few  burned discs - I used the alternative ISO and was finally able to make a  clean install of Precise.  It still only recognizes the Xircom but not  the built in NIC.  lshw shows that the ethernet is UNCLAIMED.  I  manually added the 3c59x module to startup and I know it loads because I  see it when I lsmod.  I checked the blacklist as well and the 3c59x  driver was not in there.  I have not changed anything in the BIOS, specially the IRQ settings as well.

  
So to recap - IRQ is ok, 3c59x module is loaded, blacklist is negative  but ethernet is still showing unclaimed.  I have the linux drivers and  tried installing but got an error that said the driver was not built for  the Kernel (3.0.2-67).  I tried the ubuntu manual which talked about  adding vx, ep or ie but could not find those drivers.

  
Apologies for the long story - but the question is - is there anything else I can do?

---

### Post by mörgæs on 2014-08-27
Hi, welcome to the fora.

First step is using the latest software. I would consider a Pentium 3 too old for any useful purpose, but if you want to run something Lubuntu 14.04 or [Bodhi Linux]("http://www.bodhilinux.com/") are good choices. Installing with wired connection is the way to go.

---

### Post by arivee on 2014-08-28
Thanks for the welcome!

D'oh!  I did not specify it but I am using lubuntu 12.04.  I am trying to  resurrect the 3com wired connection I have - although, the Xircom is  working - it still has persistency issues.  I have searched the forum high and low but most of the unclaimed issues seem to be driver related - drivers that were not included in the base kernel (did I say that right?).  I have seen a few folks with unclaimed wired ethernet issues but the theme is common with the wireless issues - i.e. new drivers/not included drivers.

I am trying to keep this laptop alive for both sentimental and educational purposes.  I dunno about useful purpose - but it was performing well when I use it as a print and file server.

---

### Post by mörgæs on 2014-08-28
Again, first you should reinstall using a supported operative system like the two posted above. Lubuntu 12.04 is out of support.

---

