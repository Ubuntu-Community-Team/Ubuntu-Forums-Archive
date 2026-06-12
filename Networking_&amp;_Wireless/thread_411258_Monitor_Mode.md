---
title: "Monitor Mode"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by jaymill on 2007-04-16
Ok, if this is posted somewhere else, please forgive me, I have looked, and cannot find the way to do it anywhere. I am running an acer aspire 5100 with ubuntu 6.10. This laptop has an atheros 5005g wireless card that fully supports monitor mode and packet injection, but airodump/kismet etc. do not work. I have read that I have to patch the madwifi drivers, but I am at a total loss as to where to get them (ever site that as had it has been outdated), and how to do it once I have downloaded it. If someone could let me know how to do this, or point me in the right direction, it would be greatly appreciated, thank you.

--Jay

---

### Post by FRuMMaGe on 2007-06-10
look on the aircrack forums.  Just type "aircrack" into google

---

### Post by tturrisi on 2007-06-10
First, you have to connect using a wired connection
then uninstall the existing restricted-modules madwifi (use Synaptic), 
then in a ROOT terminal do:
```
cd /usr/src
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

/etc/kismet/kismet.cong
```
# User to setid to (should be your normal user)
suiduser=YOUR-USERNAME
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=madwifi_ag,wifi0,madwifi
# SOURCES FOR OTHER CHIPSETS
#source=acx100,wlan0,acx
#source=orinoco,eth2,hermes1
#source=rt8180,wlan0,Realtek
#source=prism54g,eth1,PrismGT
#source=hostap,wlan0,Prism2
#source=wlanng,wlan0,Prism2
#source=ipw2100,eth1,Centrino_b
#source=ipw2200,eth1,Centrino_g
#source=rt2500,ra0,Ralink_g
#source=rt2500,rausb0,Ralink_g
#source=kismet_drone,192.168.2.252:3501,kismet_drone

```

---

