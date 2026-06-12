---
title: "CUPS Problem (printing)"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by jlbr21 on 2009-06-09
Hello,
I have an HP Deskjet F4280 printer, and it's always worked fine, but now, maybe due to some upgrade, change of CUPS version, who the heck knows, it started to give problems. I was then getting the following error message:

/usr/lib/cups/filter/foomatic-rip failed

So I went and reinstalled ghostcript as I read in some OpenSuse forum thread, then the message disapperead, but the printer still gives me some problems, namely, it won't print certain documents or images.

Additionally, when I run sudo hp-setup, I get the following:


> juanluis@juanluis-laptop ~ $ sudo hp-setup

HP Linux Imaging and Printing System (ver. 2.8.7)
Printer/Fax Setup Utility ver. 7.2

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: PyQt not installed. GUI not available. Exiting.
warning: PyQt init failed. Reverting to interactive mode.
(Note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.)


--------------------------
| CHOOSE CONNECTION TYPE |
--------------------------

  Num.        Connection  Connection Type Description             
              Type                                                
  ----------  ----------  ----------------------------------------
  0*          usb         Universal Serial Bus (USB)              
  1           net         Network/Ethernet/Wireless (direct       
                          connection or JetDirect)                
  2           par         Parallel Port (LPT:)                    

Enter number 0...2 for connection type (q=quit, enter=usb*) ? 


What puzzles me is the message saying PyQt is missing and that GUI is not available, what does that mean and does anybody have any idea how to fix it?

Thank you.

---

### Post by lindsay7 on 2009-06-09
Do you have HPLIP installed?

---

### Post by jlbr21 on 2009-06-09
Hi, yes I do have HPLip installed, and i can tell you something else, I've noticed the files it does not want to print are jpg images edited or created with Gimp. How is that for a weird problem?

Most everything else I try to print gets printed, but when I send those jpg's to print, I get the foomatic-rip failed message!

---

### Post by cariboo on 2009-06-10
As a test could you save one of the images as a .png and try to print it?

---

### Post by eudemus on 2009-06-16
I could really use some help on this too!

---

