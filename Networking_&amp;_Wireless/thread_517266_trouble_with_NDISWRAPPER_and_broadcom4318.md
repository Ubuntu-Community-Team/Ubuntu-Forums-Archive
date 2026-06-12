---
title: "trouble with NDISWRAPPER and broadcom4318"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by edwin.e.johnson on 2007-08-04
hello well i have read like every post on this site about ndis and most say it is included on the ubuntu cd.... well i am running feisty and every time i try to install ndiswrapper it says its not in the pools.... i also pluged into the internet and checked tghe repos its not there either... anyone know what the deal is?

all my repos are activated!

also i download the file from "broadcom 4318 the easy way post" which installs the firmware or the windows driver with ndis... but it only works when im pluged into the net.. why is this?.

and can someone please post in here exactly what you had to do to get your broadcom4318 card to work that would be awesome!..

thankyou

---

### Post by kevdog on 2007-08-04
Here are my "universal installation instructions" for ndiswrapper:

This requires installing ndiswrapper from source.  If you have a previous version of ndiswrapper installed, please see the uinstallation method at the bottom.  If the old version is not uninstalled properly, installation of a newer version may not work appropriately.

First there are a few things you need to do to compile from source -- install the build-essential package along with the linux header files.  Here is how to do this in case you dont have an internet conneciton:

```
If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


Ok, next grab the ndiswrapper source files from: _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_
You want ndiswrapper-1.47

Working at command line
```
cd ~
mkdir ndiswrapper
cd ndiswrapper
Place the ndiswrapper-1.47.tar.gz inside this ~/ndiswrapper

```
To proceed
```
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```

The output should be something like the following:
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586

```

Next create and place your Windows XP wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the WinXP driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:
> 
bcmwl5: driver installed
device (14E4:4320) present


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg
```
and look for something like:
> ndiswrapper version *version* loaded

Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.
```
sudo shutdown -r now
```

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running. 


***Addendum  Uninstallation Instructions for ndiswrapper
```

sudo aptitude purge ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo rmmod ndiswrapper
sudo rm -rf /etc/ndiswrapper/*
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko

```

---

### Post by edwin.e.johnson on 2007-08-05
well dude it kinda worked.... the only problem i had was at the "sudo aptitude update"

i HAD to be connected to the internet for it to work. i dont know why

and the last thing was i had to blacklist my old driver bcm43xx

here is the command in case anyone else is using this.

Blacklist bcm43xx:

```
sudo gedit /etc/modprobe.d/blacklist
```
At the bottom, add

```
blacklist bcm43xx
```
This should prevent bcm43xx from running again when you start up your laptop.

---

