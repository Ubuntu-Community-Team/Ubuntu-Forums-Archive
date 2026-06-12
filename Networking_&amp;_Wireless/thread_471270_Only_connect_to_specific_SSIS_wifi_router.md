---
title: "Only connect to specific SSIS wifi router"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by charlessw on 2007-06-11
Hi all. I'm using Ubuntu 7.04.

Is there a way to specify a list of allowed SSID's / Access Points to connect to, and disallowing connecting to any others?

I'd like to only connect via wireless to three different access points.

I checked the Ubuntu Wiki and also search this Networking forum for variations on "Deny SSID" "restrict Wireless" and others, but I mainly turn up pages that discuss using the GUI setup control panel- but I think this needs to be manually specified using a text file.

Does anyone know where I could learn more details about how to do this?

Charles

---

### Post by carcioni on 2007-06-11
I'm not sure if this will suit your needs, but the article below discusses managing multiple networks through wpa_supplicant. It may provide you with an alternative, but i am not sure it is quite what you are looking for. I 'think' what you would like is to be able to specify a list of ESSID values that are allowed to be connected to and nothing else. Sort of like having a line in the interfaces like wireless-essid  myAp1:myOtherAP:myLastAP

Have a look and see if this may be useful.

[http://ubuntuforums.org/archive/index.php/t-326590.html](http://ubuntuforums.org/archive/index.php/t-326590.html)


Cheers
C

---

### Post by charlessw on 2007-06-11
Thanks for the tip, carcioni. 
I think the main helpful thing the post was doing was specifying wpa_supplicant to run when the eth1 interface came up:
auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf 

It seems WPA_Supplicant may be what I need:
wpa_supplicant is designed to be a "daemon" program that runs in the background and acts as the backend component controlling the wireless connection. wpa_supplicant supports separate frontend programs and a text-based frontend (wpa_cli) and a GUI (wpa_gui) are included with wpa_supplicant.

I wonder if their frontend will allow me to specify the details this user did in .conf files.

Does anyone else have any suggestions on how to specify wireless connectivity to specific Access Points?

Charles

---

