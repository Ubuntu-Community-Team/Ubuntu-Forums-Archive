---
title: "ipw2200 and wpa [solved]"
date: 2005-04-27
forum: Networking &amp; Wireless
---

### Post by matthew on 2005-04-27
I have a centrino laptop with the Intel 2200b/g wireless adapter. I have been trying to set it up so I can use wpa with my Linksys wrt54g router. I am running Ubuntu and winxp on this laptop as a dual boot. All is well with the wireless setup under xp, but not with ubuntu. Here's the scoop:

Originally I was able to connect with no encryption or with WEP. Since I wanted WPA I followed the HOWTO instructions listed here: [http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

The firmware updated perfectly.

When I tried to update the driver from ver 0.19 to 1.0.3 this is the result:

root@matthew-linux:/home/matt/ipw2200-1.0.3 # make
make -C /lib/modules/2.6.10-5-686/build SUBDIRS=/home/matt/ipw2200-1.0.3 MODVERDIR=/home/matt/ipw2200-1.0.3 modules
make[1]: Entering directory `/lib/modules/2.6.10-5-686/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.10-5-686/build'
make: *** [modules] Error 2

I wasn't paying attention the first time and went ahead and installed the wpa_supplicant and made the config file and rebooted. Didn't work. I looked again and realized I still had the 0.19 version of the ipw2200 driver. I attempted to uninstall the driver using 

rmmod ipw2200

then I searched for all related files with

locate ipw2200.ko
sudo rm /lib/modules/2.6.10-*-686/kernel/drivers/net/wireless/ipw2200/ipw2200.ko
locate ieee80211.ko
sudo rm /lib/modules/2.6.10-*-686/kernel/drivers/net/wireless/ipw2200/ieee80211.ko

I then attempted to install the updated driver (1.0.3) as before with the same result. The bad news: I now have no new driver and since I removed the old one I can't use the wireless card at all, even without wpa.

I would appreciate any help/ideas so I can install the new driver.

---

### Post by luca_linux on 2005-04-28
If you continue reading that howto thread, you will see that you need the kernel headers, build essentials...

---

### Post by matthew on 2005-04-28
I'm sorry. I'm not quite sure what you mean. I am new to linux after years of windoze. I used to use Unix in college, but that was more than 10 years ago. I'm not computer illiterate, but I am linux illiterate for the moment. 

I read the whole thread several times and am embarrassed to say that I am still not sure what to do.

Is there a way for you to help me understand what you mean by my needing the kernel headers, build essentials... and what I need to do with them?

Thank you.

---

### Post by luca_linux on 2005-04-28
Don't worry!
You have to download and install through apt-get or synaptic the following package: linux-kernel-headers, linux-headers-2.6.10-5-386, build-essential, gcc, linux-tree-2.6.10.
Then go to the command line and type:
```

ln -s /usr/src/linux-source-2.6.10 /usr/src/linux
ln -s /usr/src/linux-source-2.6.10 /lib/modules/2.6.10-5-386/build

```
Now it should work.

---

### Post by matthew on 2005-04-28
Thank you. I acquired and installed all the packages you mentioned and made the links as you directed. Then I went back and tried to finish the install. Here's what happened:

root@matthew-linux:/home/matt/ipw2200-1.0.3 # make
make -C /lib/modules/2.6.10-5-686/build SUBDIRS=/home/matt/ipw2200-1.0.3 MODVERDIR=/home/matt/ipw2200-1.0.3 modules
make[1]: Entering directory `/lib/modules/2.6.10-5-686/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.10-5-686/build'
make: *** [modules] Error 2
root@matthew-linux:/home/matt/ipw2200-1.0.3 #

I then wondered if I needed to apt-get the package for linux-headers-2.6.10-5-686 instead of for 386 so I did and made the link for it using the same syntax as before:
ln -s /usr/src/linux-source-2.6.10 /lib/modules/2.6.10-5-686/build

Same result.

Any more ideas?

By the way, I appreciate your kindness and help! Thank you.

---

### Post by matthew on 2005-04-30
After long hours of fiddling I finally decided to re-install Ubuntu from scratch (I didn't have many hours into configuration anyway) so I have a functional ipw2200 driver, even if it is 0.19. Then I set up WEP instead of WMA. It isn't as good, but it is working and my home network doesn't have anything truly sensitive on it anyway...

So thanks to all who tried to help.

If you come up with any new ideas I would still be interested, though.

---

### Post by matthew on 2005-07-07
It's been about 2 1/2 months and I am feeling like less of a novice so I decided to try again. The whole process took me less than 30 minutes and worked perfectly. Thank you, Luca, for a great HOWTO. I'm a happy man.  :grin:  :grin:  :grin:  \\:D/  \\:D/  \\:D/

---

### Post by Psquared on 2005-08-03
[QUOTE=matthew]It's been about 2 1/2 months and I am feeling like less of a novice so I decided to try again. The whole process took me less than 30 minutes and worked perfectly. Thank you, Luca, for a great HOWTO. I'm a happy man.  :grin:  :grin:  :grin:  \\:D/  \\:D/  \\:D/[/QUOTE]

I'm kinda in the same boat as you. I keep getting an error message saying that I have old versions of ieee80211 and ipw2200 and the "make" won't go ahead. I wonder if I need to reboot?

Either that or could someone walk me through the basics of removing the old files. I see some other files that have the suffix _cryp.ko. Do those need to be deleted as well?

---

### Post by matthew on 2005-08-03
Luca has updated his howto on this page: [http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623) and it includes instructions on how to delete the old ieee80211 stuff. I would recommend spending some time reading that thread from first to last post and see if there is some little bit of insight you are missing. 

Don't worry, you will get it working!

---

### Post by scottylans on 2005-08-03
[QUOTE=matthew]Luca has updated his howto on this page: [http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623) and it includes instructions on how to delete the old ieee80211 stuff. I would recommend spending some time reading that thread from first to last post and see if there is some little bit of insight you are missing. 

Don't worry, you will get it working![/QUOTE]


You said you learnt more and now it's working - but is it working in WPA or WEP out of curiousity?

---

### Post by matthew on 2005-08-04
I am using wpa with great success.

---

