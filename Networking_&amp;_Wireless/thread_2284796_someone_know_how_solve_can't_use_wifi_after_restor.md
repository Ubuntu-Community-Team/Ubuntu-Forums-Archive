---
title: "someone know how solve can't use wifi after restore linux 12.04 but can use ethernet"
date: 2015-07-02
forum: Networking &amp; Wireless
---

### Post by miolinea on 2015-07-02
Hi! Normally I use only ubuntu 12.04 which already is installed inside dell inspriron 3537 laptop when i bought it  and  i can use it with wifi or ethernet very well but when i "Restore Ubuntu 12.04 to factory state" after that I can't only use my wifi. I ask someone to solve this please, thanks.
I did
 [COLOR=#111111][FONT=Consolas]sudo apt-get autoclean
[/FONT][/COLOR]sudo apt-get update
sudo apt-get dist-upgrade
[COLOR=#222222][FONT=Verdana]          but still can't use wifi[/FONT][/COLOR]
PS.this dell 3537 uses Atheros communications AR9565 WIRELESS network adapter / BCM43142

---

### Post by Bucky Ball on 2015-07-02
Welcome. Open a terminal and post the results of:

```
sudo lshw -C network
```

... please.

---

### Post by miolinea on 2015-07-02
Still can't use wifi after your suggestion "[COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -C network"

[/FONT][/COLOR]

---

### Post by QIII on 2015-07-02
That command returns some system information, which will help with diagnosing your problem.

It will not, in and of itself, fix the problem.

Please re-run the command, then copy the results and post them here.

---

### Post by Bucky Ball on 2015-07-02
> **Bucky Ball said:**
> Welcome. Open a terminal and _post the results of_:

```
sudo lshw -C network
```

... please.

As QIII suggests and I asked, could you post the output of that command, please.

---

### Post by miolinea on 2015-07-02
Thank you, Qlll, Bucky Ball
```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 07
       serial: ec:f4:bb:8d:3f:c2
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:61 ioport:4000(size=256) memory:c0700000-c0700fff memory:c0400000-c0403fff
  *-network DISABLED
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: f8:2f:a8:df:e2:07
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:19 memory:c0600000-c0607fff
```

---

### Post by Bucky Ball on 2015-07-02
Plug in an ethernet cable and get online. Open a terminal and issue these two commands:

```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
```

Then restart or, unplug the cable and issue these commands:

```
sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
sudo modprobe wl
```

This may work, may not. Look like you already have the correct driver in but wireless is still disabled. The card may be hard blocked. Let us know how you go with the above and report any error messages you receive in the process.

---

### Post by miolinea on 2015-07-02
```
sudo apt-get update

 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Get:1 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise Release.gpg [198 B]                 
Hit [http://oem.archive.canonical.com](http://oem.archive.canonical.com) precise-oem-sp1 Release.gpg               sue
Hit [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell Release.gpg                 
Get:2 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:3 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Hit [http://oem.archive.canonical.com](http://oem.archive.canonical.com) precise-oem-sp1 Release                   
Hit [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell Release                     
Get:4 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise Release [49.6 kB]                   
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [54.3 kB]            
Hit [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell/public Sources              
Get:6 [http://oem.archive.canonical.com](http://oem.archive.canonical.com) precise-oem-sp1/public Sources [12.8 kB]
Hit [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell/public amd64 Packages       
Get:7 [http://oem.archive.canonical.com](http://oem.archive.canonical.com) precise-oem-sp1/public amd64 Packages [21.5 kB]
Get:8 [http://oem.archive.canonical.com](http://oem.archive.canonical.com) precise-oem-sp1/public i386 Packages [21.3 kB]
Hit [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell/public i386 Packages        
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [131 kB]        
Ign [http://oem.archive.canonical.com](http://oem.archive.canonical.com) precise-oem-sp1/public TranslationIndex   
Ign [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell/public TranslationIndex     
Hit [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates Release                       
Get:10 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports Release [54.3 kB]        sue
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [3,759 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [43.4 kB]  
Get:13 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/main Sources [934 kB]              
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [2,186 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [525 kB]
Ign [http://oem.archive.canonical.com](http://oem.archive.canonical.com) precise-oem-sp1/public Translation-en_US  
Ign [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell/public Translation-en_US    
Ign [http://oem.archive.canonical.com](http://oem.archive.canonical.com) precise-oem-sp1/public Translation-en     
Ign [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell/public Translation-en       
Get:16 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/restricted Sources [5,470 B]       
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [8,943 B]
Get:18 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/universe Sources [5,019 kB]        
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [123 kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,689 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [566 kB] 
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [8,939 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [131 kB]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,876 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [208 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [199 B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [202 B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [205 B]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [230 kB]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en [1,408 B]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en [2,066 B]
Get:32 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/multiverse Sources [155 kB]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [77.4 kB]
Get:34 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/main amd64 Packages [1,273 kB]     
Get:35 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/restricted amd64 Packages [8,452 B]
Get:36 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/universe amd64 Packages [4,786 kB] 
Get:37 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/multiverse amd64 Packages [119 kB] 
Get:38 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]      
Get:39 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B] 
Get:40 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]  
Get:41 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]  
Get:42 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/main TranslationIndex [3,706 B]    
Get:43 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/multiverse TranslationIndex [2,676 B]
Get:44 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/restricted TranslationIndex [2,596 B]
Get:45 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/universe TranslationIndex [2,922 B]
Get:46 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/main Sources [490 kB]      
Get:47 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/restricted Sources [7,981 B]
Get:48 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/universe Sources [121 kB]  
Get:49 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/multiverse Sources [9,730 B]
Get:50 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/main amd64 Packages [908 kB]
Get:51 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/restricted amd64 Packages [13.6 kB]
Get:52 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/universe amd64 Packages [267 kB]
Get:53 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [16.5 kB]
Get:54 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/main i386 Packages [959 kB]
Get:55 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/restricted i386 Packages [13.6 kB]
Get:56 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/universe i386 Packages [277 kB]
Get:57 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/multiverse i386 Packages [16.7 kB]
Get:58 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/main TranslationIndex [10.6 kB]
Get:59 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [7,613 B]
Get:60 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/restricted TranslationIndex [7,297 B]
Get:61 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/universe TranslationIndex [8,333 B]
Get:62 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/main Sources [5,411 B]   
Get:63 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/restricted Sources [28 B]
Get:64 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/universe Sources [42.8 kB]
Get:65 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/multiverse Sources [5,750 B]
Get:66 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/main amd64 Packages [5,491 B]
Get:67 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/restricted amd64 Packages [28 B]
Get:68 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/universe amd64 Packages [44.2 kB]
Get:69 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [5,419 B]
Get:70 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/main i386 Packages [5,484 B]
Get:71 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/restricted i386 Packages [28 B]
Get:72 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/universe i386 Packages [44.0 kB]
Get:73 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5,413 B]
Get:74 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/main TranslationIndex [202 B]
Get:75 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/multiverse TranslationIndex [202 B]
Get:76 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/restricted TranslationIndex [193 B]
Get:77 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/universe TranslationIndex [205 B]
Get:78 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/main Translation-en [726 kB]       
Get:79 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:80 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/restricted Translation-en [2,395 B]
Get:81 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise/universe Translation-en [3,341 kB] 
Get:82 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/main Translation-en [399 kB]
Get:83 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/multiverse Translation-en [9,603 B]
Get:84 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/restricted Translation-en [2,982 B]
Get:85 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/universe Translation-en [159 kB]
Get:86 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/main Translation-en [4,911 B]
Get:87 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/multiverse Translation-en [4,838 B]
Get:88 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/restricted Translation-en [14 B]
Get:89 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/universe Translation-en [35.0 kB]
Fetched 28.7 MB in 4min 6s (116 kB/s)                                          
Reading package lists... Done

```
```
sudo apt-get --reinstall install bcmwl-kernel-source

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mingw-w64 sbsigntool gir1.2-timezonemap-1.0 realpath efibootmgr diffstat
  libdmraid1.0.0.rc16 libdebconfclient0 binutils-mingw-w64-i686 kpartx-boot
  libopts25 gir1.2-json-1.0 quilt autogen gcc-mingw-w64 user-setup
  gcc-mingw-w64-i686 kpartx rdate binutils-mingw-w64-x86-64
  libdebian-installer4 libopts25-dev btrfs-tools apt-clone localechooser-data
  gcc-mingw-w64-base gcc-mingw-w64-x86-64 archdetect-deb dmraid python-pyicu
  libkms1 mingw-w64-dev gir1.2-xkl-1.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,348 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 207538 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu0.0.2 (using .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.2_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.5.0-61-generic
Building for architecture x86_64
Building initial module for 3.5.0-61-generic
Done.

```
```
wl:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/3.5.0-61-generic/updates/dkms/

```
```
depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-61-generic
```

---

### Post by miolinea on 2015-07-02
and then ...it happened nothing, thanks

sudo  -r b43 ssb wl brcmfmac brcmsmac bcma
[sudo] password for : 
sudo modprobe wl

---

### Post by miolinea on 2015-07-02
Very sorry for my lately respond.
sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
[sudo] password for : 
sudo modprobe wl
                                 I

---

### Post by Bucky Ball on 2015-07-02
Did you restart the machine with the ethernet cable out?

---

### Post by miolinea on 2015-07-02
Thank you so much Bucky Ball and QIII I read your opinions "This may work, may not. Look like you already have the correct driver in  but wireless is still disabled. The card may be hard blocked. Let us  know how you go with the above and report any error messages you receive  in the process." Then I found 

[http://askubuntu.com/questions/139036/how-do-i-fix-a-wireless-is-disabled-by-hardware-switch-error#comment907523_139036](http://askubuntu.com/questions/139036/how-do-i-fix-a-wireless-is-disabled-by-hardware-switch-error#comment907523_139036)


that talk about how to fix Wireless is disabled by hardware switch so I did
rfkill unblock all
  rfkill list all     (showed some devices on soft block)


    sudo rfkill unblock wifi (if you just want to reactivate your wifi...)

Finally I read these.

"I don't know the Acer Travelmate 4500 but I had a similar problem with a Dell laptop.  Firstly I assume there is no hardware switch ie a physical wireless switch on the side or underneath the laptop?
  If not then, interrupt the boot sequence by pressing the F2 key "Set  up" (it may be a different key on your machine) and then look for the  wireless settings and ensure they are set correctly. "

I pressed Fn key and F2 key of keyboard dell on the left side at position up/down.So I can switch wireless on in Network-->Wireless
Now the wireless is on. 

Hope these can help the others too. :)

---

