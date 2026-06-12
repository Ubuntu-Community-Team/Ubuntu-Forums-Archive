---
title: "Getting D-Link DWL-G650+ to work with WPA"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by Two-Six on 2006-12-30
Hi all,
I need some guidance.  I am trying to get my PCMCIA D-Link DWL-G650+ to work (hardware version B1)  Apparently this card has a Texas Instruments (TI) chipset, although it could be an Atheros chipset.  I am not sure.  I have been reading lots of stuff and have tried lots of stuff but I am pretty lost in it all.  I am a noob, not a total noobie but I am still pretty useless with Linux.

I just need some guidance really.  I could do with some pointer as to which tree I should be barking up.  Right now I am properly lost in the big scary forest or Linux :-)

From what I can gather I either need to use an ACX111 driver.  See: [http://linux-wless.passys.nl/query_part.php?brandname=D-Link](http://linux-wless.passys.nl/query_part.php?brandname=D-Link)
or
[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)

But I have no idea how to do this.  

I have seen some stuff here:
[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

I have tried to follow the insttuctions and have done the 
sudo gedit /etc/network/interfaces thing.  I have also tried changing the line 
pre-up wpa_supplicant -Bw -Dwext -wlan0 -c/etc/wpa_supplicant.conf so that you replace Dwext to something else and that changes your driver....I have also tried generating a hex WPA key from my normal WPA key and got another much bigger number but that didn't seem to do much either...

I have also been looking into using Madwifi.  I really want to be able to use Madwifi as I understand that this gives me other usefull tools like aircrack and airsnort. In order to install  Madwifi it looks like I need to compile a driver or something.  However this looks a bit dangerous and might stop Ubuntu from booting....I also have no idea on how to compile stuff.

I have tried installing WI-FI Radar, this doesn't work but it could be that my router is using WPA...

I have also tried installing the WPA supplicant, it looks like it's installed but again no joy.  If I do the terminal commands iwconfig nothing seems to happen.  If I do the iwlist scan command again nothing much happens either...

So please help

Two-Six

---

