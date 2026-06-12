---
title: "FIX FOR TOSHIBA  A205-s5805 atheros 5007eg wifi"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by digitalecstacy on 2008-07-01
HOW TO fix Atheros AR5007 and 5007 and 5007EG Wireless cards
there are tons of how to(s) on this. I have tested this out on 12 toshiba A205-S5805's and all 12 worked. This fix theoretically should work for other laptops. I also have done this fix in debian,kbuntu,xubuntu, and ubuntu. all have worked upon reboot.
First disable Atheros Hardware Access Layer [HAL]:
Go to System>Administration>Hardware Drivers
and uncheck Atheros Hardware Access Layer
then reboot

after reboot type these into a terminal window:

Code:

sudo apt-get install build-essential

Code:

wget [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)

Code:

tar xfz madwifi-nr-r3366+ar5007.tar.gz

Code:

cd madwifi-nr-r3366+ar5007

Code:

sudo make

Code:

sudo make install

Code:

sudo modprobe ath_pci

NOW REBOOT YOUR COMPUTER
if your running a toshiba A205-s5805 this should work like a charm. I would appreciate feed back of if it worked with other brands of laptops.

IF  ANYONE IS ALSO RUNNING A GENTOO INSTALL AND HAS A FIX FOR THE ATHEROS 5007 LEMME KNOW. (HYPNOTICECSTACY@YAHOO.COM):guitar:

---

