---
title: "linksys wusb54g help"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by waldo007 on 2007-10-13
Hey all, 

im having problems getting wlan to install.

im following the directions from: [ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/README](ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/README)

im at step five of building linux wlan-ng

> 5)  To build the package, run 'make all'

and i get this error:

```
waldo@waldo-linux:~/Desktop/linux-wlan-ng-0.2.8$ sudo make
set -e; for d in src doc man etc; do make -C $d ; done
make[1]: Entering directory `/home/waldo/Desktop/linux-wlan-ng-0.2.8/src'
set -e; for d in mkmeta shared wlanctl nwepgen wlancfg p80211 prism2; do make WLAN_SRC=/home/waldo/Desktop/linux-wlan-ng-0.2.8/src/ -C $d ; done
make[2]: Entering directory `/home/waldo/Desktop/linux-wlan-ng-0.2.8/src/mkmeta'
mkdir -p obj
ngcc -c  -I../include -I/lib/modules/2.6.20-16-generic/build/include -D__LINUX_WLAN__ ../shared/p80211types.c -o obj/p80211types.o
make[2]: ngcc: Command not found
make[2]: *** [obj/p80211types.o] Error 127
make[2]: Leaving directory `/home/waldo/Desktop/linux-wlan-ng-0.2.8/src/mkmeta'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/waldo/Desktop/linux-wlan-ng-0.2.8/src'
make: *** [all] Error 2
waldo@waldo-linux:~/Desktop/linux-wlan-ng-0.2.8$ ]
```

the only portion i was unsure of was when it asked me for module install directory i entered: 

/lib/module/2.6.20-16-generic/


any ideas?

thanks

---

### Post by rustybronco on 2007-10-13
I ran a wusb54g v4 in fiesty, it worked but with dropped connections at times, plus it would not work in roaming mode or when first setting it up in manual config I had to set it up as iv4? (not dhcp) in system>admin>network first then close it then re-open manual config and set it to dchp for it to work.
what version do you have? (does it have a prism chipset)

---

### Post by waldo007 on 2007-10-14
im not sure of the chipset, but i think its prism54.  so i tried to go through the drivers from prime54.org but no luck.

i cant set it up as iv4 or dhcp because it isnt even recognized as connected.  it isnt shown under the network options and doesnt show anything when i use iwconfig in the terminal.

my only other guess is that maybe i have to install some other usb2 drivers to get it recognized?  could that be causing this problem?

---

### Post by rustybronco on 2007-10-15
Turn it over to see what version it is (v1-v2-v4) and post the results.

v1 prism 2 chipset, v4 ralink rt2570 

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

also post the results of iwconfig

---

### Post by tormod on 2007-10-17
linux-wlan-ng should only be installed and used for the prism2 USB cards.

---

