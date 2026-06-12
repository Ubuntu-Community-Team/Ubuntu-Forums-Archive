---
title: "wlan0 does not restart after down"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by snakeye on 2007-03-20
I've got wireless network with wpa-psk encryption, dlink-G520+ card. I'm using ndiswrapper and wpa_supplicant

First of all, if I use wpa_supplicant -Dndiswrapper it says 'wpa is not supported', very strange. Option -Dwext works ok. Is it correct?

Second, and more frustrating thing, when I lose connection with the the router, the wlan0 interface does not start up, I have to start it up manually. I tried everything here in the forum, but nothing helps. :confused:

---

### Post by teaker1s on 2007-03-20
Are we saying that it doesn't start on boot? if so
when you are happy that your wireless networking is correct then

```
gksudo gedit /etc/modules
```

Add the word ndiswrapper and save the file using "save as" this will then load everytime you boot

```
sudo apt-get install network-manager-gnome
```

**For easier wireless**
 now on your desktop panel you want to click system administration networking

it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key

---

### Post by snakeye on 2007-03-21
> **teaker1s said:**
> Are we saying that it doesn't start on boot? if so
when you are happy that your wireless networking is correct then

it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key

I haven't mentioned it's ubuntu server without gnome or kde installed. So, gnome application is not a solution :(

It works fine after but, but does not start up after network failure.

---

