---
title: "[SOLVED] Dual Boot Ubuntu/XP--networks in XP now, but not Ubuntu"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by bujutsukai on 2008-01-04
I won't apologize for being a newbie, but will apologize if this thread/problem has been resolved in the past.  I was not able to find my specific problem, or a resolution to it.  So, here it is.

I have a dual boot machine (XP/Ubuntu).  When I first installed Ubuntu, it connected to everything on my network without a hitch.  Strangely (or not), the XP side would not connect to anything--not even a printer.  I've recently replaced one of the PCs on the network with an iMac and changed the network name (windows) to Workgroup, since that's what the iMac liked.

Now, all the PCs and the iMac can connect, share and print, including my XP boot.  Sadly, my Ubuntu installation is now completely invisible to the network, except that I can still print (again, strangely).  I tried accessing the network with smb://Workgroup and also tried to access specific PCs via IP, but I get the "unavailable" message.  When I browse the network, I get a Windows Network icon, but nothing shows under it when I double click it.

Advice is much needed and greatly appreciated.  Thanks in advance!

---

### Post by metoor30 on 2008-01-04
How is the printer setup?  Is it a networked printer that you are printing to directly or was it a samba printer?  Can you access the internet on the Ubuntu box or ping the other computers?

---

### Post by bujutsukai on 2008-01-04
The printer was set up previously, when my network "worked."  I just opened the printer app and it showed up.  I can connect to the internet on Ubuntu (using that now) and I have pinged the other PCs using Ubuntu's network tools.

I should have quoted you, as I'm not sure if I've answered all questions.

---

### Post by bujutsukai on 2008-01-05
Well, I got it working, though I'm not really sure which of the things I tried was the solution.  In the end, I was able to use smb://ip.of.target.computer to access the shared network files I was in search of.  It did not work initially, so something I did along the way allowed it to.

---

