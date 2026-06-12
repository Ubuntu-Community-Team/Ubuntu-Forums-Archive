---
title: "intel pro wireless 3845abg"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by lampiao_d_braga on 2010-12-18
hi everyone ..
im new to ubuntu kde
i'm running the latest version of ubuntu ..
i been trying some packet injection with my intel pro/wireless 3945abg
however this wireless card does not support packet injection  (just monitor mode) so i have been trying to patch it but seems like i been getting a few error messages .. any help would be greatly appreciated ..thanks ..
here is what im getting :

atum@atum-debian:~$ sudo su
[sudo] password for atum: 
root@atum-debian:/home/atum# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 konq-plugins-l10n linux-headers-2.6.31-14
  linux-headers-2.6.31-20 libqtruby4shared2 kdebase-runtime-data-common
  plasma-widget-lancelot kde-style-qtcurve liblancelot0 konqueror-plugins
  libqt4-ruby1.8 libboost-program-options1.38.0
  linux-headers-2.6.31-20-generic libknotificationitem1
  kdebase-workspace-libs4+5 libkorundum4-ruby1.8 libsmokesoprano3 libkexiv2-7
  libexiv2-5 libscim8c2a libqscintilla2-5 kwin-style-qtcurve policykit
  liblzma0 ruby1.8 sdparm libx264-67 libtidy-0.99-0 ruby libpackagekit-qt11
  kdebase-runtime-bin-kde4 libpackagekit-glib11 python-sip4 libpolkit-dbus2
  libqt4-multimedia konq-plugins libqt4-phonon libpolkit-qt0
  update-notifier-kde liblsofui4 libruby1.8 linux-headers-2.6.31-14-generic
  libsmokeqt4-2 libsmokeqt4-3 libjpeg-progs libsmokekde4-2 libpolkit-grant2
  libpolkit2 libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@atum-debian:/home/atum# sudo apt-get install libssl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libssl-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 konq-plugins-l10n linux-headers-2.6.31-14
  linux-headers-2.6.31-20 libqtruby4shared2 kdebase-runtime-data-common
  plasma-widget-lancelot kde-style-qtcurve liblancelot0 konqueror-plugins
  libqt4-ruby1.8 libboost-program-options1.38.0
  linux-headers-2.6.31-20-generic libknotificationitem1
  kdebase-workspace-libs4+5 libkorundum4-ruby1.8 libsmokesoprano3 libkexiv2-7
  libexiv2-5 libscim8c2a libqscintilla2-5 kwin-style-qtcurve policykit
  liblzma0 ruby1.8 sdparm libx264-67 libtidy-0.99-0 ruby libpackagekit-qt11
  kdebase-runtime-bin-kde4 libpackagekit-glib11 python-sip4 libpolkit-dbus2
  libqt4-multimedia konq-plugins libqt4-phonon libpolkit-qt0
  update-notifier-kde liblsofui4 libruby1.8 linux-headers-2.6.31-14-generic
  libsmokeqt4-2 libsmokeqt4-3 libjpeg-progs libsmokekde4-2 libpolkit-grant2
  libpolkit2 libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@atum-debian:/home/atum# wget [http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2)
--2010-12-18 13:46:43--  [http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2)
Resolving dl.aircrack-ng.org... 94.23.241.217
Connecting to dl.aircrack-ng.org|94.23.241.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 177591 (173K) [application/octet-stream]
Saving to: `ipwraw-ng-2.3.4-04022008.tar.bz2.2'

100%[======================================>] 177,591      280K/s   in 0.6s    

2010-12-18 13:46:44 (280 KB/s) - `ipwraw-ng-2.3.4-04022008.tar.bz2.2' saved [177591/177591]

root@atum-debian:/home/atum# tar -xjf ipwraw-ng*
tar: ipwraw-ng: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Invalid argument
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: ipwraw-ng-2.3.4-04022008.tar.bz2: Not found in archive
tar: ipwraw-ng-2.3.4-04022008.tar.bz2.1: Not found in archive
tar: ipwraw-ng-2.3.4-04022008.tar.bz2.2: Not found in archive

---

### Post by fly-by-night on 2010-12-18
You downloaded ipwraw-ng-2.3.4-04022008.tar.bz2, then run: tar -xjf ipwraw-ng*

I think you need to specify the full name.

```
tar -xjvf ipwraw-ng-2.3.4-04022008.tar.bz2
```

---

