---
title: "ipw 3945 without wep"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by luzmala on 2006-09-13
Hi all,
My inspiron 640m has ipw 3945 wifi pci card and I go it working with no wep, but if I configure wep key the signal goes to cero and no way to  connect.I can still see the nets arrownd but only connect to open ones.
Kernel is 686 and all rest works fine.
Thaks for any help!!

---

### Post by themusicwave on 2006-09-13
I have the same card as you.  I found a guide that helped me get it working at one point.  I have since broken the card again tinkering...

try looking at this thread, the commands posted by justhamade worked for me before.

[http://www.ubuntuforums.org/showthread.php?t=140085](http://www.ubuntuforums.org/showthread.php?t=140085)

Also, I had to install the gnome network manager from the repositories.

Good luck!

---

### Post by luzmala on 2006-09-14
Thanks Themusicwave, but this ubuntu comes with the drivers from the box, and in any case to install them is to much for my knowledge.
I had the idea that could be something to configure but i dont iven know how to check what could be rong.
Thanks any way!

---

### Post by darwin_te on 2007-05-27
Kubuntu 7.04 (Feisty)
ASUS G1

Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

WEP 104-bit (128-bit) setting connecting to Windows AP:

/etc/network/interfaces:

########################
#home - wifi
########################

auto eth1
iface eth1 inet static
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid youressidhere

# passphrase is test
# see [http://www.powerdog.com/wepkey.cgi](http://www.powerdog.com/wepkey.cgi) (Passphrase To Hexadecimal WEP Keys)
wireless-key1 9FDF3BFDFB10AFEB0925EF9605

wireless-defaultkey 1
wireless-keymode open

command line to bring wireless network up:

>ifup eth1

---

### Post by chili555 on 2007-05-27
Here is my recipe, posted from an ipw3945 using WEP:```
sudo iwconfig eth1 essid <my_essid>
sudo iwconfig eth1 key 0123456789abcdef
sudo dhclient eth1
```Good surfin'!

---

