---
title: "Thinkpad L540, Ubuntu 13.10, ThinkPad Wireless 2 x 2 BGN+BT 4.0: No Wi-Fi."
date: 2013-11-26
forum: Networking &amp; Wireless
---

### Post by the_celestial on 2013-11-26
I just got my new Laptop and I'm running Ubuntu 13.10 as a live boot. When I click on the networking icon on the top bar no options for Wi-Fi are given. Also, no drivers are available in under 'Software & Updates'.

My Wi-Fi adapter is: ThinkPad Wireless 2 x 2 BGN+BT 4.0 (elsewhere listed as ThinkPad b/g/n BT).

Here is the output (based on the troubleshooting Howto):

ubuntu@ubuntu:~$ lspci -nn | grep 'Wireless Brand'
ubuntu@ubuntu:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 004: ID 0bda:8761 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 05dc:a810 Lexar Media, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 3c:97:0e:d3:64:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2500000-f2520000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2528 (2.5 KB)  TX bytes:2528 (2.5 KB)


ubuntu@ubuntu:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


ubuntu@ubuntu:~$ lsmod | grep "wlan_module_name"
ubuntu@ubuntu:~$ dmesg | grep "wlan_module_name"


ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Ethernet Connection I217-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: 3c:97:0e:d3:64:7f
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:f2500000-f251ffff memory:f253f000-f253ffff ioport:6080(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:5000(size=256) memory:f2400000-f2403fff


ubuntu@ubuntu:~$ iwlist scan
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


ubuntu@ubuntu:~$ lsb_release -d
Description:	Ubuntu 13.10
ubuntu@ubuntu:~$ uname -mr
3.11.0-12-generic x86_64

---

### Post by tafo on 2014-02-17
Hello everybody,
I have the same problem (same laptop and WLAN device).

Does anyone have a clue how to fix it???

Thanks,
tafo

---

### Post by chili555 on 2014-02-17
Please let us see the result of this command from the terminal:```
lspci -nn | grep 0280
```

---

### Post by tafo on 2014-02-18
Hello, 
sorry I didn't post any log because in the meanwhile I restored windows to make sure that the hardware is working, and it correctly does...

I run the 'lspci -nn | grep 0280' command on an ubuntu 12.04LTS live and obtained:

```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:818b]
```
   [LEFT][COLOR=#000000][FONT=Ubuntu Mono]
Thank for your help!




[/FONT][/COLOR][/LEFT]

---

### Post by chili555 on 2014-02-18
Your wireless device uses the rare and elusive driver rtl8192ee. I have found and compiled a driver for it. Although I compiled the tarball, I suggest you try the .deb instead. Please download this file: [http://netbook-remix.archive.canonical.com/updates/pool/public/o/oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms/oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms_0017.1016.2013~sutton1_all.deb](http://netbook-remix.archive.canonical.com/updates/pool/public/o/oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms/oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms_0017.1016.2013~sutton1_all.deb)

Assuming it was downloaded to Downloads, please open a terminal and do:```
cd ~/Downloads
sudo dpkg -i oem*.deb
sudo modprobe rtl8192ee
```Is it working?

---

### Post by tafo on 2014-02-18
I downloaded the .deb and run dpkg as indicated.
Apparently there is a dependency problem...

```

sudo dpkg -i oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms_0017.1016.2013~sutton1_all.deb 

(Reading database ... 148064 files and directories currently installed.)
Preparing to replace oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms 0017.1016.2013~sutton1 (using oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms_0017.1016.2013~sutton1_all.deb) ...
Unpacking replacement oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms ...
dpkg: dependency problems prevent configuration of oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms:
 oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms depends on dkms (>= 1.95); however:
  Package dkms is not installed.
dpkg: error processing oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms
```

---

### Post by chili555 on 2014-02-18
Please get a temporary wired ethernet connection and then:```
sudo apt-get install dkms
```Then proceed as above.

---

### Post by tafo on 2014-02-19
Oopps sorry, I'm not an expert but I should at least read the logs in the terminal...

Anyway I couldn't install dkms, that's what I get

```
ubuntu@ubuntu:~/Downloads$ sudo apt-get install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms (0017.1016.2013~sutton1) ...
Removing old oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-0017.1016.2013~sutton1 DKMS files...

------------------------------
Deleting module version: 0017.1016.2013~sutton1
completely from the DKMS tree.
------------------------------
Done.
Loading new oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-0017.1016.2013~sutton1 DKMS files...
First Installation: checking all kernels...
Building only for 3.11.0-15-generic
Building for architecture x86_64
Building initial module for 3.11.0-15-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
dpkg: error processing oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms (--configure):
 subprocess installed post-installation script returned error exit status 9
Errors were encountered while processing:
 oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by chili555 on 2014-02-19
> Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch. What is your arch; 32- or 64-bit?```
arch
```> Removing old oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-0017.1016.2013~sutton1 DKMS files...
?? Did you previously try to install this package? Am I confused?

---

### Post by tafo on 2014-02-19
Ok maybe I messed up something in some previous attempt...

The achitecture is x86_64.

I rebooted the live distro, update and upgrade, then:

1) installed dkms:
```
ubuntu@ubuntu:~$ sudo apt-get install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fakeroot
The following NEW packages will be installed:
  dkms fakeroot
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/160 kB of archives.
After this operation, 669 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.4%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20140204)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.4%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20140204)_dists_precise_restricted_binary-i386_Packages)
Selecting previously unselected package dkms.
(Reading database ... 147655 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3.2_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_amd64.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.3-1ubuntu3.2) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.4%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20140204)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.4%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20140204)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```



2) installed the driver you suggested via deb package
```
ubuntu@ubuntu:~$ sudo dpkg -i oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms_0017.1016.2013~sutton1_all.deb 
Selecting previously unselected package oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms.
(Reading database ... 147739 files and directories currently installed.)
Unpacking oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms (from oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms_0017.1016.2013~sutton1_all.deb) ...
Setting up oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms (0017.1016.2013~sutton1) ...
Loading new oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-0017.1016.2013~sutton1 DKMS files...
First Installation: checking all kernels...
Building only for 3.11.0-15-generic
Building for architecture x86_64
Building initial module for 3.11.0-15-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
dpkg: error processing oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms (--install):
 subprocess installed post-installation script returned error exit status 9
Errors were encountered while processing:
 oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms

```

---

### Post by chili555 on 2014-02-19
> Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive whichIt actually says: ```
BUILD_EXCLUSIVE_KERNEL="3\.[58]\..*"
```I'm not sure (read: skilled enough to know) what that means; perhaps it means for kernels 3.5 through 3.8. You have 3.11. As I said, I compiled the tarball on my 3.11 system. It produces a few warnings but no errors. Whether the module it builds works sufficiently to drive the hardware I don't know as I haven't the device. If you'd like to try it:```
sudo apt-get install build-essential linux-headers-generic
```Download this file to your desktop: [http://netbook-remix.archive.canonical.com/updates/pool/public/o/oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms/oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms_0017.1016.2013~sutton1.tar.gz](http://netbook-remix.archive.canonical.com/updates/pool/public/o/oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms/oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms_0017.1016.2013~sutton1.tar.gz)  Right-click it and select 'Extract Here.' Now back to the terminal:```
cd ~/Desktop/oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms-0017.1016.2013~sutton1/oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-0017.1016.2013~sutton1/driver
```You can probably get Tab to autocomplete.```
make
sudo make install
sudo modprobe rtl8192ee
```

---

### Post by tafo on 2014-02-19
It's working, finally!!!
Probably driver compilation on my architecture was needed...

I have the impression there are still some issues to be fixed. Now I'll install the distro and check carefully... 

Thanks a lot for your time and patience,
tafo

---

### Post by chili555 on 2014-02-19
> **tafo said:**
> It's working, finally!!!

tafoAwesome! You have compiled the driver for your currently running kernel only. When Update Manager offers a new kernel, also known as linux-image, you must recompile:```
cd ~/Desktop/oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms-0017.1016.2013~sutton1/oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-0017.1016.2013~sutton1/driver
make clean
make
sudo make install
sudo modprobe rtl8192ee
```I suspect you will have helped quite a few searchers.

Please use thread tools at the top to mark Solved.

---

### Post by josh41 on 2014-02-25
Thank you both for working through this.  

short version: I got the wireless working using chili555's first instructions and the first deb file on a computer with 12.04 ubuntu and the 3.5 kernel.

longer details: I just got a new t440p which has the same wireless controller as in this thread and I am using 12.04 with the 3.5 kernel.  I took my HDD from an older computer and initially neither the ethernet nor the wireless worked when the old HDD was in the new computer.  I then moved it back to the old computer to upgrade the kernel to 3.5 from 3.2 at which point the ethernet was recognized by the new computer.  From there, I used your first batch of instructions (from the first page) with the first deb file you posted and that did the trick for wireless.

Thanks!

update: there were some issues upon further use -- the computer would freeze (screen would not change but keyboard and mouse wouldn't do anything, required reset by holding power button).  This appears to have been related to power management of the wireless card which also had to be played around with. I added a script called wireless to /etc/pm/power.d which would turn of the power management using iwconfig (all this as per various suggestions elsewhere) -- this seems to be working so far.

---

### Post by PurpleDiane on 2014-08-05
Wow, thanks chili555! 
I couldn't connect with my rtl8192ee; it was like Ubuntu didn't know what to do with the hardware.  I have a fresh new install of Ubuntu 14.04 LTS, and by following your to download the oem....tar.gz file and rebuilding it per your directions above, it now works!

I have been so frustrated because there are so many places that *seem* be be the right answer, but do not work for me!
Thank you, thank you, thank you!

---

### Post by PurpleDiane on 2014-08-06
Sadly, it was a short-lived victory. I had to re-install Ubuntu (14.04 LTS) - for an unrelated reason - and now when I go through the above procedure (downloading the oem... and doing the make & make install), I get a kernel panic when I do the```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe rtl8192ee[/FONT][/COLOR]
```I am going to search through the forums some more & if I don't find anything else, I'm going to start a new thread for 14.04 LTS with RTL 8192EE. 

Meanwhile I'm going to get a USB wireless adapter. I'm tired of re-installing Ubuntu. Sigh...

---

### Post by Betina on 2014-11-06
Followed solution by chili555 #11, things were looking good, but on the last instruction got a Kernel panic response (same as PurpleDiane #16). Response looks something like this:
[   14.247617] RIP [<ffffffffa0675c45>] rtl92ee_rx_query_desc+0x175/0xaa [rtl8192ee]
[   14.247638]  RSP <ffff88021e203cd0>
[   14.254020] Kernel panic - not syncing: Fatal exception in interrupt
[   14.256297] drm_kms_helper: panic occurred, switching back to text console
  
I tried to reboot, but Ubuntu gets me back to the screen with the above error. I can't even type anything.
What to do now?

Thanks!

---

### Post by chili555 on 2014-11-06
> **Betina said:**
> Followed solution by chili555 #11, things were looking good, but on the last instruction got a Kernel panic response (same as PurpleDiane #16). Response looks something like this:
[   14.247617] RIP [<ffffffffa0675c45>] rtl92ee_rx_query_desc+0x175/0xaa [rtl8192ee]
[   14.247638]  RSP <ffff88021e203cd0>
[   14.254020] Kernel panic - not syncing: Fatal exception in interrupt
[   14.256297] drm_kms_helper: panic occurred, switching back to text console
  
I tried to reboot, but Ubuntu gets me back to the screen with the above error. I can't even type anything.
What to do now?

Thanks!Can you interrupt the boot process and get to the GRUB menu and get to recovery mode? [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) If so, log in at the terminal with your user name and password. Then do:```
cd ~/Desktop/oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms-0017.1016.2013~sutton1/oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-0017.1016.2013~sutton1/driver
sudo make uninstall
```If that works, then:```
sudo reboot now
```I will look for the more recent method to build rtl8192ee and post it in a few minutes.

EDIT: This was the thread I was referring to: [http://askubuntu.com/questions/523397/i-want-to-install-wifi-card-but-my-additional-drives-is-empty](http://askubuntu.com/questions/523397/i-want-to-install-wifi-card-but-my-additional-drives-is-empty)

However, as you can see:> Oh . When I use this way . My ubuntu was totally corrupt. Coming with a black screen writing kernel panic-not syncing fatal exception in interruption. I will keep looking, but, at this moment, I am unable to find any method to drive this device.

---

### Post by chili555 on 2014-11-06
Here is something else you both (all?) might try. With a temporary internet connection, do:```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
```Download this file and drag and drop it to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18-rc1/backports-3.18-rc1-1.tar.xz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18-rc1/backports-3.18-rc1-1.tar.xz) Right-click it and select 'Extract Here.'

Back to the terminal:```
cd ~/Desktop/backports-3.18-rc1-1
make defconfig-rtlwifi
make
sudo make install
sudo modprobe rtl8192ee
```Report back if it works as expected; we will have one more step.

---

### Post by Betina on 2014-11-06
chilli555, thank you so much for such a prompt response. 
As suggested, I tried to restart Ubuntu using the recovery mode, but it seems that the rebooting is stuck in "Loading Linux 3.13.0-39-generic ..." (so far 20+ minutes there)... I'll keep you posted of any progress.
Thanks again!

---

### Post by chili555 on 2014-11-06
At the GRUB menu, can you arrow down to an earlier kernel;for example, 3.13.0-37 or some such? If so, we can brute force the rtl8192ee module out of 3.13.0-39-generic and, I suspect, reboot successfully.

---

### Post by Betina on 2014-11-06
chili555, thanks again for your detailed instructions. 
The Good News: Ubuntu is running again! the bad news: no wireless driver available.

I followed instructions on Comment #19. During processing, I noticed that there were 18 modules and all of them return "Can't read private key" (see code below). 
```
   $ sudo make install  
 Building modules, stage 2.  
   MODPOST 18 modules 
   INSTALL /home/beatriz/Desktop/backports-3.18-rc1-1/compat/compat.ko  
 Can't read private key  rin


```
 
at the buttom of the execution, the following message was displayed:
```
     DEPMOD  3.13.0-24-generic  
 depmod will prefer updates/ over kernel/ -- OK!  
 Note:  
 You may or may not need to update your initramfs, you should if  
 any of the modules installed are part of your initramfs. To add  
 support for your distribution to do this automatically send a  
 patch against "update-initramfs.sh". If your distribution does not

 require this send a patch with the '/usr/bin/lsb_release -i -s'  
 ("Ubuntu") tag for your distribution to avoid this warning.  
 

 Your backported driver modules should be installed now.  
 Reboot.  
 


```

After rebooting, I searched for the new driver in the Additional Drivers tab on Software & Updates, but there are Not additional drivers available.

---

### Post by chili555 on 2014-11-06
> all of them return "Can't read private key" (see code below). That's trivial and may safely be ignored.> I searched for the new driver in the Additional Drivers tab on Software & Updates, but there are Not additional drivers available."Additional Drivers" is for some video cards and also some Broadcom wireless devices. It has nothing to do with the case at hand.

Did the module load?```
lsmod
```Do you see rtl8192ee listed there? If not,we wonder if you actually have that device; check:```
lspci -nn | grep 0280
```Is the pci.id listed in the aliases for rtl8192ee?```
version:        backported from Linux (v3.18-rc1-0-gf114040) using backports v3.18-rc1-1-0-g1f4af51
firmware:       rtlwifi/rtl8192eefw.bin
description:    Realtek 8192EE 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     7A5543C033E56B4AB23DF9E
alias:          pci:v0000[COLOR="#FF0000"]10EC[/COLOR]d0000[COLOR="#FF0000"]818B[/COLOR]sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,compat,btcoexist,mac80211

```If you have such a device and the aliases match, we then wonder if the firmware is missing; check:```
dmesg | grep rtl
```If it is indeed missing, I have it on my 14.10 install and we'll figure out how to get it to you.

I await your diagnostic report.

---

### Post by Betina on 2014-11-07
hi chili555, this is what I get: 
```
   [FONT=Courier 10 Pitch]$ lsmod [/FONT] 
 [FONT=Courier 10 Pitch]Module                  Size  Used by [/FONT] 
 [FONT=Courier 10 Pitch]r8188eu               814658  0 [/FONT] 
 [FONT=Courier 10 Pitch]bnep                   19624  2 [/FONT] 
 [FONT=Courier 10 Pitch]rfcomm                 69160  8 [/FONT] 
 [FONT=Courier 10 Pitch]snd_hda_codec_hdmi     46368[/FONT] 

 [FONT=Courier 10 Pitch]snd_hda_codec_realtek    65580  1 [/FONT] 
 [FONT=Courier 10 Pitch]binfmt_misc            17468  1 [/FONT] 
 [FONT=Courier 10 Pitch]rtl8192ee             139275  0 [/FONT] 
 [FONT=Courier 10 Pitch]btcoexist             105039  1 rtl8192ee [/FONT] 

 [FONT=Courier 10 Pitch]rtlwifi               129442  1 rtl8192ee [/FONT] 
 [FONT=Courier 10 Pitch]mac80211              630653  2 rtlwifi,rtl8192ee [/FONT] 
 [FONT=Courier 10 Pitch]joydev                 17381  0 [/FONT] 
 [FONT=Courier 10 Pitch]cfg80211              484040  2 mac80211,rtlwifi [/FONT] 


```

```
   [FONT=Courier 10 Pitch]$ lspci -nn | grep 0280 [/FONT]
 [FONT=Courier 10 Pitch]03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter [10ec:818b][/FONT]


```

That's all what I get. I don't see the pci.id or the aliases. Sorry if my answers don't  make sense or are incomplete, but I'm not very knowledgeable about computer systems.  Thanks for your patience.

---

### Post by chili555 on 2014-11-07
Your PCI device matches the driver you built:```
version:        backported from Linux (v3.18-rc1-0-gf114040) using backports v3.18-rc1-1-0-g1f4af51
firmware:       rtlwifi/rtl8192eefw.bin
description:    Realtek 8192EE 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     7A5543C033E56B4AB23DF9E
alias:          pci:v0000[COLOR="#FF0000"]10EC[/COLOR]d0000[COLOR="#FF0000"]818B[/COLOR]sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,compat,btcoexist,mac80211
```And your device is:```
Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter [[COLOR="#FF0000"]10ec[/COLOR]:[COLOR="#FF0000"]818b[/COLOR]]
```Also, the module loads just fine.

However, I see this is loaded, too:```
r8188eu               814658  0  
```Do you have a USB wireless, also? I'd be interested to see what happens if you detach the USB and reboot. Then run:```
iwconfig
sudo iwlist scan
dmesg | grep rtl
```Jot down those results and then connect and post the result.

---

### Post by Betina on 2014-11-07
Results:
```
   $ iwconfig 
 eth0      no wireless extensions. 

 lo        no wireless extensions. 


```
```
   $ sudo iwlist scan 
  eth0      Interface doesn't support scanning. 
  lo        Interface doesn't support scanning. 


```
```
$ dmesg | grep rtl
[    9.968827] rtlwifi: module verification failed: signature and/or  required key missing - tainting kernel
[   10.143856] rtlwifi-0:rtl_pci_probe():<0-0> mem mapped space: start: 0xf0400000 len:00004000 flags:00140204, after map:0xffffc90004e88000
[   10.143868] rtlwifi-0:_rtl_pci_find_adapter():<0-0> Pci Bridge Vendor is found index: 0
[   10.143870] rtlwifi-0:_rtl_pci_find_adapter():<0-0> pcidev busnumber:devnumber:funcnumber:vendor:link_ctl 3:0:0:10ec:0
[   10.143871] rtlwifi-0:_rtl_pci_find_adapter():<0-0> pci_bridge busnumber:devnumber:funcnumber:vendor:pcie_cap:link_ctl_reg:amd 0:28:1:8086:40:42:0
[   10.143894] rtl8192ee-0:rtl92ee_read_eeprom_info():<0-0> Boot from EFUSE
[   10.151244] rtl8192ee: 
[   10.151314] rtl8192ee-0:_rtl92ee_read_adapter_info():<0-0> dev_addr: 28:e3:47:5f:92:a4
[   10.151319] rtl8192ee-0:_rtl92ee_hal_customized_behavior():<0-0> RT Customized ID: 0x12
[   10.196124] rtl8192ee 0000:03:00.0: Direct firmware load failed with error -2
[   10.196125] rtl8192ee 0000:03:00.0: Falling back to user helper
[   10.196492] rtl8192ee-0:rtl92ee_init_sw_vars():<0-0> Failed to request firmware!
[   10.196494] rtlwifi-0:rtl_pci_probe():<0-0> Can't init_sw_vars.
 also 

```


You are right, I was trying to use a USB wireless, but it didn't work in Ubuntu. Interestedly the USB wireless works if I run Linux Mint 13 from a USB.

---

### Post by chili555 on 2014-11-08
> rtl8192ee-0:rtl92ee_init_sw_vars():<0-0> Failed to request firmware!That's easy enough to fix. The driver requires firmware:```
version:        backported from Linux (v3.18-rc1-0-gf114040) using backports v3.18-rc1-1-0-g1f4af51
[COLOR="#FF0000"]firmware:       rtlwifi/rtl8192eefw.bin[/COLOR]
description:    Realtek 8192EE 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     7A5543C033E56B4AB23DF9E
alias:          pci:v000010ECd0000818Bsv*sd*bc*sc*i*
<snip>
```The firmware is included in recent versions of *linux-firmware*. Let's install a later version of the package and try again:```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.138_all.deb
sudo dpkg -i linux-firmware*.deb
sudo modprobe -r rtl8192ee
sudo modprobe rtl8192ee
```If the wireless doesn't spring to life, check the log again:```
dmesg | grep rtl
```

---

### Post by Betina on 2014-11-08
It seems that we are getting there - Thank You!

I applied the commands suggested above. Then when I did "sudo modprobe rtl8192ee", I got Kernel Panic exception! So I restarted the machine on Recovery Mode (3.13.0-24) and bingo! my wireless connection was working! 
Next step I restarted in regular mode, but the wireless is not working in regular mode :-(  any suggestion?

---

### Post by chili555 on 2014-11-08
> **Betina said:**
> It seems that we are getting there - Thank You!

I applied the commands suggested above. Then when I did "sudo modprobe rtl8192ee", I got Kernel Panic exception! So I restarted the machine on Recovery Mode (3.13.0-24) and bingo! my wireless connection was working! 
Next step I restarted in regular mode, but the wireless is not working in regular mode :-(  any suggestion?Every method I know of that is supposed to get this device working ends in a kernel panic. Aside from a new device, I have no other suggestions.

You can uninstall backports with:```
cd ~/Desktop/backports-3.18-rc1-1
sudo make uninstall
```I regret I have no better answer.

---

### Post by Betina on 2014-11-08
Thank you chilli555. As mentioned above it works as long as I start in Recovery Mode. 
Besides the fact that it takes longer to re-start Ubuntu using Recovery Mode, is there any potential danger if I continue restarting in that mode? ...

---

### Post by chili555 on 2014-11-08
> is there any potential danger if I continue restarting in that mode? ...Not as far as I know. Recovery Mode omits some services which suggests that one of the services that's omitted is combining and conflicting  with wireless and causing the kernel panic.

I am inexperienced in such things and I suggest you ask here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331) and here: [http://askubuntu.com/questions](http://askubuntu.com/questions) Hopefully, someone can help you trace and correct the fault.

---

### Post by Betina on 2014-11-13
Last update: All my attempts to have network controller RTL8192EE working with Ubuntu 14.04 failed. After upgrading Ubuntu to 14.10, right away I got wireless connection (yupie!)

Thanks.

---

