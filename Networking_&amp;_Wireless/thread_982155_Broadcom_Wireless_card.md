---
title: "Broadcom Wireless card"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by kaustubh.bansal on 2008-11-14
Hello

I have a Broadcom Wireless 802.11 card on my laptop. I'm not able to run WLAN on ubuntu 8.04. I tried "ifconfig" to check if my device is recognized but its not even listed there. Please help me through

Thanx in advance

---

### Post by Sam Lars on 2008-11-14
Please post the output of
```
lspci -v | grep Network
```

---

### Post by Marius Derekus on 2008-11-14
try downloading this: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) 
**Make sure to get the text file also**

If i am correct, your wireless internet should be up and running after you do what the text file says. It worked for me yesterday (literally yesterday), and now i have wireless internet today. You may have to edit a certain file though, please check with me once you have installed those drivers. 

Also, go to **System>Administration>Hardware Drivers** and show me everything that is listed

---

### Post by kaustubh.bansal on 2008-11-15
The output was something like this:

30:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by kaustubh.bansal on 2008-11-15
> **Marius Derekus said:**
> try downloading this: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) 
**Make sure to get the text file also**

If i am correct, your wireless internet should be up and running after you do what the text file says. It worked for me yesterday (literally yesterday), and now i have wireless internet today. You may have to edit a certain file though, please check with me once you have installed those drivers. 

Also, go to **System>Administration>Hardware Drivers** and show me everything that is listed
Hi, I went to **System>Administration>Hardware Drivers** and this time it showed me the wireless card listed ( i have no idea why it wasn't listed earlier, i had checked it earlier too). I enbled it and required files were automatically downloaded. I dont have wireless access for next 3 days. Hopefully it will run fine next time when i try. Thanks a lot..

---

### Post by Marius Derekus on 2008-11-15
Your Welcome. Always glad to help. I'll be keeping an eye on this post just in case anything else happens.

---

