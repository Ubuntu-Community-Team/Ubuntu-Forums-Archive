---
title: "NetGear Model WNDA3100v2 Broadcom BCM4323 Chipset, Ubuntu 12.04, Driver Install Prob"
date: 2014-01-06
forum: Networking &amp; Wireless
---

### Post by newagelink on 2014-01-06
I am trying to follow [the 'STA - No Internet access' portion of the WifiDocs/Driver/bcm43xx Community Ubuntu Documentation]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access") (**my understanding is that my BCM4323 card is 'STA', not 'b43'; is that correct?**) but I am stuck at the second step, [QUOTE="the second step of the 'STA - No Internet access' portion of the WifiDocs/Driver/bcm43xx Community Ubuntu Documentation"]../pool/main/p/patch ```
cd /cdrom/pool/main/p/patch
sudo dpkg -i patch*
```[/QUOTE]

There is no 'p' folder! I have mounted an ubuntu 12.04 USB installation medium to /mnt/usb1 (from /dev/sdb) and successfully completed the first step, but could not complete the second step:
```
firstname@lastname-desktop:~$ sudo fdisk -l
[sudo] password for daniel: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008409d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968525823   484261888   83  Linux
/dev/sda2       968527870   976771071     4121601    5  Extended
/dev/sda5       968527872   976771071     4121600   82  Linux swap / Solaris

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
64 heads, 32 sectors/track, 15267 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7f75a30b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          64     1447935      723936   17  Hidden HPFS/NTFS
firstname@lastname-desktop:~$ sudo mkdir /mnt/usb1
my@desktop: sudo mount /dev/sdb /mnt/usb1
mount: block device /dev/sdb is write-protected, mounting read-only
firstname@lastname-desktop:~$ sudo mkdir /mnt/usb1
firstname@lastname-desktop:~$ sudo mount -t ntfs-3g /dev/sdb1 /mnt/usb1
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
firstname@lastname-desktop:~$ sudo mount -t ntfs-3g /dev/sdb /mnt/usb1
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
firstname@lastname-desktop:~$ man mount
firstname@lastname-desktop:~$ sudo mount -t ntfs /dev/sdb /mnt/usb1
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
firstname@lastname-desktop:~$ sudo mount /dev/sdb /mnt/usb1
mount: block device /dev/sdb is write-protected, mounting read-only
firstname@lastname-desktop:~$ cd /mnt/usb1/pool/main/d/dkms
firstname@lastname-desktop:/mnt/usb1/pool/main/d/dkms$ sudo dpkg -i dkms*
Selecting previously unselected package dkms.
(Reading database ... 176063 files and directories currently installed.)
Unpacking dkms (from dkms_2.2.0.3-1ubuntu3.1_all.deb) ...
Setting up dkms (2.2.0.3-1ubuntu3.1) ...
Processing triggers for man-db ...
firstname@lastname-desktop:/mnt/usb1/pool/main/d/dkms$ cd /mnt/usb1/pool/main/p/patch
bash: cd: /mnt/usb1/pool/main/p/patch: No such file or directory
firstname@lastname-desktop:/mnt/usb1/pool/main/d/dkms$ cd ..
firstname@lastname-desktop:/mnt/usb1/pool/main/d$ ls
dkms
firstname@lastname-desktop:/mnt/usb1/pool/main/d$ cd ..
firstname@lastname-desktop:/mnt/usb1/pool/main$ ls
b  d  f  l  m  s  u  w
firstname@lastname-desktop:/mnt/usb1/pool/main$ pwd
/mnt/usb1/pool/main
```
**Why am I missing this 'p/patch' folder that this guide assumes is present? What do I do?**

Moreover, I tried to install via double clicking, thinking that would save me terminal work, but when I double clicked it opened the Ubuntu Software Center with the 'install' option greyed out (so I was required to use terminal), another issue this guide seems unaware of.

It may be worth mentioning that I have installed Ubuntu on this desktop after its Windows Vista Home Premium installation failed: blue screen of death showing the error message (for less than one second),
```
Technical information:

*** STOP: 0X0000007B (0XFFFFF880009A9928,0XFFFFFFFFC0000034,0X0000000000000000,0
X0000000000000000)
```

I think the problem was either corrupted registry files or a corrupted hard drive, which Startup Repair and System Restore were both unable to resolve. I used 'dd' (and I think /dev/zero) to copy '0' onto the entire hard drive (someone in freenode #ubuntu said it was useful for reclaiming bad sectors), and then reformated and installed Ubuntu on the entire disk from a USB installation source (SanDisk flash drive). Pursuing the question of whether the hard drive is still functioning well: Disk Utility shows "SMART Status: [image of green filled-in circle] Disk has a few bad sectors", and the Extended Self-test result is "**[COLOR="#FF0000"]FAILED (Read)[/COLOR]**": Here is a listing of the Attributes that did not have Assessment 'Good' or 'N/A':
[table="width: 650, class: outer_border"]
[tr]
	[td]ID[/td]
	[td]Attribute[/td]
	[td]Assessment[/td]
	[td]Value[/td]
[/tr]
[tr]
	[td]5[/td]
	[td]**Reallocated Sector Count**
Count of remapped sectors. When the hard drive finds a read/write/verification error, it marks the sector as "reallocated" and transfers data to a special reserved area (spare area)[/td]
	[td]Warning[/td]
	[td]Normalized: 100
Worst: 100
Threshold: 36
Value: 230 sectors[/td]
[/tr]
[tr]
	[td]190[/td]
	[td]**Airflow Temperature**
Airflow temperature of the drive[/td]
	[td]Failed in the past[/td]
	[td]Normalized: 71
Worst: 45
Threshold: 45
Value: 29 degree C / 84 degree F[/td]
[/tr]
[tr]
	[td]197[/td]
	[td]**Current Pending Sector Count**
Number of sectors waiting to be remapped. If the sector waiting to be remapped is subsequently written or read successfully, this value is decreased and the sector is not remapped. Read errors on the sector will not remap the sector, it will only be remapped on a failed write attempt[/td]
	[td]Warning[/td]
	[td]Normalized: 100
Worst: 100
Threshold: 0
Value: 10 sectors[/td]
[/tr]
[/table]
**Is the 'p' folder missing because the hard drive is failing and needs to be replaced? Or are these issues not related?** I think they are not related, because I have mounted a USB flash drive used to install Ubuntu on this hard drive: **Surely the problem regarding the missing 'p' folder would lie with the USB drive, not the hard drive, right?**

[Additional information]("http://ubuntuforums.org/showthread.php?p=6183681") about my hardware and software:
[LIST=1]
[*]_Machine Brand and Model_: PC desktop,[LIST=1]
[*]PSU: Sparkle Power Int’l Ltd. Switching Power Supply Model No: FSP550-60PLG
[*]GPU: [GeForce GTX 260]("http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-260")
[*]Motherboard: [Intel Desktop Board DG33BU]("http://www.intel.com/p/en_US/support/highlights/dsktpboards/dg33bu")
[*]Chassis: Antec
[*]Hard Disk, ST3500320AS
[*]CDROM, HL-DT-ST BDDVDRW GGC-H20L
[/LIST]

[*]_Wireless Brand, Model and Wireless Chipset_: lsusb shows ```
Bus 001 Device 005: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
```
[*]_check interface_: ifconfig appears to not see this adapter at all: ```
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:22:f3:77  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:e3200000-e3220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:580 errors:0 dropped:0 overruns:0 frame:0
          TX packets:580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47280 (47.2 KB)  TX bytes:47280 (47.2 KB)
```
likewise for iwconfig: ```
lo        no wireless extensions.

eth0      no wireless extensions.
```
[*]_Check for modules_: lsmod does not list anything that appears to me to be related to wireless networking, e.g. no module with the text 'wlan'.
[*]_Kernel boot messages_: dmesg produced text that went further than I can scroll back in terminal; skimming through it there appears nothing related to wireless adapter, and ```
dmesg | grep "wlan"
``` returned no results -- i.e., it entered and, without any output, returned the 'my@computer:directory$' prompt.
[*]_Network configuration_: sudo lshw -C network likewise doesn't seem to show anything about wireless network: ```
firstname@lastname-desktop:/mnt/usb1/pool/main$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1c:c0:22:f3:77
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.1.4-k firmware=1.3-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:e3200000-e321ffff memory:e3224000-e3224fff ioport:3400(size=32)

```
[*]_Scan for networks_: iwlist scan returns the statement for lo and eth0 (which I think are not wireless), "Interface doesn't support scanning."
[*]_Ubuntu Version_: ```
Description: Ubuntu 12.04.3 LTS
```
[*]_Kernel/architecture (including 32 vs. 64 bit)_: ```
3.8.0-34-generic i686
```
[*]_Restarting the network_: ```
sudo service networking restart
[sudo] password for daniel:
stop: Unknown instance:
networking stop/waiting
firstname@lastname-desktop:/mnt/usb1/pool/main$
```
[/LIST]

---

### Post by newagelink on 2014-01-06
I connected an ethernet cable to my laptop and have been able to access the internet through this connection. Attempting [the 12.04 (Precise Pangolin) - 12.10 (Quantal Quetzal) section of installing STA drivers with internet access]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29_-_12.10_.28Quantal_Quetzal.29"), I encountered no error messages, yet nothing seems to have changed! I have divided the code according to input and output for ease of reading:

```
firstname@lastname-desktop:~$ sudo apt-get update
[sudo] password for firstname: 
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:3 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://us.archive.ubuntu.com precise Release                              
Get:4 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]
Get:5 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://extras.ubuntu.com precise Release                                   
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex            
Get:6 http://security.ubuntu.com precise-security/main Sources [94.9 kB]
Hit http://us.archive.ubuntu.com precise/main Sources                         
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:7 http://us.archive.ubuntu.com precise-updates/main Sources [430 kB]
Get:8 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:9 http://security.ubuntu.com precise-security/universe Sources [29.9 kB]   
Get:10 http://security.ubuntu.com precise-security/multiverse Sources [1,792 B]
Get:11 http://security.ubuntu.com precise-security/main i386 Packages [374 kB] 
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:12 http://us.archive.ubuntu.com precise-updates/restricted Sources [7,039 B]
Get:13 http://us.archive.ubuntu.com precise-updates/universe Sources [101 kB]  
Get:14 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:15 http://security.ubuntu.com precise-security/universe i386 Packages [91.1 kB]
Get:16 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,468 B]
Get:17 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,642 B]
Get:18 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:19 http://security.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:20 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:21 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:22 http://us.archive.ubuntu.com precise-updates/main i386 Packages [748 kB]
Get:23 http://security.ubuntu.com precise-security/main Translation-en [165 kB]
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Get:24 http://security.ubuntu.com precise-security/universe Translation-en [54.8 kB]
Get:25 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [11.5 kB]
Get:26 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [230 kB]
Get:27 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [14.4 kB]
Get:28 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:29 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:30 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:31 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Get:32 http://us.archive.ubuntu.com precise-updates/main Translation-en [327 kB]
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Get:33 http://us.archive.ubuntu.com precise-updates/universe Translation-en [133 kB]
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 2,942 kB in 9s (307 kB/s)                                              
Reading package lists... Done
```
```
firstname@lastname-desktop:~$ sudo apt-get --reinstall install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  thunderbird-globalmenu gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 46 not upgraded.
Need to get 1,307 kB of archives.
After this operation, 3,668 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted bcmwl-kernel-source i386 6.20.155.1+bdcom-0ubuntu0.0.2 [1,307 kB]
Fetched 1,307 kB in 7s (170 kB/s)                                                                                                          
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 176110 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.2_i386.deb) ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-34-generic
Building for architecture i686
Building initial module for 3.8.0-34-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.8.0-34-generic/updates/dkms/

depmod........

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-34-generic
```
```
firstname@lastname-desktop:~$ sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
firstname@lastname-desktop:~$ sudo modprobe wl
```

**It looks like all [the commands I was told to use]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29_-_12.10_.28Quantal_Quetzal.29") worked correctly, right? Yet doesn't the following indicate that the computer still does not recognize the adapter?**

```
firstname@lastname-desktop:~$ lsusb
[...]
Bus 001 Device 004: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
[...]

```

```
firstname@lastname-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:22:f3:77  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe22:f377/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7871860 (7.8 MB)  TX bytes:561519 (561.5 KB)
          Interrupt:20 Memory:e3200000-e3220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17186 (17.1 KB)  TX bytes:17186 (17.1 KB)
```
```
firstname@lastname-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```
```

firstname@lastname-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1c:c0:22:f3:77
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.1.4-k duplex=full firmware=1.3-0 ip=192.168.2.2 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:46 memory:e3200000-e321ffff memory:e3224000-e3224fff ioport:3400(size=32)
firstname@lastname-desktop:~$ 

```

Looking at [the 'Drivers available in Ubuntu' section]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Drivers_available_in_Ubuntu"), it appears BCM4323 is missing from that list -- mentioned instead are BCM43235, BCM43236 and BCM43238 ... **Is this why nothing seems to have changed? Or if BCM4323 is one of those three (5, 6, or 8), how do I ascertain which one it is?**

---

### Post by newagelink on 2014-01-06
Reading through [the Comprehensive ndiswrapper troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847"), I have also encountered a problem with ndiswrapper:
```
firstname@lastname-desktop:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
``````

firstname@lastname-desktop:~$ sudo apt-get install ndiswrapper-common
[sudo] password for firstname: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  thunderbird-globalmenu gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 46 not upgraded.
Need to get 5,988 B of archives.
After this operation, 72.7 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main ndiswrapper-common all 1.57-1ubuntu1 [5,988 B]
Fetched 5,988 B in 0s (23.8 kB/s)             
Selecting previously unselected package ndiswrapper-common.
(Reading database ... 176180 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.57-1ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.57-1ubuntu1) ...
``````

firstname@lastname-desktop:~$ ndiswrapper -l
Error: unable to find a version of ndiswrapper!
firstname@lastname-desktop:~$ 

```

---

### Post by chili555 on 2014-01-06
Let's skip over the question the answers to which lead us nowhere and go straight to the useful questions.> Looking at the 'Drivers available in Ubuntu' section, it appears BCM4323 is missing from that list -- mentioned instead are BCM43235, BCM43236 and BCM43238 ... Is this why nothing seems to have changed? Correct. bcmwl-kernel-source, also known as the STA driver, even patched, doesn't cover this device:> ID [COLOR="#FF0000"]0846:9011[/COLOR] NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]Not possibly, not maybe, not no how, never.

You are on the right track with ndiswrapper but you also need to install ndiswrapper-utils-1.9. Next, you need the Windows **XP** .inf and .sys files matching your device 0846:9011. They are in many threads all over this forum. You also need the files for your architecture; either 32- or 64-bit. Find out from the terminal with:```
arch
```A 32-bit system returns i686 and a 64-bit returns x86_64.

Search the forum for the term 0846:9011 and proceed. You seem pretty adept, so I'll leave you to discover the process unless you need additional guidance. 

You may also be interested in this: [http://ubuntuforums.org/showthread.php?t=2194362&p=12877081#post12877081](http://ubuntuforums.org/showthread.php?t=2194362&p=12877081#post12877081)

---

### Post by newagelink on 2014-01-06
I am considering returning this card to Staples and buying one that is more compatible with Ubuntu. This decision seems strengthened if ndiswrapper is the only solution, since I have read in this forum that it results in less-than-optimum use of the device. (Then, perhaps if enough stop buying this device with its Broadcom-sponsored issues, they will stop making incompatible products.) Would you agree that exchanging this product for one more compatible is better than trying to proceed to get it limping along with ndiswrapper? (I am still within the two-week return policy of Staples.)

---

### Post by chili555 on 2014-01-06
> Would you agree that exchanging this product for one more compatible is better than trying to proceed to get it limping along with ndiswrapper? Absolutely! This forum has about a thread a week about supported USB wireless devices so check before you buy.

I'm not sure that the 1-2% of Linux buyers has much influence at Netgear and I suspect they make some other products that work perfectly well in Linux.

---

### Post by newagelink on 2014-01-07
I exchanged the adapter for something $11 cheaper; *lsusb* reports: ```
Bus 001 Device 004: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]
``` All I had to do was plug it in. However, looking at [the HardwareSupportComponentsWirelessNetworkCardsNetgear ubuntu documentation page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear"), particularly the July 2011's WNA1100 column, I have two concerns: [LIST=1]
[*]The provided link, [http://sourceforge.net/projects/ath9...htc-installer/](http://sourceforge.net/projects/ath9...htc-installer/) leads to a page-not-found error.
[*]I would like to update this entry to correspond to January 2014 Ubuntu 12.04 LTS, but I am not sure if the drivers I installed -- as documented above -- were necessary for this device.
[/LIST]
**What should I do? Additionally, now that my (new) wireless adapter is working, is it appropriate to mark this thread as 'solved'? If so, how do I do so?** Technically, I ultimately did not get the previous adapter working, so I don't know if 'solved' applies in this case.

(Incidentally, I looked at that webpage on my cell phone at the store and that entry was decisive in my purchasing of it -- together with being told, I think in freenode's #ubuntu, to get Atheros. I'm glad it works, because it would have been somewhat vexing otherwise, given that the provided instructions in that row failed! So I am grateful and relieved.)

---

### Post by chili555 on 2014-01-08
>     I would like to update this entry to correspond to January 2014 Ubuntu 12.04 LTS, but I am not sure if the drivers I installed -- as documented above -- were necessary for this device.If you just plugged it in and it worked, then you really didn't install any drivers, did you? The only possible hitch is that the driver requires firmware:```
filename:       /lib/modules/3.12.4-031204-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
[COLOR="#FF0000"]firmware:       htc_9271.fw
firmware:       htc_7010.fw[/COLOR]
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     378262100879D7568E90646
<snip>
```The firmware is included in the package *linux-firmware* which is included in the default install of Ubuntu. That's why it's plug and play. 

You are certainly free to edit the community documentation. I'd simply say that from 12.04 forward, it's plug and play. If you wanted to add a comment, you might mention that the required firmware is installed by default. 

I suggest you not mark the thread solved as it leads searchers to think that the WNDA3100v2 is solved. 

In any event, I am glad it's working!

---

### Post by newagelink on 2014-01-08
> **chili555 said:**
> If you just plugged it in and it worked, then you really didn't install any drivers, did you?To clarify, I was referring to my earlier posts which discuss where I *did* install additional files prior to plugging in this device -- but looking again at it, perhaps I only *reinstalled* files that come with every Ubuntu 12.04 installation.

> **newagelink said:**
> [...] Attempting [the 12.04 (Precise Pangolin) - 12.10 (Quantal Quetzal) section of installing STA drivers with internet access]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29_-_12.10_.28Quantal_Quetzal.29") [...]

```
firstname@lastname-desktop:~$ sudo apt-get update
[sudo] password for firstname: 
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:3 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://us.archive.ubuntu.com precise Release                              
Get:4 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]
Get:5 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://extras.ubuntu.com precise Release                                   
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex            
Get:6 http://security.ubuntu.com precise-security/main Sources [94.9 kB]
Hit http://us.archive.ubuntu.com precise/main Sources                         
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:7 http://us.archive.ubuntu.com precise-updates/main Sources [430 kB]
Get:8 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:9 http://security.ubuntu.com precise-security/universe Sources [29.9 kB]   
Get:10 http://security.ubuntu.com precise-security/multiverse Sources [1,792 B]
Get:11 http://security.ubuntu.com precise-security/main i386 Packages [374 kB] 
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:12 http://us.archive.ubuntu.com precise-updates/restricted Sources [7,039 B]
Get:13 http://us.archive.ubuntu.com precise-updates/universe Sources [101 kB]  
Get:14 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:15 http://security.ubuntu.com precise-security/universe i386 Packages [91.1 kB]
Get:16 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,468 B]
Get:17 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,642 B]
Get:18 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:19 http://security.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:20 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:21 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:22 http://us.archive.ubuntu.com precise-updates/main i386 Packages [748 kB]
Get:23 http://security.ubuntu.com precise-security/main Translation-en [165 kB]
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Get:24 http://security.ubuntu.com precise-security/universe Translation-en [54.8 kB]
Get:25 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [11.5 kB]
Get:26 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [230 kB]
Get:27 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [14.4 kB]
Get:28 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:29 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:30 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:31 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Get:32 http://us.archive.ubuntu.com precise-updates/main Translation-en [327 kB]
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Get:33 http://us.archive.ubuntu.com precise-updates/universe Translation-en [133 kB]
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 2,942 kB in 9s (307 kB/s)                                              
Reading package lists... Done
```
```
firstname@lastname-desktop:~$ sudo apt-get --reinstall install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  thunderbird-globalmenu gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 46 not upgraded.
Need to get 1,307 kB of archives.
After this operation, 3,668 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted bcmwl-kernel-source i386 6.20.155.1+bdcom-0ubuntu0.0.2 [1,307 kB]
Fetched 1,307 kB in 7s (170 kB/s)                                                                                                          
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 176110 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.2_i386.deb) ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-34-generic
Building for architecture i686
Building initial module for 3.8.0-34-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.8.0-34-generic/updates/dkms/

depmod........

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-34-generic
```
```
firstname@lastname-desktop:~$ sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
firstname@lastname-desktop:~$ sudo modprobe wl
```I am not sure whether I installed STA drivers or if _bcmwl-kernel-source_ comes with every installation and I merely reinstalled it; so I am not sure if this new adapter required installing those STA drivers, or if it's plug-and-play as you say. There is some ambiguity to that ubuntu documentation, since it mentions installing something but the command says something about reinstalling them, and the command is literally *--reinstall install* ... (It looks to me like *--reinstall* is an option of the *install* command, though I'm not sure of its implications, even after reading about it via *man apt-get*.)

---

### Post by chili555 on 2014-01-08
I assume you are referring to this device:[ATTACH=CONFIG]249323[/ATTACH]As you can see, it uses the driver *ath9k_htc*. As well, modinfo confirms this:```
$ modinfo ath9k_htc 
filename:       /lib/modules/3.12.4-031204-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     378262100879D7568E90646
<snip>
alias:          usb:v[COLOR="#FF0000"]0846[/COLOR]p[COLOR="#FF0000"]9030[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
<snip>

```There is no reference here to bcmwl-kernel-source which creates a driver *wl* that doesn't cover your 0846:9030 at all. It isn't necessary. 

Is all this clearer now?

ath9k_htc comes with recent versions by default.

---

### Post by newagelink on 2014-01-09
Yes, thank you for the clarification!

---

