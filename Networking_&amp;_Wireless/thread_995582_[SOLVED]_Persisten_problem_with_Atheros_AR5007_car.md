---
title: "[SOLVED] Persisten problem with Atheros AR5007 card, driving me crazy"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by Brickrat on 2008-11-28
Ok, I hate to start another thread, but I've been working on getting the wireless working on my daughter's laptops for many hours, and I've reached the end of my rope.  I had it working in 8.04 until one of the updates killed it, and I went through all the steps, including updating madwifi with no luck.  So today I did the download and install of 8.10, which went just fine, but still no wifi.

I went in synaptic and checked the backport-intrepid and reloaded the repositories and then searched for ath5k, but got no results. 

Then I checked the System>hardware drivers and found that there was "Support for Atherso 80211 wireless LAN cards shown"  but still no wifie, so I did the blacklisting of ath_hal, and ath_pci in the modprobe.d and still didn't get anything.   

Then weird stuff started happening in the system>hardware drivers.  The Support for Atheros was shown as deactivated so I clicked on the Activate button and entered the root password and the program said "the driver has just be deactivated but is still in use"   I rebooted and checked again.  It was shown as deactivated, so I tried to activate it again, and got the same message.  "This driver has just been deactivated but is still in use."  One the next attempt I got the message, "A different version of this driver is in use" 

lshw -C network posted below. 

This is getting pretty frustrating, and she would like to get her computer back too. 

How do we find out what the driver is from the command line?   
Why when I search in synaptic for ath5k is nothing found, either in backport repositories or already install?  Has the name changed, or is 8.10 using some other driver? 

I need someone knowledgeable that can hang in there with me to get this fixed. 

nikole@nikole-laptop:~$ sudo lshw -C network
[sudo] password for nikole: 
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:15:58:88
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.0.196 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:9d:36:0c:86:95
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


Thanks for all the help you have given so far, I have faith in you all.

Laptop is a Acer Aspire 3680, Celeron M 2 MB RAM now running 8.10  (disregard my computer info in my signature.)

---

### Post by Brickrat on 2008-11-29
Additional Information as suggested 


Acer Aspire 3680 Celeron M processor, 2 Mb RAM 



nikole@nikole-laptop:~$ uname -mr
2.6.27-9-generic i686



nikole@nikole-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


nikole@nikole-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

nikole@nikole-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:15:58:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15416 (15.4 KB)  TX bytes:15416 (15.4 KB)

let me know if you need anything else.  

Thanks for helping.

---

### Post by Brickrat on 2008-11-29
Here is the screenshot of the Hardware Drivers 


[IMG]/home/nikole/HardwardDrivers112908.xcf[/IMG]

---

### Post by KinderX on 2008-11-29
edit 11/29/08

i have the solution!

download this:
[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-11-29.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-11-29.tar.bz2)

make sure in your restricted drivers that the support for atheros devices is disabled and reboot.

once you log back in go System > administration > Users and Groups, select your user, then give your user full priviledges under the user priviledges tab. close that. then extract the tarball to your desk top and oper your terminal. 

input these codes:

```
cd /home/username/Desktop/compat-wireless-2008-11-29
```
(substitute username for the correct directory.)

```
make
```

```
sudo make install
```

```
sudo make load
```

reboot and it should work.

---

### Post by ren4 on 2008-11-29
I had a similar problem finding the atheros drivers on for an Acer Aspire a few weeks back.  

After a lot of searches that didn't work, I eventually scrolled down in synaptic to find linux-backports-modules-intrepid.  Installed it and it appeared in the drivers gui and worked right away.  

I can't say it will work for you, but it's worth a try.  Good luck!

---

### Post by Brickrat on 2008-11-30
I used the solution that KinderX suggested, as my research had led me to the same download, but his howto really helped me get it to work, as I was reluctant to download it. 

The Wifi did start to work, although I was unable to connect with my WPA-Personal network.  It seemed to be a passcode problem.  Unfortunately I had to give the laptop back to my daughter for a while.  I will probably get to work on it again in a couple weeks after her semester ends.  

I really appreciate the help you gave me. 

Ren4, I had done the backports thing, but for some reason it didn't seem to download the new drivers that worked. 

Getting started on Ubuntu still has a pretty steep learning curve, I sure hope the make this wifi thing a whole lot easier, judging by the amount of posts.

---

