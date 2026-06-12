---
title: "Problems with another Linux distribution"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by Avidanborisov on 2010-11-11
Well it isn't really connected to Ubuntu but the community here is great so I ask for help from you guys.The problem is with multiboot on usb drive. I did my usb drive bootable with some linux ditros (multibootiso) and on of them is Backtrack 4 R1. When I selected Backtrack from the GRUB4DOS it booted a black screen like terminal with "boot@bt:~#". What should I do to boot Backtrack with the regular gui and not the terminal screen?

---

### Post by bioterror on 2010-11-11
> **Avidanborisov said:**
> Well it isn't really connected to Ubuntu but the community here is great so I ask for help from you guys.The problem is with multiboot on usb drive. I did my usb drive bootable with some linux ditros (multibootiso) and on of them is Backtrack 4 R1. When I selected Backtrack from the GRUB4DOS it booted a black screen like terminal with "boot@bt:~#". What should I do to boot Backtrack with the regular gui and not the terminal screen?

I would try first:

```
sudo /etc/init.d/<insert your display manager, like gdm> start
```

Then we could want to know what it says if it doesnt start.

---

### Post by wojox on 2010-11-11
Try startx

You should see something like this


[IMG]http://www.backtrack-linux.org/images/forensices-boot-menu.png[/IMG]

---

### Post by Avidanborisov on 2010-11-13
Thanks it works but somehow Backtrack doens't recognize wireless. I am using Asus eeepc 1201t. Any help?

---

### Post by spiky001 on 2010-11-13
By default BT4 dosn't load network, to start network make sure you are root ```
dhclient
``` that should start up all network, maybe you should have a look through here [http://www.backtrack-linux.org/forums/](http://www.backtrack-linux.org/forums/)

---

### Post by Avidanborisov on 2010-11-13
> **spiky001 said:**
> By default BT4 dosn't load network, to start network make sure you are root ```
dhclient
``` that should start up all network, maybe you should have a look through here [http://www.backtrack-linux.org/forums/](http://www.backtrack-linux.org/forums/)

Well, I tried that but it says ```
No DHCPOFFERS received.
No working leases in persisent database - sleeping.
```

The most important reason I downloaded Backtrack 4 R1 was to hack wireless with aircrack-ng but commands like ```
airodump-ng wlan0
``` just return this:
```
ioctl(SIOCGIFINDEX) failed: No such device
```

Maybe someone knows drivers for wireless for eeepc 1201t?
help!

---

### Post by spiky001 on 2010-11-13
Try a eth0 connection then ```
update
``````
upgrade
``` see if this will install drivers, if not you will have to google drivers and how to install them

---

### Post by Avidanborisov on 2010-11-13
> **spiky001 said:**
> Try a eth0 connection then ```
update
``````
upgrade
``` see if this will install drivers, if not you will have to google drivers and how to install them

I don't have a cable for ethernet connection.

---

### Post by spiky001 on 2010-11-13
What wireless card do you have? have used this wireless with aircrack tools?

---

### Post by Avidanborisov on 2010-11-14
> **spiky001 said:**
> What wireless card do you have? have used this wireless with aircrack tools?

Realtek RTL8191SE Wireless LAN 802.11n PCI-E NIC.
*Copied from Windows Device Manager...*

---

### Post by Avidanborisov on 2010-11-14
Someone? Don't tell me I spent the whole night downloading Backtrack 4 R1 for nothing! Help!!!

---

