---
title: "Wireless not working - Compaq c769us Laptop"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by carnageX on 2008-06-08
Recently bought this laptop.  Decided that I wanted to put Ubuntu on it, since I already have it on my desktop.  Install went fine, but my wireless card is not working.  I looked in the Hardware Drivers, and it shows that the drivers are installed/enabled.  Here's what it shows:

Atheros Hardware Access Layer (HAL) - In use

Looked around and saw that other people were having problems with the Atheros WLAN chipsets.  Looked up which chipset mine had, and it has AR2425.  Tried the Madwifi project, but it wouldn't work when I tried to do a make install.  So then I installed Ndiswrapper and ndisgtk (had to use my Win-box desktop to get the files, since my laptop doesnt have internet access).  So I went here: [http://www.atheros.cz/](http://www.atheros.cz/) and downloaded the Windows XP driver for the 5007EG one (since that's what my specs say my chipset is), and then tried using ndisgtk.  It says the hardware is enabled/driver is in use...but my wireless still does not work.  Then I tried just the 5007 driver (Vista 32bit; since that's the only one available), and that didn't work either.  I rebooted after each try, as well, and nothing worked.  

Is it worth the trouble to keep trying, is it a simple fix?  Or should I just try to look for a different miniPCI WLAN card that's more Linux-friendly? Or do any of you think that 7.10 would work better instead of 8.04?

Thanks for the help, appreciate it.

---

### Post by daRealScanMan on 2008-06-08
Have you tried this HOWTO?

[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

What exactly was the error when you tried to make the madwifi driver?

FWIW, I have a Compaq C751 and the madwifi 3366 driver is working great for me in 8.04.

---

### Post by carnageX on 2008-06-09
Didn't see that guide; will go through it right now.  Thanks for the link.

---

### Post by carnageX on 2008-06-09
Awesome, my wireless now works.  Thanks a lot for that link, I really appreciate it!

What I had to do was use a crossover cable from my Win-box (setup wirelessly) from the wired NIC, to my laptops wired NIC.  I followed this guide: 

And got it set up (used automatic DHCP on the linux side).  Then I downloaded build-essential and got it working.

---

