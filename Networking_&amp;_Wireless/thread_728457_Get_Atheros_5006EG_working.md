---
title: "Get Atheros 5006EG working"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by andradx on 2008-03-18
I have a LG E500 laptop with an Atheros 5006EG wifi card. An these drivers worked for me. WEP, WPA Personal, WPA Enterprise are up and running, except for the fact that once in a while one needs to install the drivers again (especially after system upgrades) no matter...

If you have one of these, "lspci | grep Wireless" on your terminal should tell if you do or not, then it might be helpful reading through the end.

Check this site if you[ please]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html") or if you don't wan't to browse out of this thread then type this on the terminal

wget -c [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
tar xvf madwifi-ng-r2756+ar5007.tar.gz
(I'd keep the extracted folder somewhere in hand, in case it might be need to rerun the installation)
cd madwifi-ng-r2756+ar5007
(or path of the extracted folder)

you might want to run     sudo apt-get update && sudo aptitude install build-essential

before these last three commands


sudo make install
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta

I should say that the last two always printed an error related to the restricted drivers being enabled. But the last times I had to reinstall the drivers only "sudo make install" got it working

Reboot et voilà, I guess...

---

### Post by OrelEagle on 2008-05-01
Hi,

I used a similar procedure to make wifi work on my LG e500 (found here in German: [http://forum.ubuntuusers.de/topic/160673/](http://forum.ubuntuusers.de/topic/160673/)). 

Is there a reason why you used -r2756 and not -r3366, which is suggested on the link I gave?


> It works well, but I have to edit the configuration every time I start the computer (under System > Admin > Network). I have to edit the password and it works again. Do you have this problem too?

This is what I get with lspci | grep Wireless

```
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

Edit: I noticed that network manager wasn't installed... It works now.

---

