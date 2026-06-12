---
title: "Requesting help setting up Broadcom WLAN on Presario V6317"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by plucesiar on 2008-06-03
Hello everyone, I have just clean-installed a dual boot of Windows XP and Hardy Desktop and was very excited to start playing around with Linux (for the first time in my life) until I realized that the wireless wasn't working. I am using XP right now to connect.


Here are some specs:
Laptop model: Compaq Presario V6317
Wireless card: Devices Manager in XP doesn't show it either for some reason. All I know is it's a Broadcom 802.11b/g WLAN and that the I used sp36684.exe to install the wifi driver for XP.  ([http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-53245-1&lc=en&cc=us&dlc=en&tool=softwareCategory&query=V6317ca&product=3379120&os=228](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-53245-1&lc=en&cc=us&dlc=en&tool=softwareCategory&query=V6317ca&product=3379120&os=228))

I tried the instructions on [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560) but got stuck on installing cabextract because I didn't know how to add universe repositories, as the references seem to be based an older version of Ubuntu.

So, as of now I've got ndiswrapper-utils-1.9, ndiswrapper-common-1.5, and sp36684.exe sitting on my desktop and I'm totally stumped :confused:

Help greatly appreciated and would greatly mitigate current state of disappointment. :(

Note: I'm really n00b with Linux right now so please don't mind really basic questions if you see any, thanks!

---

### Post by vexingmodstwo on 2008-06-03
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

This should get you there.  If it doesn't, it will get you 99% there.

In my case, it got me 99% there and then I installed wifiradar and it all finally worked.

---

### Post by plucesiar on 2008-06-03
Thanks for the quick reply. However, I've already been to that site and tried the instructions. I'm stuck on part 2 where you need to install cabextract. It gives me the "cannot find package" error and I'm having trouble getting the universe repository, because I think 
1) the instructions on that site correspond to a previous version of Ubuntu and 
2) I checked Synaptic on Hardy and the "Community Maintained (universe)" option is in the "download from internet" section on the first tab. Now the thing is I don't have an ethernet cable around with me, and even if I did go out and buy one, would I be able to connect since I don't have a driver :confused:

Is there an alternative method for me to maybe download the required files and point Ubuntu to them?

---

### Post by vexingmodstwo on 2008-06-03
> **plucesiar said:**
> Thanks for the quick reply. However, I've already been to that site and tried the instructions. I'm stuck on part 2 where you need to install cabextract. It gives me the "cannot find package" error and I'm having trouble getting the universe repository, because I think 
1) the instructions on that site correspond to a previous version of Ubuntu and 
2) I checked Synaptic on Hardy and the "Community Maintained (universe)" option is in the "download from internet" section on the first tab. Now the thing is I don't have an ethernet cable around with me, and even if I did go out and buy one, would I be able to connect since I don't have a driver :confused:

Is there an alternative method for me to maybe download the required files and point Ubuntu to them?

There's a link in the instructions for section 2a that points you to how to make the package manager connect to the required repository.

Oh, oops... I missed the second part.  Your wired connection should work so if you don't have an ethernet cable, I would get one and follow the tutorial because it assumes you're on the computer you're trying to fix instead of transferring files manually.

---

### Post by Ayuthia on 2008-06-03
> **plucesiar said:**
> Thanks for the quick reply. However, I've already been to that site and tried the instructions. I'm stuck on part 2 where you need to install cabextract. It gives me the "cannot find package" error and I'm having trouble getting the universe repository, because I think 
1) the instructions on that site correspond to a previous version of Ubuntu and 
2) I checked Synaptic on Hardy and the "Community Maintained (universe)" option is in the "download from internet" section on the first tab. Now the thing is I don't have an ethernet cable around with me, and even if I did go out and buy one, would I be able to connect since I don't have a driver :confused:

Is there an alternative method for me to maybe download the required files and point Ubuntu to them?
You can download the file from:
[http://packages.ubuntu.com/hardy/utils/cabextract](http://packages.ubuntu.com/hardy/utils/cabextract)
You will need to download the package that applies to you (32-bit = i386 64-bit = amd64).  Copy the file to your Desktop and then click on the icon.  It should install the package for you.

---

### Post by plucesiar on 2008-06-04
It worked! Thanks for the help vexingmodstwo and Ayuthia.

I ended up going to Synaptic and installing it there via wired connection; at first it didn't work but then I eventually solved it by simply clicking the "Reload" button.

W00T :guitar:

---

