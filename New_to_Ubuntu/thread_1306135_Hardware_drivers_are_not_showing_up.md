---
title: "Hardware drivers are not showing up"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by Kedster on 2009-10-30
I was using the 9.10 beta for about 2 weeks now and I had a few problems but nothing major. I liked it so last night I downloaded the finial release and installed it this morning using a usb flash drive. when I was running on the live stick I checked if my hardware drivers were there and they were but I didnt need them as the time so I finished the installation and booted up and everything was working like usual so I wanted to install my wi-fi drivers so i opened Hardware drivers and it searched and found nothing and I was confused because on the live stick i could see the wifi driver why not on a real install. Then I thought well I connect it to the internet wired and did that restarted and check the hardware drivers again but still nothing. I have no idea why this is happening the beta had the drivers the live stick did but not this install.

---

### Post by kasyl on 2009-10-30
I have the same problem. When running the live CD, my wifi device (Broadcom BCM4311) worked without a problem - it was just a matter of activating the restricted STA driver. But when I installed it, it wouldn't activate the STA driver at all. I tried several times, including restarting the computer a few times, and found I am now getting the message that the Broadcom STA driver is installed, but not activated... and my only option listed is to remove the driver. I tried using ndiswrapper (with ndisgtk, because I'm still somewhat new and am hesitant about using Terminal) to use a Windows driver for it, but it says the bcmwl5.inf file is not a valid driver (this is how I got my wifi working on the same computer using Ubuntu 8.10).

Computer is an Acer Aspire 5100.

Any help would be appreciated.

---

### Post by Kedster on 2009-10-30
Hmm that is very similar but with me I do not see anything in hardware drivers it is just blank.

I just restarted once more and then let it look for drivers again and it showed up now I will see if it works.
 I will report back asap

---

### Post by 3rdalbum on 2009-10-30
Have you reloaded the package list? Go to System > Administration > Synaptic Package Manager and hit Reload.

---

### Post by kasyl on 2009-10-30
Tried several times. I used Package Manager to install ndiswrapper, actually.

I've also checked for any updates, but there are none.

---

### Post by kasyl on 2009-10-31
OK, I've fixed my issue. I removed the driver and reinstalled it, and now it works fine.


Why is it that the solution is always the simplest one, that was overlooked due to its sheer simplicity?

---

