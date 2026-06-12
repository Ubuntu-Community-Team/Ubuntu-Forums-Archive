---
title: "Problem with Patch drivers from aircrack-ng.org"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by Joaquin Negrete on 2007-10-19
I installed aircrack-ng (Ubuntu synaptic manager). I tried to install the patch drivers from  aircrack-ng.org. Following the next instructions,  

ifconfig ath0 down
ifconfig wifi0 down
svn checkout [http://svn.madwifi.org/madwifi/trunk/](http://svn.madwifi.org/madwifi/trunk/) madwifi-ng
wget [http://patches.aircrack-ng.org/madwifi-ng-r2277.patch](http://patches.aircrack-ng.org/madwifi-ng-r2277.patch)
cd madwifi-ng
patch -Np1 -i ../madwifi-ng-r2277.patch
./scripts/madwifi-unload
make
make install
depmod -ae
modprobe ath_pci

and after the sudo make instruction, the following appears:

joaquinnegrete@Joaquin-Laptop:~/Desktop/Downloaded Programs/Cracking/madwifi-ng$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/joaquinnegrete/Desktop/Downloaded Programs/Cracking/madwifi-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** No rule to make target `Programs/Cracking/madwifi-ng'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2
joaquinnegrete@Joaquin-Laptop:~/Desktop/Downloaded Programs/Cracking/madwifi-ng$

Could you help me resolve this installation. The wifi card is working ( Atheros ).

Thanks!

Joaquin.

---

