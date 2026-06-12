---
title: "USB tethering just stopped working"
date: 2016-02-02
forum: Networking &amp; Wireless
---

### Post by timswait on 2016-02-02
I use USB tethering as my only connection on a desktop computer running Kubuntu Trusty on a boat. It's always worked without problem but had just now suddenly failed. I have checked the tethering with the same phone on a laptop also running Kubuntu Trusty and its fine. Plugging the phone in and selecting tethering doesn't show anything in network manager. There's no connection if I use Firefox. Typing ifconfig -a does list usb0 as a connection and it doesn't when I unplug the phone so this must be it. However typing sudo ifup usb0 just returns "Ignoring unknown interface usb0=usb0" How can I fix this? (and of course as I can't connect to the internet I can't download anything!)

---

### Post by Hadaka on 2016-02-02
Hi,without any internet access to the machine it may prove difficult to diagnose the problem.
Try to boot to an earlier kernel version and see if you can then connect.To boot to an earlier
version, first power down your PC then, power it back up while holding down the **SHIFT KEY**
this will take you to the GRUB recovery screen..choose **BOOT TO PREVIOUS LINUX VERSION**
not the recovery, just a regular linux version. boot and see if it will then connect to your mobile 
phone. If it does, then the issue was caused by an update. To repair you will need a working wired
connection or continue to boot each time in the grub/previous linux image untill the next update hopefully
fixes the problem. Report back and tell us if booting to an earlier version helped.
thanks.

---

### Post by timswait on 2016-02-02
Nope, tried booting into 3.13.0-74 and 3.2.0-61 as well as the normal 3.13.0-77. All give the same lack of connectivity. Actually I did install some updates recently, I can't remember for sure but I think that probably was when it stopped working. I don't remember what the updates were, I didn't really look and just installed them (there was a new kernel in there, but it does appear not to be the kernel if the old versions don't work either).

---

### Post by Hadaka on 2016-02-02
OK, to help us maybe know which direction to look if you could post the 
output of..
```
lspci -n | awk '/0280/{print$3}'
```
from the laptop running Kubuntu Trusty that works on you phone tether if possible
and on your desktop that is failing. This will help us determine
if its a driver/wifi card issue or something else.
thanks.

---

### Post by timswait on 2016-02-03
When I enter that command on the working laptop I get "14e4:4727" returned. When I enter it on the not working desktop I get nothing whatsoever returned, just another command prompt on the next line.

---

### Post by Hadaka on 2016-02-03
Hi, thanks that helps, the laptop that is working has a 14e4:4727 broadcom card which usually
has the WL bcmwl-kernel-source driver and is obviously working. Your desktop is showing no
wireless card. *Note please do not try to load the wl driver, it will make things worse if you do not
have that exact wireless card.
OK, let's dig a bit deeper and see what we find. Do you recall doing an update recently ? Last couple of days?
also please verify yes/no if you have "Pre-released updates" checked in your software sources selection.
to view..
On the left side launcher...Click - **Software Center**>>**Edit**>>**Software Sources**>>**Udates **tab
verify if the **Pre-released updates** is checked/unchecked...see attached.
[ATTACH=CONFIG]267099[/ATTACH]
It should be unchecked. Please report your findings
thanks.

---

### Post by timswait on 2016-02-03
I did install some updates shortly before it stopped working. I can't remember what they were though. There were quite a few as it had been a while since I'd updated it. It was set to install both pre released and unsupported updates (I've now unchecked these boxes!)

---

### Post by Hadaka on 2016-02-03
Hi, thanks for being patient, hopefully we are making progress
let's check one more thing please. post the out put of..
anything from the # on is just a comment..do the left side command
```
lsb_release -a | awk '/De/{print$3}' #post just the number
uname -m #If you get i686, it's 32bit. Otherwise it's 64bit
```
thanks.

---

### Post by timswait on 2016-02-03
Thank you for your help, it's very much appreciated, I'm hoping to get to the bottom of it.
It's version 14.04.3 and 64 bit (the laptop is also).
One other thing that may help - I also installed from binary a driver for a Turbosight TV tuner card. I have to re-install these every time the kernel is upgraded, it's a bit of a pain but I do it every time and have never had a problem before. Also if I recall correctly, I believe the internet had actually stopped working before I got round to reinstalling those anyway, so I don't really think this has anything to do with it, just thought I'd mention it.

---

### Post by timswait on 2016-02-03
Thinking it must be one of the pre-release updates I installed (not realising it was set to include them). It just occurred to me to look at the laptop. The laptop wasn't set to look for pre-release updates, so won't have any installed. So I decided to see how many there are so I checked the box and refreshed the list (don't worry I'm not going to install them!). The list is as follows:
```
 cpp-4.8 dvd+rw-tools g++-4.8 gcc-4.8 gcc-4.8-base gcc-4.8-base:i386
  gcj-4.8-jre-lib growisofs hplip hplip-data kde-l10n-engb language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  libasan0 libatomic1 libgcc-4.8-dev libgcj14 libgfortran3 libgomp1
  libgudev-1.0-0 libhpmud0 libibus-1.0-5 libitm1 libnl-3-200 libnl-genl-3-200
  libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-util2 libpam-systemd
  libparted0debian1 libpci-dev libpci3 libquadmath0 libsane-hpaio
  libstdc++-4.8-dev libstdc++6 libstdc++6:i386 libsystemd-daemon0
  libsystemd-login0 libtsan0 libudev1 libudev1:i386 login lsb-base lsb-core
  lsb-invalid-mta lsb-release lsb-security network-manager ntpdate
  openssh-client parted passwd pciutils printer-driver-hpcups
  printer-driver-hpijs printer-driver-postscript-hp systemd-services udev
  usb-creator-common usb-creator-kde usbutils
```
So this is presumably the list of packages that are upgraded on the desktop (that doesn't work) but not on the laptop (that does). So probably one of them is the culprit! Most of them don't mean anything to me, but I notice that network-manager and usbutils are listed there, so to me it seems a fair bet that one of those is pretty likely. How can I roll these packages back on the desktop to the same version that's on the laptop? Without having internet on the desktop to do it! I can download files on the laptop and use a flash drive to copy them onto the desktop.

---

### Post by Hadaka on 2016-02-03
OK, hopefully this will do the trick, it will require you to have a 
working internet connection and a usb stick to copy some files to transfer
to the faulty Ubuntu machine. Please go here...
[http://packages.ubuntu.com/source/trusty/libnl3](http://packages.ubuntu.com/source/trusty/libnl3)
[B]these 3 files
[/B]
 libnl-3-200_3.2.21-1_amd64.deb
 libnl-genl-3-200_3.2.21-1_amd64.deb
 libnl-route-3-200_3.2.21-1_amd64.deb
be sure to load the 64bit version.
  Download the 3 files one at a time to the usb stick
once on the stick transfer them to the Ubuntu machine and copy them to Downloads
then open a terminal and do..
```
cd Downloads
sudo dpkg -i *.deb
```
boot and cross your fingers..
please report ,

---

### Post by timswait on 2016-02-03
Maybe I'm missing something, but do you mean the files "libnl3_3.2.21-1.dsc", "libnl3_3.2.21.orig.tar.gz" and "libnl3_3.2.21-1.debian.tar.gz"? None of those file are .deb so when I try to install *.deb it just returns that no files are found. Do I need to unpack them somewhere first?

---

### Post by Hadaka on 2016-02-03
I was in rthe middle of an edit when you jumped on i think.
re read and see if that makes more sense
this is my source for the possible fix
[http://ubuntuforums.org/showthread.php?t=2311705](http://ubuntuforums.org/showthread.php?t=2311705)
thanks.

---

### Post by timswait on 2016-02-03
YAY!!!!
That's fixed it, thank you so much for your help!!

---

### Post by Hadaka on 2016-02-03
Fantastic,thanks for your [COLOR=#000000][FONT=Sans][/FONT][/COLOR]patience as i stumbeled along.
It looks like the problem may be solved with the next update per
last page here
[http://ubuntuforums.org/showthread.php?t=2311705](http://ubuntuforums.org/showthread.php?t=2311705)
i would suggest you double check your software sources are still unchecked and do...
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove 
sudo apt-get autoclean
```
thanks.

---

### Post by timswait on 2016-02-03
Cheers.

---

### Post by Hadaka on 2016-02-03
oops

---

