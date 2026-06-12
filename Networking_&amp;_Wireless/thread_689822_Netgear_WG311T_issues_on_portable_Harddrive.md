---
title: "Netgear WG311T issues on portable Harddrive"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by Hitam269 on 2008-02-06
I recently installed Gutsy Gibbon on a WD Passport portable hard drive.  So far, everything works great except for the internet.  I have a Netgear WG311T PCI card with an Atheros 5212 chipset (which should run with madwifi).  When I use my computer with my live boot CD, the internet works perfectly.  When I boot through my USB drive, though, the internet stops working.

I think this may be because my BIOS is not set up to boot from USB, so I have to use a Boot CD which I created from [this guide.]("https://help.ubuntu.com/community/BootFromUSB")  It seems that the version of Ubuntu that gets booted from the USB drive (via this boot CD) is not identical to the version on the live CD, which leads me to believe either that I need to add something to my boot CD so that the capabilities for wireless internet will boot (assuming they currently do not) or I need to install some package which was on the CD but was not transferred in the installation.  I think there is also a third possibility that the process of detecting hardware is somewhat more difficult from an external USB drive than it is from an internal drive, but if that is the case then I have absolutely no idea what I should do.

Anyway, if this helps, I have run lshw from the live CD and it returns:

> ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:07:e9:e1:6d:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:1
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: wifi0
       version: 01
       serial: 00:0f:b5:fa:4e:f2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.4 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g


when I type in iwconfig, it shows:

> ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:26:5C:66   
          Bit Rate:5 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=27/70  Signal level=-64 dBm  Noise level=-91 dBm
          Rx invalid nwid:6  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


(The emoticons are supposed to be colon o)

and ifconfig shows the following:

> ubuntu@ubuntu:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0F:B5:FA:4E:F2  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fefa:4ef2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4726 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4762406 (4.5 MB)  TX bytes:599673 (585.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:07:E9:E1:6D:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1232 (1.2 KB)  TX bytes:1232 (1.2 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-B5-FA-4E-F2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48154 errors:0 dropped:0 overruns:0 frame:21748
          TX packets:4794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:8700455 (8.2 MB)  TX bytes:719826 (702.9 KB)
          Interrupt:22 


I can run these same commands from the USB drive also, if that would be useful.  Right now, the only thing I can think to do is to install madwifi myself onto the USB drive, but it seems that that should have been installed from the CD (although I do think that my card doesn't have a driver associated with it, because the hardware itself is recognized, but from the USB drive I do not remember it showing the "driver=ath_pci" line.  Does anyone have any ideas for how I can get this card to work?  It could be something really simple; I don't have much experience with linux, so I could have easily left something out.

Thanks for your help
-Ethan

---

### Post by Hitam269 on 2008-02-06
I think that my main problem is related to the driver.  I think I need to somehow configure Madwifi to work with my card, install new repositories or packages, change settings, or completely reinstall madwifi myself.  On the live boot CD under System > Administration > Restricted Drivers it shows that Atheros Access Hardware Layer (HAL) is in use.  I don't think it shows that in the USB drive, but I'll make sure and post back here, along with what iwconfig, ifconfig, and lshw show.  If anyone has any ideas, please let me know.

Thanks
-Ethan

---

