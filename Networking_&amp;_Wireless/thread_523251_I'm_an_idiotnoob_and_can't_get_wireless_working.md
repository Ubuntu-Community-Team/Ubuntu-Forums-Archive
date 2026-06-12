---
title: "I'm an idiot/noob and can't get wireless working"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by askantik on 2007-08-11
Ok, I've read through more forums, walk-throughs, and tutorials than I can possibly recall and my head is hurting.  I'm totally new to both Ubuntu and Linux in general.  This is my first time venturing outside of ol' Winders.

I have an Acer Aspire 3002LCI that I easily installed Feisty Fawn on and I'm liking it so far.  Of course, wired ethernet connection worked flawlessly.  Wireless has been a different story.  My network is WPA.  I had a heck of a time with Network Manager, tried a bunch of terminal stuff, then tried WCID.  With WCID, I could "connect" to the router, but it got stuck on "Obtaining IP address."  After fiddling with some more ndiswrapper stuff (no idea what that even is, just did various things from links I found),_I can't even get the wired connection to work anymore._  

I believe that my wireless chipset is a Broadcom BCM4318.  This link: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom) says about my card: 

"Works on and off with both Ndiswrapper and Fwcutter methods. **The majority of the difficulty is just getting the connection.** Ndiswrapper method has been working the best."

My question to you all is, can you give me a CLEAR (clear as in to your dumbass grandma who has never turned on the computer--- that's me with Linux) guide to getting my wireless card working.  I don't care if it's long or if I have to use the terminal.  I just want to get this thing working so that I can actually use it.  I've had Ubuntu on my laptop for several days now and haven't actually been able to sit down and *use* it because I've been screwing with the wireless.

If you can point me to a noobified guide, I'll happily do a fresh install of Ubuntu and start all over.  Thanks for your time.  :)

---

### Post by kevdog on 2007-08-11
Since you have a wired connection, you are in business. 

First if you could post the following so we can definitively know about your card:

lspci -nn
lshw -C network


Next, you tried installing ndiswrapper.  How did you try to do this??? Meaning did you install ndiswrapper from source, or using synaptic.  Just wondering.

---

### Post by askantik on 2007-08-11
My wired connection isn't working right now...  It was, but apparently I screwed it up.  I think I installed ndiswrapper with the Synaptic thing.  I had 1.38 on there but I read on some forum that a newer version of ndiswrapper might fix my problem.  So I tried 1.47 (stable version), but that's when I screwed it up, I think.

Anyhow, it'd be easier to start from scratch I think, since I don't really know what all I did, but here's the info about my card:

> cody@Cody:~$ lspci -nn 
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 760/M760 Host [1039:0760] (rev 03) 
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SG86C202 [1039:0002] 
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] [1039:0963] (rev 25) 
00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller [1039:0016] 
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] 
00:02.6 Modem [0703]: Silicon Integrated Systems [SiS] AC'97 Modem Controller [1039:7013] (rev a0) 
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0) 
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f) 
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f) 
00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002] 
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91) 
00:06.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02) 
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02) 
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100] 
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101] 
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102] 
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103] 
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330] 
cody@Cody:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network:0             
       description: Ethernet interface 
       product: SiS900 PCI Fast Ethernet 
       vendor: Silicon Integrated Systems [SiS] 
       physical id: 4 
       bus info: pci@00:04.0 
       logical name: eth0 
       version: 91 
       serial: 00:c0:9f:93:29:cd 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=173 maxlatency=11 mingnt=52 multicast=yes 
       resources: ioport:1800-18ff iomemory:e2005000-e2005fff irq:16 
  *-network:1 UNCLAIMED 
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: b 
       bus info: pci@00:0b.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       configuration: latency=64 
       resources: iomemory:e2000000-e2001fff irq:4 

---

### Post by askantik on 2007-08-12
Awaitin' input :D

---

### Post by kevdog on 2007-08-12
Ok, try uninstalling ndiswrapper using synaptic first.  If it says already uninstalled, no big deal.  I just want you to check and see what synaptic thinks.  

Next I want you to manually uninstall ndiswrapper.  Here are the steps:

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

Ok, now I assume you are telling me you have no internet connection.  In this case do the following, to reinstall ndiswrapper:

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

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running.


Good Luck :)

---

