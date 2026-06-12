---
title: "WPA wireless fails to connect on startup only"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by daytimer045 on 2008-01-21
I followed a long and frustrating trail to get wireless working.  It will work, when I turn it on manually, but not on startup.  This is frustrating.  Can anyone help.

Linksys WPC54CG v2 wireless card installed using Ndiswrapper
Gutsy
WPA wireless

I can manually connect through network-admin, but it seems that I have to re-enter the WPA key.  I can also turn the card on fine at the command line, using wpa_supplicant.

It has been a fight to get here, even, but there is still one missing piece:  I have to turn it on manually.  I think it may be a combination of NDiswrapper and WPA not been sweet together.

Anybody have any thoughts or experience on this?  

Perhaps a suggestion of how to turn it on "manually" in a boot script (I tried this, but the version I used below crashes the boot -- although it does successfully turn the wireless on)

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo wpa_supplicant -iwlan0 -Dwext -c/etc/wpa_supplicant.conf
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient

---

### Post by bodymind on 2008-01-21
hei, 
you may give a try to wicd

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

[http://ubuntuforums.org/showthread.php?t=527488&highlight=wicd](http://ubuntuforums.org/showthread.php?t=527488&highlight=wicd)

---

### Post by daytimer045 on 2008-01-21
Thank you, thank you, thank you.

Your suggestion has put an end to several weeks worth of frustration.

---

### Post by kevdog on 2008-01-21
or your commands could just go in the /etc/rc.local file -- however wicd is a great alternative -- very well supported also.

---

