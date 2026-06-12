---
title: "Printing from Win2K to Ubuntu 7.10 shared USB printer"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by IddyBittyBugs on 2008-05-19
I have an Ubuntu 7.10 machine with a Samsung ML-2250 printer connected via USB.  It works fine so I have shared it, and I am able to print from other Ubuntu machines on the network using cups.  I need to share the printer with some Windows boxes, and my first test box has Win2K SP4.  Win2K cannot find the printer at all when attempting to Add A Printer in Windows.  I suspect my path may be incorrect; right now I'm using //bob-desktop:631/printers/ML-2250.

I have samba installed (and hopefully configured correctly) but still cannot find the printer from Win2K, even after re-booting both machines.

Anyone know how I might be falling through the cracks?
:confused:

---

### Post by IddyBittyBugs on 2008-05-21
Anyone at all?

---

### Post by superprash2003 on 2008-05-21
whats with the :631?? you dont need that..

---

### Post by IddyBittyBugs on 2008-05-28
I believe it's the specific port to print to on the remote machine:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu?highlight=%28printing%29%7C%28network%29](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu?highlight=%28printing%29%7C%28network%29)


But I cannot see anything from the Win2K box when trying to setup a network printer.  Do you recommend I leave the port out?  Any help with this is greatly appreciated, as I'm stuck.

---

### Post by IddyBittyBugs on 2008-05-28
superprash2003,

I followed your link and steps and I can see the printer using Windows Explorer.  But Win2K network printer setup will not work.  I get "The server on which the printer resides does not have the correct printer driver installed.  If you want to install the driver on your local computer, click OK."

Now for the fly in the ointment.  The Samsung driver has never worked for Win2K, which is why I want to use an Ubuntu machine as a print server.  The Samsung driver for Win2K just prints page after page of ascii text, no matter what you want to print.  I think Samsung focused all their energy on XP.

How do we tell Windows to use whatever cups is using?

---

