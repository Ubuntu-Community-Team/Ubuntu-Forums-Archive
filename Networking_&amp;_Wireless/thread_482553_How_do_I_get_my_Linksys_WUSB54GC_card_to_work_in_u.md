---
title: "How do I get my Linksys WUSB54GC card to work in ubuntu?"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by Coffeemonkey on 2007-06-23
I am installing Ubuntu 7.04 onto my desktop PC. I know that I'll need to use ndiswrapper to properly install the windows drivers that came on the disk for the wireless usb  device that I have. I managed to get ndiswrapper installed by downloading it to my laptop and then transferring it on my portable hard drive, but I'm not super clear about where to go from here. Is this card even going to work with ndiswrapper? I just don't know. Anyone have any help or comments? This is important because I need to be able to get on the internet. Obviously. Thanks! :)

---

### Post by giddy1945 on 2007-06-23
Coffeemonkey, we have the same exact problem with the exception that I have not installed ndiswrapper.  I, too, am using 7.04 (mint) with no internet connection, have a flash drive, and have a laptop with internet connection.  I have looked everywhere.  If you find the answer somewhere else, please direct me.  I'm about to give up.

---

### Post by scrooge_74 on 2007-06-23
Check for your card [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") 


It says it is supported right of the box.

But I know they are a pain, check this [thread]("http://ubuntuforums.org/showthread.php?t=449456&highlight=wusb54gc") also

---

### Post by giddy1945 on 2007-06-23
That was quick!  Thanks.  I will check it out.

---

### Post by Coffeemonkey on 2007-06-23
OK I checked out that other thread and it was helpful, to a point. Ubuntu is recognizing the card. I have the .inf file from the drivers. It is called rt73.inf in my case. However, the comands to install it seem to be wrong on my ubuntu distro. Again, I'm using 7.04, or feisty. It doesn't seem to have ndiswrapper included in the synaptic package manager, so I have installed it myself. I have ndiswrapper 1.47. What do I need to do next?

---

### Post by Coffeemonkey on 2007-06-24
Well I did more research myself and found documentation about how to make this wireless usb card work here:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver))

However, I am really brand new at this whole Unix and command line thing. I'm trying to be patient and learn, but this particular problem seems really difficult. Especially since the computer I'm trying to do this on can only connect to the internet through the wireless usb card in question. If anyone has easier information to follow, PLEASE let me know, or maybe point me in the right direction at least. Hopefully the above documentation will help some of you who better know what you're doing

---

### Post by scrooge_74 on 2007-06-24
The only thing I can point at this momment is that ndiswrapper is in the repos and it is marked as a Ubuntu package, it does not get preinstall and probably you could not maybe because is on the extra repositories

---

