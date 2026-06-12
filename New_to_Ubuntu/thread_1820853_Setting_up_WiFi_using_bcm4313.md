---
title: "Setting up WiFi using bcm4313"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by slavchobg on 2011-08-08
Hi, all.
 
My version of Ubuntu is (I think) [COLOR=blue]2.6.35[/COLOR]-22-generic.
 
[COLOR=darkorchid]Broadcom corporation bcm4313 802.11b/g LP-PHY (rev 01) [/COLOR][COLOR=black]is the more important detail.[/COLOR]
 
What I need is basically to connect to Wi-Fi networks.
 
Please help me out with **detailed** guidelines (a link to download some driver wouldn't be enough).
 
Thank you in advance!
 
 
Best,
 
Slavi
Bulgaria

---

### Post by gandaran on 2011-08-08
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by slavchobg on 2011-08-08
Thank you for the link.
 
I got lost here:
 
> Now in your Ubuntu Box [computer] please make your way to your **Home folder **

 
What is this home folder? I tried searching for it and could not find it.
 
>  
/lib/firmware

 
This, too. I could not find such directories.
 
Thanks again.

---

### Post by coffeecat on 2011-08-08
> **slavchobg said:**
> My version of Ubuntu is (I think) [COLOR=blue]2.6.35[/COLOR]-22-generic.

That's the kernel version. You are running Ubuntu 10.10 - Maverick Meerkat.
 

> **slavchobg said:**
> I got lost here:
 

 
What is this home folder

Open the Places menu and click on your name. Your home folder will open.

However, that link, while very good, seems over-complicated. Have a look here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

What you *should* be able to do is connect your machine with an ethernet cable, open Update Manager and click on "Check" to refresh the package metadata. Then close Update Manager and open System > Administration > Additional Drivers and see if it is prompting you to install the restricted driver for your wireless card. If it is, then the system will do everything for you.

One last point.

> **slavchobg said:**
> [COLOR=darkorchid]Broadcom corporation bcm4313 802.11b/g LP-PHY (rev 01) [/COLOR][COLOR=black]is the more important detail.[/COLOR]

It is indeed! :) The good news is that that wireless chipset will work out of the box in the latest version of Ubuntu, 11.04/Natty, which comes with a new open source driver that supports a handful of Broadcom wireless chipsets, the BCM4313 being among them. I suggest you download the ISO for 11.04 and boot up a live CD or USB and try wireless in 11.04. If it works OK for you then consider re-installing with 11.04.

---

