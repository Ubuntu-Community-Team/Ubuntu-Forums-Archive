---
title: "Problem Connecting to WIFI on 14.04.2 LTS HPG60.WIFI enabled but no available networ"
date: 2015-07-26
forum: Networking &amp; Wireless
---

### Post by Markony on 2015-07-26
[B]Hello community!

[/B]First i want to say that i am new to Ubuntu and also new to forums.So i am not very experienced but i can see you guys are amazing community.I have tried to find the solution for my problem using this forum and google search but no luck.

I have Wireless Script attached so if there is anybody willing to help that would be nice.

Also Wifi hard switch button is ON and i can connect the wifi using other computer,phone and tablet except this one which is connected via cable at the moment.

Thank you in advance

---

### Post by praseodym on 2015-07-27
Hi,

try these module parameters for this driver:
```

echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
Obviously, your country code (US ?) allows 11 channels only. On which channel does the router send?

---

### Post by Markony on 2015-07-27
Hi *praseodym,*

thank for your fast reply and for wanting to help.
I just solved my problem by switching from Lubuntu 14.04. to LXLE distro.I dont know how that solved my problem but it works and i think i like it more at first glance.

I actually did tried that code and tried switching channels also with no luck

Thank you for your reply one more time.'

I guess this goes under solved.

Cheers

---

