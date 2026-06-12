---
title: "ndiswrapper + BCM4310 +hp dv2000"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by Enriquecaribe on 2008-04-29
Well Hardy installed on my HP pavilion dv2000 perfectly and everything works execpt the wireless.

I HAVE read through countless post about this but has yet to get it to work. 

I used nbounds how-to and It did install the driver, yet no internet connection.

So now that the driver has installed how do I use it? The switch is on (still has orange light) And I have been using the ethnet connection for a while. BUT I need wireless to use at work. 

Please help.

---

### Post by teaker1s on 2008-04-29
you have tried 
```
sudo modprobe ndiswrapper
```
post output of 
```
ndiswrapper -l
```
and
```
iwconfig
```
While no expert on ndiswrapper, have you used a recommended driver or used cabextract or unzip to unzip exe for your model.

---

### Post by Enriquecaribe on 2008-04-29
-Teaker1s
I tried that and I got:

```
rico@rico-laptop:~$ sudo modprobe ndiswrapper
[sudo] password for rico: 
rico@rico-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
rico@rico-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rico@rico-laptop:~$ 



```

---

### Post by teaker1s on 2008-04-29
from what I can see, it looks like the driver is not working with your hardware. I would expect something similar to
[B]installed drivers:
bcmwl5          driver installed, hardware (14E4:4324) present (alternate driver: bcm43xx)
[/B]

note that yours doesn't mention hardware.
From my experience it's either
1) Sometimes repository ndiswrapper is outdated and non functional-need to compile later version.
2) the driver is right for the chipset, but not right for your setup- resolved by getting exe wireless file from manufacturers site and using either
**cabextract** or **unzip** as required to strip required driver file

---

### Post by blong1385 on 2008-04-29
I have the same problem except im using a dell, but still using bcm4310. It has certainly given me many headaches. I was using gutsy gibon and got the wireless working fine. upgraded to hardy, and boom no wireless. i made the mistake of removing the driver from ndiswrapper without investigating further. since then i have reinstalled the driver and it shows the driver being installed and device present but no wireless. i got the same output running iconfig. it shows no wlan....

---

### Post by Enriquecaribe on 2008-04-29
i just googled ndiswrapper, and it seems the repo has 1.50. the latest version is 1.52, I'll try that and see if it works... gimmie a minute. . .

---

### Post by Enriquecaribe on 2008-04-29
> **blong1385 said:**
> I have the same problem except im using a dell, but still using bcm4310. It has certainly given me many headaches. I was using gutsy gibon and got the wireless working fine. upgraded to hardy, and boom no wireless. i made the mistake of removing the driver from ndiswrapper without investigating further. since then i have reinstalled the driver and it shows the driver being installed and device present but no wireless. i got the same output running iconfig. it shows no wlan....

yea, ndiswrapper worked fine in 6.10 (i only use lts distros) but as soon as I upgraded it seemed to have a problem. I heard some people got it working but I'm not sure how. The repo uses ndiswrapper 1.50 and theres about to be a 1.53 release so the repo may need to get upgraded. I downloaded the tar file for 1.52 but I have no clue how to use that (Im used to googling deb packages for stuff but cant find one for ndiswrapper 1.52) so I'm stuck with using the cable, but I need wifi for work.

---

### Post by teaker1s on 2008-04-29
also worth a look
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851")

hack at bottom got a stubborn hardy heron working on broadcom

---

