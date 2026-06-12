---
title: "Wifi connection issue, WPA2 enterprise with cert using ubuntu 12.04 LTS"
date: 2014-02-01
forum: Networking &amp; Wireless
---

### Post by akansha2 on 2014-02-01
Hii,

I am trying to connect to my school's wifi. I have been instructed to use the following configuration. But the issue is I am unable to connect.
I was able to connect to a different wifi network in my apt.

Wireless Security: WPA & WPA2 Enterprise
Authentication: Protected EAP (PEAP)
Anonymous Identity: _______
CA Certificate: AddTrust_External_Root.pem (Can usually be found in /etc/ssl/certs)
PEAP version: Version 0 or Auto
Inner Authentication: MSCHAPv2
Username: ###
Password: ###

Please let me know if you need any other information.

Thanks,
Akansha

---

### Post by varunendra on 2014-02-02
Hello Akansha, Welcome to the forums !

So.. have you saved the relevant settings in Network Manager? Could you post a screenshot of the settings box showing the settings you have saved? (of course blur or blank out the username and password fields)

If you are sure the settings (including the CA Certificate) have been saved correctly, please try what is suggested in this post : [http://ubuntuforums.org/showthread.php?t=2202941&p=12917219#post12917219](http://ubuntuforums.org/showthread.php?t=2202941&p=12917219#post12917219) (change "eduroam" with your connection's name).

---

