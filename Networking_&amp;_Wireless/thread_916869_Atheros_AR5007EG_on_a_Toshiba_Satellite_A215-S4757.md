---
title: "Atheros AR5007EG on a Toshiba Satellite A215-S4757"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by mcamardo on 2008-09-11
I have read the archived posts on this. This is what i did since I tried madwifi first. quoting [http://ubuntuforums.org/showthread.php?p=3202754#post3202754](http://ubuntuforums.org/showthread.php?p=3202754#post3202754)

> 
Step 1:
Because I tried Madwifi before so I had to remove it:
Code:
cd /lib/modules/$(uname -r)
sudo rm -rf net
sudo rm -rf madwifi
sudo rm -rf madwifi-ng

Then:
cd /to your directory of madwifi-version, do the following:
sudo make clean (you can do this step again and again to make sure madwifi is removed completely)

Code: (Check for the existence of any wlan, ath_hal, ath_pci modules)
lsmod

Remove existing loaded modules:
sudo rmmod (moduleName)

reboot

Step 2: (you might not have to do this step if you haven't installed ndiswrapper)

remove the installed ndiswrapper by doing:

cd /directory of ndiswrapper-1.47/

sudo rmmod ndiswrapper
sudo make distclean
sudo make -C driver clean

Go to Places-->seach for files, seach ndiswrapper, you will see a list of ndiswrapper files and folders. In the command line go to each location to delete ndiswrapper either with sudo rm (for files) or sudo rm -r (for folders).

Step 3:

Then go back to directory of ndiswrapper-1.47/
sudo make
sudo make install

Step 4:

And finally install the driver:

cd /directory of XP driver/

sudo ndiswrapper -i net5211.inf (your file would be different, something like file.inf)
ndiswrapper -l ==> if u see this message: "net5211: driver installed device (168C:001C (not same with ur )

sudo modprobe ndiswrapper

dmesg (show that the card installed)
iwlist wlan0 scan (will show all APs arround you)

sudo ndiswrapper -m

sudo reboot

And the wireless should work.


It works fine except I syill cannot see wlan0. It does npt load in ifconfig. ndiswrapper -l shows - netathw : driver installed device (168C:001C) present. It works just fine when using Vista and when directly connected...

---

