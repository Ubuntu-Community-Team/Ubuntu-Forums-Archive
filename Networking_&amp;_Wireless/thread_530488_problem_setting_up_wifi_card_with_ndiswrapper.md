---
title: "problem setting up wifi card with ndiswrapper"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by mindtch0101 on 2007-08-20
hi i've been trying to install a wifi card on my notebook with ndiswrapper and i'm stuck at one step.

here are some specs:
Compaq Presario v2000
Broadcom BCM4318 (AirForce One 54g) wireless LAN controller
Ubuntu 6.06 LTS

When I first installed ubuntu and tried configuring the wireless connection and activated it, it acted like it was activated, but when I clicked ok, it seemingly deactivated. I thought it was a bad driver, so I downloaded and installed ndiswrapper from add/remove programs, got the windows drivers, and proceeded with these steps:

root@mason-laptop:/home/mason/Desktop/wlandriverstuff/wlandriver# ndiswrapper -i bcmwl5.ini
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
(the above message duplicated itself 14 times)

root@mason-laptop:/home/mason/Desktop/wlandriverstuff/wlandriver# ndiswrapper -l
Installed ndis drivers:
bcmwl5     driver present, hardware present

root@mason-laptop:/home/mason/Desktop/wlandriverstuff/wlandriver# modprobe ndiswrapper

root@mason-laptop:/home/mason/Desktop/wlandriverstuff/wlandriver# ndiswrapper -m
modprobe config already contains alias directive

And this is where i'm stuck. I've done these steps once before but i accidentily skipped entering "modprobe ndiswrapper" before "ndiswrapper -m". Maybe i should find the modprobe config, delete the alias directive, and retry?, if so where would i find the modprobe config file? Any suggestions would be appreciated

Thanks,
Mason

---

### Post by tommy18crowe on 2007-08-20
uninstall ndiswrapper  > open terminal > sudo apt-get install bcm43xx-fwcutter

---

### Post by hghtn on 2007-08-22
This might sound isane but how and where do I install ndiswrapper? I have it on a memory stick in the usb, I see it but don't know how to install it

---

### Post by kevdog on 2007-08-22
Mason

I see nothing wrong with what you have done.  Things might not work, but it wasnt from anything you have done wrong previous to this point

For all posters Ive included my ndiswrapper install instructions -- assuming you want to install from source (which is what I recommend). 

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

***The following section will work if you have an internet connection
*** If you do not have an internet connection, on a different computer you will need to download the ndiswrapper source file from: 
[http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz)
Please place this file on a flash drive (USB Flash drive), transfer it to the Ubuntu machine, and then place it in the ~/ndiswrapper directory.  Continue with the next following set of instructions
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

### Post by likemindead on 2007-08-22
Follow [this thread]("http://ubuntuforums.org/showthread.php?t=405990") exactly.

Also uninstall network-manager and install Wicd.

I did and my BCM4318 is rocking and rolling now! :guitar:

---

