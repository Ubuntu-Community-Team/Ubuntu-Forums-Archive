---
title: "ndiswrapper wireless hangs when connecting"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by GunnarKj on 2008-07-14
I have got a older laptop Packard Bell Easynote G1320, with Agere wireless network card. 
I have loaded the following driver with ndiswrapper:
 [http://support.packardbell.com/no/item/index.php?i=7015530000&psn=101948330133](http://support.packardbell.com/no/item/index.php?i=7015530000&psn=101948330133)
When I try to connect to the wireless network, with WEP ASCII password, the computer hangs after the first green dot appears. 
I then have to turn off the laptop with the power button. 
Anyone any ideas?

---

### Post by kevdog on 2008-07-15
Look for another driver -- you have the wrong windows driver.

---

### Post by GunnarKj on 2008-07-18
It is the right driver. I have used the driver in windows.

---

### Post by GunnarKj on 2008-07-19
I have also tried Ubuntu 8.10 Intrepid Ibex. 
The same thing happens here.
But now lspci no longer lists the network card as unknown. 

02:04.0 Network controller: Agere Systems: Unknown device ab34

now i get the following:

02:04.0 Network controller: Agere Systems Device ab34

---

