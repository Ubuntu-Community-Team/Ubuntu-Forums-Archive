---
title: "[SOLVED] Problem with madwifi in Gutsy"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by kidux on 2008-08-26
I got tired of the hard locks I was having on Hardy, so I went back to Gutsy, but now I’m having issues with getting my wifi card working. I’ve tried the HowTo’s and wiki at madwifi, but cannot seem to get it working right, and it is an atheros card, though I am at work right now and will have to wait until I get home to get the exact specs. It won’t load the ath_pci module. I uninstalled madwifi that came with gutsy, and installed a compiled version made with make/checkinstall from the madwifi website. It was working on Hardy with no problem, but not on Gutsy. 

I also installed wicd, but for some reason I can’t get it to reconnect to networks automatically upon resuming from sleep, so if anyone has a clue about that as well, I would be most appreciative.

---

### Post by kidux on 2008-08-28
I found the solution to this here: [http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)
THis worked perfectly once I figured out that I needed the HAL version of the driver (which is explained later in the thread) and needed to turn off the restricted drivers being loaded by default.

---

