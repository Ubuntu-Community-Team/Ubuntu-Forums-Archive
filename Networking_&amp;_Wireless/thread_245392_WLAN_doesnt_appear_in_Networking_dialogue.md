---
title: "WLAN doesnt appear in Networking dialogue"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by peliot on 2006-08-27
I have a Dell Inspiron 4150 on which I jsut installed Ubuntu 6.06. The machine has a wireless LAN mini PCI card in it. The chip is a Broadcom BCM4303. Because there is no linux driver available, I tried to install the driver with ndiswrapper. 

ndiswrapper -l responds "driver present" for the driver (but nothing about hardware)
System->Administration->Device Manager shows the broadcom PCI card
I blacklisted bcm43xx (other websites suggested this was an issue)

Nonetheless after all that, when I go to the Networking control panel, there is no entry for the wireless lan.

Any ideas?

Thanks,
Philip

---

### Post by peliot on 2006-08-27
I seem to have narrowed the problem down - 
dmesg shows the ndiswrapper module loading but not finding the card.
The pciid shown by lspci -n is different from the pciids in the names of the .conf files in /etc/ndiswrapper/<driver name>
Other people seem to have gotten it to work with this driver (bcmwl5.inf). Possible issue - the card itself says BCM4301 on it, and the pciid that shows up in lspci ends in 4301, yet the Device manager thinks it is a BCM4303. Is there any chance that caused it to load the wrong .conf files when it installed the driver?
Apologies if that made no sense - I havent used ndiswrapper before so I am learning as I go.
Thanks,
Philip

---

### Post by peliot on 2006-08-27
Problem solved - I had downloaded a bcmwl5 driver from a website. I then went back and downloaded the windows xp driver from dell for this specific machine. though the file title was the same, the pciid numbers (.conf files in /etc/ndiswrapper/bcmwl5) were different and now line up with the pciid listed in lspci -n.

---

