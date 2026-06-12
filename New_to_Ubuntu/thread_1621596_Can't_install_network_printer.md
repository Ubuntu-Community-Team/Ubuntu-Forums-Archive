---
title: "Can't install network printer"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by dagelm on 2010-11-14
Hi--I'm having trouble installing my Brother HL-5370DW printer with Ubuntu 10.10. It's wirelessly attached to my home network (stand alone, not through another computer/server. I start installing it through  system-admin-printers.  The printer shows up fine under "network printers."  But when I proceed to install it, it starts searching for drivers. The drivers it comes up with are all for other printer brands (Ricoh, Oki, etc.). So I went on the Brother website and downloaded and installed (using the Software Center) a "LPR" driver and a "CUPS wrapper" driver for my printer.  Install of both went fine; now they show up as installed software.  Went back to the printer setup and tried to add the printer, but no luck.  Same as before--list of non-Brother drivers. How do I get it to "see" the Brother driver(s) I installed from the website?  Thanks!

---

### Post by migs73 on 2010-11-14
Welcome to the forums!

Try this tutorial; [http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)

It is a bit old but still works (did for me and another recently).

Best of luck.

Mike

---

### Post by dagelm on 2010-11-15
Thanks, Mike!  That got me much of the way there.  The printer is now installed.  Test page (and print jobs from other programs) queue up as expected, but still the printer is not seen as "connected" (even though it shows up on the network printer list if I'd begin to add it as a new printer from system>admin>printers).  I'll keep trying....

---

### Post by jtarin on 2010-11-15
Are you networked with other Linux Operating systems or is there a Windows OS on your network your sharing?

---

### Post by dagelm on 2010-11-15
Ah, working now!  Finally found on the Brother support site that I needed to change the URI from the "usb...." one that showed up after install to "socket://<IP address of my printer>".  That did the trick.

BTW: yes, the printer is shared by two other Windows machines on my network.

Thanks to all!

---

