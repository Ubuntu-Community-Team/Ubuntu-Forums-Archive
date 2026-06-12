---
title: "ubuntu 8.10 no connection with netgear wnda3100 wireless"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by alberto2323 on 2008-11-21
I am a newbie but do know a bit about computers but just not linux. I cant seem to figure out how to get my wireless connection to work. I have my computer connected through a wired connection but its upstairs and I need to bring my puter downstairs wirelessly. I also do not have the disk for my netgear wnda3100 wireless usb adapter so I don't know how i would be able to use windows drivers if that is an option. I would greatly appreciate if someone could walk me through step by step. Thank you

---

### Post by pytheas22 on 2008-11-22
If you could please open a terminal, run the following commands and post the output, I'll try to give you instructions on what to do:
```

lshw -C Network
lsusb
lspci -nn
uname -m
```

Remember that case matters in Linux, so make sure that the capital C in those commands is indeed capitalized.

---

### Post by alberto2323 on 2008-11-22
Thank you, here is the output.
alberto2323@alberto2323-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:14:2a:a3:44:2a
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.3 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 06:df:6d:1f:c7:25
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by alberto2323 on 2008-11-22
alberto2323@alberto2323-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 002 Device 002: ID 045e:00bb Microsoft Corp. Fingerprint Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0846:9010 NetGear, Inc. 
Bus 001 Device 004: ID 046d:08c5 Logitech, Inc. QuickCam Pro 5000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by alberto2323 on 2008-11-22
alberto2323@alberto2323-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 002 Device 002: ID 045e:00bb Microsoft Corp. Fingerprint Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0846:9010 NetGear, Inc. 
Bus 001 Device 004: ID 046d:08c5 Logitech, Inc. QuickCam Pro 5000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
alberto2323@alberto2323-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 81)
00:01.0 PCI bridge [0604]: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port [8086:2771] (rev 81)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV530LE [Radeon X1600/X1650 PRO] [1002:71c6]
01:00.1 Display controller [0380]: ATI Technologies Inc RV530LE [Radeon X1650 PRO] (Secondary) [1002:71e6]
02:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)

---

### Post by alberto2323 on 2008-11-22
alberto2323@alberto2323-desktop:~$ uname -m
i686

---

### Post by Joe2Shoe on 2008-11-22
alberto,
See if this works.
Go to System/Administration/Hardware Drivers and see if your wireless adapter drivers are listed.  If so, click on it, then click the 'activate' button below.  Reboot if necessary.
Good luck,
Joe2Shoe.

---

### Post by pytheas22 on 2008-11-22
alberto: please try running these commands; they should get the device working:
```

sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz
tar -xzvf wnda3100_win_32.tar.gz
sudo ndiswrapper -i arusb_lh.inf
echo ndiswrapper | sudo tee -a /etc/modules
```

Then reboot your computer and see if the wireless works.  If it still doesn't work at this point, please post the output of:
```

lsmod | grep ndis
lshw -C Network
sudo modprobe ndiswrapper
dmesg | grep -e ndis -e wlan
sudo iwlist scan
```

---

### Post by Joe2Shoe on 2008-11-22
Using Windows Wireless Drivers

Ubuntu supports a system known as NDISWrapper.  This allows you to use a Windows wireless device driver under Ubuntu.

   1. Obtain the Windows Driver for your system and locate the file that ends with .inf.
   2. Install ndisgtk (System/Administration/Synaptic Package Manager).
   3. Open ndisgtk (System/Administration/Windows Wireless Drivers).
   4. Select Install new driver.
   5. Choose the location of your Windows .inf file and click Install.
   6. Click OK.


[https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)
Install NDISwrapper so you can install the Windows driver for your wifi card.

Even though the driver seems to be activated and 'working fine', even though you have great signal strength, it isn't.  That was my case, also.

Copy the .inf Window's driver file for your wifi's card to a flash drive or cd, then copy it to your desktop in Ubuntu.
After installing NDISwrapper per the above link, locate the driver file and install it.
Then go to System/Administration/Hardware Drivers, and the driver should be listed, activate it, reboot if necessary (most often is), and check wifi connection.

---

### Post by alberto2323 on 2008-11-23
thanks you guys for your help. **Joe2shoe** the answer is it didnt show up in hardware drivers. 
**Pytheas22** here is the output since it still didnt work.
alberto2323@alberto2323-desktop:~$ lsmod | grep ndis
ndiswrapper           196380  0 
usbcore               149104  10 usb_storage,libusual,ndiswrapper,snd_usb_audio,uvcvideo,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd
alberto2323@alberto2323-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:14:2a:a3:44:2a
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.3 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f2:f5:93:fa:05:1c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
alberto2323@alberto2323-desktop:~$ sudo modprobe ndiswrapper
[sudo] password for alberto2323: 
alberto2323@alberto2323-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

alberto2323@alberto2323-desktop:~$ 

Thanks again for your help

---

### Post by pytheas22 on 2008-11-23
alberto2323: thanks for the information.  I see some strange things going on, but so that I can get a better idea of it all, could you please post the output of these commands, in this order:
```

lsusb
ndiswrapper -l
lsmod | grep ndis
dmesg | grep -e ndis -e wlan
```

Sorry to ask for more information, but I'm still not positive what's happening.

---

### Post by alberto2323 on 2008-11-26
Oh My God Im an Idiot. Im sorry it took me a little while to respond but i didnt even see that there was a second page to this post. any way thanks for the help and here is the output.

alberto2323@alberto2323-desktop:~$ lsusb
Bus 005 Device 005: ID 046d:08c5 Logitech, Inc. QuickCam Pro 5000
Bus 005 Device 004: ID 0846:9010 NetGear, Inc. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 001 Device 005: ID 045e:00bb Microsoft Corp. Fingerprint Reader
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 043d:0072 Lexmark International, Inc. X6170 Printer
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
alberto2323@alberto2323-desktop:~$ ndiswrapper -l
alberto2323@alberto2323-desktop:~$ lsmod | grep ndis
ndiswrapper           196380  0 
usbcore               149360  11 usb_storage,libusual,ndiswrapper,uvcvideo,usblp,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd
alberto2323@alberto2323-desktop:~$ dmesg | grep -e ndis -e wlan
[   14.484571] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.556893] usbcore: registered new interface driver ndiswrapper
alberto2323@alberto2323-desktop:~$

---

### Post by pytheas22 on 2008-11-27
Thanks for the post.  It seems that you don't have any Windows driver loaded into ndiswrapper, or at least ndiswrapper can't find it.  Please run the following commands, which should get the driver installed, and post all of the output here so that I can make sure that it's being installed correctly:
```

wget http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz
tar -xzvf wnda3100_win_32.tar.gz
sudo ndiswrapper -i arusb_lh.inf
ndiswrapper -l
```

---

### Post by alberto2323 on 2008-11-27
here is the output you requested.


alberto2323@alberto2323-desktop:~$ wget [http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz](http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz)
--2008-11-27 12:49:01--  [http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz](http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz)
Resolving burnthesorbonne.com... 174.133.198.114
Connecting to burnthesorbonne.com|174.133.198.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 178939 (175K) [application/x-gzip]
Saving to: `wnda3100_win_32.tar.gz'

100%[======================================>] 178,939     38.6K/s   in 4.5s    

2008-11-27 12:49:07 (38.6 KB/s) - `wnda3100_win_32.tar.gz' saved [178939/178939]

alberto2323@alberto2323-desktop:~$ tar -xzvf wnda3100_win_32.tar.gz
arusb_lh.cat
arusb_lh.inf
arusb_lh.sys
alberto2323@alberto2323-desktop:~$ sudo ndiswrapper -i arusb_lh.inf
[sudo] password for alberto2323: 
installing arusb_lh ...
alberto2323@alberto2323-desktop:~$ ndiswrapper -l
arusb_lh : driver installed
	device (0846:9010) present
alberto2323@alberto2323-desktop:~$

---

### Post by pytheas22 on 2008-11-28
Thanks.  Things look better now--'ndiswrapper -l' gives the output that you want to see.  Are you able to connect by using the Network Manager applet in the top-right corner of your screen?

If not, what is the output of:
```

sudo iwlist scan
lshw -C Network
ndiswrapper -l
dmesg | grep -e ndis -e wlan
```

---

### Post by alberto2323 on 2008-11-28
I really appreciate all the help you have given me. I brought the modem down from upstairs and have it connected through a wired connection at the moment. I checked the connection manager in the upper right hand corner and its not giving me any wireless connections. here is the output for what you gave me.

alberto2323@alberto2323-desktop:~$ sudo iwlist scan
[sudo] password for alberto2323: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

alberto2323@alberto2323-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:14:2a:a3:44:2a
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.3 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:57:2f:92:5b:e3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
alberto2323@alberto2323-desktop:~$ ndiswrapper -l
arusb_lh : driver installed
	device (0846:9010) present
alberto2323@alberto2323-desktop:~$ dmesg | grep -e ndis -e wlan
[   13.430543] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   13.817968] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   13.817985] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   13.817997] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   13.818010] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   13.818022] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   13.818034] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   13.818065] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   13.818081] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   13.818093] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   13.818108] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   13.818130] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   13.818148] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   13.818161] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   13.818206] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   13.818218] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   13.818242] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   13.818254] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   13.818266] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   13.818278] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   13.818300] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   13.818312] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   13.818324] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   13.818336] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   13.818345] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   13.818353] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   13.818358] ndiswrapper (load_sys_files:206): couldn't prepare driver 'arusb_lh'
[   13.819150] ndiswrapper (load_wrap_driver:108): couldn't load driver arusb_lh; check system log for messages from 'loadndisdriver'
[   13.824133] usbcore: registered new interface driver ndiswrapper
alberto2323@alberto2323-desktop:~$

---

### Post by pytheas22 on 2008-11-28
Unfortunately, ndiswrapper doesn't seem to like the Windows driver that you loaded into it, which is strange because I got it from a link on a page where someone had gotten a wnda3100 working through ndiswrapper.  It does however happen from time to time that certain versions of the Windows drivers don't agree with ndiswrapper, even though they should, so this isn't the end of the world.

It may help to try compiling ndiswrapper from source.  Please run these commands (and post output so that we can be sure all goes as intended), and they should get ndiswrapper compiled from source:
```

sudo apt-get install build-essential
sudo apt-get remove --purge ndiswrapper*
wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005&big_mirror=0
tar -xzvf ndiswrapper*
cd ndiswrapper*
make
sudo make install
wget http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz
tar -xzvf wnda3100_win_32.tar.gz
sudo ndiswrapper -i arusb_lh.inf
ndiswrapper -l
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
dmesg | tail
```

At this point, if you're lucky, your card should be working--but if not, there are other things that we can try.

I did find [this page]("http://ubuntuforums.org/showthread.php?t=690699") (see post #3), where someone says that he got the wnda3100 working on Debian using ndiswrapper, so it should definitely be possible to make it work on Ubuntu with a little more persistence.

---

### Post by alberto2323 on 2008-11-29
Ok so I dont know if i did this correctly cus im still hazy on the whole command thing and how its done but i hope i did it correctly for the most part. here is the output and this one is a long one. 

u11 [1354kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main g++-4.3 4.3.2-1ubuntu11 [4128kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main g++ 4:4.3.1-1ubuntu2 [1444B]  
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main dpkg-dev 1.14.20ubuntu6 [612kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main build-essential 11.4 [7172B]  
Fetched 6103kB in 37s (161kB/s)                                                
Selecting previously deselected package libstdc++6-4.3-dev.
(Reading database ... 161461 files and directories currently installed.)
Unpacking libstdc++6-4.3-dev (from .../libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb) ...
Selecting previously deselected package g++-4.3.
Unpacking g++-4.3 (from .../g++-4.3_4.3.2-1ubuntu11_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.3.1-1ubuntu2_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.20ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_i386.deb) ...
Processing triggers for man-db ...
Setting up dpkg-dev (1.14.20ubuntu6) ...
Setting up libstdc++6-4.3-dev (4.3.2-1ubuntu11) ...
Setting up g++-4.3 (4.3.2-1ubuntu11) ...
Setting up g++ (4:4.3.1-1ubuntu2) ...

Setting up build-essential (11.4) ...
alberto2323@alberto2323-desktop:~$ sudo apt-get remove --purge ndiswrapper*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting ndiswrapper-common for regex 'ndiswrapper*'
Note, selecting ndiswrapper-utils for regex 'ndiswrapper*'
Note, selecting ndiswrapper-source for regex 'ndiswrapper*'
Note, selecting ndiswrapper-modules-1.9 for regex 'ndiswrapper*'
Note, selecting ndiswrapper-utils-1.9 for regex 'ndiswrapper*'
The following packages were automatically installed and are no longer required:
  menu libgpac0.4.4 torcs-data-tracks libogmrip0 torcs-data-cars libpcrecpp0
  ogmtools ocrad mkvtoolnix
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ndisgtk* ndiswrapper-common* ndiswrapper-utils-1.9*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 676kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 162349 files and directories currently installed.)
Removing ndisgtk ...
Purging configuration files for ndisgtk ...
Removing ndiswrapper-utils-1.9 ...
Removing ndiswrapper-common ...
dpkg - warning: while removing ndiswrapper-common, directory `/etc/ndiswrapper' not empty so not removed.
Processing triggers for man-db ...
Processing triggers for menu ...
alberto2323@alberto2323-desktop:~$ wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005&big_mirror=0](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005&big_mirror=0)
[1] 11584
alberto2323@alberto2323-desktop:~$ tar -xzvf ndiswrapper*
tar: ndiswrapper*: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
alberto2323@alberto2323-desktop:~$ --2008-11-29 20:41:29--  [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005)
Resolving downloads.sourceforge.net... 216.34.181.60
Connecting to downloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.53.tar.gz](http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.53.tar.gz) [following]
--2008-11-29 20:41:29--  [http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.53.tar.gz](http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.53.tar.gz)
Resolving internap.dl.sourceforge.net... 74.201.0.131
Connecting to internap.dl.sourceforge.net|74.201.0.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198629 (194K) [application/x-tar]
Saving to: `ndiswrapper-1.53.tar.gz'

100%[======================================>] 198,629      158K/s   in 1.2s    

2008-11-29 20:41:30 (158 KB/s) - `ndiswrapper-1.53.tar.gz' saved [198629/198629]

cd ndiswrapper*
bash: cd: ndiswrapper-1.53.tar.gz: Not a directory
[1]+  Done                    wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005)
alberto2323@alberto2323-desktop:~$ cd ndiswrapper*
bash: cd: ndiswrapper-1.53.tar.gz: Not a directory
alberto2323@alberto2323-desktop:~$ tar -xzvf ndiswrapper*
ndiswrapper-1.53/
ndiswrapper-1.53/README
ndiswrapper-1.53/loadndisdriver.8
ndiswrapper-1.53/ndiswrapper.spec
ndiswrapper-1.53/INSTALL
ndiswrapper-1.53/ChangeLog
ndiswrapper-1.53/ndiswrapper.8
ndiswrapper-1.53/utils/
ndiswrapper-1.53/utils/ndiswrapper
ndiswrapper-1.53/utils/loadndisdriver.c
ndiswrapper-1.53/utils/ndiswrapper-buginfo
ndiswrapper-1.53/utils/Makefile
ndiswrapper-1.53/driver/
ndiswrapper-1.53/driver/mkexport.sh
ndiswrapper-1.53/driver/wrapmem.c
ndiswrapper-1.53/driver/pnp.h
ndiswrapper-1.53/driver/longlong.h
ndiswrapper-1.53/driver/rtl.c
ndiswrapper-1.53/driver/ntoskernel.c
ndiswrapper-1.53/driver/loader.h
ndiswrapper-1.53/driver/iw_ndis.c
ndiswrapper-1.53/driver/win2lin_stubs.S
ndiswrapper-1.53/driver/wrapper.c
ndiswrapper-1.53/driver/winnt_types.h
ndiswrapper-1.53/driver/wrapndis.h
ndiswrapper-1.53/driver/usb.h
ndiswrapper-1.53/driver/pe_linker.h
ndiswrapper-1.53/driver/ndis.h
ndiswrapper-1.53/driver/divdi3.c
ndiswrapper-1.53/driver/ndiswrapper.h
ndiswrapper-1.53/driver/hal.c
ndiswrapper-1.53/driver/wrapndis.c
ndiswrapper-1.53/driver/ntoskernel.h
ndiswrapper-1.53/driver/crt.c
ndiswrapper-1.53/driver/workqueue.c
ndiswrapper-1.53/driver/ntoskernel_io.c
ndiswrapper-1.53/driver/lin2win.h
ndiswrapper-1.53/driver/pnp.c
ndiswrapper-1.53/driver/loader.c
ndiswrapper-1.53/driver/ndis.c
ndiswrapper-1.53/driver/iw_ndis.h
ndiswrapper-1.53/driver/pe_linker.c
ndiswrapper-1.53/driver/wrapmem.h
ndiswrapper-1.53/driver/mkstubs.sh
ndiswrapper-1.53/driver/usb.c
ndiswrapper-1.53/driver/wrapper.h
ndiswrapper-1.53/driver/Makefile
ndiswrapper-1.53/driver/proc.c
ndiswrapper-1.53/AUTHORS
ndiswrapper-1.53/Makefile
alberto2323@alberto2323-desktop:~$ cd ndiswrapper*
alberto2323@alberto2323-desktop:~/ndiswrapper-1.53$ make
make -C driver
make[1]: Entering directory `/home/alberto2323/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.27-10-generic M=/home/alberto2323/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-10-generic'
  LD      /home/alberto2323/ndiswrapper-1.53/driver/built-in.o
  MKEXPORT /home/alberto2323/ndiswrapper-1.53/driver/crt_exports.h
  MKEXPORT /home/alberto2323/ndiswrapper-1.53/driver/hal_exports.h
  MKEXPORT /home/alberto2323/ndiswrapper-1.53/driver/ndis_exports.h
  MKEXPORT /home/alberto2323/ndiswrapper-1.53/driver/ntoskernel_exports.h
  MKEXPORT /home/alberto2323/ndiswrapper-1.53/driver/ntoskernel_io_exports.h
  MKEXPORT /home/alberto2323/ndiswrapper-1.53/driver/rtl_exports.h
  MKEXPORT /home/alberto2323/ndiswrapper-1.53/driver/usb_exports.h
  CC [M]  /home/alberto2323/ndiswrapper-1.53/driver/crt.o
  CC [M]  /home/alberto2323/ndiswrapper-1.53/driver/hal.o
  CC [M]  /home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.o
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c: In function ‘ndis_translate_scan’:
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1037: error: too few arguments to function ‘iwe_stream_add_event’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1047: error: too few arguments to function ‘iwe_stream_add_point’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1053: error: too few arguments to function ‘iwe_stream_add_event’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1064: error: too few arguments to function ‘iwe_stream_add_event’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1079: error: too few arguments to function ‘iwe_stream_add_event’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1093: error: too few arguments to function ‘iwe_stream_add_event’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1104: error: too few arguments to function ‘iwe_stream_add_point’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1120: error: too few arguments to function ‘iwe_stream_add_value’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1131: error: too few arguments to function ‘iwe_stream_add_point’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1137: error: too few arguments to function ‘iwe_stream_add_point’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1159: error: too few arguments to function ‘iwe_stream_add_point’
make[3]: *** [/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/alberto2323/ndiswrapper-1.53/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-10-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/alberto2323/ndiswrapper-1.53/driver'
make: *** [all] Error 2
alberto2323@alberto2323-desktop:~/ndiswrapper-1.53$ sudo make install
make -C driver install
make[1]: Entering directory `/home/alberto2323/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.27-10-generic M=/home/alberto2323/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-10-generic'
  CC [M]  /home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.o
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c: In function ‘ndis_translate_scan’:
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1037: error: too few arguments to function ‘iwe_stream_add_event’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1047: error: too few arguments to function ‘iwe_stream_add_point’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1053: error: too few arguments to function ‘iwe_stream_add_event’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1064: error: too few arguments to function ‘iwe_stream_add_event’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1079: error: too few arguments to function ‘iwe_stream_add_event’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1093: error: too few arguments to function ‘iwe_stream_add_event’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1104: error: too few arguments to function ‘iwe_stream_add_point’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1120: error: too few arguments to function ‘iwe_stream_add_value’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1131: error: too few arguments to function ‘iwe_stream_add_point’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1137: error: too few arguments to function ‘iwe_stream_add_point’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1159: error: too few arguments to function ‘iwe_stream_add_point’
make[3]: *** [/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/alberto2323/ndiswrapper-1.53/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-10-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/alberto2323/ndiswrapper-1.53/driver'
make: *** [install] Error 2
alberto2323@alberto2323-desktop:~/ndiswrapper-1.53$ sudo make install
make -C driver install
make[1]: Entering directory `/home/alberto2323/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.27-10-generic M=/home/alberto2323/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-10-generic'
  CC [M]  /home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.o
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c: In function ‘ndis_translate_scan’:
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1037: error: too few arguments to function ‘iwe_stream_add_event’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1047: error: too few arguments to function ‘iwe_stream_add_point’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1053: error: too few arguments to function ‘iwe_stream_add_event’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1064: error: too few arguments to function ‘iwe_stream_add_event’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1079: error: too few arguments to function ‘iwe_stream_add_event’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1093: error: too few arguments to function ‘iwe_stream_add_event’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1104: error: too few arguments to function ‘iwe_stream_add_point’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1120: error: too few arguments to function ‘iwe_stream_add_value’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1131: error: too few arguments to function ‘iwe_stream_add_point’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1137: error: too few arguments to function ‘iwe_stream_add_point’
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.c:1159: error: too few arguments to function ‘iwe_stream_add_point’
make[3]: *** [/home/alberto2323/ndiswrapper-1.53/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/alberto2323/ndiswrapper-1.53/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-10-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/alberto2323/ndiswrapper-1.53/driver'
make: *** [install] Error 2
alberto2323@alberto2323-desktop:~/ndiswrapper-1.53$ wget [http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz](http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz)
--2008-11-29 20:43:36--  [http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz](http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz)
Resolving burnthesorbonne.com... 174.133.198.114
Connecting to burnthesorbonne.com|174.133.198.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 178939 (175K) [application/x-gzip]
Saving to: `wnda3100_win_32.tar.gz'

100%[======================================>] 178,939      151K/s   in 1.2s    

2008-11-29 20:43:38 (151 KB/s) - `wnda3100_win_32.tar.gz' saved [178939/178939]

alberto2323@alberto2323-desktop:~/ndiswrapper-1.53$ tar -xzvf wnda3100_win_32.tar.gz
arusb_lh.cat
arusb_lh.inf
arusb_lh.sys
alberto2323@alberto2323-desktop:~/ndiswrapper-1.53$ sudo ndiswrapper -i arusb_lh.inf
sudo: ndiswrapper: command not found
alberto2323@alberto2323-desktop:~/ndiswrapper-1.53$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
alberto2323@alberto2323-desktop:~/ndiswrapper-1.53$ sudo ndiswrapper -i arusb_lh.inf
sudo: ndiswrapper: command not found
alberto2323@alberto2323-desktop:~/ndiswrapper-1.53$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
alberto2323@alberto2323-desktop:~/ndiswrapper-1.53$ sudo rmmod ndiswrapper
alberto2323@alberto2323-desktop:~/ndiswrapper-1.53$ sudo modprobe ndiswrapper
alberto2323@alberto2323-desktop:~/ndiswrapper-1.53$ dmesg | tail
[84292.737890] matrixview[9536]: segfault at 200 ip b80b9fed sp bfec1080 error 4 in ld-2.8.90.so[b80a7000+1a000]
[84892.742926] matrixview[9583]: segfault at 200 ip b7f45fed sp bfe4d010 error 4 in ld-2.8.90.so[b7f33000+1a000]
[85492.728852] matrixview[9586]: segfault at 200 ip b80b2fed sp bfbbbd80 error 4 in ld-2.8.90.so[b80a0000+1a000]
[86092.752488] matrixview[9591]: segfault at 200 ip b7fe8fed sp bf8f22b0 error 4 in ld-2.8.90.so[b7fd6000+1a000]
[86692.747826] matrixview[9594]: segfault at 200 ip b7f51fed sp bf858a20 error 4 in ld-2.8.90.so[b7f3f000+1a000]
[86712.060805] matrixview[9597]: segfault at 200 ip b80e7fed sp bf8eeab0 error 4 in ld-2.8.90.so[b80d5000+1a000]
[92881.131020] usbcore: deregistering interface driver ndiswrapper
[92881.132562] ndiswrapper (ntoskernel_exit:2671): object f6bc9a20(2) was not freed, freeing it now
[92893.874196] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[92893.904401] usbcore: registered new interface driver ndiswrapper
alberto2323@alberto2323-desktop:~/ndiswrapper-1.53$

---

### Post by pytheas22 on 2008-12-02
Sorry for not responding sooner; I've been traveling.

Apparently ndiswrapper doesn't compile on Ubuntu 8.10 for some reason, which is why you got so many error messages.  I'm sorry for not checking on this before.  I assumed it would compile because I've never had problems with ndiswrapper on any other Linux kernel in the past.

Fortunately, there is a patch that should allow you to compile and install ndiswrapper on Ubuntu 8.10.  Please try running these commands:

```

mkdir ndiswrapper
cd ndiswrapper
wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005&big_mirror=0
tar -xzvf ndiswrapper*
cd ndiswrapper*
wget http://www.slackware.com/~alien/slackbuilds/ndiswrapper/build/ndiswrapper_kernel_2.6.27.patch
patch -p0 < ndiswrapper_kernel_2.6.27.patch
make
sudo make install
wget http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz
tar -xzvf wnda3100_win_32.tar.gz
sudo ndiswrapper -i arusb_lh.inf
ndiswrapper -l
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
dmesg | tail
```

This should work.  Please post all output.

---

### Post by alberto2323 on 2008-12-06
Thank you so much for your response. I havent responded back in a while either because I thought you were gone and so I havent checked recently. I tryed this and here is the output.


alberto2323@alberto2323-desktop:~$ mkdir ndiswrapper
alberto2323@alberto2323-desktop:~$ cd ndiswrapper
alberto2323@alberto2323-desktop:~/ndiswrapper$ wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005&big_mirror=0](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005&big_mirror=0)
--2008-12-06 13:23:17--  [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005)
Resolving downloads.sourceforge.net... [1] 29278
alberto2323@alberto2323-desktop:~/ndiswrapper$ 216.34.181.60
Connecting to downloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://voxel.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.53.tar.gz](http://voxel.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.53.tar.gz) [following]
--2008-12-06 13:23:17--  [http://voxel.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.53.tar.gz](http://voxel.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.53.tar.gz)
Resolving voxel.dl.sourceforge.net... 208.122.28.18, 208.122.28.22, 208.122.28.3, ...
Connecting to voxel.dl.sourceforge.net|208.122.28.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198629 (194K) [application/x-gzip]
Saving to: `ndiswrapper-1.53.tar.gz'

100%[======================================>] 198,629      156K/s   in 1.2s    

2008-12-06 13:23:19 (156 KB/s) - `ndiswrapper-1.53.tar.gz' saved [198629/198629]


[1]+  Done                    wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005)
alberto2323@alberto2323-desktop:~/ndiswrapper$ tar -xzvf ndiswrapper*
ndiswrapper-1.53/
ndiswrapper-1.53/README
ndiswrapper-1.53/loadndisdriver.8
ndiswrapper-1.53/ndiswrapper.spec
ndiswrapper-1.53/INSTALL
ndiswrapper-1.53/ChangeLog
ndiswrapper-1.53/ndiswrapper.8
ndiswrapper-1.53/utils/
ndiswrapper-1.53/utils/ndiswrapper
ndiswrapper-1.53/utils/loadndisdriver.c
ndiswrapper-1.53/utils/ndiswrapper-buginfo
ndiswrapper-1.53/utils/Makefile
ndiswrapper-1.53/driver/
ndiswrapper-1.53/driver/mkexport.sh
ndiswrapper-1.53/driver/wrapmem.c
ndiswrapper-1.53/driver/pnp.h
ndiswrapper-1.53/driver/longlong.h
ndiswrapper-1.53/driver/rtl.c
ndiswrapper-1.53/driver/ntoskernel.c
ndiswrapper-1.53/driver/loader.h
ndiswrapper-1.53/driver/iw_ndis.c
ndiswrapper-1.53/driver/win2lin_stubs.S
ndiswrapper-1.53/driver/wrapper.c
ndiswrapper-1.53/driver/winnt_types.h
ndiswrapper-1.53/driver/wrapndis.h
ndiswrapper-1.53/driver/usb.h
ndiswrapper-1.53/driver/pe_linker.h
ndiswrapper-1.53/driver/ndis.h
ndiswrapper-1.53/driver/divdi3.c
ndiswrapper-1.53/driver/ndiswrapper.h
ndiswrapper-1.53/driver/hal.c
ndiswrapper-1.53/driver/wrapndis.c
ndiswrapper-1.53/driver/ntoskernel.h
ndiswrapper-1.53/driver/crt.c
ndiswrapper-1.53/driver/workqueue.c
ndiswrapper-1.53/driver/ntoskernel_io.c
ndiswrapper-1.53/driver/lin2win.h
ndiswrapper-1.53/driver/pnp.c
ndiswrapper-1.53/driver/loader.c
ndiswrapper-1.53/driver/ndis.c
ndiswrapper-1.53/driver/iw_ndis.h
ndiswrapper-1.53/driver/pe_linker.c
ndiswrapper-1.53/driver/wrapmem.h
ndiswrapper-1.53/driver/mkstubs.sh
ndiswrapper-1.53/driver/usb.c
ndiswrapper-1.53/driver/wrapper.h
ndiswrapper-1.53/driver/Makefile
ndiswrapper-1.53/driver/proc.c
ndiswrapper-1.53/AUTHORS
ndiswrapper-1.53/Makefile
alberto2323@alberto2323-desktop:~/ndiswrapper$ cd ndiswrapper*
alberto2323@alberto2323-desktop:~/ndiswrapper/ndiswrapper-1.53$ wget [http://www.slackware.com/~alien/slackbuilds/ndiswrapper/build/ndiswrapper_kernel_2.6.27.patch](http://www.slackware.com/~alien/slackbuilds/ndiswrapper/build/ndiswrapper_kernel_2.6.27.patch)
--2008-12-06 13:24:24--  [http://www.slackware.com/~alien/slackbuilds/ndiswrapper/build/ndiswrapper_kernel_2.6.27.patch](http://www.slackware.com/~alien/slackbuilds/ndiswrapper/build/ndiswrapper_kernel_2.6.27.patch)
Resolving [www.slackware.com](www.slackware.com)... 64.57.102.34
Connecting to [www.slackware.com|64.57.102.34|:80](www.slackware.com|64.57.102.34|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4310 (4.2K) [text/plain]
Saving to: `ndiswrapper_kernel_2.6.27.patch'

100%[======================================>] 4,310       --.-K/s   in 0.1s    

2008-12-06 13:24:24 (41.1 KB/s) - `ndiswrapper_kernel_2.6.27.patch' saved [4310/4310]

alberto2323@alberto2323-desktop:~/ndiswrapper/ndiswrapper-1.53$ patch -p0 < ndiswrapper_kernel_2.6.27.patch
patching file driver/iw_ndis.c
Hunk #11 succeeded at 1236 with fuzz 1.
alberto2323@alberto2323-desktop:~/ndiswrapper/ndiswrapper-1.53$ make
make -C driver
make[1]: Entering directory `/home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.27-10-generic M=/home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-10-generic'
  LD      /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/built-in.o
  MKEXPORT /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/crt_exports.h
  MKEXPORT /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/hal_exports.h
  MKEXPORT /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/ndis_exports.h
  MKEXPORT /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/ntoskernel_exports.h
  MKEXPORT /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/ntoskernel_io_exports.h
  MKEXPORT /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/rtl_exports.h
  MKEXPORT /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/usb_exports.h
  CC [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/crt.o
  CC [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/hal.o
  CC [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.o
  CC [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/loader.o
  CC [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/ndis.o
  CC [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/ntoskernel.o
  CC [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/ntoskernel_io.o
  CC [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/pe_linker.o
  CC [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/pnp.o
  CC [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/proc.o
  CC [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/rtl.o
  CC [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/wrapmem.o
  CC [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/wrapndis.o
  CC [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/wrapper.o
  CC [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/usb.o
  CC [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/divdi3.o
  LD [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/ndiswrapper.mod.o
  LD [M]  /home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-10-generic'
make[1]: Leaving directory `/home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver'
make -C utils
make[1]: Entering directory `/home/alberto2323/ndiswrapper/ndiswrapper-1.53/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/alberto2323/ndiswrapper/ndiswrapper-1.53/utils'
alberto2323@alberto2323-desktop:~/ndiswrapper/ndiswrapper-1.53$ sudo make install
[sudo] password for alberto2323: 
make -C driver install
make[1]: Entering directory `/home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.27-10-generic M=/home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-10-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-10-generic'
echo /lib/modules/2.6.27-10-generic/misc
/lib/modules/2.6.27-10-generic/misc
mkdir -p /lib/modules/2.6.27-10-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.27-10-generic/misc
/sbin/depmod -a 2.6.27-10-generic -b /
make[1]: Leaving directory `/home/alberto2323/ndiswrapper/ndiswrapper-1.53/driver'
make -C utils install
make[1]: Entering directory `/home/alberto2323/ndiswrapper/ndiswrapper-1.53/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/alberto2323/ndiswrapper/ndiswrapper-1.53/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
alberto2323@alberto2323-desktop:~/ndiswrapper/ndiswrapper-1.53$ wget [http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz](http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz)
--2008-12-06 13:25:30--  [http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz](http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz)
Resolving burnthesorbonne.com... 174.133.198.114
Connecting to burnthesorbonne.com|174.133.198.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 178939 (175K) [application/x-gzip]
Saving to: `wnda3100_win_32.tar.gz'

100%[======================================>] 178,939      150K/s   in 1.2s    

2008-12-06 13:25:31 (150 KB/s) - `wnda3100_win_32.tar.gz' saved [178939/178939]

alberto2323@alberto2323-desktop:~/ndiswrapper/ndiswrapper-1.53$ tar -xzvf wnda3100_win_32.tar.gz
arusb_lh.cat
arusb_lh.inf
arusb_lh.sys
alberto2323@alberto2323-desktop:~/ndiswrapper/ndiswrapper-1.53$ sudo ndiswrapper -i arusb_lh.inf
driver arusb_lh is already installed
alberto2323@alberto2323-desktop:~/ndiswrapper/ndiswrapper-1.53$ ndiswrapper -l
arusb_lh : driver installed
	device (0846:9010) present
alberto2323@alberto2323-desktop:~/ndiswrapper/ndiswrapper-1.53$ sudo rmmod ndiswrapper
alberto2323@alberto2323-desktop:~/ndiswrapper/ndiswrapper-1.53$ sudo modprobe ndiswrapper
alberto2323@alberto2323-desktop:~/ndiswrapper/ndiswrapper-1.53$ dmesg | tail
[671356.452554] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[671356.452576] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[671356.452589] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[671356.452600] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[671356.452613] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[671356.452621] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[671356.452629] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[671356.452633] ndiswrapper (load_sys_files:206): couldn't prepare driver 'arusb_lh'
[671356.467491] ndiswrapper (load_wrap_driver:108): couldn't load driver arusb_lh; check system log for messages from 'loadndisdriver'
[671356.483010] usbcore: registered new interface driver ndiswrapper
alberto2323@alberto2323-desktop:~/ndiswrapper/ndiswrapper-1.53$

Again you are a great help and I am willing to take the time if you are. Thank you.

---

### Post by pytheas22 on 2008-12-06
hmmmm, it seems that even with a clean build from source, ndiswrapper doesn't like the Windows driver that you're giving it.

However, I found an [obscure native Linux driver]("http://wireless.kernel.org/en/users/Drivers/otus#Featuressupported") that purports to support your card (it mentions your card specifically).  So before continuing to fight with ndiswrapper, let's try compiling and installing this new driver by typing (please post all output so that I can make sure it compiles properly...it compiled successfully on my Ubuntu 8.10 machine):

```
sudo apt-get install git git-core build-essential
git clone git://git.kernel.org/pub/scm/linux/kernel/git/mcgrof/otus.git ~/Desktop/otus
cd ~/Desktop/otus
make
sudo make install
```

Now reboot.  After rebooting, what is the output of:
```

sudo modprobe otus
lshw -C Network
lsmod | grep otus
sudo iwlist scan
```

If this doesn't work--and I'm a bit hesitant because I've never heard of this driver before, even though it's on the official linuxwireless.org site--we can go back to fighting with ndiswrapper.

---

### Post by alberto2323 on 2008-12-07
here you go buddy.

alberto2323@alberto2323-desktop:~$ sudo modprobe otus
[sudo] password for alberto2323: 
FATAL: Module otus not found.
alberto2323@alberto2323-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:14:2a:a3:44:2a
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.3 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: ath0
       serial: 00:03:7f:11:22:33
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-MIMO
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 32:ac:85:ef:aa:aa
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
alberto2323@alberto2323-desktop:~$ lsmod | grep otus
alberto2323@alberto2323-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ath0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

---

### Post by pytheas22 on 2008-12-07
Ah, well this is major progress: the driver seems to have installed properly, and you now have an interface called 'ath0', which corresponds to your wireless card.  Unfortunately, it doesn't look like the card can actually see networks.

Please try typing:
```

sudo ifconfig ath0 down
sudo ifconfig ath0 up
sudo iwlist scan
```

Does that show you a list of networks in range?  If not, what is the output of:
```

lsmod
dmesg | grep -e otus -e ath -e arusb
```

Since I've never heard of this driver, it might take some fidgeting to make it actually work, but I think it's really good that it compiled and brings up an interface for you.

---

### Post by alberto2323 on 2008-12-07
it finally shows a list of connections within range and one of them is mine but why does it not show it in network connections only in terminal.

---

### Post by pytheas22 on 2008-12-07
That's really good that it shows a list of networks in range.  I'm not sure why they won't show up in Network Manager (are you sure you're left-clicking on the applet, not right-clicking?), but one thing to try is to install wicd, an alternative connection manager that may work better, especially with obscure drivers.  You can install wicd by typing:
```

echo 'deb http://apt.wicd.net intrepid extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

(Note that this will uninstall Network Manager; if you want it back at any time, type 'sudo apt-get install network-manager-gnome'.)

Then launch it from the Applications>Internet menu.  Can you see networks and connect to them using wicd?

---

### Post by alberto2323 on 2008-12-08
Well It says that theres no wireless networks found. dont get why. I was trying it on the first network mannager and tryed left clicking on it and/or right clicking on it and editing connections but didnt show the wireless connections and still doesnt show it with this one either. It just keep showing me the wired connection that I have it connected to. Thanks

---

### Post by pytheas22 on 2008-12-08
Strange.  First thing to check is to go to preferences in wicd and make sure that the name of the wireless interface is specified as 'ath0'--this could be why wicd won't see any networks.

If that doesn't help, please post the output of:
```

sudo iwlist scan
```

at a time when it displays your networks.  With that, we could try connecting manually in order to verify that the driver itself actually works.

---

### Post by alberto2323 on 2008-12-09
It doesnt give me the option to change it to atho just shows wired as default. but heres the output you requested and just in case your wondering my wireless router is the netgear one.


alberto2323@alberto2323-desktop:~$ sudo iwlist scan
[sudo] password for alberto2323: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:1B:2F:D5:DC:94
                    ESSID:"NETGEAR2323"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=188/100  Signal level=94/154  Noise level=0/154
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    Extra:rsn_ie=30140100000fac020100000fac040100000fac020000
          Cell 02 - Address: 00:0F:66:9E:5D:11
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=72/100  Signal level=36/154  Noise level=0/154
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000
          Cell 03 - Address: 00:12:88:AE:3F:69
                    ESSID:"2WIRE821"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/100  Signal level=17/154  Noise level=0/154
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

pan0      Interface doesn't support scanning.

alberto2323@alberto2323-desktop:~$

---

### Post by pytheas22 on 2008-12-09
> It doesnt give me the option to change it to atho just shows wired as default. but heres the output you requested and just in case your wondering my wireless router is the netgear one.

Are you sure you looked in the right place?  You should click 'preferences' in the main wicd window, and a box should pop up where you can tell it the name of the wireless interface (among other things).  I'll attach a screenshot.

It is possible, however, that wicd doesn't want to play nicely with this wireless driver, which wouldn't surprise me since this driver is so obscure.  But connecting to WPA by hand is complicated and not very fun (I was hoping you only used WEP), so let's be absolutely sure that wicd won't work before we go into wpa_supplicant and all that.

---

### Post by alberto2323 on 2008-12-10
yup I went there and it only shows MIMO and in the drop down arrow it doesnt show atho either. dont know if its supposed to but either way it doesnt.

---

### Post by pytheas22 on 2008-12-10
I guess we can try connecting manually then.  First, let's do it without the WPA, just to ensure that the card can definitely complete a connection--it will be much simpler without the WPA variable in there.  So please disable encryption on your router temporarily (leave it on the same channel, 9), then run these commands:
```

sudo iwconfig ath0 essid "NETGEAR2323" channel 9 mode managed
sudo dhclient ath0
```

That should get you an IP address and allow you to browse the Internet; does it work?

> yup I went there and it only shows MIMO and in the drop down arrow it doesnt show atho either. dont know if its supposed to but either way it doesnt.

I'm not sure what you mean; could you take a screenshot?

---

### Post by alberto2323 on 2008-12-11
ok so I do have internet when connected through the cable but its just the wireless that is the problem. Also I guess im an idiot cuz I can not for the life of me remember how to take a screenshot and I feel so stupid for not remembering but I guess Im just having a brain fart.

---

### Post by alberto2323 on 2008-12-11
Ok so I remembered. Here you go.

---

### Post by pytheas22 on 2008-12-11
Thanks for the screenshots.

You should just be able to type 'ath0' in the box that currently reads 'MIMO'.  There's no drop-down menu or anything; you just have to type the interface name manually in the box.  Are you able to do that, and if so can you see networks then?

---

### Post by alberto2323 on 2008-12-13
I was able to type ath0 in the box and then refreshed it but still nothing.

---

### Post by pytheas22 on 2008-12-13
I guess the only thing left to do at this point, then, is to connect manually.  As I said earlier, it would make things much less complicated if you could please disable security on your router temporarily, so that we at least can get connected that way and verify that the driver can handle that much.

After disabling the security, type these commands to connect:
```

sudo iwconfig ath0 mode managed essid "NETGEAR2323" channel 9
sudo dhclient ath0
```

That should get you and IP address and allow you to connect via the wireless.  Does it work?  If so, we can next deal with connecting under WPA.

---

### Post by alberto2323 on 2008-12-14
ok so I first tryed what you asked and there was nothing but then thought to myself why not disconnect the wired internet and then all of a sudden it was showing the wireless networks but just wouldnt stay connected. Now it doesnt want to show anything. Security is turned off like you asked. I am posting the output of what comes up now that I try those commands again.


alberto2323@alberto2323-desktop:~$ sudo iwconfig ath0 mode managed essid "NETGEAR2323" channel 9
alberto2323@alberto2323-desktop:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 12669
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ath0/00:1b:2f:bb:42:84
Sending on   LPF/ath0/00:1b:2f:bb:42:84
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.2 on ath0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.2 on ath0 to 255.255.255.255 port 67
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
Trying recorded lease 192.168.1.2
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
alberto2323@alberto2323-desktop:~$ 



Well atleast you were able to get the networks to show. Even if it was for just a minute. Guess well just have to keep on trying. Thanks

---

### Post by pytheas22 on 2008-12-14
When you unplug the cable, the wireless networks show up in wicd?  Can you connect to them for a few seconds and then it drops, or do you not get connected at all?

Unfortunately it doesn't seem like manually requesting an IP address is working either.  It may help if you run these commands:
```

sudo dhclient -r eth0
sudo dhclient -r ath0
sudo iwconfig ath0 mode managed essid "NETGEAR2323" channel 9
sudo dhclient ath0
```

But it may not...I'm thinking at this point that this driver is just not going to work, and we may to go back to the drawing board and figure out a new strategy.  I'm really sorry this is taking so long...but I've never met a Linux problem that I couldn't solve if I committed enough time.

---

### Post by alberto2323 on 2008-12-15
now its not even showing me the wireless networks. But to answer your question yes it was allowing me to connect but it just kept disconnecting. It didnt stay connected for longer than a min. Anyway thanks for all the help I know how it is when i get frustrated and cant seem to figure out what the problem is but like you I dont give up either. The thing is that im comming from windows and linux is way to knew for me but I really like it better than windows. I had enough of windows. So again thanks for the help and here is the output for the commands you asked me to use. 


alberto2323@alberto2323-desktop:~$ sudo dhclient -r eth0
[sudo] password for alberto2323: 
There is already a pid file /var/run/dhclient.pid with pid 6730
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:14:2a:a3:44:2a
Sending on   LPF/eth0/00:14:2a:a3:44:2a
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
alberto2323@alberto2323-desktop:~$ sudo dhclient -r ath0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ath0/00:1b:2f:bb:42:84
Sending on   LPF/ath0/00:1b:2f:bb:42:84
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
alberto2323@alberto2323-desktop:~$ sudo iwconfig ath0 mode managed essid "NETGEAR2323" channel 9
alberto2323@alberto2323-desktop:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ath0/00:1b:2f:bb:42:84
Sending on   LPF/ath0/00:1b:2f:bb:42:84
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
alberto2323@alberto2323-desktop:~$

---

### Post by pytheas22 on 2008-12-17
Sorry for the slow reply.

After googling exhaustively, I came across [this thread]("http://ubuntuforums.org/showthread.php?t=885520"), which explains how to get this card working on Ubuntu 8.04 using ndiswrapper (you will need to grab the driver for it from a Windows computer; hopefully you have one available).

Of course, we already tried ndiswrapper and found that it didn't work because it didn't like the Windows driver for some obscure reason.  You might have better luck following the steps in that guide, or you might have to use Ubuntu 8.04 instead of 8.10--it's possibly that the ndiswrapper issues with this card are specific to 8.10.

Before following that guide, you will need to blacklist the otus driver so that it won't interfere with ndiswrapper.  To do that, run these commands:

```
echo 'blacklist arusb' | sudo tee -a /etc/modprobe.d/blacklist
```

Also, type this command:

```
sudo gedit /etc/modprobe.d/blacklist

```
and a file will open up.  Delete any lines in that file that say:
```

blacklist ndiswrapper
```

Hopefully the page I linked to above will do the trick.  Please let me know, and again, sorry this is taking so long.

---

### Post by alberto2323 on 2008-12-22
I actually tried that before I made this post and since i didnt have the disk I couldnt follow it exactly and couldnt get it to work. I dont know how else to get it to work. I wouldnt trouble myself to much more over this. I at least have it connected via cable. I was in real need of this before because I didnt have a line in the basement where the computer is connected and that was my problem but now its up and running. Thanks for all your help and if you still want to continue to try ill keep trying also but work yourself up over it to much. Again thanks for everything.

---

### Post by pytheas22 on 2008-12-22
I started trying to [help another user]("http://ubuntuforums.org/showthread.php?p=6420019") with the same card yesterday; unfortunately we don't seem to be having much luck so far.  I'm hoping that compiling the 'otus' driver using the latest git code will do the trick--hopefully it's been improved since when you tried it a couple weeks ago.  But if not, I guess I can try ndiswrapper with that other user, and see what happens.  I don't know if he has the Windows driver CD.

I imagine that in a few months' time, the otus driver should be drastically improved, and will hopefully be merged with the kernel by April so that Ubuntu 9.04 can come with out-of-the-box support for this card.  But for the time being, if ndiswrapper won't work, I'm not sure what to do besides compiling the latest otus code every week or so until you happen upon a snapshot that works (and if you do find code that works, please save it so that others can access it easily).

---

### Post by alberto2323 on 2008-12-28
Not a problem. Thank you

---

### Post by sku_dave on 2009-03-25
> **pytheas22 said:**
> alberto: please try running these commands; they should get the device working:
```

sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget http://burnthesorbonne.com/files/wnda3100_win_32.tar.gz
tar -xzvf wnda3100_win_32.tar.gz
sudo ndiswrapper -i arusb_lh.inf
echo ndiswrapper | sudo tee -a /etc/modules
```

Then reboot your computer and see if the wireless works.  If it still doesn't work at this point, please post the output of:
```

lsmod | grep ndis
lshw -C Network
sudo modprobe ndiswrapper
dmesg | grep -e ndis -e wlan
sudo iwlist scan
```

THANK YOU ! Works flawlessly on my R3000 w/ broadcom wifi. Now this machine will never see windows again :)

---

### Post by sku_dave on 2009-04-24
unfortunately this fix doesn't appear to work with ubuntu 9.04

any ideas ?


dave@dave-laptop:~$ lsmod | grep ndis
ndiswrapper           193436  0 
dave@dave-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:47:bb:a7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.192 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:b7:aa:f4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b2:e8:67:a1:4b:5d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
dave@dave-laptop:~$ 
dave@dave-laptop:~$ dmesg | grep -e ndis -e wlan
[   17.407607] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   17.512279] usbcore: registered new interface driver ndiswrapper
dave@dave-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

dave@dave-laptop:~$ clear

dave@dave-laptop:~$ lsmod | grep ndis
ndiswrapper           193436  0 
dave@dave-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:47:bb:a7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.192 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:b7:aa:f4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b2:e8:67:a1:4b:5d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
dave@dave-laptop:~$ sudo modprobe ndiswrapper
dave@dave-laptop:~$ dmesg | grep -e ndis -e wlan
[   17.407607] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   17.512279] usbcore: registered new interface driver ndiswrapper
dave@dave-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

---

### Post by pytheas22 on 2009-04-24
**sku_dave**: it looks like you have a totally different kind of wireless card than the other users in this thread--you have a Broadcom 4306 card, not a Netgear wnda3100.

For your card, it should be sufficient to run these commands to get it to work:
```

sudo apt-get install b43-fwcutter
```

You should also be able to make it work by enabling it in System>Administration>Hardware Drivers.

If it still doesn't work after a reboot, please post the output of these commands:
```

dmesg | grep -e b43 -e wlan
ls /lib/firmware
```

---

### Post by sku_dave on 2009-04-25
Oh jeez, I didn't even have the driver installed ! So I guess the previous fix still works :P

Thanks for the help though !

---

