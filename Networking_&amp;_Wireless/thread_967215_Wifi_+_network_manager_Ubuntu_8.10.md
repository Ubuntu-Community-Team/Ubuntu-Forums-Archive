---
title: "Wifi + network manager Ubuntu 8.10"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by tomszyszko on 2008-11-01
I just upgraded to the new version of ubuntu. But Netowrk manager does not appear without typing
```
sudo /etc/init.d/NetworkManager stop
sudo /etc/init.d/NetworkManager start

```
And it says my wired connection is unmanaged

And when I try to compile the mad wifi drivers I get:
```
tom@tom-laptop2:~/madwifi-ng-r2756+ar5007$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/tom/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/tom/madwifi-ng-r2756+ar5007/net80211/ieee80211_power.o
/home/tom/madwifi-ng-r2756+ar5007/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/tom/madwifi-ng-r2756+ar5007/net80211/ieee80211_power.c:242: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/tom/madwifi-ng-r2756+ar5007/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/tom/madwifi-ng-r2756+ar5007/net80211] Error 2
make[1]: *** [_module_/home/tom/madwifi-ng-r2756+ar5007] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2

```
Any help would be apprieciated. I need this up to type my coursework - due in MONDAY!!

---

### Post by .kkursor on 2008-11-30
I have an absolutely similar problem and also want to find a solution. Please, anybody help if you can.

Some information about my system (Samsung R60 laptop)

> kkursor@notebook:/home/config/madwifi-ng-r2756+ar5007$ lspci | grep "Atheros"
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
kkursor@notebook:/home/config/madwifi-ng-r2756+ar5007$ uname -a
Linux notebook 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux // kubuntu 8.10 kde4
kkursor@notebook:/home/config/madwifi-ng-r2756+ar5007$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/config/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/config/madwifi-ng-r2756+ar5007/net80211/ieee80211_power.o
/home/config/madwifi-ng-r2756+ar5007/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/config/madwifi-ng-r2756+ar5007/net80211/ieee80211_power.c:242: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/config/madwifi-ng-r2756+ar5007/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/config/madwifi-ng-r2756+ar5007/net80211] Error 2
make[1]: *** [_module_/home/config/madwifi-ng-r2756+ar5007] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [modules] Error 2


SVN snapshot driver installed by script found by GO_ogle on this forum does not detect my card. It is actually AR5007, while it appears to system as AR2424, AR5006, etc.

---

### Post by tomszyszko on 2009-01-03
_[SIZE="7"]Solved[/SIZE]_

Download madwifi-hal-0.10.5.6-r3835-20080801

Compile & restart

Works perfectly

---

### Post by .kkursor on 2009-01-03
I have switched to ath5k wireless stack, it works perfectly for me and I have no need to build a Slackware from Ubuntu (c) anymore ;))

My solution about Wi-Fi is described [here](http://kkursor.livejournal.com/117669.html) in Russian, currently I have no time to translate it. If anyone can, do it.

UPD: Sorry, the solution in English is available on Ubuntu site [here](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros), sorry, I forgot about it =) my description is a short summary in Russian of the official one.

---

