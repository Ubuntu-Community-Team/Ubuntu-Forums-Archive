---
title: "[Xubuntu] Wireless Card not detected after upgrade to 16.04"
date: 2016-08-07
forum: Networking &amp; Wireless
---

### Post by ridz2 on 2016-08-07
Today i've upgraded Xubuntu in my laptop from 15.04 to 16.04 using USB. I choose the delete and reinstall option because the upgrade options was grayed out. Also, same like before, it's dual-booted with win 7.

Several week before, at 15.04 xubuntu detects my wireless card as Intel Centrino Wireless. Even though it's detected, it's faulty. It discovers nearby wifi networks with low signal and can't connect to it. One of my reason to upgrade is to (hopefully) fix this problem. Now it's even worse, the card doesn't showed itself when i use lspci, lshw, or lsusb.

Also, I downloaded the suitable driver for that card and place it at /lib/firmware, severe weeks before the upgrade. It doesn't seem to matter. I'm sure it's wiped out after the upgrade.

I need some help. Thanks before.

---

### Post by DrScum on 2016-08-07
linux-firmware-nonfree needs to be installed
here is how I did it: first download the gdebi installer and install it, then download the .deb package for linux-firmware-nonfree install that as well and after reboot your card should be available.

Sorry, the forum doesn't allow to attach.deb files otherwise I would attach them here.

---

### Post by chili555 on 2016-08-08
> **DrScum said:**
> linux-firmware-nonfree needs to be installed
here is how I did it: first download the gdebi installer and install it, then download the .deb package for linux-firmware-nonfree install that as well and after reboot your card should be available.

Sorry, the forum doesn't allow to attach.deb files otherwise I would attach them here.I assume you mean this package: [https://packages.debian.org/jessie/firmware-linux-nonfree](https://packages.debian.org/jessie/firmware-linux-nonfree)

If so, that is not an Ubuntu package and I suggest that ridz2 be very cautious about installing a package not intended for Ubuntu. Second, as I read the list of files, I see nothing that relates to Intel wireless. Perhaps you can help us understand why you think it is helpful.

---

### Post by ridz2 on 2016-08-09
> **DrScum said:**
> linux-firmware-nonfree needs to be installed
here is how I did it: first download the gdebi installer and install it, then download the .deb package for linux-firmware-nonfree install that as well and after reboot your card should be available.

Sorry, the forum doesn't allow to attach.deb files otherwise I would attach them here.

Thanks for the suggestion. I'd like to try it soon.
****
> **chili555 said:**
> I assume you mean this package: [https://packages.debian.org/jessie/firmware-linux-nonfree](https://packages.debian.org/jessie/firmware-linux-nonfree)

If so, that is not an Ubuntu package and I suggest that ridz2 be very cautious about installing a package not intended for Ubuntu. Second, as I read the list of files, I see nothing that relates to Intel wireless. Perhaps you can help us understand why you think it is helpful.

Thanks for the warning, too. I also a little confused, between 'firmware-linux-nonfree' or 'linux-firmware-nonfree'. Maybe the two is different ?

After browsing through the internet i've got some ubuntu based links to 'linux-firmware-nonfree'. I saw some similar looking wireless problem were solved by installing these. Here's some of the link :

[http://packages.ubuntu.com/wily/linux-firmware-nonfree](http://packages.ubuntu.com/wily/linux-firmware-nonfree)

[https://launchpad.net/ubuntu/xenial/+package/linux-firmware-nonfree](https://launchpad.net/ubuntu/xenial/+package/linux-firmware-nonfree)

The version is same, I'll try it out from the launchpad.

---

### Post by ridz2 on 2016-08-09
I have found interesting facts when i boot into win 7, it also don't detect the wireless card.

Oh, and couldn't i use dpkg -i to install the .deb file instead ?
I've installed it with dpkg and going to reboot soon.
Hope it works.

Update : It still not showing up. Maybe I miss something ?

---

### Post by jeremy31 on 2016-08-09
See if wireless is enabled in BIOS.  If it is enabled or there is no setting you may have to power down the computer remove and install the wifi to see if it is detected then

---

### Post by DrScum on 2016-08-12
@chilli555

all I can say is that I installed ubuntu 16.04, and the wireless card wasn't working. Then I installed the package "linux-firmware-nonfree_1.16_all.deb" and the card worked fine. That's why I thought my post would be helpful.

BTW I did the same for several ubuntu installs between 14.04 and 16.04 on various machines (Desktops and Laptops) and it always did the trick.

---

