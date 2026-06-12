---
title: "No more Ath0"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by darkreaction on 2008-09-10
everything was working fine until I did an update.I restarted and then no more Ath0 in my network list it says the card is there on ```
lspci
``` the drive is enabled and in use. please help.

---

### Post by darkreaction on 2008-09-10
no one?

---

### Post by arunvir on 2008-09-11
Looks wierd.....:confused::confused:

Please check whether the same card is detected or does it detect it as some different card. 

because sometime atheros cards are detected much differently after each kernel update.

Try re-installing madwifi( ithink ath0 is something detected by madwifi) or ndisgtk drivers that you used.

 Issue could be due to the updation of the actual madwifi drivers that come with ubuntu 8.04,

 which you would have disabled to run the madwifi drivers you downloaded

and the old drivers could have been updated and made by the kernel to replace your running drivers.

so the correct madwifi drivers (the ones you installed manually) could have been neglected  by the kernel.

:):)

I think a re-install of the mad-wifi drivers should do just fine.


Btw whats your laptop model??

---

