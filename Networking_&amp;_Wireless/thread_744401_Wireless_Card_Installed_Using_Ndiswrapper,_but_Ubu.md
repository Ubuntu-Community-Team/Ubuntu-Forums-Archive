---
title: "Wireless Card Installed Using Ndiswrapper, but Ubuntu Freezes when trying to connect"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by rayishu on 2008-04-03
Hello guys ive recently installed my ENLWI-G2 using the Ndiswrapper ([http://www.encore-usa.com/product_download.php?region=us&bid=3&pgid=83_11&pid=285](http://www.encore-usa.com/product_download.php?region=us&bid=3&pgid=83_11&pid=285))

there are linux drivers for this card but when i tried to install them i got multiple errors. i checked the readme and saw that it was only for fedora, so i tried using the windows xp drivers and ndiswrapper instead.

i got the drivers to install with ndiswrapper, and i got no errors yet when i go to the "just works" connection manager i see all the SSIDs in my area except the signal strengh is 0 and none of them support WPA, also if change my router to WEP and try connecting then the entire PC freezes and i have to reboot

if anyone has this card and knows a better method for installation can you please tell me? and is thier something wrong with my current method of installation?

---

### Post by Raphaff on 2008-04-03
Hey your card has a native linux driver why aren't you using it ?
@ terminal Check it:
lscpi -nn | grep Eth
you have other commands to use to stop it before going throw this steps 
sudo dhclient -r wlan0
sudo ifconfig wlan0 down
sudo /etc/init.d/networking stop
Commands and iface names might differ from our versions  of linux so use tab to complete commands and find right paths to scripts
remove modules loaded by ndiswrapper !
[B]
Page info about your wlan card:[/B]
[http://www.encore-usa.com/product_download.php?region=us&bid=3&pgid=83_11&pid=285](http://www.encore-usa.com/product_download.php?region=us&bid=3&pgid=83_11&pid=285)
[B]
Driver of your card:[/B]
[http://www.encore-usa.com/download/driver/ENLWI-G2_ENPWI-G2_Linux_Driver.tar.gz](http://www.encore-usa.com/download/driver/ENLWI-G2_ENPWI-G2_Linux_Driver.tar.gz)
[COLOR="YellowGreen"]
**Just check it.**[/COLOR]

---

