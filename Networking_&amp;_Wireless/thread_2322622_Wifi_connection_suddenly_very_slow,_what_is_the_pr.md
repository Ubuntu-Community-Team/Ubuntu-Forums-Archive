---
title: "Wifi connection suddenly very slow, what is the problem?"
date: 2016-04-29
forum: Networking &amp; Wireless
---

### Post by federicodemaria on 2016-04-29
Hi all, 
my wifi connection used to work well, but lately it has become very slow. I run a speed test and it gives me that download is 0.10 Mbps, sometimes it doesn't even manage to load the page. I'm sitting next to the router. At the same time, if I connect via LAN then I get 2 to 3 Mbps. Same, when I run a speed test with my tablet, I get again 2 to 3 Mbps; or with another laptop also with Ubuntu. So, I think it's a problem with my laptop.  

I called the internet provider, and they too told that it could be a problem with my own computer. In particular, they suggested I update the driver of the wifi card. 
Now, in the past, it used to work well. So, since I'm a beginner, I'm asking for help before I make a bigger problem while trying to solve it. 

Below I paste the info regarding my network and drivers, from the info I've found online. I couldn't solve the problem myself. 
[http://askubuntu.com/questions/524142/how-to-update-all-driver-software-via-terminal](http://askubuntu.com/questions/524142/how-to-update-all-driver-software-via-terminal)
[http://ubuntuforums.org/showthread.php?t=1012700](http://ubuntuforums.org/showthread.php?t=1012700) 

[B]The questions are: 
1) What could the problem be that suddenly makes my wifi connection so slow? 
2) Is my wifi card driver updated? If not, how could I update it? [/B]

I'm with Ubuntu 14.04.4 LTS. I use Firefox where I have installed some security and privacy add-on like Ghostery and Privacy Badger. 
However, I get the same problem from Google Chrome where I don't have those installed. I think I regularly update my system properly, but might be wrong. 

In case you can provide any suggestions or solutions, they would be most welcome. 

Thank you for your kind support 

Best, 
jhonny 

```
Interface: 802.11 WiFi (wlan0)

**MY NETWORK **
Following these instructions [http://ubuntuforums.org/showthread.php?t=1012700](http://ubuntuforums.org/showthread.php?t=1012700) 
I run: 
lspci -nn
lshw -C network

jhonny@jhonny-ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM77 Express Chipset LPC Controller [8086:1e57] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
jhonny@jhonny-ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network              
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 1c:3e:84:dc:36:09
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.1.163 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:f0500000-f0507fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 07
       serial: 3c:97:0e:9f:6f:35
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.15 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:25 ioport:2000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
jhonny@jhonny-ubuntu:~$




**ARE THE DRIVERS UP TO DATE? **
I followed these instructions: [http://askubuntu.com/questions/524142/how-to-update-all-driver-software-via-terminal](http://askubuntu.com/questions/524142/how-to-update-all-driver-software-via-terminal)
and run 
apt-cache policy linux-image-generic 
apt-cache policy linux-firmware

jhonny@jhonny-ubuntu:~$ apt-cache policy linux-image-generic
linux-image-generic:
  Installed: (none)
  Candidate: 3.13.0.85.91
  Version table:
     3.13.0.85.91 0
        500 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
     3.13.0.24.28 0
        500 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
jhonny@jhonny-ubuntu:~$ ^C
jhonny@jhonny-ubuntu:~$

jhonny@jhonny-ubuntu:~$ apt-cache policy linux-firmware
linux-firmware:
  Installed: 1.127.22
  Candidate: 1.127.22
  Version table:
 *** 1.127.22 0
        500 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1.127 0
        500 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
jhonny@jhonny-ubuntu:~$

**INFO ABOUT MY SYSTEM **
lshw - List Hardware

jhonny@jhonny-ubuntu:~$ sudo lshw -short
[sudo] password for jhonny: 
H/W path       Device      Class          Description
=====================================================
                           system         62742QG (LENOVO_MT_6274)
/0                         bus            62742QG
/0/5                       processor      Intel(R) Core(TM) i3-2348M CPU @ 2.30GHz
/0/5/7                     memory         32KiB L1 cache
/0/5/8                     memory         256KiB L2 cache
/0/5/9                     memory         3MiB L3 cache
/0/6                       memory         32KiB L1 cache
/0/c                       memory         4GiB System Memory
/0/c/0                     memory         DIMM [empty]
/0/c/1                     memory         4GiB SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
/0/0                       memory         128KiB BIOS
/0/100                     bridge         2nd Generation Core Processor Family DRAM Controller
/0/100/2                   display        2nd Generation Core Processor Family Integrated Graphics Controller
/0/100/14                  bus            7 Series/C210 Series Chipset Family USB xHCI Host Controller
/0/100/16                  communication  7 Series/C210 Series Chipset Family MEI Controller #1
/0/100/1a                  bus            7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
/0/100/1b                  multimedia     7 Series/C210 Series Chipset Family High Definition Audio Controller
/0/100/1c                  bridge         7 Series/C210 Series Chipset Family PCI Express Root Port 1
/0/100/1c.1                bridge         7 Series/C210 Series Chipset Family PCI Express Root Port 2
/0/100/1c.1/0  wlan0       network        BCM43142 802.11b/g/n
/0/100/1c.3                bridge         7 Series/C210 Series Chipset Family PCI Express Root Port 4
/0/100/1c.3/0  eth0        network        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/1d                  bus            7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
/0/100/1f                  bridge         HM77 Express Chipset LPC Controller
/0/100/1f.2                storage        7 Series Chipset Family 6-port SATA Controller [AHCI mode]
/0/100/1f.3                bus            7 Series/C210 Series Chipset Family SMBus Controller
/0/1           scsi1       storage        
/0/1/0.0.0     /dev/sda    disk           500GB HGST HTS545050A7
/0/1/0.0.0/1   /dev/sda1   volume         511MiB Windows FAT volume
/0/1/0.0.0/2   /dev/sda2   volume         461GiB EXT4 volume
/0/1/0.0.0/3   /dev/sda3   volume         3947MiB Linux swap volume
/0/2           scsi4       storage        
/0/2/0.0.0     /dev/cdrom  disk           DVD-RW DS8A8SH
/0/3           scsi6       storage        
/0/3/0.0.0     /dev/sdb    disk           Card  Reader
/0/3/0.0.0/0   /dev/sdb    disk           
jhonny@jhonny-ubuntu:~$ ^C

UBUNTU RELEASE 

jhonny@jhonny-ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty
jhonny@jhonny-ubuntu:~$
```

Just to be sure, I have run an update from the Terminal and keep having the same problem. 

sudo apt-get dist-upgrade
sudo apt-get dist-upgrade

After upgrade, I've re-started the system and the problem seem to be solved. 

For updating, I followed these instructions: [http://askubuntu.com/questions/476679/how-to-update-software-using-terminal](http://askubuntu.com/questions/476679/how-to-update-software-using-terminal) 

Thank you and sorry for bothering you 

Best, 
jhonny

---

