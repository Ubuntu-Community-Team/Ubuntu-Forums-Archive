---
title: "connection problems with tplink TL-WN881ND on ubuntu 14.04"
date: 2014-06-18
forum: Networking &amp; Wireless
---

### Post by william35 on 2014-06-18
I'm new to the Linux scene I'm used to windows but after install the wireless card was showing networks but when u try to connect it will keep asking for network key I have the drivers but it's a exe and the earthanet cable will not work either I have tried installing wine but as I'm new I haven't been able to do this many thanks

---

### Post by nknwn on 2014-06-19
It's interesting that it seems Ubuntu already has Linux drivers for your device maybe someone else will come along and advise on how to get it working correctly.

However I've had some success with windows drivers for wifi devices.
To use the windows driver for your device:
Download the Windows driver from here: [http://uk.tp-link.com/support/download/?model=TL-WN881ND&version=V1#tbl_a](http://uk.tp-link.com/support/download/?model=TL-WN881ND&version=V1#tbl_a)
Make sure it unzipped. (I would create a folder named windowsdrivers in your home folder)
Install a program named **ndisgtk** using the Ubuntu software centre
When that has been installed open a terminal and type: **sudo ndisgtk**
In the Wireless network drivers window click install new driver
Another window lets you locate your newly downloaded driver
(you're looking for a filename ending in .inf)
Click install
Then configure your network from the Wireless Network Drivers window.

---

### Post by william35 on 2014-06-19
I wonder could it be my isp I use vigin media anyone had problems with that or could it just be ubuntu 14.04 drivers are messed up??

---

### Post by william35 on 2014-06-21
Bumb I desperately,need help any ideas anyone

---

### Post by nknwn on 2014-06-21
Did you try the suggestion re windows drivers?

---

### Post by nknwn on 2014-06-21
Maybe before trying the above. Please read point 2 here: [http://www.omgubuntu.co.uk/2013/04/10-things-to-do-after-installing-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/04/10-things-to-do-after-installing-ubuntu-13-04) 
[h=3]2. Enable Additional Drivers[/h]

---

### Post by chili555 on 2014-06-21
> **nknwn said:**
> Maybe before trying the above. Please read point 2 here: [http://www.omgubuntu.co.uk/2013/04/10-things-to-do-after-installing-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/04/10-things-to-do-after-installing-ubuntu-13-04) 
[h=3]2. Enable Additional Drivers[/h]Do you think his TL-WN881ND is actually a Broadcom device? I doubt it is.

---

### Post by Vladlenin5000 on 2014-06-21
[https://wikidevi.com/wiki/TP-LINK_TL-WN881ND](https://wikidevi.com/wiki/TP-LINK_TL-WN881ND)

Assuming the above is correct the chipset is **Atheros** **AR9287**. The working driver should be 'ath9k', already included. It should just work - and it does -.
You're probably typing in the wrong password.

---

### Post by jtarin on 2014-11-14
> **william35 said:**
> it will keep asking for network key As mentioned above.....You  Network Key is your password you setup to access your wireless point.

---

