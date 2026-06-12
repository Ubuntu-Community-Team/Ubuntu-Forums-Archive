---
title: "Reseting Wireless Config?"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by mespinos on 2008-10-09
Hey all, I have searched a bit and could not find the solution.

The wireless network I am trying to connect to is not broadcasted, so I have to connect via "Connect to other.."

I have been using my schools WiFi like this for months.  I recently downgraded Ubuntu 8.04 64Bit to 32Bit and started clean.

I got the network to work on this fresh install, but I accidentally entered in the wrong credentials.  Normally it NEVER saves any data regarding "Connect to other.." networks.  When I enter the proper credentials in, it comes back with the error "Passphrase required by wireless network", and the options are selected that I "accidentally" selected once.  Is there a way to clear this configuration entirely?  

Thanks,
Andres

---

### Post by mespinos on 2008-10-09
Anyone have any ideas?

---

### Post by jmbargar on 2008-10-09
I suppose you are using network manager for connecting your computer via wireless. Well, all you have to know is that gconf remembers the networks data you have tried to connect your PC, so just remove the directory that you can find in /home/user/.gconf/system/networking/wireless/networks/ which is agree with the essid you want to configure in other way. Next, configure it another time using the Network Manager frontend.

Good luck!

---

### Post by mespinos on 2008-10-10
Thanks, I will try that ASAP!

---

### Post by mespinos on 2008-10-10
I found the folders and XML data for all my wireless networks and deleted them.  When I tried to connect via network manager, I got the same error, and when the login prompted again, it still had the information I entered several days ago saved.

Any other thoughts?

---

