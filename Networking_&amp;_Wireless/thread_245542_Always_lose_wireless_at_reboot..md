---
title: "Always lose wireless at reboot."
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by Anthem on 2006-08-28
Not sure what the problem is.  I'm using ndiswrapper on a Broadcom card; it's always worked fine in the past.  I start the computer, and I have no wireless.  I "sudo modprobe ndiswrapper" and all is peachy.  I thought the solution was "ndiswrapper -m" but I get "modprobe config already contains alias directive".

What am I doing wrong?

---

### Post by codejunkie on 2006-08-28
> **Anthem said:**
> Not sure what the problem is.  I'm using ndiswrapper on a Broadcom card; it's always worked fine in the past.  I start the computer, and I have no wireless.  I "sudo modprobe ndiswrapper" and all is peachy.  I thought the solution was "ndiswrapper -m" but I get "modprobe config already contains alias directive".

What am I doing wrong?
you could try adding ndiswrapper to /etc/modules and it should load ndiswrapper at boot.

---

### Post by Anthem on 2006-08-28
Yeah, that was the problem.  Thanks!

---

### Post by haiku99 on 2006-08-29
thanks, worked for me too, developed the same problem.  FWIW the howto at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
 has some info on this, but implies that the two methods are just different ways of accomplishing the same thing, but in my case the file also need editing despite a response that ndiswrapper was already setup to load....
anyway, from the page mentioned...

2.4.3. Automatically loading at start-up

    *

      If everything works, you need to tell your system to load the module when the system starts-up. You can either type the following into the Terminal, which will add the proper line to the /etc/modules file:

        sudo ndiswrapper -m
        

      or you can add it manually by opening the file with this command:

        gksudo gedit /etc/modules
        

      and add the word ndiswrapper to the end of this file and save it.

/!\ It is strongly recommended that you make a backup copy of the /etc/modules file before manually editing it.

---

