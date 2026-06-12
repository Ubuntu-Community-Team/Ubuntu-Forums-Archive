---
title: "No wireless after last update after madwifi reinstall"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by damu on 2008-06-22
To get the RT wireless working on this laptop I did :

download and untar madwifi...
cd /home/tech/madwifi-ng-r2756+ar5007

sudo apt-get update && sudo aptitude install build-essential
make
sudo make install
sudo modprobe ath_pci

It worked, even though I had to redo the whole process as for some reason, the proprietary drivers were back to "in use" mode. So I 'unticked' them and reinstalled the madwifi and it worked again.

After the last update this morning, it didn't work anymore.

I tried the same process to no end.
I tried it again with the last build of madwifi, just in case, but no luck.

I also changed sudo gedit /etc/default/linux-restricted-modules-common
 DISABLED_MODULES=""
to 
DISABLED_MODULES="ath_hal"

and reverted back to the initial state as it didn't make any difference, even after reinstalling the madwifi drivers and restarting.

My last attempt was done as follow:
> last wifi attempt

make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/maggie/tech/madwifi-trunk-r3742-20080622 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
sh scripts/find-madwifi-modules.sh -r 2.6.24-19-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/ath'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_pci.ko //lib/modules/2.6.24-19-generic/net
make[1]: Leaving directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/ath'
make[1]: Entering directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/ath_hal'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_hal.ko //lib/modules/2.6.24-19-generic/net
make[1]: Leaving directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/ath_hal'
make[1]: Entering directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i install || exit 1; \
	done
make[2]: Entering directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/ath_rate/amrr'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_rate_amrr.ko //lib/modules/2.6.24-19-generic/net
make[2]: Leaving directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/ath_rate/amrr'
make[2]: Entering directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/ath_rate/onoe'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_rate_onoe.ko //lib/modules/2.6.24-19-generic/net
make[2]: Leaving directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/ath_rate/onoe'
make[2]: Entering directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/ath_rate/sample'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_rate_sample.ko //lib/modules/2.6.24-19-generic/net
make[2]: Leaving directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/ath_rate/sample'
make[2]: Entering directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/ath_rate/minstrel'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_rate_minstrel.ko //lib/modules/2.6.24-19-generic/net
make[2]: Leaving directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/ath_rate/minstrel'
make[1]: Leaving directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/ath_rate'
make[1]: Entering directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/net80211'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
		f=`basename $i .o`; \
		install -m 0644  $f.ko //lib/modules/2.6.24-19-generic/net; \
	done
make[1]: Leaving directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/net80211'
(export KMODPATH=/lib/modules/2.6.24-19-generic/net; /sbin/depmod -ae 2.6.24-19-generic)
make -C ./tools  all || exit 1
make[1]: Entering directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/tools/ath_info'
make[1]: Leaving directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/tools'
make -C ./tools  install || exit 1
make[1]: Entering directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/tools/ath_info'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig wpakey; do \
		install $i /usr/local/bin/$i; \
		strip /usr/local/bin/$i; \
	done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
install ../scripts/madwifi-unload /usr/local/bin/madwifi-unload
for d in ath_info; do \
		make -C $d install || exit 1; \
	done
make[2]: Entering directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/tools/ath_info'
install -d /usr/local/bin
install -m 755 ath_info /usr/local/bin
install -d /usr/local/share/man/man8
install -m 644 ath_info.8 /usr/local/share/man/man8
make[2]: Leaving directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/tools/ath_info'
make[1]: Leaving directory `/home/maggie/tech/madwifi-trunk-r3742-20080622/tools'
maggie@maggie-laptop:~/tech/madwifi-trunk-r3742-20080622$ sudo modprobe ath_pci
maggie@maggie-laptop:~/tech/madwifi-trunk-r3742-20080622$ sudo modprobe wlan_scan_sta
maggie@maggie-laptop:~/tech/madwifi-trunk-r3742-20080622$ 


I tried with 'make clean' before make with no difference.

Any clue how to save the day?

thanks,

---

### Post by damu on 2008-06-27
bump

---

### Post by damu on 2008-06-28
Any help would be very welcome now, as the usb dongle that I have been using in the meantime is now broken...so no wireless connection at all...work without connection ... mmm...

---

