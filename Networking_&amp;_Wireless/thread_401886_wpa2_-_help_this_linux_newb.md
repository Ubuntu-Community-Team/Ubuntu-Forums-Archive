---
title: "wpa2 - help this linux newb"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by martymcfry on 2007-04-05
Hi, I just installed ubuntu drapper for the first time a few hours ago so I'm _really really new_ to the whole linux thing.  I have a Dell D620 with a 1390 (broadcom 43xx) wireless card.  The drivers are installed and it can detect the other wireless points in my area... however I can't seem to connect to my own router with Network Manager.  

My router settings are as follows: WPA2 Personal, TKIP, Broadcast disabled, MAC filter ON.

I tried turning the mac filter off but that didn't help.  Any ideas where to start looking?  

THANKS!

---

### Post by Kobalt on 2007-04-05
You can start looking this way : [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)
I advise you to install Network-manager if you can, it will handle your wifi & wpa just fine and easily.

---

### Post by handaxe on 2007-04-05
Hi,

Kobalt is right, Network Manager is a good app.  However, I think you have your essid hidden, right?  N-M does not deal with that situation (AFAIK):

[http://ubuntuforums.org/showthread.php?t=204937](http://ubuntuforums.org/showthread.php?t=204937)
[http://ubuntuforums.org/showthread.php?t=290334](http://ubuntuforums.org/showthread.php?t=290334)
[http://ubuntuforums.org/showthread.php?t=348796](http://ubuntuforums.org/showthread.php?t=348796)
[http://ubuntuforums.org/showthread.php?t=354494](http://ubuntuforums.org/showthread.php?t=354494)

There is also **Wicd**, obtainable at 
[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

There is a deb install (gdebi should run when you click on the downloaded deb file). Also installs a tray icon BUT does not put an entry is startup. You do that by going to "System" "Preferences" "Sessions" "Startup Programs" and enter /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper).

Wicd has a facility for hidden essids.

HA

---

### Post by crush_157 on 2007-04-05
Hi,

I'm another newbie - just spent a really frustrating few hours this afternoon looking at the how to's, tried WICD, nothing seems to work.

I've allowed my SSID to be broadcast, specified new stations connecting automatically and I'm running WPA+WPA2 (that's as insecure as I'm prepared to be).

What's really frustrating is that the machine (Dell Inspiron 700M with Intel PRO/Wireless 2200BG onboard card) can see all WiFi networks in the street it just won't connect.

If anyone can help that would be great!

Cheers,

Crush

---

### Post by handaxe on 2007-04-05
Hi crush_157,

commiserations....

Assuming you are not going to use either Wicd or Network-Manager and want WPA and other encryption the following link refers:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

This assumes that you are going to enter the connection parameters in /etc/network/interfaces

Good luck, I am puzzled that both N-M and Wicd failed for you.

HA

---

### Post by martymcfry on 2007-04-05
Hi,  thanks for the replies!  I was using N-M last night (at least i think that's what it is) and I enabled broadcasting, but, like crush, I still couldn't connect nor to any unsecured access points in my area.  Anyway, I'll play with this some more when I get home tonight.  For now, I gotta get back to work ;-)  Thanks again.

---

### Post by martymcfry on 2007-04-05
I guess I should also note that I got my wireless set up using a script I found at [http://ubuntu-laptop.sourceforge.net/](http://ubuntu-laptop.sourceforge.net/)  The page mentions the following things regarding the wireless setup

    * Blacklist "bcm43xx" wireless network driver (interferes with ndiswrapper)
    * Installs and configures wireless card (utilizes ndiswrapper for unsupported cards)

It was written for the D620, which is the laptop i have, so I thought it's perfect.  Any ideas if any of those things could interfere with my wireless connection (especially ndiswrapper)?  

Thanks!

---

### Post by martymcfry on 2007-04-07
I GOT WIRELESS TO WORK!  I'm running on wireless right now =)  I just had to upgrade to edgy and re-ran the script I found at [http://ubuntu-laptop.sourceforge.net/](http://ubuntu-laptop.sourceforge.net/)

---

### Post by handaxe on 2007-04-07
Congrats - really, those broadcom cards!!!!

I doubt that is of help to crush for the intel card - they generally work on Dapper etc

HA

---

