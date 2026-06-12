---
title: "help setting up wireless connection"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by gonzal on 2007-07-01
i have ubuntu 7.04 installed in my dell laptop connected to the linksys wireless router through smc wireless card ( when using windows). i can see the list of available network under network manager, so i guess the driver should be properly installed. but i can't connect to the router after inputting the network key. by the way, the security option i have on the router is wep 64 bit hex. any idea how to get it connected? need help!!!!!

---

### Post by gonzal on 2007-07-03
after googling for whole day. i try iwconfig with my network card and it shows as

eth1      IEEE 802.11-DS  ESSID:"surfer"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:6D:27:37   
          Bit Rate:11 Mb/s   
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:****-****-**   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


looks like it is connected to the router but only the connection is not well established. any idea? desperately need help...

---

### Post by lisati on 2007-07-03
[[LIST=1]
[*]Be careful about who you give your network key to
[*]Was your network working before you upgraded?
[/LIST]

---

### Post by gonzal on 2007-07-03
it is the first time i install linux on my laptop. i didn't successfully use the wireless before.

---

### Post by gonzal on 2007-07-06
after another day of searching, i found that because the card i use is smc 2632 V2 card and there is a bug with it. but i have difficulty installing the atmel driver. any suggestion?

---

### Post by kevdog on 2007-07-06
Not sure if I can help you but please list the following -- enter commands at command prompt and cut and paste output:

lspci -nn
lshw -C network

---

### Post by gonzal on 2007-07-06
the following are the output




00:00.0 Host bridge [0600]: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB (Hub #1) [8086:2482] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1420 [104c:ac51]
02:01.1 CardBus bridge [0607]: Texas Instruments PCI1420 [104c:ac51]
07:00.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
07:00.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
07:00.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 04)
wangjiahong@wangjiahong:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:9f:d9:8e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x ip=192.168.1.105 latency=32 maxlatency=10 mingnt=10 multicast=yes
       resources: ioport:ec80-ecff iomemory:f8fffc00-f8fffc7f irq:11
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:04:e2:46:ad:4e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS

---

### Post by kevdog on 2007-07-06
I must be missing something because Im confused!!  This is a pci device correct??

There is no driver associated with eth1 (compare eth0 to eth1) and the device is not showing up on the pci bus scan - lspci.

Did you try installing a driver for the card, and if so by what method?

---

### Post by kevdog on 2007-07-06
Could you post the exact version/model number of the card if you have it.  Here is what I was able to find on the ubuntu wiki:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsSmc](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsSmc)

---

### Post by t4thfavor on 2007-07-06
If you are using wep or wpa you may have to issue these commands on the command line

sudo iwconfig ethX key open
sudo iwconfig ethX key "your key"

I believe security mode restricted means your using external authentication.

---

### Post by gonzal on 2007-07-06
the card i'm using is smc 2632w version 2, which has a bug. the bug description from ubuntu is 



Bug description [edit]

I had to create a .conf file in /etc/pcmcia/ to let my SMC 2632W-V2 be detected.
It uses the atmel_cs driver and works fine with it:

device "atmel_cs"
  class "network" module "atmel_cs"

card "SMC 2632W-V2"
  manfid 0x01bf, 0xb301
  bind "atmel_cs"


but i have problem installing the atmel_cs driver for it.

---

### Post by kevdog on 2007-07-06
Thanks for the info, thats good detective work on your part.  From what you have read, does the driver need to work with ndiswrapper, or is it a native linux driver.  ndiswrapper drivers are windows type.

---

### Post by gonzal on 2007-07-07
the atmel driver is open source driver and i have to compile it myself but i have difficulty compiling it. i also have official driver from smc. also have problem using ndiswrapper to install it.

---

### Post by kevdog on 2007-07-07
You are going to have to explain "difficulty".  

As far as compiling things, you will need the build-essential package installed.

Just quick tutorial, if you have a wired connection skip to step#4.  All commands typed at command prompt
1. Stick ubuntu installation cd in drive, wait to become ready
2. sudo apt-cdrom add
3. sudo aptitude update
4. sudo aptitude install build-essential

That probably will help you.  To compile its usually
cd to source directory
./configure <---may not need this step if configure file is not present
make <--- This command does the compiling
sudo make install <----- Installs executables.

If you knew all of this before, sorry.

---

### Post by gonzal on 2007-07-07
here are what i got 

output for ./configure

./configure: No such file or directory

the make output

Building pcmf504A_2958
Bootstraping target pcmf504A_2958
-e      Debug
[: 10: ==: unexpected operator
[: 10: ==: unexpected operator
-e      Release
[: 10: ==: unexpected operator
[: 10: ==: unexpected operator


by the way, the source code is from [http://downloads.sourceforge.net/atmelwlandriver/atmelwlandriver-3.4.1.1.tar.bz2?modtime=1122029770&big_mirror=0](http://downloads.sourceforge.net/atmelwlandriver/atmelwlandriver-3.4.1.1.tar.bz2?modtime=1122029770&big_mirror=0)

---

### Post by kevdog on 2007-07-07
Is there a README or INSTALL file contained in the download? A lot of times this gives pointers.

---

