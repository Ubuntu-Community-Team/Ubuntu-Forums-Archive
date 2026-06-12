---
title: "Broadcom 4318 in compaq v2570nr laptop"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by sonofskywalker3 on 2008-04-23
I have installed a clean install of 64bit kubuntu 7.10 gutsy on my v2570nr laptop. i went through the howto guide to install ndiswrapper, and have successfully been able to get the wireless light to turn on, but have no success with connecting. It does not detect the local wireless networks. i have tried manually connecting to my local ssid, but it gets to 28%, "configuring device" and then says it failed. log is below.


Log of echo Script version: 0.1.3 
Wed Apr 23 00:26:49 2008

Script version: 0.1.3

Wed Apr 23 00:26:49 2008
----------------
Log of lspci 
Wed Apr 23 00:26:49 2008

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

Wed Apr 23 00:26:49 2008
----------------
Log of echo /etc/issue MD5 sum: a949fb2f0596e677b5f12a6f62f19d50 
Wed Apr 23 00:26:49 2008

/etc/issue MD5 sum: a949fb2f0596e677b5f12a6f62f19d50

Wed Apr 23 00:26:49 2008
----------------
Log of cat /etc/issue 
Wed Apr 23 00:26:49 2008

Ubuntu 7.10 \n \l


Wed Apr 23 00:26:49 2008
----------------
Log of ps -e 
Wed Apr 23 00:26:49 2008

  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   25 ?        00:00:00 kblockd/0
   26 ?        00:00:00 kacpid
   27 ?        00:00:00 kacpi_notify
  120 ?        00:00:00 kseriod
  148 ?        00:00:00 pdflush
  149 ?        00:00:00 pdflush
  150 ?        00:00:00 kswapd0
  203 ?        00:00:00 aio/0
 2234 ?        00:00:00 ksuspend_usbd
 2235 ?        00:00:00 khubd
 2253 ?        00:00:00 ata/0
 2254 ?        00:00:00 ata_aux
 2345 ?        00:00:00 khpsbpkt
 2483 ?        00:00:00 knodemgrd_0
 2636 ?        00:00:00 kjournald
 2836 ?        00:00:00 udevd
 3713 ?        00:00:00 tifm
 3731 ?        00:00:00 pccardd
 3737 ?        00:00:00 kmmcd
 3739 ?        00:00:00 kpsmoused
 4515 tty4     00:00:00 getty
 4516 tty5     00:00:00 getty
 4520 tty2     00:00:00 getty
 4521 tty3     00:00:00 getty
 4527 tty1     00:00:00 getty
 4528 tty6     00:00:00 getty
 4732 ?        00:00:00 acpid
 4759 ?        00:00:00 kondemand/0
 4884 ?        00:00:00 syslogd
 4938 ?        00:00:00 dd
 4940 ?        00:00:00 klogd
 4961 ?        00:00:00 dbus-daemon
 4977 ?        00:00:00 NetworkManager
 4991 ?        00:00:00 NetworkManagerD
 5010 ?        00:00:02 hald
 5011 ?        00:00:00 hald-runner
 5058 ?        00:00:00 hald-addon-keyb
 5059 ?        00:00:00 hald-addon-keyb
 5060 ?        00:00:00 hald-addon-keyb
 5061 ?        00:00:00 hald-addon-keyb
 5065 ?        00:00:00 hald-addon-cpuf
 5069 ?        00:00:00 hald-addon-acpi
 5070 ?        00:00:00 hald-addon-keyb
 5116 ?        00:00:00 hald-addon-stor
 5159 ?        00:00:00 kdm
 5179 tty7     00:00:21 Xorg
 5182 ?        00:00:00 kdm
 5190 ?        00:00:00 cupsd
 5297 ?        00:00:00 avahi-daemon
 5298 ?        00:00:00 avahi-daemon
 5312 ?        00:00:00 dhcdbd
 5332 ?        00:00:00 hcid
 5342 ?        00:00:00 bluetoothd-serv
 5343 ?        00:00:00 bluetoothd-serv
 5348 ?        00:00:00 krfcommd
 5382 ?        00:00:00 atd
 5396 ?        00:00:00 cron
 5540 ?        00:00:00 x-session-manag
 5581 ?        00:00:00 ssh-agent
 5618 ?        00:00:00 start_kdeinit
 5619 ?        00:00:00 kdeinit
 5622 ?        00:00:00 dcopserver
 5625 ?        00:00:00 klauncher
 5627 ?        00:00:02 kded
 5813 ?        00:00:00 kwrapper
 5815 ?        00:00:00 ksmserver
 5816 ?        00:00:01 kwin
 5818 ?        00:00:02 kdesktop
 5826 ?        00:00:00 kio_uiserver
 5829 ?        00:00:03 kicker
 5847 ?        00:00:06 artsd
 5849 ?        00:00:00 kaccess
 5852 ?        00:00:00 kmix
 5854 ?        00:00:00 katapult
 5856 ?        00:00:30 konqueror
 5860 ?        00:00:00 knotify
 5862 ?        00:00:02 guidance-power-
 5863 ?        00:00:01 restricted-mana
 5864 ?        00:00:00 aspell
 5867 ?        00:00:00 klipper
 5869 ?        00:00:00 knetworkmanager
 5870 ?        00:00:00 konqueror
 5871 ?        00:00:00 kblueplugd
 5872 ?        00:00:02 adept_notifier
 6630 ?        00:00:00 dhclient
 6722 ?        00:00:00 kio_file
 6725 ?        00:00:00 kio_http
 6815 ?        00:00:00 kwalletmanager
 7019 ?        00:00:00 kio_http
 7170 ?        00:00:00 konsole
 7171 pts/1    00:00:00 bash
 7306 ?        00:00:00 kio_file
 7375 ?        00:00:00 kio_file
 7384 ?        00:00:00 kio_thumbnail
 7405 ?        00:00:00 kio_trash
 7406 ?        00:00:00 kio_trash
 7411 ?        00:00:00 kio_system
 7444 pts/1    00:00:00 ndiswrapper_set
 7463 pts/1    00:00:00 logsave
 7464 pts/1    00:00:00 ps

Wed Apr 23 00:26:50 2008
----------------
Log of echo Gutsy release detected. 
Wed Apr 23 00:26:50 2008

Gutsy release detected.

Wed Apr 23 00:26:50 2008
----------------
Log of rmmod ndiswrapper 
Wed Apr 23 00:26:50 2008

ERROR: Module ndiswrapper does not exist in /proc/modules
rmmod died with exit status 1

Wed Apr 23 00:26:50 2008
----------------
Log of rmmod bcm43xx 
Wed Apr 23 00:26:50 2008


Wed Apr 23 00:26:50 2008
----------------
Log of echo Gutsy 
Wed Apr 23 00:26:50 2008

Gutsy

Wed Apr 23 00:26:50 2008
----------------
Log of apt-get --assume-yes install ndiswrapper-common ndiswrapper-utils-1.9 
Wed Apr 23 00:26:50 2008

Reading package lists...
Building dependency tree...
Reading state information...
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/53.3kB of archives.
After unpacking 242kB of additional disk space will be used.
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 83361 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.43-1ubuntu2_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.43-1ubuntu2_amd64.deb) ...
Setting up ndiswrapper-common (1.43-1ubuntu2) ...
Setting up ndiswrapper-utils-1.9 (1.43-1ubuntu2) ...

Wed Apr 23 00:27:13 2008
----------------
Log of ndiswrapper -e bcmwl5 
Wed Apr 23 00:27:13 2008

couldn't delete /etc/ndiswrapper/bcmwl5: No such file or directory

Wed Apr 23 00:27:13 2008
----------------
Log of ndiswrapper -e bcmwl5a 
Wed Apr 23 00:27:13 2008

couldn't delete /etc/ndiswrapper/bcmwl5a: No such file or directory

Wed Apr 23 00:27:15 2008
----------------
Log of ndiswrapper -l 
Wed Apr 23 00:27:15 2008


Wed Apr 23 00:27:16 2008
----------------
Log of echo You appear to have a 64bit system...installing the 64bit drivers... 
Wed Apr 23 00:27:16 2008

You appear to have a 64bit system...installing the 64bit drivers...

Wed Apr 23 00:27:16 2008
----------------
Log of tar -xf drivers-64.tar.gz 
Wed Apr 23 00:27:16 2008


Wed Apr 23 00:27:16 2008
----------------
Log of ndiswrapper -i bcmwl5.inf 
Wed Apr 23 00:27:16 2008

installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2

Wed Apr 23 00:27:16 2008
----------------
Log of modprobe ndiswrapper 
Wed Apr 23 00:27:16 2008


Wed Apr 23 00:27:17 2008
----------------
Log of iwconfig 
Wed Apr 23 00:27:17 2008

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Wed Apr 23 00:27:17 2008
----------------
Log of ifconfig 
Wed Apr 23 00:27:17 2008

eth0      Link encap:Ethernet  HWaddr 00:16:36:1F:AA:2A  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe1f:aa2a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2113464 (2.0 MB)  TX bytes:228234 (222.8 KB)
          Interrupt:18 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:6B:B2:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Memory:c0204000-c0206000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Wed Apr 23 00:27:17 2008
----------------
Log of iwlist scan 
Wed Apr 23 00:27:17 2008

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results


Wed Apr 23 00:27:20 2008
----------------

---

### Post by herbie_popnecker on 2008-04-23
Give up!
I tried every posted method and could not get the damn Broadcom to work on my HP dv6000. 
Wouln't work in either Gutsy or the Hardy beta, and that was the 32 bit version.
Some just don't work.
Now looking for a compatable PCM card, because I ran into the same issue with my Realtek 8187B on the other laptop!

---

### Post by sonofskywalker3 on 2008-04-23
i'm about at that point too man, it's really frustrating. can't get it to work on windows either, i'm about to just buy the restore disks, but i really don't want to.

---

### Post by kutjara on 2008-04-23
> **sonofskywalker3 said:**
> I have installed a clean install of 64bit kubuntu 7.10 gutsy on my v2570nr laptop. i went through the howto guide to install ndiswrapper, and have successfully been able to get the wireless light to turn on, but have no success with connecting. It does not detect the local wireless networks. i have tried manually connecting to my local ssid, but it gets to 28%, "configuring device" and then says it failed.


Is this the HOWTO you used? -

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I had big problems getting my Broadcom BCM4328 card working with 64 bit Hardy, but this HOWTO worked for me. The only problem I had was that WPA simply wouldn't work with my card. In the end, I had to switch to a Belkin card (the F5D7050), which does support WPA under 64 bit Hardy, using the Serialmonkey drivers.

If you don't need WPA, or can make do with WEP, the how-to above should get you up and running.

---

### Post by kevdog on 2008-04-23
The 4318 card should work without any problems if you set it up correctly.  This is a very common chipset and has been discussed before.

---

### Post by sonofskywalker3 on 2008-04-28
well, i was so frustrated that i turned the computer off for a week, now i come back and it works perfectly. thanks for all the help from everyone on this wonderful forum!

---

