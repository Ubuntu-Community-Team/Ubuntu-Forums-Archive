---
title: "can't even install ndiswrapper!"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by Kaneda_help_me on 2006-09-04
i'm having alot of issues getting my wireless on my hp zx5000 notebook to work. it's using a broadcom 4306 card. 

i've installed ndiswrapper via synaptic (also installed the gtk and source). i've installed the driver using ndiswrapper both by the gui and by command line (not that it makes any difference). either way, when i type ndiswrapper -l or go to the ndiswrapper gui, it says that the driver is installed and the hardware is detected. the next step in the process is supposed to be "modprobe ndiswrapper" but when i do that i get an error saying that the ndiswrapper module could not be found. 

i've read that if you compile ndiswrapper from source it should get around this problem, however i can't do that either. i'm currently trying to follow the ndiswrapper INSTALL instructions exactly. but, the first step is to do "ls /lib/modules/`uname -r`/build" but when i do that it can't find the /build directory. 

also, when i try to make install i get 

make -C driver install
make[1]: Entering directory `/home/evan/Desktop/ndiswrapper-1.23/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/evan/Desktop/ndiswrapper-1.23/driver'
make: *** [install] Error 2

if anybody could help me with this i would be eternally greatful. i'll even send you 5 bucks over paypal or something so that you can go get a big mac or something. please, i just want to roam around my house with ubuntu internet access!

---

### Post by x64Jimbo on 2006-09-04
try this:
sudo modprobe ndiswrapper

---

### Post by haiku99 on 2006-09-04
this writeup worked for me....
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by lupine_nickt on 2006-09-04
Forget about the money :). 

The compilation problem you're having is that make is looking in /lib/modules/`uname -r`/build for your kernel headers... they aren't there: they're in /usr/src/linux-headers-`uname -r`

(In case you're wondering, anything in `backticks` is run as a command, and replaced with the output of the command - in this case, it's your kernel version).

So, you need to do two things:-

1) Install the kernel headers - really easy: "sudo apt-get install linux-headers-`uname -r`"
2) Sreate a symlink (a "shortcut") so that anyone accessing that build directory gets your kernel headers (this might already be done... check by running "ls -l /lib/modules/`uname -r`/build" - if nothing shows up, then run "sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build")

A few other things you'll need...
1) Firmware: you'll find it at [http://www.lupine.me.uk/bcm43xx/bcm43xx-firmware.tar.gz](http://www.lupine.me.uk/bcm43xx/bcm43xx-firmware.tar.gz) and it wants to go into your /lib/firmware and /lib/firmware/`uname -r` directories.

Easy enough... in terminal:-

```

cd /lib/firmware
sudo wget http://www.lupine.me.uk/bcm43xx/bcm43xx-firmware.tar.gz
sudo tar -xzvf bcm43xx-firmware.tar.gz
sudo mv bcm43xx-firmware.tar.gz `uname -r`
cd `uname -r`
sudo tar -xzvf bcm43xx-firmware.tar.gz
sudo rm  bcm43xx-firmware.tar.fgz

```

You could probably do it with nautilus/Konq. running as root, but this is easier :)

2) If you're not using the native bcm43xx driver, then you want to blacklist it so it doesn't conflict with ndiswrapper... so (as root/sudo) append the following to /etc/modprobe.d/blacklist: "blacklist bcm43xx"

HTH...

xF,

...Nick

---

### Post by madmorpheus on 2006-09-04
Believe it or not I have tried this and it worked consistently for any NDIS wrapper drivers I had to install.

If it installs and works under windows, Install WINE and then install the drivers through WINE.  Then run your NDIS and look for the drivers in the WINE > windows\ directory that WINE creates you will find your driver there and not have the headaches of looking for the right versions over the web.

---

### Post by Kaneda_help_me on 2006-09-06
alright, i got ndiswrapper installed. modprobe worked. it still doesn't seem to be picking up the wireless card though. it seems that when i blacklisted bcm43xx ubuntu stopped recognizing that i even have a wireless card (under system>administrative>networking the card does not show up anymore). is there another way around this?

sorry for being such a nub.

edit: looks like my wired networking has stopped working as well.

---

