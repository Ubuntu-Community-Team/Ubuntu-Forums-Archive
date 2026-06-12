---
title: "Troubleshooting Wireless"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by Isthan on 2007-07-06
To introduce myself, I'm a fairly new Linux user but I do understand how to use the command line.  I am troubleshooting the wireless connection on my Compaq V5000 laptop.  I am using Kubuntu Fiesty 7 x64.  I had the fear that this wireless card would have issues with Linux because to even use the card in Windows XP I have to use proprietary HP software (Wireless Assistant) to make it work effectively.  Essentially my touch key for the wireless card wouldnt work without that software.

In Linux I go into my Network Settings and see my wired Ethernet port as being enabled.  The Wireless card shows up as Eth1.  When I try to enable Eth1, it enables and disables instantly.  I do no see any LED light appear on the laptop that would normally in Windows.

lspci output =
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

lshw -C network output =
lshw -C network
  *-network:0 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@06:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:a5:21:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:b0204000-b0205fff irq:21
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:0a:ea:52
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.55 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resourcesI : ioport:a000-a0ff iomemory:b020a400-b020a4ff irq:22


I've read about ndiswrapper and my device is in the list of known supported devices.  But I thought that i'd see if there was a simpler solution before I had to learn how to compile and install programs from command line.
If anyone has any advice that could help, please share!
If the info I provided is not conclusive enough, please let me know and i'll follow whatever steps to share that information.

---

### Post by kevdog on 2007-07-06
I noticed you were running the 64 bit version of Kubuntu.  Do you have a 64 bit version driver for the card?? Thats probably the solution right there.

If someone could confirm, but the driver associated with the card right now is the bcm43xx driver.  I not aware of the bcm43xx-cutter driver supporting 64 bit??? It might possibly, but you would have to check on this.

If you have a 64 bit windows driver then you are going to have to use ndiswrapper.  If there is a bcm43xx 64 bit driver then this would be the easiest.  May have to search the forum or google for this.  If you cant find either then you will have to reinstall the 32 bit version of Kubuntu.

---

### Post by Isthan on 2007-07-06
Oh wow thats an excellent point. I dont have a 64bit driver.  Compaq wasn't kind enough to even offer me a 64-bit vista driver.  I've got a "Vista Capable" sticker on my laptop...not likely without drivers.  Best to re-install the 32-bit Kubuntu?

---

### Post by Ayuthia on 2007-07-06
bcm43xx-fwcutter does exist for 64-bit.  It is actually in the Restricted Drivers Manager in Gutsy.

---

### Post by ksieg on 2007-07-06
I'm on an HP Pavilion dv8040us and seem to have the same card.  

Where do I find and how do I install the 64bit driver?

---

### Post by Isthan on 2007-07-06
Alright, well i've installed the 32 bit version of Kubuntu because I have the 32 bit driver on hand.  All the same i'm not having good luck with ndiswrapper.  When I launch it it just seems to fizzle and does nothing.  It seems my problem remains that I dont have drivers installed for the wireless.  Anyone able to help with the ndiswrapper side of it?

---

### Post by kevdog on 2007-07-07
Despite what anyone tells you the 32 bit version is much more tested than the 64 bit.  I cant speak to Gusty -- probably a lot of things will change with the new release.

Ok as far as ndiswrapper.
Its best to compile and install from source.  If you have used Synaptic, apt,aptitude,automatix or any other method up to this point to install ndiswrapper, please reverse the process to uninstall.  If you somehow managed to install from source, jump to the end of this post to see if ndiswrapper was installed correctly.

Here is my mini how to:

Setup for compiling source files.  If you have an internet wired connection goto step#4. (Note all commands typed at command prompt)
1. Stick ubuntu installation cd into computer, wait to become ready
2. sudo apt-cdrom add
3. sudo aptitude update
4. sudo aptitude install build-essential

Setup for ndiswrapper compilation, installation
mkdir ~/ndiswrapper
Download ndiswrapper-1.47.tar.gz from:[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482) and place into ~/ndiswrapper directory
cd ~/ndiswrapper
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make 
sudo make install

Check if installation was down properly:
ndiswrapper -v

Please post output of above.  If everything goes as planned, we will work with windows drivers next

---

### Post by Isthan on 2007-07-07
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-15-generic SMP mod_unload 586

Thanks so much for your help so far!

I'm ready to begin with the windows drivers.

---

### Post by Isthan on 2007-07-09
I'm having trouble tracking down the right drivers for my wireless device.  I downloaded a driver that matched the exact description of my lspci output and when I loaded it and did ndiswrapper -l in the terminal it said driver invalid...Any help on this driver situation?

---

### Post by kevdog on 2007-07-09
Could you post the following
lspci
lspci -n

Also where did you get the driver you tried?

---

### Post by Isthan on 2007-07-09
The driver is from ndiswrapper.sourceforge.net's listing for a Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) device.

"
Card: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
 Chipset Name: BCM94318MPG
 PC: Emachines W4630 (Amd Turion 64)
PCIID: 03:09.0 0280: 14e4:4318 (rev 02)
ndiswrapper version: 1.47
OS: Ubuntu 7.04 - Linux 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux
driver: BCMWL564.SYS
driver url: [ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip)
"

It says an Emachines W4630 but the (Amd Turion 64) is the same about my compaq.

Here is my lspci

"00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
"

Here is my lspci -n

"
00:00.0 0600: 1002:5950 (rev 01)
00:01.0 0604: 1002:5a3f
00:05.0 0604: 1002:5a37
00:13.0 0c03: 1002:4374
00:13.1 0c03: 1002:4375
00:13.2 0c03: 1002:4373
00:14.0 0c05: 1002:4372 (rev 11)
00:14.1 0101: 1002:4376
00:14.3 0601: 1002:4377
00:14.4 0604: 1002:4371
00:14.5 0401: 1002:4370 (rev 02)
00:14.6 0703: 1002:4378 (rev 02)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:05.0 0300: 1002:5955
06:02.0 0280: 14e4:4318 (rev 02)
06:04.0 0607: 104c:8031
06:04.2 0c00: 104c:8032
06:04.3 0180: 104c:8033
06:04.4 0805: 104c:8034
06:06.0 0200: 10ec:8139 (rev 10)
"

Thanks for your help!

---

### Post by kevdog on 2007-07-09
You selected a 64bit driver -- which although you have a 64 bit processor, you have a 32 bit operating system.

Im not sure what the right selection for your driver is but lets try this one:
[ftp://ftp.hp.com/pub/softpaq/sp30001-30500/SP30379.exe](ftp://ftp.hp.com/pub/softpaq/sp30001-30500/SP30379.exe)

I dont know if the exe file is a self extracting zip file, or a cabinet file.  If you have a windows machine handy, see if you can extract the drivers to a USB drive and then bring the extracted drivers over to linux.

---

### Post by Isthan on 2007-07-09
I have a driver that is also one of those "soft packs" from compaq's website.  The driver that I have currently working for my windows XP partition Wireless (on the same laptop) differs from the one you found.  I suppose I could try the one you found first, but i'm not exactly clear on what you mean by extracting from the exe file.  I wasnt aware you could do that.

---

### Post by kevdog on 2007-07-09
Use your XP driver first -- I thought you didnt have a disk.  You dont have 64bit WinXP do you?

---

### Post by Carleton91 on 2007-07-09
A piece of advice that could save you some hair pulling and teeth grinding is making sure that you are in the directory of the driver files you are trying to install when you do ndiswrapper -i.  For instance, if your driver files are on the desktop do cd Desktop before trying to install.  That alone took me like 5 hours to figure out :(

---

### Post by Isthan on 2007-07-09
What I have is the same type of downloaded driver pack like you found.  My laptop didnt come with any disks for drivers and came with XP home. I reinstalled with XP professional 32-bit and the drivers i'm using currently I downloaded from the compaq support site.  My question still remains how to get the inf and sys files from that SP######.exe soft pack.

---

### Post by kevdog on 2007-07-09
I you have windows then I would run the exe file.  If you do not then try to open the file with arK.  If the file will not open with arK then you are going to have to install cabextract.

I dont think you have an internet connection.  Grab the deb file for cabextract here: [http://packages.debian.org/stable/utils/cabextract](http://packages.debian.org/stable/utils/cabextract)

To install you are going to have to do the following, type commands at command prompt:
1. Stick ubuntu installation cd in drive and then wait to become ready
2. sudo apt-cdrom add
3. sudo aptitude update
4. sudo aptitude install build essential

Then change into directory where cabextract.deb file is located
sudo dpkg -i *****.deb  <---substitute file name here

Then change into directory were .exe is located.
cabextract ****.exe <---substitue exe file here

Then you are going to have to weed through the extracted package and find the xp .sys and .inf files.

---

### Post by Isthan on 2007-07-09
Okay, I installed cabextract and successfully retrieved the .inf file from the .exe softpack.  I got the following message as I installed .inf driver.


installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2

my ndiswrapper -l output is:
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)

Alright, driver is installed, now what is left to configuring my wireless device to run?

---

### Post by kevdog on 2007-07-09
Great job -- I guess you are no linux newbie anymore.  I hope those messages dont mean anything.  We will find out.


Ok lets load the module
sudo depmod -a <---Make sure you dont get any errors -- if you do stop and post them
sudo modprobe -i ndiswrapper 

Check if no errors loading the installation:
dmesg | grep ndiswrapper

If you see anything about an error or something doesnt look right, stop and post the message

Load module at boot
sudo ndiswrapper -m
sudo echo "ndiswrapper" | tee -a /etc/modules

Blacklist bcm43xx module
sudo echo "blacklist bcm43xx" | tee -a /etc/modprobe.d/blacklist

Reboot.

Ok everything might work now, but it may not.  If it doesnt work then post the following
/etc/network/interfaces
/etc/iftab
lshw -C network
iwlist scan

---

### Post by kevdog on 2007-07-09
Great job -- I guess you are no linux newbie anymore.  I hope those messages dont mean anything.  We will find out.


Ok lets load the module
sudo depmod -a <---Make sure you dont get any errors -- if you do stop and post them
sudo modprobe -i ndiswrapper 

Check if no errors loading the installation:
dmesg | grep ndiswrapper

If you see anything about an error or something doesnt look right, stop and post the message

Load module at boot
sudo ndiswrapper -m
sudo echo "ndiswrapper" | tee -a /etc/modules

Blacklist bcm43xx module
sudo echo "blacklist bcm43xx" | tee -a /etc/modprobe.d/blacklist

Reboot.

Ok everything might work now, but it may not.  If it doesnt work then post the following
/etc/network/interfaces
/etc/iftab
lshw -C network
iwlist scan

---

### Post by Isthan on 2007-07-09
/etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

/etc/iftab
eth0 mac 00:16:d4:0a:ea:52 arp 1
eth1 mac 00:14:a5:a5:21:da arp 1

lshw -C network
*-network:0 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@06:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:a5:21:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:b0204000-b0205fff irq:22
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:0a:ea:52
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.107 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:b020a400-b020a4ff irq:20

iwlist scan:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results


I suppose you can tell by this point that the reboot didnt resolve it, so here is the information you requested.

---

### Post by kevdog on 2007-07-10
two  problems that I can pick off right now

1. > configuration: broadcast=yes [COLOR="Red"]driver=bcm43xx[/COLOR] driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g

You need to blacklist the bcm43xx driver:
> gksu gedit /etc/modprobe.d/blacklist

Make sure there is a line with
```
blacklist bcm43xx driver present
```

2. /etc/iftab
> eth1 mac 00:14:a5:a5:21:da arp 1

This needs to be:
```
wlan0 mac 00:14:a5:a5:21:da arp 1
```

---

### Post by Isthan on 2007-07-10
Okay! 

I made the changes and when I rebooted I saw that trusty wireless light turn on!  So I know my device has functional drivers but now i'm still trying to get connected to the internet.  I know my SSID and encryption key, but even when I enter it in KWiFiManager it cant seem to find my access point.  Any ideas?

---

### Post by kevdog on 2007-07-10
Point of clarification
within /etc/modprobe.d/blacklist  line should read
blacklist bcm43xx


OK onto the next

Can you post the following:
lshw -C network
iwlist scan
dmesg (may need to include this as an attachment -- or only include relevant sections relating to either ndiswrapper or wlan0).

---

### Post by Isthan on 2007-07-10
lshw -C network:
*-network:0
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@06:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:a5:21:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.47+Broadcom,04/21/2005, 3.100. ip=192.168.1.155 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:b0204000-b0205fff irq:22
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:0a:ea:52
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.107 latency=128 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:a000-a0ff iomemory:b020a400-b020a4ff irq:21

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

dmesg |grep wlan0
[   23.504000] wlan0: ethernet device 00:14:a5:a5:21:da using NDIS driver: bcmwl5, version: 0x3644101, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[   23.504000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   23.872000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  176.200000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1141.464000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1312.744000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1351.552000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

dmesg |grep ndiswrapper
[   22.992000] ndiswrapper version 1.47 loaded (smp=yes)
[   23.116000] ndiswrapper: driver bcmwl5 (Broadcom,04/21/2005, 3.100.65.1) loaded
[   23.124000] ndiswrapper: using IRQ 22
[   23.504000] usbcore: registered new interface driver ndiswrapper
[  176.204000] ndiswrapper (add_wep_key:798): adding encryption key 1 failed (C0010015)

i'm sure a few lines in there are telling, but if you can see what the problem is from that info i'd appreciate it.

---

### Post by kevdog on 2007-07-10
Turn off WEP on the router for right now.  I think it may be causing problems.

Do 
sudo /etc/init.d/dbus restart

iwlist scan
Include entire dmesg as an attachment!

---

### Post by Isthan on 2007-07-10
Well I've got the wireless working, believe it or not!

The issue I was having with my WEP was that I had "ASCII" selected instead of "Hexedecimal" which my WEP key is a 64-bit hex key.  It didnt dawn on me until I took a good hard look at that network configuration.  Thanks for all of your help, I greatly appreciate it!  You made a friend out here in Nebraska!  Hope you're getting paid for your expertise in troubleshooting!

---

### Post by kevdog on 2007-07-10
Hey maybe you can help me --- Where do I pick up my Check?????  I really could use the extra cash! :)

---

### Post by Isthan on 2007-07-10
Check's in the mail!

---

