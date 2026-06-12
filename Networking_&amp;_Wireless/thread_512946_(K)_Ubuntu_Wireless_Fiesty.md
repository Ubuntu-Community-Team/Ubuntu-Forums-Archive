---
title: "(K) Ubuntu Wireless Fiesty"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by Frizguru on 2007-07-29
I have been running Ubuntu for almost 3 years now and have consistantlly has issues in regards to the wireless internet, but have been able to work them out. 

Recently, I switched to Kubuntu for a change of pace. Instantly, my wireless internet crashed. I was not allowed to install via CD since it would come up with a BCM43xx-microcode error. Others have gotten it too so I am not alone.

However, after reading hundreds of forums about fixing wireless networks, I have made it only so far.

I am able to search and find all wireless networks in my area, but when I try to connect it will always say "Configuring Device" and will never go farther. It will then time out and I cannot connect. 

I have tried using knetworkmanager (network-manager-kde no longer exists apparently), WICD, KWifi, and WifiRadar.

Any and all help would be greatly appreciated. I know others could use it as well.

---

### Post by kevdog on 2007-07-29
You need to tell us more about your wireless card, drivers you use for the card.  32 vs 64 bit Ubuntu.

---

### Post by Frizguru on 2007-07-30
lspci prints: 02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Originally I had used ndiswrapper, but switched to bcm43xx-fwcutter with Edgy, and Fiesty now, and have not had problems. Until Kubuntu which will not let me use either to connect.  I am using the 32bit version. Any other info needed?

---

### Post by kevdog on 2007-07-30
What driver is currently installed??
lshw -C network

Im missing something -- the bcm43xx driver was working with Feisty Ubuntu, but will not with with Feisty Kubuntu?

Have you checked the /etc/modprobe.d/blacklist to make sure that the correct driver is not blacklisted??

Which do you prefer -- ndiswrapper or bcm43xx.  Both should work for you?

Are you getting further error messages in dmesg that might help clarify the problem you are having?  I have the exact same wireless card as you (well at least the Broadcom chipset - brand of card a Linksys WPC54GS), originally installed bcm43xx drivers, then switched to ndiswrapper, then switched to ubuntu (for change) from Kubuntu (both desktops are installed), and can confirm I didnt do anything to change the wireless drivers.  When you switched to Kubuntu, is this a totally new installation or did you just install the kde desktop on top of the ubuntu distribution?

---

### Post by Frizguru on 2007-07-30
lsch -C network:
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:18:7a:4c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.1.205 latency=32 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:f5ffe000-f5ffffff irq:17
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 03
       serial: 00:90:96:be:3f:d8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=32 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:f5ffc000-f5ffdfff irq:20

There is no blacklisting of anything to do with networking. And yes, I had bcm43xx working properly and smoothly in Fiesty Ubuntu, but when I switched to Fiesty Kubuntu, it stopped. It made no sense since it should not make a difference. I would prefer to use bcm43xx I guess, but I will switch to get it to work.

When I installed the Kubuntu desktop, I tried to install over Ubuntu, But the installation would not proceed due to the bcm43xx-microcode.fw error. So I installed Kubuntu's desktop over Gnome and have to use Gnome to access the internet.

dmseg: (this is repeated over and over, but is the only thing appearing to be network related)

[39720.540000] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[39720.540000]     Additional sense: Medium not present
[39720.540000] end_request: I/O error, dev sr0, sector 0
[39720.540000] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[39720.540000]     Additional sense: Medium not present
[39720.540000] end_request: I/O error, dev sr0, sector 4

---

### Post by kevdog on 2007-07-30
A strange problem for sure.  Have you tried reinstalling the bcm43xx drivers??  I you have and no luck I guess we are stuck with ndiswrapper.

---

### Post by Frizguru on 2007-07-30
I have tried completely removing the bcm43xx driver and reinstalling it, and have tried to update it. It says it is up to date and I have the newest release.

---

### Post by kevdog on 2007-07-30
Here are my "universal instructions" for ndiswrapper:

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

---

### Post by Frizguru on 2007-07-30
When I do this step:

> Ensuring the ***.sys and ***.inf file for the WinXP driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Here is what I get for ndiswrapper -l:
```
frizguru@Frizguru:~$ ndiswrapper -l
bcmwl5 : invalid driver!
bcmwl5a : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
bcmwl5.sys : invalid driver!
wl_apsta.o : invalid driver!
```

---

### Post by kevdog on 2007-07-30
First blacklist the bcm43xx driver

```
sudo gedit /etc/modprobe.d/blacklist
```

Add to the bottom of the file (if not already present):
```
blacklist bcm43xx
```

Next
You can not have multiple drivers loaded with ndiswrapper -- or an error will occur.  Delete all the old drivers like this:
```
sudo rm -R /etc/ndiswrapper/*
```

Then pick up on the tutorial attempting to load the windows driver into ndiswrapper

```
sudo ndiswrapper ****.inf
```

---

### Post by Frizguru on 2007-07-30
Alright, I am not sure what happened, but it suddenly works now. However, not in Ubuntu, only in Kubuntu. But that should be fine for now.
 Thank you so much for your help! Hopefully it will continue to work. If not, I will let you know.

THANKS!!

---

### Post by kevdog on 2007-07-30
Did it work before of after what I recommended in the previous post??

---

### Post by Frizguru on 2007-07-30
Just before. I realized I should probably get rid of bcm43xx driver before continuing, and apparently, that did the same as blacklisting bcm43xx. Ndiswrapper could not run with both simultaneously apparently.

---

### Post by kevdog on 2007-07-30
you might be listed as a noob in this forum, but I give you credit.  You actually "used your brain" and figured something out "logically".  Now if only most of the people in this forum would do this??:confused:

---

### Post by Frizguru on 2007-07-30
For some reason, when I reboot, I still do not have a connection. I can find them all, but can still not connect to any networks. I have looked into /etc/iftab and /etc/network/interfaces.

---

