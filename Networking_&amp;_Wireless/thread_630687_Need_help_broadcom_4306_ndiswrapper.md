---
title: "Need help broadcom 4306 ndiswrapper"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by bobbymcsteels on 2007-12-03
Ok I know there are hundreds of how tos on the forum and I know cos I have tried about 15 of them and I still cant get my wireless card to work.

This one gave me the most promising results but still no wireless
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-8c17800e39e4aa9908db7a64a75a8447be9adf2f](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-8c17800e39e4aa9908db7a64a75a8447be9adf2f)


```
mcsteels@mcsteels-desktop:~$ sudo ndiswrapper -i bcmwl5.inf
Password:
driver bcmwl5 is already installed
mcsteels@mcsteels-desktop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
mcsteels@mcsteels-desktop:~$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
mcsteels@mcsteels-desktop:~$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

mcsteels@mcsteels-desktop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

mcsteels@mcsteels-desktop:~$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
mcsteels@mcsteels-desktop:~$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
ENABLED=0

```

If anyone could point me to the right direction or offer some help that would be greatly appreciated.
Thanx
Bobby

---

### Post by bobbymcsteels on 2007-12-03
Ok found away round it using the firmware, only problem now is wpa-psk and I dont think that my wifi card can find my default gateway.
I have run through this guide, but not too sure if its right.
[http://ubuntuforums.org/showthread.php?t=571188&highlight=WPA-PSK+Encryption](http://ubuntuforums.org/showthread.php?t=571188&highlight=WPA-PSK+Encryption)

---

### Post by bobbymcsteels on 2007-12-04
Anyone??

---

### Post by rustybronco on 2007-12-04
> **bobbymcsteels said:**
> I have run through this guide, but not too sure if its right.
[http://ubuntuforums.org/showthread.php?t=571188&highlight=WPA-PSK+Encryption](http://ubuntuforums.org/showthread.php?t=571188&highlight=WPA-PSK+Encryption)
Did you try it?

---

### Post by bobbymcsteels on 2007-12-04
Yeah did that and it didnt seem to do anything. What I have done now is dist-upgrade to gutsy and it asked straight away after restart for wpa, typed it and worked straight away..... not sure why but the only thing that guide did was confuse me:P
Thanx for the response tho

---

