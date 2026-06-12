---
title: "Noob needs help with wifi"
date: 2015-12-01
forum: Networking &amp; Wireless
---

### Post by Jacob_Fleming on 2015-12-01
Ok so I have never had ubuntu before but i was given a hp pavillion dv6-1030us and it had a messed up version of windows 7 on it, couldnt even be booted up lol so i put whatever the most reliable version of ubuntu is (the recommended one on their site) onto said notebook and everything is working fine except the wifi. It will not scan and I cant get it to find the wifi card or whatever via the terminal commands (never used these either) so basically I think I need to download missing drivers? Im in the dark here so detailed tips would be extremely appreciated. I can get into the terminal but will need detailed instructions on the commands to use and what to do and such. Thank you for any help or instructions!

---

### Post by blade4 on 2015-12-01
Hi Jacob, welcome to ubuntu ! 

From what you say, I guess you're running version 14.04.3. 

There are several things you can do to solve this I'll suggest two possible ways. 

The best way would be to download additional drivers using ubuntu's built in functions. This does need an internet connection so if you can connect via ethernet cable, follow the instructions as described in the link below ( for your system you'll be looking for additional wireless drivers - **follow the video from 00:50 onwards** since the additional drivers feature should already be installed ) :

[https://www.youtube.com/watch?v=xUp9pSqK61U](https://www.youtube.com/watch?v=xUp9pSqK61U)



If the above doesn't work, try downloading and installing wicd . The link for downloading can be found from here : 

[https://packages.debian.org/sid/all/wicd/download](https://packages.debian.org/sid/all/wicd/download)

Don't be concerned that it doesn't say anything about ubuntu. Ubuntu and Debian Os are very similar and use the same installation package formats (.deb). Just double click on it after downloading and follow the instructions (the installation will work via ubuntu software center )

---

### Post by slickymaster on 2015-12-01
*Moved to the ***Networking & Wireless*** sub- forum*

Hi Jacob_Fleming, welcome to the forums.

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

---

### Post by Bucky Ball on 2015-12-01
> **slickymaster said:**
> 
Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

+1. If there is nothing in Additional Drivers, don't install wicd. That may cause more conflict and confusion as we've no idea what the issue is or which card you're using yet.

Supply the wirelessinfo thanks. You could also just supply the output of:

```
sudo lshw -C network
```

... and the problem might be obvious from that. :)

PS: Sounds odd, but have you booted the machine with the ethnet cable out? If you have ethernet in, that can override wireless and it won't come up properly.

---

### Post by grahammechanical on 2015-12-01
I do not have a laptop or a netbook but I understand that as a power saving feature the WiFi adapter can be switched off in hardware by a key combination. If the WiFi adapter is switched off in hardware then Ubuntu will not detect a working WiFi adapter during installation and may not install a WiFi driver.

It is also usual to have an internet connection when installing Ubuntu. If we do not have an ethernet connection then the installer will ask us to set up a wireless connection as part of the install process. The Network Manager Icon (2 arrows) should have options to enable Networking & WiFi. If either of those are disabled then we will not have a working WiFi adapter.

So, there is more information that can be given just by telling us what you see in the menus on the top panel.

Do you still have a messed up Windows that you cannot boot into? If you do and WiFi was turned off in Windows then WiFi will still be off in Ubuntu.

Regards

---

### Post by kurt18947 on 2015-12-01
> PS:  Sounds odd, but have you booted the machine with the ethnet cable out?  If you have ethernet in, that can override wireless and it won't come up  properly.

That was my thought as well. I supported a DV5-xxxxUS for a while and pretty much everything worked 'out of the box' including wifi. If there's nothing in the 'additional drivers' window, I'd strongly suspect Intel wifi which should work. The wireless script info should help.

---

