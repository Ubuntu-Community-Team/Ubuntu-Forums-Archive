---
title: "Wireless won't connect but will if i manual connect"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by Dark-Angel on 2007-10-23
hi all,
       I have been trying for ages to get my wireless working with wpa encryption. I have just tried to connect manual by using terminal and it won't connect but if i try manually with no encryption it will connect that why but still not automatically. 
Any suggestions on how to get wpa working.

---

### Post by kevdog on 2007-10-23
Have you tried to manually connect with wpa encryption?? What steps have you tried?

Can you do the following:
sudo updatedb
locate wpa_supplicant.conf

---

### Post by Hero of Time on 2007-10-23
Check the sticky about wireless encryption: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
It should have enough information to get your network going with WPA.

---

### Post by Dark-Angel on 2007-10-23
yes i've tried to maunally connect with wpa but it just drops out

---

### Post by kevdog on 2007-10-23
Can you be more specific about drop out??

With the wpa_supplicant command or dhclient command?

---

### Post by Dark-Angel on 2007-10-23
well i just look and it was your guide i was using for connecting manually and i tried with wpa and this was what i was getting

Sending on   Socket/fallback
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 7
then something about no connection and going to sleep but when i tried with no encryption it connected fine.

---

### Post by kevdog on 2007-10-23
Are you running wpa1 vs 2?? Have you matched the cipher type set in the router to that specified in the wpa_supplicant.conf file?

I take it by what you are saying the wpa_supplicant.conf command that references the wpa_supplicant.conf file goes through?

Can you post your command line statement and you wpa_supplicant.conf file?

---

### Post by Dark-Angel on 2007-10-23
ok well i'm not really sure on wether it vs2 or what i just know it wpa tkip. I will post the stuff tomorrow when i can transfer them over.

---

### Post by Hero of Time on 2007-10-23
Did you run your WPA key trought wpa_passphrase? You need that for wpa_supplicant. See the man file for info about it. It is something like wpa_passphrase <ssid> <key> (when using spaces, be sure to put single quotes around it). The key you get needs to be pasted in your wpa_supplicant.conf file. This is also noted in the howto.

---

