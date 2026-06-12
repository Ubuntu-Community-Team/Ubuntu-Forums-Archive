---
title: "Lenovo B590: Wireless can't discover any network"
date: 2015-08-29
forum: Networking &amp; Wireless
---

### Post by skyfoxxy on 2015-08-29
Hi! I have such problem. Lenovo B590 with Ubuntu 15.04. Wi-fi module is Broadcom BCM43142 [14e4:4365] (rev 01).  Installed package is bcmwl-kernel-source. Wi-fi can't discover any network and can't connect to network directly too. I tried to use different wi-fi settings on my router, but unsuccessfully. My android-phone and win7 see my and others networks very good.

[IMG]http://oi59.tinypic.com/2uy3728.jpg[/IMG]

```

skyfoxxy@skyfoxxy-ubuntu-2:~$ lspci -vnn | grep Network
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
skyfoxxy@skyfoxxy-ubuntu-2:~$ iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.

skyfoxxy@skyfoxxy-ubuntu-2:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
skyfoxxy@skyfoxxy-ubuntu-2:~$ 

```

---

### Post by ajgreeny on 2015-08-29
Have a look at these two threads which may either answer your problem or if not allow you to run the wifi-info script to show us more information.
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by skyfoxxy on 2015-08-29
Thanks. Here is wireless-info.txt

---

### Post by Hadaka on 2015-08-29
Hi, please do..
```
sudo sed -i '/^b43/ d' /etc/modules
```
then do..
```
sudo iw reg set RU
sudo sed -i 's/^REG.*=$/&RU/' /etc/default/crda
```
BOOT
got wireless?

---

### Post by skyfoxxy on 2015-08-29
No, no networks... (

---

### Post by skyfoxxy on 2015-08-29
Sorry, but didn't work ( I spent so many hours before I've posted here and there is no solution yet. Win7 is also installed on this laptop and wi-fi works on it.

---

### Post by Hadaka on 2015-08-29
ok,please run and post the wireless script again
see how it liked the latest changes
thanks.

---

### Post by skyfoxxy on 2015-08-29
Here

---

### Post by Hadaka on 2015-08-29
from a working wired connection please do..
post any errors
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install  bcmwl-kernel-source
sudo modprobe wl
```
please post the output of..
```
dmesg | grep wl
```
thanks

---

### Post by skyfoxxy on 2015-08-29
Thanks for helping.

I did first 4 commands. There is no errors. But I decide to show output of "sudo apt-get install  bcmwl-kernel-source".

```
skyfoxxy@skyfoxxy-ubuntu-2:~$ sudo apt-get install  bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1 509 kB of archives.
After this operation, 8 038 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 187059 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu2_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.19.0-26-generic
Building for architecture x86_64
Building initial module for 3.19.0-26-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-26-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-26-generic
```

And... Something bad in output of "dmesg | grep wl"

```
skyfoxxy@skyfoxxy-ubuntu-2:~$ dmesg | grep wl
[   12.071485] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.074103] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   12.075940] wl 0000:02:00.0: PCI->APIC IRQ transform: INT A -> IRQ 19
[   12.217831] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[ 1758.016709] ERROR @wl_dev_intvar_get : error (-1)
[ 1758.016716] ERROR @wl_cfg80211_get_tx_power : error (-1)
```

---

### Post by Hadaka on 2015-08-29
Hi please repeat and post all the commands in post #9 again
please run the purge command twice ..it should say file not found
on the second run...but im curious, be sure to post the dmesg file also
thanks

---

### Post by skyfoxxy on 2015-08-31
Thanks and excuse me, I've just seen your post.
I did all you asked.

```

skyfoxxy@skyfoxxy-ubuntu-2:~$ sudo apt-get update
[sudo] password for skyfoxxy: 
Ign http://ru.archive.ubuntu.com vivid InRelease
Ign http://ru.archive.ubuntu.com vivid-updates InRelease
Ign http://ru.archive.ubuntu.com vivid-backports InRelease
Hit http://ru.archive.ubuntu.com vivid Release.gpg    
Get:1 http://ru.archive.ubuntu.com vivid-updates Release.gpg [933 B]
Hit http://ru.archive.ubuntu.com vivid-backports Release.gpg                            
Hit http://ru.archive.ubuntu.com vivid Release                               
Get:2 http://ru.archive.ubuntu.com vivid-updates Release [63,5 kB]    
Ign http://security.ubuntu.com vivid-security InRelease                       
Hit http://ru.archive.ubuntu.com vivid-backports Release
Hit http://ru.archive.ubuntu.com vivid/main Sources                    
Hit http://ru.archive.ubuntu.com vivid/restricted Sources     
Hit http://ru.archive.ubuntu.com vivid/universe Sources       
Hit http://ru.archive.ubuntu.com vivid/multiverse Sources
Hit http://ru.archive.ubuntu.com vivid/main amd64 Packages
Get:3 http://security.ubuntu.com vivid-security Release.gpg [933 B]
Hit http://ru.archive.ubuntu.com vivid/restricted amd64 Packages
Hit http://ru.archive.ubuntu.com vivid/universe amd64 Packages      
Hit http://ru.archive.ubuntu.com vivid/multiverse amd64 Packages    
Hit http://ru.archive.ubuntu.com vivid/main i386 Packages
Hit http://ru.archive.ubuntu.com vivid/restricted i386 Packages
Get:4 http://security.ubuntu.com vivid-security Release [63,5 kB]
Hit http://ru.archive.ubuntu.com vivid/universe i386 Packages          
Hit http://ru.archive.ubuntu.com vivid/multiverse i386 Packages        
Hit http://ru.archive.ubuntu.com vivid/main Translation-en
Hit http://ru.archive.ubuntu.com vivid/main Translation-ru
Hit http://ru.archive.ubuntu.com vivid/multiverse Translation-en
Hit http://ru.archive.ubuntu.com vivid/multiverse Translation-ru
Hit http://ru.archive.ubuntu.com vivid/restricted Translation-en
Hit http://ru.archive.ubuntu.com vivid/restricted Translation-ru
Hit http://ru.archive.ubuntu.com vivid/universe Translation-en
Hit http://ru.archive.ubuntu.com vivid/universe Translation-ru
Get:5 http://ru.archive.ubuntu.com vivid-updates/main Sources [78,5 kB]
Get:6 http://ru.archive.ubuntu.com vivid-updates/restricted Sources [1 366 B]    
Get:7 http://ru.archive.ubuntu.com vivid-updates/universe Sources [35,8 kB]
Get:8 http://ru.archive.ubuntu.com vivid-updates/multiverse Sources [1 966 B]
Get:9 http://ru.archive.ubuntu.com vivid-updates/main amd64 Packages [185 kB]                 
Get:10 http://ru.archive.ubuntu.com vivid-updates/restricted amd64 Packages [3 283 B]                  
Get:11 http://ru.archive.ubuntu.com vivid-updates/universe amd64 Packages [99,8 kB]  
Get:12 http://ru.archive.ubuntu.com vivid-updates/multiverse amd64 Packages [3 496 B]               
Get:13 http://security.ubuntu.com vivid-security/main Sources [39,2 kB]                                 
Get:14 http://ru.archive.ubuntu.com vivid-updates/main i386 Packages [183 kB]
Get:15 http://ru.archive.ubuntu.com vivid-updates/restricted i386 Packages [3 273 B]                 
Get:16 http://ru.archive.ubuntu.com vivid-updates/universe i386 Packages [99,8 kB]                                  
Get:17 http://ru.archive.ubuntu.com vivid-updates/multiverse i386 Packages [3 680 B]                            
Hit http://ru.archive.ubuntu.com vivid-updates/main Translation-en                                                  
Hit http://ru.archive.ubuntu.com vivid-updates/multiverse Translation-en                             
Hit http://ru.archive.ubuntu.com vivid-updates/restricted Translation-en                  
Hit http://ru.archive.ubuntu.com vivid-updates/universe Translation-en                   
Hit http://ru.archive.ubuntu.com vivid-backports/main Sources     
Hit http://ru.archive.ubuntu.com vivid-backports/restricted Sources
Hit http://ru.archive.ubuntu.com vivid-backports/universe Sources
Get:18 http://security.ubuntu.com vivid-security/restricted Sources [28 B]
Hit http://ru.archive.ubuntu.com vivid-backports/multiverse Sources
Hit http://ru.archive.ubuntu.com vivid-backports/main amd64 Packages
Hit http://ru.archive.ubuntu.com vivid-backports/restricted amd64 Packages
Hit http://ru.archive.ubuntu.com vivid-backports/universe amd64 Packages
Hit http://ru.archive.ubuntu.com vivid-backports/multiverse amd64 Packages
Hit http://ru.archive.ubuntu.com vivid-backports/main i386 Packages
Get:19 http://security.ubuntu.com vivid-security/universe Sources [15,9 kB]
Hit http://ru.archive.ubuntu.com vivid-backports/restricted i386 Packages                
Hit http://ru.archive.ubuntu.com vivid-backports/universe i386 Packages
Hit http://ru.archive.ubuntu.com vivid-backports/multiverse i386 Packages
Get:20 http://security.ubuntu.com vivid-security/multiverse Sources [1 966 B]
Hit http://ru.archive.ubuntu.com vivid-backports/main Translation-en           
Hit http://ru.archive.ubuntu.com vivid-backports/multiverse Translation-en
Hit http://ru.archive.ubuntu.com vivid-backports/restricted Translation-en
Hit http://ru.archive.ubuntu.com vivid-backports/universe Translation-en
Get:21 http://security.ubuntu.com vivid-security/main amd64 Packages [109 kB]
Get:22 http://security.ubuntu.com vivid-security/restricted amd64 Packages [28 B]
Get:23 http://security.ubuntu.com vivid-security/universe amd64 Packages [52,1 kB]
Get:24 http://security.ubuntu.com vivid-security/multiverse amd64 Packages [3 496 B]
Get:25 http://security.ubuntu.com vivid-security/main i386 Packages [108 kB]
Get:26 http://security.ubuntu.com vivid-security/restricted i386 Packages [28 B]
Get:27 http://security.ubuntu.com vivid-security/universe i386 Packages [52,1 kB]
Get:28 http://security.ubuntu.com vivid-security/multiverse i386 Packages [3 680 B]
Get:29 http://security.ubuntu.com vivid-security/main Translation-en [57,3 kB]
Hit http://security.ubuntu.com vivid-security/multiverse Translation-en    
Hit http://security.ubuntu.com vivid-security/restricted Translation-en
Get:30 http://security.ubuntu.com vivid-security/universe Translation-en [32,5 kB]
Fetched 1 303 kB in 7s (164 kB/s)                                                                                                              
Reading package lists... Done
skyfoxxy@skyfoxxy-ubuntu-2:~$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
After this operation, 8 038 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 187133 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-26-generic
skyfoxxy@skyfoxxy-ubuntu-2:~$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
skyfoxxy@skyfoxxy-ubuntu-2:~$ sudo apt-get install  bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/1 509 kB of archives.
After this operation, 8 038 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 187059 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu2_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.19.0-26-generic
Building for architecture x86_64
Building initial module for 3.19.0-26-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-26-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-26-generic
skyfoxxy@skyfoxxy-ubuntu-2:~$ sudo modprobe wl
skyfoxxy@skyfoxxy-ubuntu-2:~$ dmesg | grep wl
[   12.597074] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.599662] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   12.601440] wl 0000:02:00.0: PCI->APIC IRQ transform: INT A -> IRQ 19
[   12.746824] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
skyfoxxy@skyfoxxy-ubuntu-2:~$ 
```

---

