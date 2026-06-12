---
title: "Sooo close, but no WPA :("
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by JoeCan on 2007-04-05
Ok so I've been working on this for a few days now and it is driving me nuts.  I successfully installed a rt73 chipset-based USB wireless stick.  The problem is, getting it to connect to something.  I can't manage to get it to connect to my router.

I have WPA installed on my router...but I can't get Ubuntu to tell the USB stick what to do to connect.  The Network assistant in Gnome and Kde only allow me WEP.  I downloaded wifi-radar and it shows the SSID of my router but it doesn't allow me to edit that connection or do anything to it.  I tried creating a new connection but when I type in the SSID, it tells me that SSID already exists :S  

I have no idea what to do.  In a terminal I can find my SSID and it shows everything correct...I just need to be able to connect to it with WPA somehow.  I've tried editing the interface file to no avail...it just seems to mess-up my network manager more than anything.

Does anyone have any suggestions?  Can I get the network manager to do WPA or is there another utility...or program to help out?

Thanks so much for any help!!

---

### Post by JoeCan on 2007-04-05
I saw some new info in the sticky above that might help.  I'm going to try it out and report on my findings.  Thanks in the meantime.

---

### Post by handaxe on 2007-04-05
see if the info here helps, particularly the bits about the wireless managing applications.

Without them you need wpa_supplicant as noted (the apps use wpa_supplicant themselves but transparently).
[I][B]
[http://ubuntuforums.org/showpost.php?p=2401488&postcount=9](http://ubuntuforums.org/showpost.php?p=2401488&postcount=9)[/B][/I] 

HA

---

