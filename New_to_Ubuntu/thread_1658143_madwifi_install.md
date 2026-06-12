---
title: "madwifi install"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by fin2010 on 2011-01-02
anyone know how to install madwifi? need a complete beginners guide...been looking on the ubuntu forums but wouldnt load any of the pages.
I also downloaded and followed a script but that didn't work either.
Just need to install madwifi, got ubuntu and a ahteros wlm54g network adapter

---

### Post by gandaran on 2011-01-02
> **fin2010 said:**
> anyone know how to install madwifi? need a complete beginners guide...been looking on the ubuntu forums but wouldnt load any of the pages.
I also downloaded and followed a script but that didn't work either.
Just need to install madwifi, got ubuntu and a ahteros wlm54g network adapter
if you can connect the laptop to ethernet internet I would recommend installing first 'module-assistant' from the package manager then choose the madwifi from the module assistant list, use the module assistant to download the madwifi drivers, install and compile them and load the madwifi module, it will save you a lot of work doing it by any other method.
module-assistant runs from the terminal command line.

---

### Post by fin2010 on 2011-01-02
ok great , thanks for the advice.
I have installed module assistant and started it in the termina.
I opened module assistant and ran the update. 
Then I selected the madwifi from the list 

When  select the first option "list"

responds "madwifi-source (source package not installed):                             &#9474;
 &#9474;   -- Binary package(s) for kernel(s):                                      &#9474;
 &#9474;    + (2.6.35-24-generic): not found                                        &#9474;
 &#9474; Some packages could not be found. The "search" command can search in the   &#9474;
 &#9474; package pool for precompiled packages."

When I select "Search"

Responds - "madwifi-source (source package not installed):                             &#9474;
 &#9474;   -- Binary package(s) for kernel(s):                                      &#9474;
 &#9474;    + (2.6.35-24-generic):     "


When I select "Get"

Responds - "Installation of the madwifi-source source failed.                    
     &#9474;                                                                      
     &#9474; Ignoring this package. Maybe you need to add something to            
     &#9474; sources.list, maybe the contrib and non-free archives. "

When I select "Build"

REsponds - "Installation of the madwifi-source source failed.                    
     &#9474;                                                                      
     &#9474; Ignoring this package. Maybe you need to add something to            
     &#9474; sources.list, maybe the contrib and non-free archives. "

When I select Installl nothing happens.

Any ideas on what im doing wrong?

---

### Post by gandaran on 2011-01-02
update the software package list
```
sudo apt-get update
```
or click the reload button in synaptic package manager, maybe this will fix the issue, try using synaptic package manager to download/install the madwifi source code first then use module-assistant for the rest compile/build and load madwifi module.
you need internet connection for all of this.

---

### Post by fin2010 on 2011-01-02
Thanks again for all the help.

Well I have internet on my laptop at the moment.
When I try to reload on the synaptic package manager this happens -
It downloads most of the files but some it could not download.
The error message reads -
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to archive.canonical.com:80 (91.167.0.4). - connect (110: Connection timed out)
I believe it maybe because I added a couple of lines to the sources list after following instructions on this site 
- [http://www.punknix.com/?q=node/110](http://www.punknix.com/?q=node/110)
The lines I added were - 
deb [http://ftp.hk.debian.org/debian/](http://ftp.hk.debian.org/debian/) etch main contrib non-free
deb-src [http://ftp.hk.debian.org/debian/](http://ftp.hk.debian.org/debian/) etch main contrib non-free


As I am completley new to Ubuntu  when I follow guides I follow the instructions but dont neccessarily know what I am doing.

---

### Post by gandaran on 2011-01-02
sorry for all this, I checked with synaptic package manager and the mad-wifi source code is no longer there, I don't know why it was removed in ubuntu 10.10! I did compile the mad-wifi drivers in ubuntu 10.04 but the atheros open source driver is working well on my ubuntu 10.10 netbook so I hadn't checked if they where still available from the repositories.

---

### Post by fin2010 on 2011-01-02
Also could not find madwifi under synaptic package manager

---

### Post by wep940 on 2011-01-02
I think if you look at the madwifi web page you will find that they are incorporating the drivers into the distribution itself.  I don't use those drivers, but perhaps there is a module that needs to be loaded, a module that needs to be blacklisted or some other simple thing to get this working.
 
Please, when searching for information on wireless in Ubuntu, be sure to include the version of ubuntu in your search.  Many people are looking at old outdated posts and finding things like downloading the source for ndiswrapper, etc., when that is not necessary.  When in doubt, post the following information in a request here for help:
 
lspci
 
lsusb
 
lshw -C network
 
ifconfig
 
iwconfig

---

### Post by fin2010 on 2011-01-02
Well this is so confusing lol .
I don't understand why I can't just use assistant-module to install madwifi from the madwifi folder , as I already downloaded a madwifi zip and extracted it to desktop. So shouldnt I be able to install madwifi through assistant-module without being online ?
Damn I just wish I could get it working

---

### Post by gandaran on 2011-01-02
well since you have installed all the necessary compiling tools now all you have to do is compile the madwifi driver, extract the madwifi tar package you downloaded earlier and look for the readme file which should have the run instructions.
after compiling the package I think but not totally sure you have to remove the atheros open source module and load the madwifi module.
one question before you do anything, doesn't the default wireless open source driver work? I have some doubts, if its not working now probably it want work with the proprietary driver too.

---

### Post by fin2010 on 2011-01-02
Regarding wep940's comments 
After typing these commands this is what i got-
lspci
 
lsusb
 
lshw -C network
 
ifconfig
 
iwconfig 	



  	 	 	 	p { margin-bottom: 0.21cm; }  [COLOR=#800000]Lspci[/COLOR]
 
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge 
 00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge 
 00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge 
 00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge 
 00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge 
 00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller 
 00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device 
 00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge 
 00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge 
 00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80) 
 00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80) 
 00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80) 
 00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) 
 00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
 00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
 00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
 00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
 00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) 
 00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge 
 00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller 
 00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c) 
 00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge 
 00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge 
 01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01) 
 04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10) 
 05:01.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01) 
 

 
[COLOR=#800000]lsusb[/COLOR]


 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 002: ID 076b:4321 OmniKey AG CardMan 4321 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 
[COLOR=#800000]lshw -C network[/COLOR]


  *-network                
        description: Ethernet interface 
        product: VT6102 [Rhine-II] 
        vendor: VIA Technologies, Inc. 
        physical id: 12 
        bus info: pci@0000:00:12.0 
        logical name: eth0 
        version: 7c 
        serial: 00:14:0b:0b:7d:b5 
        size: 10MB/s 
        capacity: 100MB/s 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=24 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s 
        resources: irq:23 ioport:6800(size=256) memory:c9400400-c94004ff 
   *-network 
        description: Wireless interface 
        product: AR2413 802.11bg NIC 
        vendor: Atheros Communications Inc. 
        physical id: 1 
        bus info: pci@0000:05:01.0 
        logical name: wlan0 
        version: 01 
        serial: 00:c0:a8:d0:fe:18 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=ath5k driverversion=2.6.35-24-generic firmware=N/A ip=192.168.2.4 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg 
        resources: irq:18 memory:60600000-6060ffff 
 

 
[COLOR=#800000]ifconfig[/COLOR]
 

 eth0      Link encap:Ethernet  HWaddr 00:14:0b:0b:7d:b5   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
           Interrupt:23 Base address:0x4400  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B) 
  
 wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:d0:fe:18   
           inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0 
           inet6 addr: fe80::2c0:a8ff:fed0:fe18/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:20182 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:15283 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:12234638 (12.2 MB)  TX bytes:3378573 (3.3 MB) 

[COLOR=#800000]iwconfig[/COLOR]
 

 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 wlan0     IEEE 802.11bg  ESSID:"digitalpunk"   
           Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:3F:E9:E5:CD    
           Bit Rate=54 Mb/s   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off 
           Encryption key:off 
           Power Management:off 
           Link Quality=55/70  Signal level=-55 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
Regarding Gandaran comment - I'm not to sure about drivers and all that , I have always used windows and using aircrack on windows is a piece of cake. Then I got this laptop recently and put ubuntu on it to make it run quicker.
Now when ever I use aircrack it says something about a channel 1 being used by AP or something and I was told this is because I haven't patched my drivers. So I've been searching for answers for two days now. From what I gathered I have an Atheros network card and found out online that by installing madwifi I would be able to use aircrack-ng.
I also have wepcrack gui and it runs fine only problem is when ever I test injection it only gets up to a maximum of 80% and I was told again this is because I haven't patched my drivers.
Been using the aircrack-ng guide for patching however it makes no sense to me.
So I'm hoping to be able to install madwifi

---

### Post by gandaran on 2011-01-02
> Now when ever I use aircrack it says something about a channel 1 being used by AP or something and I was told this is because I haven't patched my drivers. So I've been searching for answers for two days now. From what I gathered I have an Atheros network card and found out online that by installing madwifi I would be able to use aircrack-ng.
I also have wepcrack gui and it runs fine only problem is when ever I test injection it only gets up to a maximum of 80% and I was told again this is because I haven't patched my drivers.
Been using the aircrack-ng guide for patching however it makes no sense to me.
So I'm hoping to be able to install madwifi
I'm thinking of doing the same thing to my netbook:p:p not because or aircrack but ettercap, I cant get anything out of ettercap with the default diver so I will install the madwifi driver one of these days to see if it really works better, if you haven't solved how to install I will let you know then.

---

### Post by fin2010 on 2011-01-02
That would be great :) .
See I'm reading the install document for madwifi but it doesn't make any sense to me.
I just need some step by step instructions on how to build and compile madwifi as it doesn't seem to work with the module-assistant

---

### Post by fin2010 on 2011-01-02
What does ettecap do?

---

### Post by gandaran on 2011-01-02
> **fin2010 said:**
> That would be great :) .
See I'm reading the install document for madwifi but it doesn't make any sense to me.
I just need some step by step instructions on how to build and compile madwifi as it doesn't seem to work with the module-assistant
I found a PPA repository with madwifi but for hardy and lucid only so I don't know if it will work in maverick or even break your system if it's not compatible with the new kernel , if you are up to trying it update the software package list then go to system » administration » additional drivers, maybe the madwifi driver is there if so then you just have to enable it, no need to use module-assistant.
[https://launchpad.net/~dnjl/+archive/kernel](https://launchpad.net/~dnjl/+archive/kernel)

---

### Post by gandaran on 2011-01-02
> **fin2010 said:**
> What does ettecap do?
[http://ettercap.sourceforge.net/index.php](http://ettercap.sourceforge.net/index.php)

---

### Post by perspectoff on 2011-01-02
I haven't needed to install the Madwifi drivers manually for quite some time (for Atheros wireless cards).

Are you sure you haven't gotten some bad advice somewhere along the line?

There are maybe hundreds of threads indicating problems with wireless, but they are not because of the wireless drivers. They are because of Network Manager.

Perhaps you should try the solution of uninstalling Network-Manager and installing Wicd instead and seeing if that clears up your wireless problems, before going the long-distance route of installing Madwifi drivers manually (which in the end may not even help you).

---

### Post by fin2010 on 2011-01-02
Well the only reason I'm trying to get madwifi is because I'm trying to use aircrack-ng .
When I used aircrack before it said "Wlan0  is on *channel 0*, but the AP uses channel X"  something like that anyway. I was told to patch my drivers , that is all I have been trying to do.
As for deleting network manager and installing Wcid I'l try that. Like I say internet and everything works fine It's just aircrack as I believe my network adapter isn't set up to go into monitor mode and use injections

---

### Post by wep940 on 2011-01-03
```
Regarding wep940's comments 
After typing these commands this is what i got-
lspci
 
lsusb
 
lshw -C network
 
ifconfig
 
iwconfig 
 
 
 
p { margin-bottom: 0.21cm; } [COLOR=#800000]Lspci[/COLOR]
 
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge 
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge 
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge 
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge 
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge 
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller 
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device 
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge 
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge 
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80) 
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80) 
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80) 
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) 
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) 
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge 
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller 
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c) 
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge 
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge 
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01) 
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10) 
05:01.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01) 
 
 
 
[COLOR=#800000]lsusb[/COLOR]
 
 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 002: ID 076b:4321 OmniKey AG CardMan 4321 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 
[COLOR=#800000]lshw -C network[/COLOR]
 
 
*-network 
description: Ethernet interface 
product: VT6102 [Rhine-II] 
vendor: VIA Technologies, Inc. 
physical id: 12 
bus info: pci@0000:00:12.0 
logical name: eth0 
version: 7c 
serial: 00:14:0b:0b:7d:b5 
size: 10MB/s 
capacity: 100MB/s 
width: 32 bits 
clock: 33MHz 
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=24 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s 
resources: irq:23 ioport:6800(size=256) memory:c9400400-c94004ff 
*-network 
description: Wireless interface 
product: AR2413 802.11bg NIC 
vendor: Atheros Communications Inc. 
physical id: 1 
bus info: pci@0000:05:01.0 
logical name: wlan0 
version: 01 
serial: 00:c0:a8:d0:fe:18 
width: 32 bits 
clock: 33MHz 
capabilities: pm bus_master cap_list ethernet physical wireless 
configuration: broadcast=yes driver=ath5k driverversion=2.6.35-24-generic firmware=N/A ip=192.168.2.4 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg 
resources: irq:18 memory:60600000-6060ffff 
 
 
 
[COLOR=#800000]ifconfig[/COLOR]
 
 
eth0 Link encap:Ethernet HWaddr 00:14:0b:0b:7d:b5 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
Interrupt:23 Base address:0x4400 
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:720 (720.0 B) TX bytes:720 (720.0 B) 
 
wlan0 Link encap:Ethernet HWaddr 00:c0:a8:d0:fe:18 
inet addr:192.168.2.4 Bcast:192.168.2.255 Mask:255.255.255.0 
inet6 addr: fe80::2c0:a8ff:fed0:fe18/64 Scope:Link 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 
RX packets:20182 errors:0 dropped:0 overruns:0 frame:0 
TX packets:15283 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:12234638 (12.2 MB) TX bytes:3378573 (3.3 MB) 
 
[COLOR=#800000]iwconfig[/COLOR]
 
 
lo no wireless extensions. 
 
eth0 no wireless extensions. 
 
wlan0 IEEE 802.11bg ESSID:"digitalpunk" 
Mode:Managed Frequency:2.437 GHz Access Point: 00:17:3F:E9:E5:CD 
Bit Rate=54 Mb/s Tx-Power=20 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off 
Encryption key:off 
Power Management:off 
Link Quality=55/70 Signal level=-55 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0 
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 
 
Regarding Gandaran comment - I'm not to sure about drivers and all that , I have always used windows and using aircrack on windows is a piece of cake. Then I got this laptop recently and put ubuntu on it to make it run quicker.
Now when ever I use aircrack it says something about a channel 1 being used by AP or something and I was told this is because I haven't patched my drivers. So I've been searching for answers for two days now. From what I gathered I have an Atheros network card and found out online that by installing madwifi I would be able to use aircrack-ng.
I also have wepcrack gui and it runs fine only problem is when ever I test injection it only gets up to a maximum of 80% and I was told again this is because I haven't patched my drivers.
Been using the aircrack-ng guide for patching however it makes no sense to me.
So I'm hoping to be able to install madwifi
```
 
 
So, given the output, we know you have a working connection using the ath5k driver. So your problem lies in trying to use aircrack-ng with your existing connection. Perhaps you would be better served with a title more reflective of the problem - using aircrack-ng with AR2413 802.11bg adapter.
 
If a moderator can't change the title for you, I would suggest closing this thread, starting a new thread with a title reflective of the problem (*IF* the madwifi drivers come into play in that solution, so be it, but they shouldn't be the title - aircrack-ng with ath5k driver is more reflective).
 
You may also want to check into using the ath-pci driver and see if it makes any difference.

---

