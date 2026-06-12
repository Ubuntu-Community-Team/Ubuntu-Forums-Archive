---
title: "ndiswrapper freezes system"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by nolefan_01 on 2007-08-14
I'm completely new to Linux so please excuse the question if it's simple or redundant. I just installed 7.04 on an older Dell desktop. The network card worked fine at install but I ultimately want to use the PC in a location that will require wireless access. 

I'm trying to install a Trendnet 444UB (usb device). I followed the directions in help and everything went fine through the ndiswrapper -l step, where I can see that the drivers are loaded. The problem comes when I do modprobe ndiswrapper. Following this command the terminal session and system completely freezes and the only way out is a power off restart. 

I know I'm close because the device lights up when I do the command and the system freezes. Any help would be greatly appreciated.

---

### Post by kevdog on 2007-08-14
Do you know the chipset of your device -- may have to google for it?  The only reason Im asking is that there are multiple ways to install drivers for a wireless device.  ndiswrapper works for many devices, however probably not the ideal choice for all chipsets, for example ra chipsets.

---

### Post by nolefan_01 on 2007-08-14
I believe the chipset is AR5523, from Atheros Communications Inc.

Thanks.

---

### Post by kevdog on 2007-08-14
Ok so you are right, you will need to use ndiswrapper since the madwifi drivers do not support USB - only pci devices.  Where did you get your driver??? Did you check the ndiswrapper website for a possble alternative driver??  

Can you also post your ndiswrapper version??

ndiswrapper -v

---

### Post by nolefan_01 on 2007-08-14
I used the driver off the manufacturer's CD. I checked the ndiswrapper website for drivers and it said the one they had is the same as the one of the CD. As for the version of ndiswrapper, I'm not in front of the system at the moment but I can tell you that I just installed 7.04 and did not make any changes to the version of ndiswrapper that was included (I don't know how at this point).

---

### Post by kevdog on 2007-08-14
To my knowledge (in fact Im almost certain), ndiswrapper isnt installed by default.  You either need to install it from repository (like Synaptic), or download, compile and install ndiswrapper from source files.

When you get back if you can post the version of ndiswrapper it would help.  The old version 1.38 included in the repositories causes a lot of problems for many users in feisty.  My recommended approach is to compile and install the latest release candidate version (1.48rc1 I believe).

Post back with more info and i can walk you through how to do this!

---

### Post by nolefan_01 on 2007-08-14
I think you're correct. I remember clicking on ndiswrapper-util.....to install it. The terminology is a bit different for me at this point. I will post the version information this evening. In the meantime, can you point me to a link that will tell me how to upgrade my ndiswrapper version to the one you suggest?

Thanks.

---

### Post by kevdog on 2007-08-14
**[SIZE="4"]Ndiswrapper Uninstall Instructions[/SIZE]**
Ok before installing the new ndiswrapper packages we need to uninstall the old version completely. Dont worry if some of these commands dont do anything or seem not to work -- some may be repetitive.

```

sudo aptitude purge ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo sh -c "sed '/^ndiswrapper$/d' /etc/modules > /etc/modules.temp.rm; mv /etc/modules.temp.rm /etc/modules"
sudo rmmod ndiswrapper
sudo /lib/modules/`uname -r`/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
sudo rm -rf /etc/ndiswrapper
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko

```

**[SIZE="4"]Download, Compiling, Installing and Configuring Ndiswrapper from Source Files[/SIZE]**

If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

```

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


OK next we want to download the ndiswrapper source files (Reference URL = _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_)

We are grabbing ndiswrapper-1.48-rc1

```
cd ~
mkdir ndiswrapper
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz -O ~/ndiswrapper/ndiswrapper-1.48rc1.tar.gz 
cd ndiswrapper

```

Extract, compile, and install ndiswrapper
```
tar -zxvf ndiswrapper-1.48rc1.tar.gz
cd ndiswrapper-1.48rc1
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
version:        1.48rc1
vermagic:       2.6.20-16-generic SMP mod_unload 586

```

Next create and place your Window's wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the Window's driver are in the~/driver directory:
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

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running

---

### Post by nolefan_01 on 2007-08-14
I found some notes I made last night and I believe I'm using version 1.38 of ndiswrapper. Tonight I will try the process you outlined and let you know how it goes.

Thank you.

---

