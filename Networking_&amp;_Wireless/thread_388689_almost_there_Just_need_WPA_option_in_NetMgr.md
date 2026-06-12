---
title: "*almost there* Just need WPA option in NetMgr"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by MrDetermination on 2007-03-19
I have come at this thing from 10 different ways and today (linux nub) compiled my first thing from source.  I found the rt61 driver at serial monkey:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)

and followed this how to:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

But I may have gotten tripped up in there.  I now have the network manager applet finding SSIDs but when I go to connect I do not have a WPA option.

Clues?

wmp54g v4.1 PCI card on Edgy

---

### Post by teaker1s on 2007-03-19
[http://www.ubuntuforums.org/showthread.php?t=341357]("http://www.ubuntuforums.org/showthread.php?t=341357")

---

### Post by MrDetermination on 2007-03-19
I have network manager running.  And wpa_supplicant works if I do it this way*, but it only works temporarily then I have to reboot.  I'm trying to get wpa to come up as an option in NM.

[http://www.ubuntuforums.org/showthread.php?p=2321712#post2321712](http://www.ubuntuforums.org/showthread.php?p=2321712#post2321712)

---

### Post by teaker1s on 2007-03-19
```
sudo apt-get install network-manager-gnome
```

 now on your desktop panel you want to click system administration networking

it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key 
=WPA

---

### Post by MrDetermination on 2007-03-19
```
chip@Metallo:~$ sudo apt-get install network-manager-gnome
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager-gnome is already the newest version.
The following packages were automatically installed and are no longer required:
  libsamplerate0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I'm saying that applet won't give me an option for WPA.

---

### Post by teaker1s on 2007-03-19
I'n which case I'm not sure, I run edgy with ndiswrapper and wpa and network-manager-gnome on edgy

---

