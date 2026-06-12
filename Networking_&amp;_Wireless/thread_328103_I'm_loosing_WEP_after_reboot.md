---
title: "I'm loosing WEP after reboot"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by insub2 on 2006-12-30
I'm using my laptop at my girlfriend's house where the wireless network is hidden and has a WEP hex key.  In order for my wireless to work i need to use [NetworkManager Applet 0.6.3]("http://www.gnome.org/projects/NetworkManager/").

I can connect rather easily if i click "Connect to Other Wireless Network..." and putting the name and key in.

the problem is that when i shut down or hibernate, all the settings are lost and i have to put all that in again.  I'm over there enough to make this an issue.  does anybody have a solution?

---

### Post by TheWizzard on 2006-12-30
```
sudo nano /etc/network/interfaces
```
here you can store your wireless-essid and wireless-key

---

### Post by insub2 on 2006-12-30
> **TheWizzard said:**
> ```
sudo nano /etc/network/interfaces
```
here you can store your wireless-essid and wireless-key

i need a little more help please.

---

### Post by TheWizzard on 2006-12-31
maybe you want to check the help pages for networkmanager. i'm not using this, so i can only helping you configuring manually. 

1) check your wireless interface:
```
iwconfig
```
on a laptop, this is probably eth1

2) open /etc/network/interfaces you should see something like this: 

```
auto eth1
iface eth1 inet dhcp
wireless-essid type_name_here
wireless-key type_key_here
```

this is the place where you can store your key permanently. 
the "auto eth1" makes your computer hook to the network at startup.

there are GUI to do this, but i'm not using gnome so i can't help you here.

---

