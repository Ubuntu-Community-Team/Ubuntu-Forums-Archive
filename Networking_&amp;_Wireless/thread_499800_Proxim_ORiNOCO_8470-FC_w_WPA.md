---
title: "Proxim ORiNOCO 8470-FC w/ WPA"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by J-Wreck on 2007-07-13
I've been browsing the forums for a while, but never actually posted before. But, alas, it seems I have a problem that there isn't a good topic on. I'm planning on installing Xubuntu on my parents' old notebook. Everything is compatible, and fine, with the exception of the wireless card, a Proxim OriNOCO 11b/g GOLD (8470-FC). It isn't natively detected. I've heard it will work with madwifi, but I just wanted to confirm this (preferably from someone whose done it). In addition, I need it to work with WPA. I'm not going to install anything on the notebook until I'm 100% sure it will work. It wouldn't be good to give my parents the whole 'sales pitch' of Linux, then have it not be able to connect to the wireless network. 

In all my time with Ubuntu, I've never found a problem I couldn't work through. However, since this is my parents first experience with Linux, I want to make sure everything works before I install it, so it leaves a better impression. So, if there is anyone who has successfully configured this card to work, please tell me how you did it so I can (hopefully) bring two more people into the wonderful world of the *buntus.

---

### Post by tturrisi on 2007-07-13
That card will work fine.  It does have an atheros chipset and requires the madwifi drivers.  The madwifi drivers are in the ubuntu linux-restricted-modules package which automatically install with latest version of ubuntu..   Some folks have issues with these drivers in ubuntu due to some documented ubuntu bugs.  I suggest you remove the ubuntu madwifi drivers and install the madwifi-ng drivers from source.  Remove the drivers, connect by ethernet (wired), then do this:
Open a ROOT terminal
```
# if not yet installed, install wpasupplicant to support WPA
apt-get install wpasupplicant
# next install packages necessary to build from source:
apt-get install build-essential linux-headers-`uname -r`
# next install subversion to be able to use the svn repositories:
apt-get install subversion
cd /usr/src
svn checkout http://svn.madwifi.org/trunk/ madwifi-ng
cd madwifi-ng
make
make install
depmod -ae
# load the madwifi module and all dependant modules:
modprobe ath_pci
```

---

### Post by J-Wreck on 2007-07-19
I did that, then tried to use [this]("http://ubuntuforums.org/showthread.php?t=318539") tutorial to connect to the network (WPA1). No dice. This is the output i get when i try to connect
```

ioctl[SIOCSIWPMKSA]: Invalid argument
ioctl[SIOCSIWMODE]: Invalid argument
Could not configure driver to use managed mode
ioctl[SIOCGIWRANGE]: Invalid argument
ioctl[IEEE80211_IOCTL_SETPARAM]: Invalid argument
ioctl[SIOCSIWAP]: Invalid argument
Failed to initialize driver interface
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.wifi0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: File exists
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2

```

---

### Post by tturrisi on 2007-07-19
What command sdid you use to get that output?  Also, that guide is from 2006.
If you do NOT use network-manager (uninstall it) then all you should have to do is edit your /etc/network/intefrfaces file & reboot, or do the command:  /etc/init.d/networking restart

interfaces file:

# WPA GENERAL
iface ath0 inet dhcp
wpa-ssid thisismynetworkname
wpa-key_mgmt WPA-PSK
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-psk thisismypassword
wpa-driver wext
auto ath0

---

### Post by J-Wreck on 2007-07-20
I fixed that error (I did something stupid, misread ifconfig). Now it returns no errors, it just doesn't get any DHCPOFFERS and can't connect. I know the network name and passphrase is good, I know the network is up (there are other wireless devices connected), and it picks it up on 'iwlist scan' but for some reason it won't connect now. Nothing needs to be in quotes in the interaces file, correct?

---

