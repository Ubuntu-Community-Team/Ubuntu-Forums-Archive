---
title: "Broadcom Corporation BCM4312 802.11b/g"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by lance bermudez on 2009-01-03
the card is turned on and is activate. network is working when i use my use my usb netgear wireless i can get on my network but when i try to  use the bcm4312 that is built into my computer i get nothing. Just to let know i do unplug the netgear before I try to us the BCM4312 802.11b/g and i have also restarted the computer after activating BCM4312 802.11b/g which ubuntu calls broadcom sta wireless driver

---

### Post by Ayuthia on 2009-01-03
Can you provide the results of:
```
lspci -nn
```along with which version of Ubuntu you are using and the make and model of your computer?  It will help us see what might need to be done.

---

### Post by lance bermudez on 2009-01-03
acer aspire 7420z

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

---

### Post by lance bermudez on 2009-01-03
installed ndisgtk
then system | administration | windows wireless drivers
I used the driver in the attached files both the .rar and .zip have the same driver I added both to make it easer for people

---

### Post by lance bermudez on 2009-01-03
files did not attach last time so here they are

[http://www.rapidshare.com/files/65887676/wireless_broadcom.zip](http://www.rapidshare.com/files/65887676/wireless_broadcom.zip)

and

[http://www.gigasize.com/get.php/3197507619/WIFI_BROADCOM.rar](http://www.gigasize.com/get.php/3197507619/WIFI_BROADCOM.rar)

---

### Post by thefrozenpenguin on 2009-01-04
in your lsmod listing there appears to be none of the usual drivers for any network links, ie b44 or ssb both of which should be required for wired network.  Was the lsmod run while you were still connected with the usb wireless card?

Can you re-run lsmod after the sta driver or the windows drivers have been installed with ndisgtk please?

---

### Post by lance bermudez on 2009-01-04
as for the first lsmod i do not remember when i did it. However this time my computer is only on the wireless and i´m using the windows driver for my wireless.

---

### Post by thefrozenpenguin on 2009-01-04
Is it now all working?  With the ndiswrapper module loaded and the wireless working are you still experiencing problems?

---

### Post by lance bermudez on 2009-01-04
thank you for your help but things seem to be working fine now.

---

### Post by lance bermudez on 2009-01-14
Does any body know if the new kernel from kernel.org
linux-2.6.28.tar will have better driver then 2.6.27 that ubuntu has for 8.10 for Broadcom Corporation BCM4312 802.11b/g?

---

### Post by prajakta on 2009-01-14
> **lance bermudez said:**
> files did not attach last time so here they are

[http://www.rapidshare.com/files/65887676/wireless_broadcom.zip](http://www.rapidshare.com/files/65887676/wireless_broadcom.zip)

and

[http://www.gigasize.com/get.php/3197507619/WIFI_BROADCOM.rar](http://www.gigasize.com/get.php/3197507619/WIFI_BROADCOM.rar)

Hi.. I installed ndisgtk but unable to download any of the above files.
It's a torture to download from these sites. Could you please tell some other source to get the windows broadcom drivers?

Thanks.

---

### Post by rajeev1204 on 2009-01-14
> **prajakta said:**
> Hi.. I installed ndisgtk but unable to download any of the above files.
It's a torture to download from these sites. Could you please tell some other source to get the windows broadcom drivers?

Thanks.

For windows?

---

### Post by prajakta on 2009-01-14
Oh this is about Lance bermudez's post on wireless network forum, which mentioned 

"mine works chech it out here
[http://ubuntuforums.org/showthread.p...08#post6488308](http://ubuntuforums.org/showthread.p...08#post6488308)
I used windows xp driver for it."

I do not know how to get windows xp driver.

---

### Post by lance bermudez on 2009-01-14
to find my driver I did a google search for drivers for my acer aspire 7420z labtop. I used the windows xp drivers for the wireless card becuse the vista drivers did not work for me.

---

