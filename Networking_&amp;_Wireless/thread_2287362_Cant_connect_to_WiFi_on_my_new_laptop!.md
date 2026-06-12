---
title: "Cant connect to WiFi on my new laptop!"
date: 2015-07-18
forum: Networking &amp; Wireless
---

### Post by miguel42 on 2015-07-18
Hello, I recently bought a Asus VivoBook F200MA and now Im installing Ubuntu. The problem is that I cant connect to wifi anyway. I tried everything, by bash, installing new drivers but nothing. Clicking the icon of connections in the bar of ubuntu there arent any wifi option to connect. I need help quickly please. When the laptop had windows the wifi was ok but not now. I think that the system dont recognize the wifi device or maybe the drivers are incorrect. Please help me. :(
My network device is 'Broadcom BCM43142'

---

### Post by sandyd on 2015-07-18
Moved to *Networking and Wireless*

---

### Post by Geoffrey_Arndt on 2015-07-19
did you try to install the broadcom driver by using the Ubuntu"Systems Settings" application?   

System Settings>Software & Updates>Additional Drivers Tab

IF you incorrectly tried to install the drivers via the CLI (command line interface or terminal), you may have to purge what you did . . . but first try the standard method listed above.

---

### Post by miguel42 on 2015-07-19
I solved it at end, and it wasn't easy.

For the people that have the same problem that me, these are the steps that I did:

-Reinstall Lubuntu but this time with a connection to Internet by cable.
-Once finished install all updates of the OS and reboot.
-If isn't solved now you have to install a new driver.
In my case for the Broadcom BCM43142, you can check if its the same network device by ```
sudo lshw
```

For this network device do this:
-```
sudo apt-get install bcmwl-kernel-source
``` (this is the official driver for BCM43142 for ubuntu)
-Now reboot the laptop/pc
-```
sudo modprobe wl
```
-Now you can disconnect the Ethernet cable and connect by wifi!

---

### Post by Bucky Ball on 2015-07-19
Welcome and well done! Please mark the thread as solved. See the second link in my signature. Thanks. :)

---

