---
title: "Wireless in Dell Desktop XPS 8100 dont work"
date: 2014-08-25
forum: Networking &amp; Wireless
---

### Post by Rubens_ on 2014-08-25
Hi all, 

Im new in linux and i try install The most new ubuntu on my machine, creat a new particion, everything is fine, when i start i cant conect to my wireless network.
The network card dont have any light , nothing blinks.
i search in someplaces and find something about my driver, i know he is the BCM4321 802.11 a/b/g/n. So i find the driver and i dont know how to install this drivers. Somebody can help me?

Sry for my english.

---

### Post by slickymaster on 2014-08-25
Hi Rubens_, welcome to the forums.

I'm moving your thread to the **Networking & Wireless** sub-forum which is the proper one for your issue.

---

### Post by varunendra on 2014-08-25
If you can connect to internet using Ethernet cable or other means, open a terminal (Ctrl-Alt-T) and run the following command to install the driver for your card -
```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by Rubens_ on 2014-08-25
The awnser was.: impossible find the packedg bcmwl-kernel-source. 
And now?

---

### Post by varunendra on 2014-08-25
Were you connected to internet when you ran the command? If yes, make sure you have "restricted" repository enabled in "Software Sources" (Shortcut : press Alt-F2 > type "software-properties-gtk" > press 'Enter'). Save and close, then in the terminal -
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```

---

### Post by Rubens_ on 2014-08-26
No im not connect to internet, this is the main problem, i cant find any wireless conection. so i think could be some problem about wireless driver?

---

### Post by praseodym on 2014-08-26
It should work with the native driver. Install this package via doubl-click with the software-center and reboot

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

---

