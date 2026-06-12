---
title: "Can't get wireless to work on my dell d620 - edgy"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by neum on 2006-11-17
My switch to Ubuntu from windows is almost complete, except I cannot get my wireless to work, which is critical especially at work. I have a dell d620 with the Intel PRO/Wireless ipw3495 network card. Running Ubuntu 6.10 

I've read through many threads about this card and followed the directions as I understand them - new to all this. I made sure I had linux-restricted-modules-generic (installed it using synaptic) according to [this post]("http://ubuntuforums.org/showthread.php?t=271808&highlight=3495"). I even got the linux-restricted-modules-686 according to another post. Neither worked. I have installed network-manager-gnome and it recognizes my wired network connection no problem. 

I cannot manually configure wireless for work because it is wpa, (which is why I need network manager?) 

If I go to a terminal and check for the right driver it appears to be correct.
```
$ lsmod | grep ipw3945
ipw3945               124576  1 
ieee80211              35272  1 ipw3945

```

If I go to system>administration>networking I can manually enter the ssid at work, but network manager does not scan and find available networks like I've seen it do and it does not allow me to login to the wpa network and I do not have the cingular bar icon in the tray. 

Any help on what else I can try greatly appreciated.

---

### Post by jogeek on 2006-11-18
try opening /etc/network/interfaces and removing any entries having to do with eth1. log out and back in to reload network-manager.

this is all my has in it and it works fine, using it to post this:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

I had this happen to me when I first started using network-manager, because I was using plain old "networking" to set a wep connection and that adds entries to "interfaces" and that was not letting net-man have control of eth1.

---

### Post by neum on 2006-11-20
Jogeek you are awesome. Thanks a ton. It finally works! I have been trying to figure this out for a month. 

So... if you are on a laptop and are going to use network manager don't mess with your network settings until AFTER you intall network manager. (Or  just use the instructions above and then you're alright)

Again, thanks. I had almost given up on using Linux.

---

