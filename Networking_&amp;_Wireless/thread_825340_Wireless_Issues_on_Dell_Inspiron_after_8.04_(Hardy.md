---
title: "Wireless Issues on Dell Inspiron after 8.04 (Hardy Heron) Upgrade"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by DanseNoir on 2008-06-10
Hello all, 

I am using a Dell Inspiron 1501.  It took me a while to figure out how to get my wireless to work on 7.10 (Gutsy Gibbon); after trying several tutorials with no success, I managed to stumble upon [this thread]("http://ubuntuforums.org/showthread.php?t=598849&highlight=Dell+Inspiron+1501+wireless"); in the third post down, "erichill" details how to use the Restricted Driver Manager in order to download the firmware for the Broadcom 43xx chipset.  Once I did that, my wireless worked perfectly!  It was so simple!

I recently upgraded to 8.04 and as soon as I did, my wireless quit working.  I tried to go back and do what I did before; only problem is that things have changed on 8.04; there is no "Restricted Driver Manager" under System/Administration now.  Instead, there is a "Hardware Drivers" tab.  When I access that, it lists two "device drivers", the second of which says "Broadcom B43 wireless driver."  The status box says "In Use" and I have clicked on the box that says "enabled" several times; each time I do so, it tells me I must restart for the setting to take affect and yet, my wireless still never works when I restart.

Does anyone have an easy solution to this?

---

### Post by Ayuthia on 2008-06-10
> **DanseNoir said:**
> Hello all, 

I am using a Dell Inspiron 1501.  It took me a while to figure out how to get my wireless to work on 7.10 (Gutsy Gibbon); after trying several tutorials with no success, I managed to stumble upon [this thread]("http://ubuntuforums.org/showthread.php?t=598849&highlight=Dell+Inspiron+1501+wireless"); in the third post down, "erichill" details how to use the Restricted Driver Manager in order to download the firmware for the Broadcom 43xx chipset.  Once I did that, my wireless worked perfectly!  It was so simple!

I recently upgraded to 8.04 and as soon as I did, my wireless quit working.  I tried to go back and do what I did before; only problem is that things have changed on 8.04; there is no "Restricted Driver Manager" under System/Administration now.  Instead, there is a "Hardware Drivers" tab.  When I access that, it lists two "device drivers", the second of which says "Broadcom B43 wireless driver."  The status box says "In Use" and I have clicked on the box that says "enabled" several times; each time I do so, it tells me I must restart for the setting to take affect and yet, my wireless still never works when I restart.

Does anyone have an easy solution to this?

It could be possible that there is a conflict with the bcm43xx (Gutsy and older) driver and the b43 (Hardy and newer) driver.  You might check and see what is currently blacklisted:
```
cat /etc/modprobe.d/blacklist*|grep -i -e bcm43xx -e b43
```
If you don't see 'blacklist bcm43xx', then most likely the bcm43xx module is interfering with the b43 module.  You can fix this by doing:
```
sudo echo blacklist bcm43xx|sudo tee -a /etc/modprobe.d/blacklist
```

To see if the b43 module works try the following:
```
sudo modprobe -r b43 ssb bcm43xx
sudo modprobe b43
sudo ifconfig wlan0 up
```

To see if the bcm43xx module still works in Hardy:
```
sudo modprobe -r b43 ssb bcm43xx
sudo modprobe bcm43xx
sudo ifconfig  wlan0 up
```
If the bcm43xx module works for you and you want to keep it, you will need to blacklist the b43 driver and make sure that bcm43xx is not blacklisted.  You can to edit /etc/modprobe.d/blacklist by:
```
gksu gedit /etc/modprobe.d/blacklist
```
and make sure that 'blacklist b43' (without the quotes) is in the file and that 'blacklist bcm43xx' is not in the file.

---

### Post by Cygoku on 2008-06-10
... then you will get 1Mb / s transfert rate.  

Wich is very bad.

Cygoku

---

### Post by Ayuthia on 2008-06-11
> **Cygoku said:**
> ... then you will get 1Mb / s transfert rate.  

Wich is very bad.

Cygoku
That is not always true.  It all depends on the card.  My card has no speed issues.  Mine has occasionally reported 1Mb, but when it transfers the files, it transfers at a faster rate.  I have not had any problems transferring files over my network using the b43 driver.  It goes just as fast as Windows or NDISwrapper.

---

### Post by rehaby on 2008-06-24
> 

To see if the b43 module works try the following:
```
sudo modprobe -r b43 ssb bcm43xx

```



i typed this in and got

 FATAL: Module ssb is in use.

what does this mean.
im a linux noob please help

---

### Post by Ayuthia on 2008-06-24
> **rehaby said:**
> i typed this in and got

 FATAL: Module ssb is in use.

what does this mean.
im a linux noob please helpThis means that the b44 module is also in use.  You will also have to back it out also:
```
sudo modprobe -r b43 b44 ssb bcm43xx
```

---

