---
title: "No Wifi on Lubuntu 14.04"
date: 2016-10-29
forum: Networking &amp; Wireless
---

### Post by ratty2016 on 2016-10-29
Hi,

I tried to post this before; for some reason, it's not showing. Apologies for double-posting.

I have a Dell Latitude E4200. Don't know squat 'bout Linux.

I tried troubleshooting and installing a Broadcom driver. Got the following error massage:

bullwinkle@bullwinkle-Latitude-E4200:~$ lspci -nn -d 14e4:
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
bullwinkle@bullwinkle-Latitude-E4200:~$ sudo apt-get install firmware-b43-installer
[sudo] password for bullwinkle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 firmware-b43-installer : Depends: b43-fwcutter (>= 1:018-2) but it is not installable
E: Unable to correct problems, you have held broken packages.
bullwinkle@bullwinkle-Latitude-E4200:~$ 


I don't like this "broken packages" stuff. Where should I turn next?

Thanks,
Ratt

---

### Post by chili555 on 2016-10-29
Is the message the same if you do:```
sudo apt-get update
sudo apt-get upgrade
```Reboot.```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```

---

### Post by ratty2016 on 2016-10-30
That did it! I don't know what I did (other than doing what you suggested; I mean, I don't know any of the gobbledegook that I put into the system), butt it worked!

Thank you so much! Dr. Sheldon C. would be proud of you!

---

