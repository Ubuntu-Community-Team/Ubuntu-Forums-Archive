---
title: "I have the file -- How do I patch my Wifi drivers"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by Cziltang Brone on 2007-06-01
I'm using Feisty. I downloaded the patched drivers for my Atheros wifi card -- specifically the madwifi-ng-r2277.patch

I'm just a little new to linux in general. How do I actually apply this patch? 

Thanks.

---

### Post by blazercist on 2007-06-01
generally you would put the patch in the same dir as the driver source and in console you do 

patch patch_name target_patch_file

then compile the driver as usual.

---

### Post by tturrisi on 2007-06-01
you can't patch your existing madwifi driver!

uninstall the linux-restricted-modules madwif first. else you will get build errors.
connect by cat5 cable.
do as root:
```
apt-get install build-essential 
apt-get install linux-headers-$(uname -r)
ifconfig ath0 down
ifconfig wifi0 down
rmmod wlan_wep ath_rate_sample ath_rate_onoe ath_pci wlan ath_hal ath_rate_amrr 2>/dev/null
svn checkout http://svn.madwifi.org/trunk/ madwifi-ng
wget http://patches.aircrack-ng.org/madwifi-ng-r2277.patch
cd madwifi-ng
patch -Np1 -i ../madwifi-ng-r2277.patch
make
make install
depmod -ae
modprobe ath_pci
```

---

