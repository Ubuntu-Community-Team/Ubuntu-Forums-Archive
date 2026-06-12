---
title: "rtl8187 patched and updated, but won't work"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by datapusher on 2007-07-20
Ok, so i am at a standstill here. I don't seem to be having any luck. I have googled this issue and looked on all the relevant forums.  I have reinstalled ubuntu 5 times now trying to get aircrack-ng to work with Ubuntu with my Netgear WG111v2 USB dongle.  Below I have included my complete process from install of the OS to where I am now.  i have included as much info as possible for you (I used to be an admin long ago, so I am big on backups and documentation).  I have also formatted it in an easy to read fashion.  I know it may seem long, but I have tried to provide everything you need to help me with this dilema.  thank you for your time...

Some essential info:
Ubuntu 7.04 Feisty Fawn Kernal 2.6.20.15 Generic
Netgear WG111v2 USB Wireless (Realtech 8187 Chipset)

Configured nic to allow internet access

Saved orig Dmesg output for future reference:
```
 sudo dmesg > Desktop/dmesg.txt
```

Copied and modified grub to allow boot to Win + FreeBSD
```
 sudo cp /boot/grub/menu.lst Desktop/menu.lst.backup
 sudo pico /boot/grub/menu.lst
```

Updated Repositories and installed essentials to computer:
```
 sudo aptitude update
 sudo aptitude install build-essential
```

Moved to Desktop for easier access:
```
 cd Desktop/
```

Downloaded Stable Aircrack-ng as per Aircrack website instructions:
```
 wget [http://download.aircrack-ng.org/aircrack-ng-0.9.1.tar.gz](http://download.aircrack-ng.org/aircrack-ng-0.9.1.tar.gz)
 tar -zxvf aircrack-ng-0.9.1.tar.gz
 cd aircrack-ng-0.9.1
 make
 sudo make install
```

Rebooted Machine

Checked what the output of iwconfig was:
```
 wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
           RTS thr:off   Fragment thr=2346 B   
          
 wlan0     IEEE 802.11g  ESSID:""  
           Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
           RTS thr:off   Fragment thr=2346 B   
           Link Quality:0  Signal level:0  Noise level:0
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Confirmed that monito mode was not supported with current drivers (ya know, just to be sure):
```
 sudo airmon-ng start wlan0

 Interface       Chipset         Driver
 wmaster         Unknown         Unknown (MONITOR MODE NOT SUPPORTED)
 wlan0           Unknown         Unknown (MONITOR MODE NOT SUPPORTED)
```

Ok now time to patch the drivers.  this is where everything goes pear shaped.  Now remember that I am running kernal 2.6.20.15.  However I have to use the instructions for kernals above 2.6.21 found here: [http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187)

Why you may ask, because after reading the instructions on the R8187 driver on aircracks site.  This is based soley on the fact that when i run ifconfig or iwconfig I see that wmaster0 is present.  Based on this fact, I need to (or it appears to me) use the kernal > 2.6.21 instructions. Now keep in mind, at this very point in time, I am still able to use my wireless card.  i can still see and join networks.  If the last 4 attempts this week have shown me anything, this is all about to change... right now.  ok moving on.

First I need to rmmod the rtl8187 module:
 ```
sudo ifconfig wlan0 down	 
 sudo rmmod rtl8187
```

As instructed I move the rtl8187.ko to a safe place:
 ```
sudo mv /lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rtl8187/rtl8187.ko Desktop/rtl8187.ko.backup
```

Now I download and install the updated driver from aircrack's mirrors:
```
 wget [ftp://220.228.150.22/cn/wlan/rtl8187_linux_26.1010.zip](ftp://220.228.150.22/cn/wlan/rtl8187_linux_26.1010.zip)
 unzip rtl8187_linux_26.1010.zip
 cd rtl8187_linux_26.1010.0622.2006/
 wget [http://patches.aircrack-ng.org/rtl8187_2.6.21v5.patch](http://patches.aircrack-ng.org/rtl8187_2.6.21v5.patch)
 tar xzf drv.tar.gz
 tar xzf stack.tar.gz
 patch -Np1 -i rtl8187_2.6.21v5.patch
 make
 sudo make install
```

Then I reboot.

Ok, let's see what iwconfig sees now that I updated and patched the drivers:
Hrm... Just as the previous attempts, iwconfig no longer shows wmaster0 or wlan0.

Let's try some things.
They are absent from the output of ifconfig as well
hrm, ok

 ```
sudo sh wlan0up
 sh: Can't open wlan0up
```

ok let's see what happens when i do this:
```
 lsusb
 Bus 001 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
 Bus 001 Device 001: ID 0000:0000
```

Ok might as well save a new dmesg so you can compare if need be:
 ```
dmesg > Desktop/dmesg_afterpatch.txt 
```

Ok so it still sees it is there, it just won't let me do anything.  Now I have no idea where to go. I have googled this issue and looked on all the relevant forums.  Any guidence on where to go next would be appreciated.  I know I can't use ndiswrapper becasue it does not allow monitor mode in aircrack.  So how do I get my WG111v2 to work with ubuntu abd aircrack-ng? Thank you again for your time.

At the very least since I have been so indepth with the steps, maybe this could help someone else going through the same problem as myself.  Who know...

---

### Post by kevdog on 2007-07-20
Ive never done this before, but something seems missing from what you posted.  I see you did the following:

>  wget [ftp://220.228.150.22/cn/wlan/rtl8187_linux_26.1010.zip](ftp://220.228.150.22/cn/wlan/rtl8187_linux_26.1010.zip)
 unzip rtl8187_linux_26.1010.zip
 cd rtl8187_linux_26.1010.0622.2006/
 wget [http://patches.aircrack-ng.org/rtl8187_2.6.21v5.patch](http://patches.aircrack-ng.org/rtl8187_2.6.21v5.patch)
 tar xzf drv.tar.gz
 tar xzf stack.tar.gz
 patch -Np1 -i rtl8187_2.6.21v5.patch
 make
 sudo make install

So I guess you installed a new rtl8187 driver, but did you really?  Dont you need to add the driver with
sudo modprobe rtl8187? (Im just assuming this)

Here's a couple of things you can do to check things.
sudo modinfo
is a good command.  It gives you info about modules you have installed.  Do a sudo modinfo rtl8187 and see what it states.  It should give you info where you downloaded the version, etc.

Another good debugging command is:
lshw -C network

This will show the driver currently associated with your card.  If no driver is associated, then the driver is either bad, not loaded, etc.

Of course you know about dmesg, this may help you also debug.

Keep me posted!!

---

### Post by datapusher on 2007-07-20
Ok so I did: sudo lshw -C network and it only shows my PCI 10/100 card.  no mention of a USB wireless card anywhere.

I also ran sudo modinfo rtl8187 and got:
modinfo: could not find module rtl8187

I also noticed earlier when i compared the dmesg outputs that the dmesg oputput from after the patch and make install... this dmesg has no mention of the wlan0 wmaster or anywhere where it says rtl8187.  howevger my original dmesg does.

So why would aircracks minstall and patching instructions leave out the actual install.  What did my make and make install do?  What did the patching do?

I looked in the driver directory where I made make install.  I saw something and went for it.  i ran sudo sh wlan0up and now I can see wlan0 in iwconfig, ifconfig and lshw -C network.  however, nothing comes up in modinfo rtl8187.

Also for the record, wmaster0 is no longer present, but wlan0 is.

here is the output from the various commands I ran.  i can surf the web on my wireless, but on reboot I havbe to run sudo sh wlan0up again to get wireless working.  So whats the deal here.  how do i fix this.

/Desktop/rtl8187_linux_26.1010.0622.2006$ sudo sh wlan0up

sudo modprobe rtl8187
FATAL: Module rtl8187 not found.

ifconfig

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:D4:0A:CE  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:16 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1222 (1.1 KiB)  TX bytes:2563 (2.5 KiB)

sudo lshw -C network
  *-network               
       (Ethernet interface info deleted for space)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:b5:d4:0a:ce
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.100 multicast=yes wireless=802.11b/g linked

sudo modinfo rtl8187
modinfo: could not find module rtl8187

sudo modprobe rtl8187
FATAL: Module rtl8187 not found.

Where do i go from here.  i would count this as progress. 

Why did they not mention this in the tutorial.  odd

Thanks

---

### Post by kevdog on 2007-07-21
Again, Ive never done this so Im only speculating.

Its obvious that the module isnt loaded even after make install.  Im not sure if this is a mistake or how its designed.  Is there an INSTALL or README file in the directory where you downloaded the patches or drivers?

Could you also post a link to the rtl8187 patch site where the instructions are listed??  Ive read them once about a week ago, but since I dont have a rtl card, I didnt delve into it with great enthusiasm.

I wouldn't worry about the wlan0 or wmaster right now.  It might be resolved once the driver is loaded.  Concentrate on getting the driver loaded with the card for now.  The interface name is just a distraction.

The rtl8187 isnt still blacklisted in the blacklist file is it?

EDIT
I found the documentation
What does 
sudo modinfo r8187
show?

Can you post you blacklist file?

---

### Post by datapusher on 2007-07-25
> **kevdog said:**
> Again, Ive never done this so Im only speculating.

Its obvious that the module isnt loaded even after make install.  Im not sure if this is a mistake or how its designed.  Is there an INSTALL or README file in the directory where you downloaded the patches or drivers?

Could you also post a link to the rtl8187 patch site where the instructions are listed??  Ive read them once about a week ago, but since I dont have a rtl card, I didnt delve into it with great enthusiasm.

I wouldn't worry about the wlan0 or wmaster right now.  It might be resolved once the driver is loaded.  Concentrate on getting the driver loaded with the card for now.  The interface name is just a distraction.

The rtl8187 isnt still blacklisted in the blacklist file is it?

EDIT
I found the documentation
What does 
sudo modinfo r8187
show?

Can you post you blacklist file?

The documentation you desire has been linked in a previous post by me above.

I was able to get it working temporarily.  I have since successfully used the  aircrack-ng suite for it's desired purpose.  So the wireless drivers work.

HOWEVER, this is only temporary.  Everytime I reboot, I still lose connectivity.  When the machine comes back up I have no wireless. ifconfig and iwconfig both mention no wireless.   I have found that 2 methods bring the card back up.

Either sudo modinfo r8187 or sh wlan0up make my wireless magically come back.

So that is a pain in the but.  I ended up looking at the blacklist file and I commented out the r8187 but **NOT **the r818x.

Since then it seems to load the wireless on boot.

Should I comment out the other driver?  Or leave as be since it appears to be working?

As for the blacklist file:
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
[B]blacklist r818x
#blacklist r8187
[/B]

---

### Post by kevdog on 2007-07-25
Congratulations on getting it to work -- your the first person Ive seen to get this to work.  As far as the uncommenting, you could try commenting the other line to see what it does.  If it doesnt work, then reblacklist it.  Personally I dont think its going to matter.

I guess everything works then for you.  Supposedly you can use the aircrack utilities to find WEP addresses from another network using this patch.

If you get time - think about posting a How-To for patching.  I think it would be a welcome addition to these forums.

---

### Post by salvatore001 on 2007-08-10
hi

i installed xubuntu and trying to get the r8187 patched module to work

i have accomplished all the steps above withouth problems but when i modprobe the modules i get the 'unknow symbol in module, or unknown parameter' error


i already tried this

```
cd beta-8187
rm -f Modules.symvers
ln -s ../ieee80211/Modules.symvers Modules.symvers
### NOTE versions of GCC may require this instead: ln -s ../ieee80211/Module.symvers Module.symvers
cd ..
sh makedrvbk
```

but still get the same error
can you help me with this one?

kernel installed is 2.6.20-16-generic

thanks

---

### Post by datapusher on 2007-08-11
> **kevdog said:**
> Congratulations on getting it to work -- your the first person Ive seen to get this to work.  As far as the uncommenting, you could try commenting the other line to see what it does.  If it doesnt work, then reblacklist it.  Personally I dont think its going to matter.

I guess everything works then for you.  Supposedly you can use the aircrack utilities to find WEP addresses from another network using this patch.

If you get time - think about posting a How-To for patching.  I think it would be a welcome addition to these forums.

I think I might just have to do that

---

### Post by salvatore001 on 2007-08-13
oh please i'll be glad of that :) :)

---

