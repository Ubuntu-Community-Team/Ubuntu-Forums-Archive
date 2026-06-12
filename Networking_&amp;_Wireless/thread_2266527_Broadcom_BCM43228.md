---
title: "Broadcom BCM43228"
date: 2015-02-23
forum: Networking &amp; Wireless
---

### Post by Alexander_Andersen on 2015-02-23
I have just installed ubuntu 14.04 today on my Acer laptop but the wifi is not working. 
I have looked for additional drivers, but the window is empty. 
There is no light in my wifi lamp, and the usual fn + f3 doesnt do anything. 
But my card does not seem to be hard blocked. 

alexander@AlexanderPC:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

Can you please help me?

---

### Post by JeQhdMD on 2015-02-23
What kind of wireless card/chipset do you have?  

Please access the Terminal Window (ctrl+alt+T) and enter:   
lspci -vvnn | grep -A 9 Network

Post results

---

### Post by Alexander_Andersen on 2015-02-24
alexander@AlexanderPC:~$ lspci -vvnn | grep -A 9 Network
03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Foxconn International, Inc. Device [105b:e04b]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at b3500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: bcma-pci-bridge

---

### Post by mörgæs on 2015-02-24
Alexander, please use CODE tags for posting terminal output.

---

### Post by Bucky Ball on 2015-02-24
> **mörgæs said:**
> Alexander, please use CODE tags for posting terminal output.

See last link in my signature for how. Thanks.

---

### Post by Alexander_Andersen on 2015-02-24
```


alexander@AlexanderPC:~$ lspci -vvnn | grep -A 9 Network
03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Foxconn International, Inc. Device [105b:e04b]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at b3500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: bcma-pci-bridge

```

---

### Post by Bucky Ball on 2015-02-24
Install the STA driver using the instructions for 12.04 [HERE]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29"). You may need to blacklist the bcma-pci-bridge driver currently in use.

---

### Post by Alexander_Andersen on 2015-02-24
```


alexander@AlexanderPC:~$ sudo apt-get update
[sudo] password for alexander: 
Ign http://dk.archive.ubuntu.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://dk.archive.ubuntu.com trusty-updates InRelease
Ign http://dk.archive.ubuntu.com trusty-backports InRelease
Hit http://extras.ubuntu.com trusty Release.gpg
Ign http://security.ubuntu.com trusty-security InRelease
Hit http://dk.archive.ubuntu.com trusty Release.gpg
Hit http://extras.ubuntu.com trusty Release    
Get:1 http://dk.archive.ubuntu.com trusty-updates Release.gpg [933 B] 
Get:2 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Hit http://extras.ubuntu.com trusty/main Sources                               
Get:3 http://dk.archive.ubuntu.com trusty-backports Release.gpg [933 B]        
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://dk.archive.ubuntu.com trusty Release                                
Get:4 http://security.ubuntu.com trusty-security Release [62.0 kB]             
Get:5 http://dk.archive.ubuntu.com trusty-updates Release [62.0 kB]          
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:6 http://dk.archive.ubuntu.com trusty-backports Release [62.0 kB]          
Hit http://dk.archive.ubuntu.com trusty/main Sources                           
Hit http://dk.archive.ubuntu.com trusty/restricted Sources                     
Hit http://dk.archive.ubuntu.com trusty/universe Sources                       
Get:7 http://security.ubuntu.com trusty-security/main Sources [71.1 kB]
Hit http://dk.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://dk.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://dk.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://dk.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://dk.archive.ubuntu.com trusty/multiverse amd64 Packages 
Get:8 http://security.ubuntu.com trusty-security/restricted Sources [2,061 B]
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://dk.archive.ubuntu.com trusty/main i386 Packages                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:9 http://security.ubuntu.com trusty-security/universe Sources [17.9 kB]    
Hit http://dk.archive.ubuntu.com trusty/restricted i386 Packages               
Get:10 http://security.ubuntu.com trusty-security/multiverse Sources [1,896 B] 
Hit http://dk.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://dk.archive.ubuntu.com trusty/multiverse i386 Packages   
Get:11 http://security.ubuntu.com trusty-security/main amd64 Packages [216 kB]
Hit http://dk.archive.ubuntu.com trusty/main Translation-en                    
Hit http://dk.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://dk.archive.ubuntu.com trusty/restricted Translation-en             
Hit http://dk.archive.ubuntu.com trusty/universe Translation-en
Get:12 http://dk.archive.ubuntu.com trusty-updates/main Sources [180 kB]
Get:13 http://dk.archive.ubuntu.com trusty-updates/restricted Sources [2,061 B]
Get:14 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Get:15 http://dk.archive.ubuntu.com trusty-updates/universe Sources [104 kB]   
Get:16 http://security.ubuntu.com trusty-security/universe amd64 Packages [87.6 kB]
Get:17 http://dk.archive.ubuntu.com trusty-updates/multiverse Sources [4,463 B]
Get:18 http://dk.archive.ubuntu.com trusty-updates/main amd64 Packages [442 kB]
Get:19 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,458 B]
Get:20 http://security.ubuntu.com trusty-security/main i386 Packages [207 kB]  
Get:21 http://dk.archive.ubuntu.com trusty-updates/restricted amd64 Packages [8,875 B]
Get:22 http://dk.archive.ubuntu.com trusty-updates/universe amd64 Packages [252 kB]
Get:23 http://dk.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.2 kB]
Get:24 http://dk.archive.ubuntu.com trusty-updates/main i386 Packages [433 kB] 
Get:25 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
Get:26 http://security.ubuntu.com trusty-security/universe i386 Packages [87.5 kB]
Get:27 http://dk.archive.ubuntu.com trusty-updates/restricted i386 Packages [8,846 B]
Get:28 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,624 B]
Get:29 http://dk.archive.ubuntu.com trusty-updates/universe i386 Packages [254 kB]
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Get:30 http://dk.archive.ubuntu.com trusty-updates/multiverse i386 Packages [11.3 kB]
Hit http://dk.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://dk.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://dk.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://dk.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Get:31 http://dk.archive.ubuntu.com trusty-backports/main Sources [5,298 B]    
Get:32 http://dk.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:33 http://dk.archive.ubuntu.com trusty-backports/universe Sources [20.7 kB]
Get:34 http://dk.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:35 http://dk.archive.ubuntu.com trusty-backports/main amd64 Packages [5,536 B]
Get:36 http://dk.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:37 http://dk.archive.ubuntu.com trusty-backports/universe amd64 Packages [24.1 kB]
Get:38 http://dk.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,245 B]
Get:39 http://dk.archive.ubuntu.com trusty-backports/main i386 Packages [5,550 B]
Get:40 http://dk.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:41 http://dk.archive.ubuntu.com trusty-backports/universe i386 Packages [24.1 kB]
Get:42 http://dk.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,249 B]
Hit http://dk.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://dk.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://dk.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://dk.archive.ubuntu.com trusty-backports/universe Translation-en      
Ign http://dk.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://dk.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://dk.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://dk.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 2,707 kB in 9s (284 kB/s)                                              
Reading package lists... Done
alexander@AlexanderPC:~$ sudo modprobe wl
modprobe: FATAL: Module wl not found.
alexander@AlexanderPC:~$ sudo apt-get --reinstall install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot libfakeroot
Suggested packages:
  dpkg-dev debhelper
The following NEW packages will be installed:
  bcmwl-kernel-source dkms fakeroot libfakeroot
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,271 kB of archives.
After this operation, 6,564 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://dk.archive.ubuntu.com/ubuntu/ trusty-updates/main dkms all 2.2.0.3-1.1ubuntu5.14.04 [64.6 kB]
Get:2 http://dk.archive.ubuntu.com/ubuntu/ trusty/restricted bcmwl-kernel-source amd64 6.30.223.141+bdcom-0ubuntu2 [1,126 kB]
Get:3 http://dk.archive.ubuntu.com/ubuntu/ trusty/main libfakeroot amd64 1.20-3ubuntu2 [25.4 kB]
Get:4 http://dk.archive.ubuntu.com/ubuntu/ trusty/main fakeroot amd64 1.20-3ubuntu2 [55.0 kB]
Fetched 1,271 kB in 2s (621 kB/s)  
Selecting previously unselected package dkms.
(Reading database ... 165131 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5.14.04_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5.14.04) ...
Selecting previously unselected package bcmwl-kernel-source.
Preparing to unpack .../bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../libfakeroot_1.20-3ubuntu2_amd64.deb ...
Unpacking libfakeroot:amd64 (1.20-3ubuntu2) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../fakeroot_1.20-3ubuntu2_amd64.deb ...
Unpacking fakeroot (1.20-3ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up dkms (2.2.0.3-1.1ubuntu5.14.04) ...
Setting up bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Loading new bcmwl-6.30.223.141+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.16.0-30-generic
Building for architecture x86_64
Building initial module for 3.16.0-30-generic
Error! Bad return status for module build on kernel: 3.16.0-30-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/make.log for more information.
modprobe: FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Setting up libfakeroot:amd64 (1.20-3ubuntu2) ...
Setting up fakeroot (1.20-3ubuntu2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-30-generic
alexander@AlexanderPC:~$ sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
modprobe: FATAL: Module wl not found.
alexander@AlexanderPC:~$ sudo modprobe wl
modprobe: FATAL: Module wl not found.


```

I can now see my network card in the network menu (upper right part of screen). It says it is disconnected.

---

### Post by jeremy31 on 2015-02-24
Download the file from one of the mirror sites [http://packages.ubuntu.com/utopic/amd64/bcmwl-kernel-source/download](http://packages.ubuntu.com/utopic/amd64/bcmwl-kernel-source/download) the 3.16 kernel needs a different version with a patch so it can work

---

### Post by Alexander_Andersen on 2015-02-24
*Thanks jeremy its working now :)*

---

### Post by jeremy31 on 2015-02-24
> **Alexander_Andersen said:**
> *Thanks jeremy its working now :)*
Please use the 'thread tools' at the top of the page to mark as solved, until they get this package into trusty repos we are likely going to see this question again

---

### Post by Bucky Ball on 2015-02-24
Good news! Enjoy the ride. ;)

---

