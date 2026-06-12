---
title: "HP Pavilion dv6000"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by René Haas on 2008-07-01
Hi.

I am an absolute beginner to Ubuntu and to this forum, and i am not especially skilled in computers in general.
Just installed from the live cd today.
My problem is that i cannot get my wireless lan to work.
My laptop is a HP pavilion dv6000.
Hope somebody can help, or point me in the right direction
/René

---

### Post by lisati on 2008-07-01
There are a couple of things we can check. Go to the terminal (It's on the "Applications"-->"Accessories" menu) and type in the following, and let us know the results:
```
iwconfig
```
```
iwlist scan
```
These may help us start guiding you through setting things up.

---

### Post by René Haas on 2008-07-01
Hey again. 

Thanks for the quick answer. Sure an active community inhere.
Here's the results:
 
rene@rene-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rene@rene-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

rene@rene-laptop:~$ 

Doesn't sound too promising. or?

/rené

---

### Post by Ayuthia on 2008-07-01
Can you post the results of this from the terminal:
```
lspci -nn
```
This will give us the list of your PCI cards and this will help us figure out what wireless card you have.

---

### Post by René Haas on 2008-07-02
rene@rene-laptop:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP65 Memory Controller [10de:0444] (rev a3)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP65 LPC Bridge [10de:0442] (rev a3)
00:01.1 SMBus [0c05]: nVidia Corporation MCP65 SMBus [10de:0446] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP65 SMU [10de:0447] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP65 USB Controller [10de:0454] (rev a3)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP65 USB Controller [10de:0455] (rev a3)
00:06.0 Ethernet controller [0200]: nVidia Corporation MCP65 Ethernet [10de:0450] (rev a3)
00:07.0 Audio device [0403]: nVidia Corporation MCP65 High Definition Audio [10de:044a] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI bridge [10de:0449] (rev a1)
00:09.0 IDE interface [0101]: nVidia Corporation MCP65 IDE [10de:0448] (rev a1)
00:0a.0 IDE interface [0101]: nVidia Corporation MCP65 SATA Controller [10de:045d] (rev a3)
00:0b.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:045b] (rev a1)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:045a] (rev a1)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:0458] (rev a1)
00:0e.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:0459] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
05:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
rene@rene-laptop:~$

---

### Post by Ayuthia on 2008-07-02
> **René Haas said:**
> 
03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)

This is your wireless card.  The Linux Broadcom Driver (b43) does not support the wireless-n cards yet so you will need to use NDISwrapper.

Here is a link that might help:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by mmelville3 on 2008-07-02
I have an HP Pavilion ze2000 with Broadcom wireless card. I was having trouble getting my wireless card to work. Last night I upgraded to Ubuntu 7.10 (Gutsy Gibbon) and when I rebooted I was prompted at the desktop to install the driver. After another reboot it worked. The wireless blue light came on and everything.

type this at the command prompt to find what version of Ubuntu you are currently running: lsb_version

What version are you running?

---

### Post by René Haas on 2008-07-02
Hey again.

Ayuthia > The link didn't provide much help - simply can't find out what to do?

mmelville3 > Where do i find the command prompt ?

---

### Post by mmelville3 on 2008-07-02
I don't know exactly off hand. I'm sure it's under applications somewhere... I think its called Terminal. not command prompt.

---

### Post by René Haas on 2008-07-02
mmelville3
Then i type it in terminal: 
rene@rene-laptop:~$ lsb_version
bash: lsb_version: command not found
rene@rene-laptop:~$ 
Whats wrong?

Ayuthia
Okay decided to give the link another go.
Just got frigthened by the technical apperence of the site.

Step 1

rene@rene-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
[sudo] password for rene: 
blacklist bcm43xx
rene@rene-laptop:~$ sudo apt-get install ndiswrapper-utils-1.9
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
Foreslåede pakker:
  ndiswrapper-source
Følgende NYE pakker vil blive installeret:
  ndiswrapper-utils-1.9
0 opgraderes, 1 nyinstalleres, 0 afinstalleres og 0 opgraderes ikke.
19,0kB skal hentes fra arkiverne.
After this operation, 119kB of additional disk space will be used.
Henter:1 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy/main ndiswrapper-utils-1.9 1.50-1ubuntu1 [19,0kB]
Hentede 19,0kB på 0s (33,3kB/s)         
Vælger tidligere fravalgt pakke ndiswrapper-utils-1.9.
(Læser database... 115528 filer og mapper aktuelt installeret.)
Udpakker ndiswrapper-utils-1.9 (fra .../ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb)...
Sætter ndiswrapper-utils-1.9 (1.50-1ubuntu1) op...
rene@rene-laptop:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
rene@rene-laptop:~/bcm43xx$ 

step 2

rene@rene-laptop:~$ lspci -n | grep '14e4:43'
03:00.0 0280: 14e4:4328 (rev 03)
rene@rene-laptop:~$ 

Which means that i should now make step 2d Right?

step 2d

rene@rene-laptop:~$ wget [http://myspamb8.googlepages.com/R151517-pruned.zip](http://myspamb8.googlepages.com/R151517-pruned.zip)
--17:56:16--  [http://myspamb8.googlepages.com/R151517-pruned.zip](http://myspamb8.googlepages.com/R151517-pruned.zip)
           => `R151517-pruned.zip.1'
Løser myspamb8.googlepages.com... 209.85.173.118
Connecting to myspamb8.googlepages.com|209.85.173.118|:80... forbundet.
HTTP forespørgsel sendt, afventer svar... 200 OK
Længde: 730.544 (713K) [application/octet-stream]

100%[====================================>] 730.544      208.92K/s    ETA 00:00

17:56:20 (208.30 KB/s) - `R151517-pruned.zip.1' saved [730544/730544]

rene@rene-laptop:~$ unzip R174291-pruned.zip
unzip:  cannot find or open R174291-pruned.zip, R174291-pruned.zip.zip or R174291-pruned.zip.ZIP.
rene@rene-laptop:~$ 

Step 3
-- Okay made some errors here, but i hope it makes sence anyway

rene@rene-laptop:~$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
rene@rene-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4328) present
rene@rene-laptop:~$ sudo depmod -a
rene@rene-laptop:~$ sudo modprobe ndiswrapper
rene@rene-laptop:~$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
rene@rene-laptop:~$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

rene@rene-laptop:~$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

rene@rene-laptop:~$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
rene@rene-laptop:~$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
ENABLED=0
rene@rene-laptop:~$ 

Last step

rene@rene-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1b:24:ec:fc:e8
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.16 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
rene@rene-laptop:~$ 

Okay. As i understand it the last line (configuration: should either say: "module=ssb" or "module=ndiswrapper" but is says latency=0

What has gone wrong.

I hope this long post make any sence at all, i am, as before mentioned very new to this stuff. And thansk to all who takes time to help me.

/René

---

### Post by mmelville3 on 2008-07-02
sorry! it's lsb_release

---

### Post by mmelville3 on 2008-07-02
or try this: lsb_release -a

---

### Post by René Haas on 2008-07-02
rene@rene-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy
rene@rene-laptop:~$

---

### Post by mmelville3 on 2008-07-02
I'm only guessing now but look for something called restricted drivers under system > Adminstration.

Also, yesterday I found this article that more closely matches your situation:

[http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/)

---

### Post by René Haas on 2008-07-02
mmelville3 
After lot of frustration, and endless typing into the terminal my wireless network is now working. 
Phew. I don't hope that using Ubuntu will remain to be this difficult.
But thanks a million for helping me out.

---

### Post by mmelville3 on 2008-07-02
I have found it a struggle to get a few things working in Ubuntu. With Ubuntu you have to be willing to learn about the system as you go.

---

