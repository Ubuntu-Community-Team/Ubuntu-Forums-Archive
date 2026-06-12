---
title: "SOLVED &gt;&gt; Updates killed wireless (mad wifi)"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by Midwest-Linux on 2008-06-21
OK, the updates killed my wireless, but not my LAN ethernet. I tried redoing the script in the terminal. Problem is madwifi.org site is down, so the script won't work. So do a modified script, this worked in my laptop and restored my wireless. It worked because I had tar xfz madwifi-ng-r2756+ar5007.tar.gz still in my system.


Try this in terminal Modified script or modify it further minus the 
tar xfz madwifi-ng-r2756+ar5007.tar.gz
-----------------------------------------------------------------


tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

sudo make 

sudo make install

sudo modprobe ath_pci

sudo reboot

(if it doesn't reboot after re installing ..try typing in (sudo reboot)manually and it should reboot or just do a reboot from the control panel.

----------------------------------------------------------------

Original script below

-----------------------------------------------------------------


sudo apt-get install build-essential

wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

sudo make 

sudo make install

sudo modprobe ath_pci

sudo reboot

---

