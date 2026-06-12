---
title: "HP Pavalion DV6701us using BroadCom BCM4310 USB Wireless Hacked!"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by SirLawrence on 2008-05-08
HP Pavalion DV6701us using BroadCom BCM4310 USB for Wireless Hacked!  I is Hardy Wireless!  First of all I'm a complete noob to linux so perhaps someone more knowledgable than I can do a better write up of the hack. 

**PreSetup 0:**
===========
I had to do on online chat with HP to get the windows xp drivers for the interal wireless broadcom chips.  The DV6701us laptop I bought came with  Vista pre-installed, the ftp site is:  

[[COLOR="RoyalBlue"]ftp://ftp.hp.com/pub/softpaq/sp36501-37000/sp36684.exe[/COLOR]]("ftp://ftp.hp.com/pub/softpaq/sp36501-37000/sp36684.exe")

I did a cabextract on sp36684.exe to get the bcmwl5.inf driver.

**Step 0:**
=======
alex_kent_18 has a good step by step on how to setup up ndiswrapper with your *.inf driver file
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=766560[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560")

This link also has the same info that Alex has, except Alex has a wirelessfix.sh script file that runs on boot.  However this thread at the end shows how to remove ndiswrapper and compile a new version which I ended up doing.
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851")

[COLOR="Purple"]I followed alex_kent_18's steps exactly and I also compiled and installed the latest ndiswrapper version 1.52.

Arrrgh! My wireless was still not working:
"ndiswrapper -l" showed "bcmwl5 : driver installed" but no device present
"lshw -C network" showed my ethernet ok but my wireless device as UNCLAIMED.
"ifconfig" showed eth0, and local loopback (lo), but no wlan0![/COLOR]

**Step 1: **
=======
[COLOR="Blue"]lspci -nn | grep Broadcom[/COLOR]

02:00.0 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [COLOR="Red"][14e4:4315] [/COLOR](rev 01)


**Step 2 (THE HACK):**
==================
firstly create a link to a similar driver:
[COLOR="Blue"]cd /etc/ndiswrapper/bcmwl5
sudo  ln  -s   14E4:4311:1363:103C.5.conf   14E4:4315.5.conf[/COLOR]

If you list this directory where ndiswrapper installs your *.inf driver, you'll find a list of *.conf files and links to those files.  In my case there was a link 14E4:4311.5.conf that also points to a 14E4:4311:1363:103C.5.conf driver(?).   I chose to link my BCM4310 device to the file pointed to by the link  14E4:4311.5.conf based on the assumption that what's good for BCM4311 Broadcom chips will be good for BCM4310.  I used 4315 instead of 4310 because that is how the device is addressed(?)/recognized(?) on the bus (see the [COLOR="Red"][xxxx : xxxx][/COLOR] from Step 1)

next make sure b44 and sbb are not loaded and reload ndiswrapper:
[COLOR="Blue"]sudo modprobe -r b44
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo depmod -a
sudo modprobe ndiswrapper[/COLOR]

I immediatley had a good feeling after this because '[COLOR="Blue"]ndiswrapper -l[/COLOR]' showed:

bcmwl5 : driver installed
	device (14E4:4315) present

where previously it did not show the device as present.

**Step 3: **
=======
I added the following as blacklisted modules to the [COLOR="Blue"]/etc/modprob.d/blacklist[/COLOR] file to make sure there is no conflict with any other drivers.  I'm still not sure if this step is necessary but I show it anyway.

[COLOR="Blue"]blacklist b43
blacklist b44
blacklist ssb[/COLOR]

**Step 4:**
=======
reboot and wireless device shows up as a connection option in the panel!


**Step 5:**
=======
Register and post my fix on ubuntu forums, i is a leet haxxor :) ... but seriously, Thanks to those before me that posted their fixes!




==============================
**Final FYI for those that care:**
==============================
Here's what modules are loaded while I'm wirelessly connected,
notice that b43, b44, bcm43xx and ssb do not show as loaded!:
================================================================
[COLOR="Blue"]lsmod | grep -i -e b44 -e b43 -e bcm43xx -e ssb -e ndiswrapper[/COLOR]
ndiswrapper           193564  0 
usbcore               146028  5 ndiswrapper,uvcvideo,ehci_hcd,uhci_hcd

Here's my network now looks like:
=================================
[COLOR="Blue"]lshw -C network[/COLOR]
  *-network               
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:1a:73:f1:67:ac
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,07/11/2007, 4.150. ip=192.168.1.103 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:20:16:2e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes


Here's what '[COLOR="Blue"]ifconfig[/COLOR]' shows:
=============================
eth0      Link encap:Ethernet  HWaddr 00:1e:68:20:16:2e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1752 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87600 (85.5 KB)  TX bytes:87600 (85.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:f1:67:ac  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fef1:67ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6541 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6469237 (6.1 MB)  TX bytes:892516 (871.5 KB)
          Interrupt:17 Memory:f4000000-f4004000 

Here's my network businfo for my hardware:
=========================================
[COLOR="Blue"]lshw -businfo | grep network[/COLOR]
pci@0000:02:00.0  wlan0   network     BCM4310 USB Controller
pci@0000:06:00.0  eth0    network     RTL8101E PCI Express Fast Ethernet controller



HERE IS A COMPLETE LISTING OF MY HARDWARE:
===============================================================
[COLOR="Blue"]sudo lshw -businfo[/COLOR]

Bus info          Device      Class       Description
=====================================================
                              system      HP Pavilion dv6700 Notebook PC
                              bus         30CC
                              memory      100KiB BIOS
cpu@0                         processor   Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz
                              memory      64KiB L1 cache
                              memory      1MiB L2 cache
                              processor   Logical CPU
                              processor   Logical CPU
                              memory      2GiB System Memory
                              memory      1GiB DIMM Synchronous 533 MHz (1.9 ns)
                              memory      1GiB DIMM Synchronous 533 MHz (1.9 ns)
cpu@1                         processor   
                              processor   Logical CPU
                              processor   Logical CPU
pci@0000:00:00.0              bridge      Mobile PM965/GM965/GL960 Memory Controller Hub
pci@0000:00:02.0              display     Mobile GM965/GL960 Integrated Graphics Controller
pci@0000:00:02.1              display     Mobile GM965/GL960 Integrated Graphics Controller
pci@0000:00:1a.0              bus         82801H (ICH8 Family) USB UHCI Controller #4
pci@0000:00:1a.1              bus         82801H (ICH8 Family) USB UHCI Controller #5
pci@0000:00:1a.7              bus         82801H (ICH8 Family) USB2 EHCI Controller #2
pci@0000:00:1b.0              multimedia  82801H (ICH8 Family) HD Audio Controller
pci@0000:00:1c.0              bridge      82801H (ICH8 Family) PCI Express Port 1
pci@0000:02:00.0  wlan0       network     BCM4310 USB Controller
pci@0000:00:1c.1              bridge      82801H (ICH8 Family) PCI Express Port 2
pci@0000:00:1c.5              bridge      82801H (ICH8 Family) PCI Express Port 6
pci@0000:06:00.0  eth0        network     RTL8101E PCI Express Fast Ethernet controller
pci@0000:00:1d.0              bus         82801H (ICH8 Family) USB UHCI Controller #1
pci@0000:00:1d.1              bus         82801H (ICH8 Family) USB UHCI Controller #2
pci@0000:00:1d.2              bus         82801H (ICH8 Family) USB UHCI Controller #3
pci@0000:00:1d.7              bus         82801H (ICH8 Family) USB2 EHCI Controller #1
pci@0000:00:1e.0              bridge      82801 Mobile PCI Bridge
pci@0000:07:09.0              bus         R5C832 IEEE 1394 Controller
pci@0000:07:09.1              system      R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
pci@0000:07:09.2              system      R5C592 Memory Stick Bus Host Adapter
pci@0000:07:09.3              system      xD-Picture Card Controller
pci@0000:07:09.4              generic     Illegal Vendor ID
pci@0000:00:1f.0              bridge      82801HEM (ICH8M) LPC Interface Controller
pci@0000:00:1f.1  scsi3       storage     82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
scsi@3:0.0.0      /dev/cdrom  disk        DVDRAM GSA-T20N
                  /dev/cdrom  disk        
pci@0000:00:1f.2  scsi0       storage     82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
scsi@0:0.0.0      /dev/sda    disk        160GB WDC WD1600BEVS-6
scsi@0:0.0.0,1    /dev/sda1   volume      80GiB Windows NTFS volume
scsi@0:0.0.0,2    /dev/sda2   volume      3386MiB Windows NTFS volume
scsi@0:0.0.0,3    /dev/sda3   volume      65GiB Extended partition
                  /dev/sda5   volume      62GiB Linux filesystem partition
                  /dev/sda6   volume      2761MiB Linux swap / Solaris partition
pci@0000:00:1f.3              bus         82801H (ICH8 Family) SMBus Controller

---

### Post by thejem on 2008-05-23
Thanks guys and gals. Finally got my HP dv6701 working wirelessly.

---

### Post by alroger on 2008-05-29
Thank you SirLawrence!
I did need all the blacklists. I suppose that if your linux detects and loads b43, you do need to black list it with ssb in order to use ndiswrapper.
In my case (Dell Latitude 131L) the ssb black list only works if b44 is blacklisted also, that's the regular ethernet card, and b44 calls for ssb.
So no cable LAN with the fix above, but that's ok for me.

In another case (Dell Vostro 1000) I didn't need to blacklist anything, since b43 was not automatically loaded.... and the cable LAN (b44+ssb) still works fine.

PS: I did not need any symbolic links as in step 2.

---

### Post by yoursdhansh on 2008-05-31
Thanks  a ton!
I got my wireless  worked finally after several attempts of the steps above.

I am not pretty sure which method worked :(

I used similar kind of steps several times and finally my wireless light lits up!!

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

last step
[http://nohair.com/code/computers:ubuntu:hp_pavilion_dv2718us](http://nohair.com/code/computers:ubuntu:hp_pavilion_dv2718us)

I did a re-install of network manager in application -> add/remove and search for network manager

---

### Post by thejem on 2008-06-12
I did get my wireless working however I have no wep or wpa security only open connections

---

### Post by Ayuthia on 2008-06-12
> **thejem said:**
> I did get my wireless working however I have no wep or wpa security only open connectionsIf you are using kernel 2.6.24-18 or higher, it looks like there is a native driver just for your card.  You should be able to enable it by using linux-restricted-modules-`uname-r`-generic.  After you install it, you should be able to test it out by doing the following:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe wl
sudo ifconfig wlan0 up
```

I have not seen anyone try it out yet, but I did see the announcement of this driver come from Broadcom.

---

### Post by daugusto_go on 2008-07-22
I also have HP Pavalion DV6701us using BroadCom BCM4310 USB for Wireless since May 2008. I configured my wireless connection as suggested here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc)

and it was working very well.

But last week (July 17, 2008) I updated my kernel, wich now is 2.6.24-19-386 i686 (on Ubuntu Hardy Heron), and now I'm having problems with my wireless device. I've tried lot of issues found on web (I'm a begginer :confused:) but my connection is still bad. Sometimes it connects but just after lot of tries on Network Manager. When connected, everything goes well.

I'd like to get connected faster. Do you have a clue about what I can do to improve it?

---

### Post by smalldog on 2008-07-22
I have just purchase a Dell laptop which installed with a BCM4310 USB wireless card. 

Check it by : **lspci -nn | grep Broadcom**
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)

The wireless card work well under the bundle vista OS. However, after I have install the Ubuntu 8.04, the wireless card seem go beyond my control. But it is because I have chosen a wrong way due my router is configured using WPA to encryption. 

The native driver "wl" loaded by OS is working under non-encrypted condition by using NetworkManager. 

Check it by : **lsmod | grep wl**
wl                   1062164  0 
ieee80211_crypt         7040  2 wl,ieee80211_crypt_tkip

However, the native driver does not total supported by the developer, you can found it on "http://www.devicescape.com/docs/uwp/package_guide/pkg_broadcom-wl.php" [http://www.devicescape.com/docs/uwp/package_guide/pkg_broadcom-wl.php]("http://www.devicescape.com/docs/uwp/package_guide/pkg_broadcom-wl.php") it cannot working under any encryption condition. I had try many time to using different method encryption but with no joy. wpa_supplicant report that such driver is  unsupported.

In addition, sometimes the network connection seems cannot build. Even though, I have using NetworkManager to disconnect & connect several times manually. Finally, I discover, the connection problem can easily solve by stop & start the NetworkManager such as:
[B]  /etc/dbus-1/event.d/25NetworkManager stop
  /etc/dbus-1/event.d/25NetworkManager start[/B]

I also have tried using ndiswrapper with the vista bundled driver bcmwl6 but it also failed.

I will try using ndiswrapper with bcmwl5 and remove wl to test encrypted communication. Wait for my result. Thanks

---

### Post by SirLawrence on 2008-09-05
> **daugusto_go said:**
> I also have HP Pavalion DV6701us using BroadCom BCM4310 USB for Wireless since May 2008. I configured my wireless connection as suggested here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc)

and it was working very well.

But last week (July 17, 2008) I updated my kernel, wich now is 2.6.24-19-386 i686 (on Ubuntu Hardy Heron), and now I'm having problems with my wireless device. I've tried lot of issues found on web (I'm a begginer :confused:) but my connection is still bad. Sometimes it connects but just after lot of tries on Network Manager. When connected, everything goes well.

I'd like to get connected faster. Do you have a clue about what I can do to improve it?


Well.  I'm not exactly sure what's going on with your intermitency.  I also updated my kernal but from 2.6.24-16 to 2.6.24.19, somewhere along the way, the OS got in the habit of loading restricted wl drivers.

I suspected something was wrong a weeks ago because my light on the wireless device was orange instead of blue.  But I filed it under 'low priority' since my internet connection was working.

Then...

Today, I tried to sftp to my university and I was getting hung!?!  Well after scouring google for hours and hours and after finally following a link to back to these forums, I find out the wl drivers might be screwing with the sftp / ssh protocols.  

So I went to System->Administration->Hardware Drivers and sure enough wl is enabled and running!  So I disabled it.  Reboot and now I can sftp and ssh to my university.

Also, before disabling the restricted wl drivers, here's what [COLOR="RoyalBlue"]lshw -C network[/COLOR] was showing:
==============================================================
  *-network
       description: Wireless interface
      [COLOR="Red"] product: BCM4312 802.11b/g[/COLOR]
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:f1:67:ac
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.101 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:20:16:2e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
=======================================================================


Grrrr :), [COLOR="Red"] product: BCM4312 802.11b/g[/COLOR],  I was doing great with [COLOR="RoyalBlue"]product: BCM4310 USB Controller[/COLOR] from my original post.

What's really bugging me is that just last week I sftp'd perfectly fine and I was able use vpnclient to establish a VPN connection to the university.  [U]Well, I've fixed my sftp/ssh problem but in my frustration I uninstalled vpnclient and gave up on it.  Grrrr, now I'm suspecting the same problem. I'm going to reinstall vpnclient and verify.
[/U]

[U]
Edit: Yup.  I reinstalled vpnclient and I can now extablish a VPN with my university.  Looks like the restricted wl drivers were messing that up as well.[/U]

---

### Post by joao_debianfanatic on 2008-09-25
Congratulations!!
Runs great on Debian Lenny - HP2718US - BROADCOM 4310 USB!!!!


TY!!!

BEST REGARDS,
JOAO GUSTAVO CABRAL
BRAZIL:guitar:

---

