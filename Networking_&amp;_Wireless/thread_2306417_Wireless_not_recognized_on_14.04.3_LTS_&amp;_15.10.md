---
title: "Wireless not recognized on 14.04.3 LTS &amp; 15.10 installation - GITHUB install help?"
date: 2015-12-15
forum: Networking &amp; Wireless
---

### Post by keithwwalker on 2015-12-15
I need some help.

I have a brand new Asus GR8 PC.
It is a very nice design, and like every PC I get, I do a dual boot installation asap.

Upon booting the live CD (USB actually), the internal wireless card is not recognized.
I tried this with both 14.04.3 LTS & 15.10. (I also have an external wireless card that also is not recognized, Asus AC56 AC1200)

I continued the Ubuntu installation, and the wireless card is still not recognized after boot up into Ubuntu (again both 14.04.3 LTS & 15.10).

If I go to the Asus support page for the GR8, I find that the wireless card is a **Realtek 8811AU**:
*Realtek RTL8811AU 802.11ac Wireless LAN*

Now the big issue is that I don't have a wired connection to easily take advantage of, so I can't enter repositories to download and install any drivers that may be available out there.

What I would like to do is manually download the drivers and load them into terminal (I am not great at terminal commands either).

I have searched around and possibly found some drivers that may work.
[https://github.com/Braklet/rtl8811AU_rtl8821A-linux](https://github.com/Braklet/rtl8811AU_rtl8821A-linux)

I have downloaded that zip file in Windows 10 and have transferred it to my Ubuntu /Home disk space.

**Can anyone help me with terminal commands to install the drivers?**

I don't know anything about github, most of the tutorials are about hosting files there.  I just want to install the wireless driver.

Thanks!
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**Solution:**
If you don't wish to read through all the thread, here is the solution commands:
github is here:
[https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git]("https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git")

Terminal commands here:
```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd ~/rtl8812AU_8821AU_linux
make
sudo make install
sudo modprobe 8812au
```

Thread here:
[http://ubuntuforums.org/showthread.php?t=2240631&p=13104149#post13104149]("http://ubuntuforums.org/showthread.php?t=2240631&p=13104149#post13104149")

Thanks to everyone for their help!!!!

---

### Post by Bucky Ball on 2015-12-15
Run this in a terminal, please:

```
sudo lshw -C network
```

Post the output back here between [noparse][code][code][noparse] tags (see last link in my signature).

Unzip the file you downloaded and there should be a file called README, or something like it. That will tell you what to do, but wait until we know if your card is using a driver already.

There is no way you can get an ethernet cable or take the computer to somewhere there is one? Would save a LOT of time. But post that output and we'll see what it says.

---

### Post by keithwwalker on 2015-12-15
Thank you for your response.

There doesn't seem to be a readme file, or any documentation in the zip file.

```

keithwwalker@keithwwalker-GR8:~$ sudo lshw -C network
[sudo] password for keithwwalker: 
  *-network               
       description: Ethernet interface
       product: Ethernet Connection I218-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 08:62:66:9c:eb:5d
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.6-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:f7800000-f781ffff memory:f783c000-f783cfff ioport:f080(size=32)

```

---

### Post by Hadaka on 2015-12-15
Hi, open a terminal ctrl/alt/ then COPY and paste
one line at a time.
```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/Braklet/rtl8811AU_rtl8821A-linux
cd ~/rtl8811AU_rtl8821A-linux
make
sudo make install
sudo modprobe 8811au
```
boot,remove wired connection,test wireless


*After every linux image update you will need to do..
```
cd rtl8811AU_rtl8821A-linux/
make clean
make
sudo make install
sudo modprobe 8811au
```
.........SAVE........

---

### Post by keithwwalker on 2015-12-18
Thanks, it will take some driving, but I think I will be able to get a wired connection to try to install this weekend.
I really appreciate your help!

---

### Post by praseodym on 2015-12-18
Please check
```

lspci -nnk
lsusb
pccardctl info
```
The wireless card is not shown there. Is wireless active in your BIOS?

---

### Post by keithwwalker on 2015-12-18
I noticed that there didn't seem to be a wireless when I typed in the terminal:
```
sudo lshw -C network
```

I went into the ASUS bios and could not find anything related to wifi.
There was "PXE OpROM" disabled, but I don't think this has anything to do with wifi.
There was another option disabled: "Network Stack"

I tried the rfkill commands but there was absolutely no output???!???

fwiw, I also have a similar problem with one of my two Asus EB1503 nettop pc's.  These like the GR8 that I am posting about, are all built on a laptop architecture, but are desktops designed for low noise and power consumption.

It is worth reiterating that the GR8 is running dual boot and absolutely no problems with the wifi on Windows 10 (or Win8.1 before upgrade).

---

### Post by keithwwalker on 2015-12-19
I followed Hadaka's instructions and got stuck at the following command:

```
sudo modprobe 8811au
```

it returned the following:
```
modprobe: FATAL: Module 8811au not found.
```

I have a wired connection for the next two days, so I will continue to update Ubuntu and report back if rebooting shows up anything.

Thanks 

Here's the entire terminal session dump:

```
keithwwalker@keithwwalker-GR8:~$ sudo apt-get update
[sudo] password for keithwwalker: 
Get:1 http://security.ubuntu.com trusty-security InRelease [64.4 kB]
Ign http://us.archive.ubuntu.com trusty InRelease                              
Get:2 http://us.archive.ubuntu.com trusty-updates InRelease [64.4 kB]          
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:3 http://security.ubuntu.com trusty-security/main Sources [101 kB]         
Get:4 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Get:5 http://us.archive.ubuntu.com trusty-backports InRelease [64.5 kB]        
Get:6 http://extras.ubuntu.com trusty Release [11.9 kB]                        
Get:7 http://security.ubuntu.com trusty-security/restricted Sources [4,035 B]  
Get:8 http://us.archive.ubuntu.com trusty Release.gpg [933 B]                  
Get:9 http://security.ubuntu.com trusty-security/universe Sources [31.9 kB]    
Get:10 http://extras.ubuntu.com trusty/main Sources [14 B]                     
Get:11 http://us.archive.ubuntu.com trusty-updates/main Sources [246 kB]       
Get:12 http://security.ubuntu.com trusty-security/multiverse Sources [2,353 B]
Get:13 http://security.ubuntu.com trusty-security/main amd64 Packages [394 kB] 
Get:14 http://extras.ubuntu.com trusty/main amd64 Packages [14 B]              
Get:15 http://us.archive.ubuntu.com trusty-updates/restricted Sources [5,359 B]
Get:16 http://extras.ubuntu.com trusty/main i386 Packages [14 B]               
Get:17 http://security.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Get:18 http://us.archive.ubuntu.com trusty-updates/universe Sources [145 kB]   
Get:19 http://security.ubuntu.com trusty-security/universe amd64 Packages [122 kB]
Get:20 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [4,795 B]
Get:21 http://security.ubuntu.com trusty-security/main i386 Packages [371 kB]  
Get:22 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,167 B]
Get:23 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [674 kB]
Get:24 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Get:25 http://security.ubuntu.com trusty-security/universe i386 Packages [122 kB]
Get:26 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4,972 B]
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Get:27 http://security.ubuntu.com trusty-security/main Translation-en [216 kB] 
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:28 http://security.ubuntu.com trusty-security/multiverse Translation-en [2,437 B]
Get:29 http://security.ubuntu.com trusty-security/restricted Translation-en [3,206 B]
Get:30 http://security.ubuntu.com trusty-security/universe Translation-en [71.1 kB]
Get:31 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Get:32 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [332 kB]
Get:33 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.0 kB]
Get:34 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [652 kB]
Get:35 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:36 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [334 kB]
Get:37 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.2 kB]
Get:38 http://us.archive.ubuntu.com trusty-updates/main Translation-en [337 kB]
Get:39 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [6,832 B]
Get:40 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:41 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [174 kB]
Get:42 http://us.archive.ubuntu.com trusty-backports/main Sources [8,221 B]    
Get:43 http://us.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:44 http://us.archive.ubuntu.com trusty-backports/universe Sources [33.2 kB]
Get:45 http://us.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:46 http://us.archive.ubuntu.com trusty-backports/main amd64 Packages [9,402 B]
Get:47 http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:48 http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages [39.6 kB]
Get:49 http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,571 B]
Get:50 http://us.archive.ubuntu.com trusty-backports/main i386 Packages [9,411 B]
Get:51 http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:52 http://us.archive.ubuntu.com trusty-backports/universe i386 Packages [39.6 kB]
Get:53 http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Get:54 http://us.archive.ubuntu.com trusty-backports/main Translation-en [5,549 B]
Get:55 http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
Get:56 http://us.archive.ubuntu.com trusty-backports/restricted Translation-en [14 B]
Get:57 http://us.archive.ubuntu.com trusty-backports/universe Translation-en [34.5 kB]
Get:58 http://us.archive.ubuntu.com trusty Release [58.5 kB]                   
Get:59 http://us.archive.ubuntu.com trusty/main Sources [1,064 kB]             
Get:60 http://us.archive.ubuntu.com trusty/restricted Sources [5,433 B]        
Get:61 http://us.archive.ubuntu.com trusty/universe Sources [6,399 kB]         
Get:62 http://us.archive.ubuntu.com trusty/multiverse Sources [174 kB]         
Get:63 http://us.archive.ubuntu.com trusty/main amd64 Packages [1,350 kB]      
Get:64 http://us.archive.ubuntu.com trusty/restricted amd64 Packages [13.0 kB] 
Get:65 http://us.archive.ubuntu.com trusty/universe amd64 Packages [5,859 kB]  
Get:66 http://us.archive.ubuntu.com trusty/multiverse amd64 Packages [132 kB]  
Get:67 http://us.archive.ubuntu.com trusty/main i386 Packages [1,348 kB]       
Get:68 http://us.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB]  
Get:69 http://us.archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]   
Get:70 http://us.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]   
Get:71 http://us.archive.ubuntu.com trusty/main Translation-en [762 kB]        
Get:72 http://us.archive.ubuntu.com trusty/multiverse Translation-en [102 kB]  
Get:73 http://us.archive.ubuntu.com trusty/restricted Translation-en [3,457 B] 
Get:74 http://us.archive.ubuntu.com trusty/universe Translation-en [4,089 kB]  
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 32.2 MB in 54s (592 kB/s)                                              
Reading package lists... Done
keithwwalker@keithwwalker-GR8:~$ sudo apt-get install linux-headers-generic build-essential gitReading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.8 git-man libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl liberror-perl
  libfakeroot libstdc++-4.8-dev linux-headers-3.13.0-74
  linux-headers-3.13.0-74-generic
Suggested packages:
  debian-keyring g++-multilib g++-4.8-multilib gcc-4.8-doc libstdc++6-4.8-dbg
  git-daemon-run git-daemon-sysvinit git-doc git-el git-email git-gui gitk
  gitweb git-arch git-bzr git-cvs git-mediawiki git-svn libstdc++-4.8-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.8 git git-man
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  liberror-perl libfakeroot libstdc++-4.8-dev linux-headers-3.13.0-74
  linux-headers-3.13.0-74-generic linux-headers-generic
The following packages will be upgraded:
  libdpkg-perl
1 upgraded, 16 newly installed, 0 to remove and 247 not upgraded.
Need to get 30.1 MB of archives.
After this operation, 138 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libstdc++-4.8-dev amd64 4.8.4-2ubuntu1~14.04 [1,052 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main g++-4.8 amd64 4.8.4-2ubuntu1~14.04 [15.0 MB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty/main g++ amd64 4:4.8.2-1ubuntu6 [1,490 B]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libdpkg-perl all 1.17.5ubuntu5.5 [179 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main dpkg-dev all 1.17.5ubuntu5.5 [726 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty/main build-essential amd64 11.6ubuntu6 [4,838 B]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty/main libfakeroot amd64 1.20-3ubuntu2 [25.4 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty/main fakeroot amd64 1.20-3ubuntu2 [55.0 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty/main liberror-perl all 0.17-1.1 [21.1 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main git-man all 1:1.9.1-1ubuntu0.2 [699 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main git amd64 1:1.9.1-1ubuntu0.2 [2,701 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ trusty/main libalgorithm-diff-perl all 1.19.02-3 [50.0 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ trusty/main libalgorithm-diff-xs-perl amd64 0.04-2build4 [12.6 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ trusty/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-74 all 3.13.0-74.118 [8,889 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-74-generic amd64 3.13.0-74.118 [698 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-generic amd64 3.13.0.74.80 [2,240 B]
Fetched 30.1 MB in 25s (1,159 kB/s)                                            
E: Sub-process /usr/bin/dpkg returned an error code (2)
keithwwalker@keithwwalker-GR8:~$ git clone https://github.com/Braklet/rtl8811AU_rtl8821A-linux
The program 'git' is currently not installed. You can install it by typing:
sudo apt-get install git
keithwwalker@keithwwalker-GR8:~$ sudo apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  git-man liberror-perl
Suggested packages:
  git-daemon-run git-daemon-sysvinit git-doc git-el git-email git-gui gitk
  gitweb git-arch git-bzr git-cvs git-mediawiki git-svn
The following NEW packages will be installed:
  git git-man liberror-perl
0 upgraded, 3 newly installed, 0 to remove and 248 not upgraded.
Need to get 0 B/3,421 kB of archives.
After this operation, 21.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package liberror-perl.
(Reading database ... 164694 files and directories currently installed.)
Preparing to unpack .../liberror-perl_0.17-1.1_all.deb ...
Unpacking liberror-perl (0.17-1.1) ...
Selecting previously unselected package git-man.
Preparing to unpack .../git-man_1%3a1.9.1-1ubuntu0.2_all.deb ...
Unpacking git-man (1:1.9.1-1ubuntu0.2) ...
Selecting previously unselected package git.
Preparing to unpack .../git_1%3a1.9.1-1ubuntu0.2_amd64.deb ...
Unpacking git (1:1.9.1-1ubuntu0.2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up liberror-perl (0.17-1.1) ...
Setting up git-man (1:1.9.1-1ubuntu0.2) ...
Setting up git (1:1.9.1-1ubuntu0.2) ...
keithwwalker@keithwwalker-GR8:~$ git clone https://github.com/Braklet/rtl8811AU_rtl8821A-linux
Cloning into 'rtl8811AU_rtl8821A-linux'...
remote: Counting objects: 405, done.
remote: Total 405 (delta 0), reused 0 (delta 0), pack-reused 405
Receiving objects: 100% (405/405), 1.76 MiB | 1.47 MiB/s, done.
Resolving deltas: 100% (154/154), done.
Checking connectivity... done.
keithwwalker@keithwwalker-GR8:~$ cd ~/rtl8811AU_rtl8821A-linux
keithwwalker@keithwwalker-GR8:~/rtl8811AU_rtl8821A-linux$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.19.0-25-generic/build M=/home/keithwwalker/rtl8811AU_rtl8821A-linux  modules
make[1]: Entering directory `/usr/src/linux-headers-3.19.0-25-generic'
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_cmd.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_security.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_debug.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_io.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_ioctl_query.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_ioctl_set.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_ieee80211.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_mlme.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_mlme_ext.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_wlan_util.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_vht.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_pwrctrl.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_rf.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_recv.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_sta_mgt.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_ap.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_xmit.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_p2p.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_tdls.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_br_ext.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_iol.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_sreset.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_btcoex.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_beamforming.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_odm.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/efuse/rtw_efuse.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/osdep_service.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/os_intfs.o
/home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/os_intfs.c:713:2: warning: initialization from incompatible pointer type [enabled by default]
  .ndo_select_queue = rtw_select_queue,
  ^
/home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/os_intfs.c:713:2: warning: (near initialization for ‘rtw_netdev_ops.ndo_select_queue’) [enabled by default]
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/usb_intf.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/usb_ops_linux.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/ioctl_linux.o
/home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/ioctl_linux.c: In function ‘translate_scan’:
/home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/ioctl_linux.c:771:1: warning: the frame size of 1204 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/xmit_linux.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/mlme_linux.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/recv_linux.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/wifi_regd.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/rtw_android.o
/home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/rtw_android.c: In function ‘rtw_android_priv_cmd’:
/home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/rtw_android.c:766:14: warning: initialization makes pointer from integer without a cast [enabled by default]
    u8 *ptr = priv_cmd.buf;
              ^
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/rtw_proc.o
/home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/rtw_proc.c:438:2: warning: initialization from incompatible pointer type [enabled by default]
  {"rx_info", proc_get_rx_info, proc_reset_rx_info},
  ^
/home/keithwwalker/rtl8811AU_rtl8821A-linux/os_dep/linux/rtw_proc.c:438:2: warning: (near initialization for ‘adapter_proc_hdls[16].write’) [enabled by default]
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/hal_intf.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/hal_com.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/hal_com_phycfg.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/hal_phy.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/hal_btcoex.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/hal_hci/hal_usb.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/led/hal_usb_led.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/HalPwrSeqCmd.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/rtl8812a/Hal8812PwrSeq.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/rtl8812a/Hal8821APwrSeq.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/rtl8812a/rtl8812a_xmit.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/rtl8812a/rtl8812a_sreset.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/rtl8812a/rtl8812a_hal_init.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/rtl8812a/rtl8812a_phycfg.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/rtl8812a/rtl8812a_rf6052.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/rtl8812a/rtl8812a_dm.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/rtl8812a/rtl8812a_rxdesc.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/rtl8812a/rtl8812a_cmd.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/rtl8812a/usb/usb_halinit.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/rtl8812a/usb/rtl8812au_led.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/rtl8812a/usb/rtl8812au_xmit.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/rtl8812a/usb/rtl8812au_recv.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/rtl8812a/usb/usb_ops_linux.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/rtl8812a/rtl8812a_mp.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/odm_debug.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/odm_AntDiv.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/odm_interface.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/odm_HWConfig.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/odm.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/HalPhyRf.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8812a/HalHWImg8812A_FW.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8812a/HalHWImg8812A_MAC.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8812a/HalHWImg8812A_BB.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8812a/HalHWImg8812A_RF.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_FW.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_MAC.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_BB.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_RF.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8812a/HalPhyRf_8812A.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8812a/odm_RegConfig8812A.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8812a/odm_RTL8812A.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8821a/HalHWImg8821A_FW.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8821a/HalHWImg8821A_MAC.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8821a/HalHWImg8821A_BB.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8821a/HalHWImg8821A_RF.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8821a/HalHWImg8821A_TestChip_MAC.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8821a/HalHWImg8821A_TestChip_BB.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8821a/HalHWImg8821A_TestChip_RF.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8821a/HalPhyRf_8821A.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8821a/odm_RegConfig8821A.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/hal/OUTSRC/rtl8821a/odm_RTL8821A.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/platform/platform_ops.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_mp.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_mp_ioctl.o
  CC [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/core/rtw_bt_mp.o
  LD [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/8812au.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/keithwwalker/rtl8811AU_rtl8821A-linux/8812au.mod.o
  LD [M]  /home/keithwwalker/rtl8811AU_rtl8821A-linux/8812au.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.19.0-25-generic'
keithwwalker@keithwwalker-GR8:~/rtl8811AU_rtl8821A-linux$ sudo make install
install -p -m 644 8812au.ko  /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.19.0-25-generic
keithwwalker@keithwwalker-GR8:~/rtl8811AU_rtl8821A-linux$ sudo modprobe 8811au
modprobe: FATAL: Module 8811au not found.
keithwwalker@keithwwalker-GR8:~/rtl8811AU_rtl8821A-linux$ cd ~/rtl8811AU_rtl8821A-linux
keithwwalker@keithwwalker-GR8:~/rtl8811AU_rtl8821A-linux$ sudo modprobe rtl8811AU
modprobe: FATAL: Module rtl8811AU not found.
keithwwalker@keithwwalker-GR8:~/rtl8811AU_rtl8821A-linux$ 

```

---

### Post by keithwwalker on 2015-12-19
I believe the wifi is showing up as a usb (see the Realtek list):

```

keithwwalker@keithwwalker-GR8:~/rtl8811AU_rtl8821A-linux$ lsusb
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:1123 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:a811 **Realtek** Semiconductor Corp. 
Bus 001 Device 002: ID 24ae:2000  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
keithwwalker@keithwwalker-GR8:~/rtl8811AU_rtl8821A-linux$ pccardctl info
keithwwalker@keithwwalker-GR8:~/rtl8811AU_rtl8821A-linux$ 

```

I don't think it showed up here:
```

keithwwalker@keithwwalker-GR8:~/rtl8811AU_rtl8821A-linux$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 0b)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8534]
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8534]
	Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 0b)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8534]
	Kernel driver in use: snd_hda_intel
00:14.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB xHCI HC [8086:9c31] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8534]
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation Lynx Point-LP HECI #0 [8086:9c3a] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8534]
	Kernel driver in use: mei_me
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I218-V [8086:1559] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:85c4]
	Kernel driver in use: e1000e
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:860d]
	Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 1 [8086:9c10] (rev e4)
	Kernel driver in use: pcieport
00:1c.4 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 5 [8086:9c18] (rev e4)
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB EHCI #1 [8086:9c26] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8534]
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation Lynx Point-LP LPC Controller [8086:9c43] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8534]
	Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8534]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Lynx Point-LP SMBus Controller [8086:9c22] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8534]
02:00.0 3D controller [0302]: NVIDIA Corporation GM107M [GeForce GTX 860M] [10de:1392] (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device [1043:861e]
	Kernel driver in use: nouveau

```

---

### Post by praseodym on 2015-12-19
```
install -p -m 644 [COLOR="#FF0000"]8812au.ko[/COLOR]  /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/
```
```

sudo modprobe -v 8812au

```
should do the trick

---

### Post by keithwwalker on 2015-12-19
> **praseodym said:**
> ```
install -p -m 644 [COLOR="#FF0000"]8812au.ko[/COLOR]  /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/
```
```

sudo modprobe -v 8812au

```
should do the trick

It is not finding the file:

```
keithwwalker@keithwwalker-GR8:~$ install -p -m 644 8812au.ko  /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/
install: cannot stat &#8216;8812au.ko&#8217;: No such file or directory
 
```

BUT: I was able to find the 8812au.ko file in an Asus AC56 USB driver folder and was able to install:

```
keithwwalker@keithwwalker-GR8:~/Desktop/rtl8812AU_linux_v4.3.13_14061.20150505$ sudo install -p -m 644 8812au.ko  /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/
keithwwalker@keithwwalker-GR8:~/Desktop/rtl8812AU_linux_v4.3.13_14061.20150505$ sudo modprobe -v 8812au
insmod /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/8812au.ko 
```

Let's see if that works with a reboot, fingers crossed...

Nope, nothing is indicating that the wireless is here.
Any ideas?  I can't be the only Asus PC out here with this problem.  What frustration...

---

### Post by Hadaka on 2015-12-19
hi..posts 4 and 6
ubuntuforums.org/showthread.php?t=224063http://ubuntuforums.org/showthread.php?t=2240631&1&

---

### Post by keithwwalker on 2015-12-20
Wow, that github worked, where the others didn't!

[http://ubuntuforums.org/showthread.php?t=2240631&p=13104149#post13104149]("http://ubuntuforums.org/showthread.php?t=2240631&p=13104149#post13104149")

Thank you Hadaka!  Have an anchovy, herring and squid pizza with clam sauce!:
[https://www.facebook.com/berkeleybreathed/]("https://www.facebook.com/berkeleybreathed/")

This machine is now awesome with the wifi working!
Asus GR8 with Two SSD's, added 8gb RAM, and the secret internal USB port will be getting a bluetooth adaptor soon.

Thanks to everyone who helped out.  Each time I have a problem, I learn a bit more.

---

### Post by Hadaka on 2015-12-20
Awesome !!

---

### Post by keithwwalker on 2015-12-20
Wow, just when I thought I was out of the woods - the wifi was connecting good, but with every reboot, it has gotten progressively worse until now it recognizes the wifi signal, but won't make a connection.
Will have to research this snafu now....

I was able to reconnect by reloading into terminal:

```
cd rtl8812AU_8821AU_linux/
make clean
make
sudo make install
sudo modprobe 8812au
```

I have to experiment more to see if I have to reload the wifi every time I load an incremental software update.  The only other change was that I had my Note 4 phone plugged in and that was giving me some errors....

---

