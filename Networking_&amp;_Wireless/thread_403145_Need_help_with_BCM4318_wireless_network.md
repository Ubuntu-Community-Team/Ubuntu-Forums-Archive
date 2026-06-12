---
title: "Need help with BCM4318 wireless network"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by GB2732 on 2007-04-06
I need some help if someone has time. I've worked on this for 3 days and have done all the diagnostics that I could find. But since it was a fresh install, I'll lose nothing by starting over again.

So, now I've done a clean install of Ubuntu 6.10 on a Gateway Laptop w/AMD 64 Athlon, installed 2.6.18.5 custom Kernel and run the script in step 6 of the BCM4318 tutorial on this site.

Here is my log file:

Log of echo Script version: 0.1.2
Fri Apr 6 14:54:34 2007
Script version: 0.1.2
Fri Apr 6 14:54:34 2007
----------------
Log of lspci
Fri Apr 6 14:54:34 2007
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
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
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
08:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
08:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
08:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
Fri Apr 6 14:54:34 2007
----------------
Log of echo /etc/issue MD5 sum: 11046fbe3787d2ba4fc5821d5a41617e
Fri Apr 6 14:54:34 2007
/etc/issue MD5 sum: 11046fbe3787d2ba4fc5821d5a41617e
Fri Apr 6 14:54:34 2007
----------------
Log of cat /etc/issue
Fri Apr 6 14:54:34 2007
Ubuntu 6.10 \n \l
Fri Apr 6 14:54:34 2007
----------------
Log of ps -e
Fri Apr 6 14:54:34 2007
PID TTY TIME CMD
1 ? 00:00:00 init
2 ? 00:00:00 migration/0
3 ? 00:00:00 ksoftirqd/0
4 ? 00:00:00 events/0
5 ? 00:00:00 khelper
6 ? 00:00:00 kthread
10 ? 00:00:00 kblockd/0
11 ? 00:00:00 kacpid
109 ? 00:00:00 kseriod
151 ? 00:00:00 pdflush
152 ? 00:00:00 pdflush
153 ? 00:00:00 kswapd0
154 ? 00:00:00 aio/0
1679 ? 00:00:00 khubd
1710 ? 00:00:00 khpsbpkt
1722 ? 00:00:00 knodemgrd_0
1782 ? 00:00:00 kjournald
1855 ? 00:00:00 logd
1984 ? 00:00:00 udevd
2795 ? 00:00:00 kpsmoused
2865 ? 00:00:00 pccardd
3635 tty1 00:00:00 getty
3636 tty2 00:00:00 getty
3637 tty3 00:00:00 getty
3638 tty4 00:00:00 getty
3646 tty5 00:00:00 getty
3649 tty6 00:00:00 getty
3830 ? 00:00:00 acpid
3918 ? 00:00:00 syslogd
3944 ? 00:00:00 dd
3946 ? 00:00:00 klogd
4019 ? 00:00:00 gdm
4020 ? 00:00:00 gdm
4039 tty7 00:00:08 Xorg
4055 ? 00:00:00 cupsd
4074 ? 00:00:00 hpiod
4077 ? 00:00:00 python
4119 ? 00:00:00 dbus-daemon
4134 ? 00:00:01 hald
4135 ? 00:00:00 hald-runner
4141 ? 00:00:00 hald-addon-acpi
4147 ? 00:00:00 hald-addon-keyb
4167 ? 00:00:00 hald-addon-stor
4190 ? 00:00:00 perl
4222 ? 00:00:00 kondemand/0
4258 ? 00:00:00 hcid
4267 ? 00:00:00 sdpd
4277 ? 00:00:00 krfcommd
4311 ? 00:00:00 atd
4324 ? 00:00:00 cron
4419 ? 00:00:00 x-session-manag
4454 ? 00:00:00 ssh-agent
4457 ? 00:00:00 dbus-launch
4458 ? 00:00:00 dbus-daemon
4460 ? 00:00:00 gconfd-2
4463 ? 00:00:00 gnome-keyring-d
4466 ? 00:00:00 gnome-settings-
4482 ? 00:00:00 sh
4483 ? 00:00:00 esd
4490 ? 00:00:01 metacity
4495 ? 00:00:02 gnome-panel
4497 ? 00:00:01 nautilus
4501 ? 00:00:00 bonobo-activati
4503 ? 00:00:00 gnome-volume-ma
4516 ? 00:00:00 gnome-vfs-daemo
4518 ? 00:00:00 update-notifier
4524 ? 00:00:00 evolution-alarm
4536 ? 00:00:00 gnome-cups-icon
4539 ? 00:00:00 gnome-power-man
4563 ? 00:00:00 mapping-daemon
4579 ? 00:00:00 trashapplet
4595 ? 00:00:00 gnome-netstatus
4597 ? 00:00:00 mixer_applet2
4617 ? 00:00:00 gnome-screensav
4628 ? 00:00:00 dhclient3
4632 ? 00:00:00 dhclient3
4795 ? 00:00:00 logsave
4817 ? 00:00:00 gnome-terminal
4821 ? 00:00:00 gnome-pty-helpe
4822 pts/1 00:00:00 bash
4849 pts/1 00:00:00 sh
4875 pts/1 00:00:00 logsave
4876 pts/1 00:00:00 ps
Fri Apr 6 14:54:34 2007
----------------
Log of echo Edgy final release detected.
Fri Apr 6 14:54:34 2007
Edgy final release detected.
Fri Apr 6 14:54:34 2007
----------------
Log of rmmod ndiswrapper
Fri Apr 6 14:54:34 2007
ERROR: Module ndiswrapper does not exist in /proc/modules
rmmod died with exit status 1
Fri Apr 6 14:54:34 2007
----------------
Log of rmmod bcm43xx
Fri Apr 6 14:54:34 2007
Fri Apr 6 14:54:34 2007
----------------
Log of echo Edgy
Fri Apr 6 14:54:34 2007
Edgy
Fri Apr 6 14:54:34 2007
----------------
Log of apt-get --assume-yes install ndiswrapper-common ndiswrapper-utils-1.8
Fri Apr 6 14:54:34 2007
Reading package lists...
Building dependency tree...
Reading state information...
ndiswrapper-common is already the newest version.
ndiswrapper-utils-1.8 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Fri Apr 6 14:54:34 2007
----------------
Log of ndiswrapper -e bcmwl5
Fri Apr 6 14:54:34 2007
Driver bcmwl5 is not installed.Use -l to list installed drivers
Fri Apr 6 14:54:34 2007
----------------
Log of ndiswrapper -e bcmwl5a
Fri Apr 6 14:54:34 2007
Driver bcmwl5a is not installed.Use -l to list installed drivers
Fri Apr 6 14:54:34 2007
----------------
Log of ndiswrapper -l
Fri Apr 6 14:54:34 2007
No drivers installed
ndiswrapper died with exit status 1
Fri Apr 6 14:54:35 2007
----------------
Log of echo You appear to have a 64bit system...installing the 64bit drivers...
Fri Apr 6 14:54:35 2007
You appear to have a 64bit system...installing the 64bit drivers...
Fri Apr 6 14:54:35 2007
----------------
Log of tar -xf drivers-64.tar.gz
Fri Apr 6 14:54:35 2007
Fri Apr 6 14:54:35 2007
----------------
Log of ndiswrapper -i bcmwl5.inf
Fri Apr 6 14:54:35 2007
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Fri Apr 6 14:54:35 2007
----------------
Log of modprobe ndiswrapper
Fri Apr 6 14:54:35 2007
FATAL: Module ndiswrapper not found.
modprobe died with exit status 1
Fri Apr 6 14:54:35 2007
----------------
Log of iwconfig
Fri Apr 6 14:54:35 2007
lo no wireless extensions.
eth1 no wireless extensions.
sit0 no wireless extensions.
Fri Apr 6 14:54:35 2007
----------------
Log of ifconfig
Fri Apr 6 14:54:35 2007
eth1 Link encap:Ethernet HWaddr 00:03:25:28:B9:53
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:233
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:36 errors:0 dropped:0 overruns:0 frame:0
TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:2568 (2.5 KiB) TX bytes:2568 (2.5 KiB)
Fri Apr 6 14:54:35 2007
----------------
Log of iwlist scan
Fri Apr 6 14:54:35 2007
lo Interface doesn't support scanning.
eth1 Interface doesn't support scanning.
sit0 Interface doesn't support scanning.
Fri Apr 6 14:54:35 2007

I'm really desperate here...

---

### Post by Zeroedout on 2007-04-06
Hey, I have the same chipset and it was a bitch and half to get up the first time. ```
http://bcm43xx.berlios.de
``` is the team that brought us this beauty and is an invaluable resource. First off, that chipset uses the bcm43xx module, if it isn't loaded, ```
sudo modprobe bcm43xx
``` and if you installed ndiswrapper ```
sudo modprobe -r ndiswrapper
```  Note however that this is a reverse engineered driver, and though it works in some instances and is great for kismet, I've found I need a really strong connection to use the native driver. For most purposes I end up using ndiswrapper. Now the important part to getting the native driver to work under linux is grabbing the firmware and being able to extract it. ```
sudo apt-get install bcm43xx-fwcutter
``` [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) This page is actually really good, found it while looking for the link to the firmware, it should explain everything much better than I did. Essentially though, once you grab the firmware, use fwcutter to extract it from the .sys file and copy everything over to /lib/firmware/<YOUR KERNEL HERE>/ Hope this helped.

---

### Post by GB2732 on 2007-04-06
Zeroedout, thank you so much for the reply. I'll check into your lead and see what happens.

GB

---

### Post by stchman on 2007-05-03
> **GB2732 said:**
> I need some help if someone has time. I've worked on this for 3 days and have done all the diagnostics that I could find. But since it was a fresh install, I'll lose nothing by starting over again.

So, now I've done a clean install of Ubuntu 6.10 on a Gateway Laptop w/AMD 64 Athlon, installed 2.6.18.5 custom Kernel and run the script in step 6 of the BCM4318 tutorial on this site.

Here is my log file:

Log of echo Script version: 0.1.2
Fri Apr 6 14:54:34 2007
Script version: 0.1.2
Fri Apr 6 14:54:34 2007
----------------
Log of lspci
Fri Apr 6 14:54:34 2007
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
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
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
08:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
08:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
08:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
Fri Apr 6 14:54:34 2007
----------------
Log of echo /etc/issue MD5 sum: 11046fbe3787d2ba4fc5821d5a41617e
Fri Apr 6 14:54:34 2007
/etc/issue MD5 sum: 11046fbe3787d2ba4fc5821d5a41617e
Fri Apr 6 14:54:34 2007
----------------
Log of cat /etc/issue
Fri Apr 6 14:54:34 2007
Ubuntu 6.10 \n \l
Fri Apr 6 14:54:34 2007
----------------
Log of ps -e
Fri Apr 6 14:54:34 2007
PID TTY TIME CMD
1 ? 00:00:00 init
2 ? 00:00:00 migration/0
3 ? 00:00:00 ksoftirqd/0
4 ? 00:00:00 events/0
5 ? 00:00:00 khelper
6 ? 00:00:00 kthread
10 ? 00:00:00 kblockd/0
11 ? 00:00:00 kacpid
109 ? 00:00:00 kseriod
151 ? 00:00:00 pdflush
152 ? 00:00:00 pdflush
153 ? 00:00:00 kswapd0
154 ? 00:00:00 aio/0
1679 ? 00:00:00 khubd
1710 ? 00:00:00 khpsbpkt
1722 ? 00:00:00 knodemgrd_0
1782 ? 00:00:00 kjournald
1855 ? 00:00:00 logd
1984 ? 00:00:00 udevd
2795 ? 00:00:00 kpsmoused
2865 ? 00:00:00 pccardd
3635 tty1 00:00:00 getty
3636 tty2 00:00:00 getty
3637 tty3 00:00:00 getty
3638 tty4 00:00:00 getty
3646 tty5 00:00:00 getty
3649 tty6 00:00:00 getty
3830 ? 00:00:00 acpid
3918 ? 00:00:00 syslogd
3944 ? 00:00:00 dd
3946 ? 00:00:00 klogd
4019 ? 00:00:00 gdm
4020 ? 00:00:00 gdm
4039 tty7 00:00:08 Xorg
4055 ? 00:00:00 cupsd
4074 ? 00:00:00 hpiod
4077 ? 00:00:00 python
4119 ? 00:00:00 dbus-daemon
4134 ? 00:00:01 hald
4135 ? 00:00:00 hald-runner
4141 ? 00:00:00 hald-addon-acpi
4147 ? 00:00:00 hald-addon-keyb
4167 ? 00:00:00 hald-addon-stor
4190 ? 00:00:00 perl
4222 ? 00:00:00 kondemand/0
4258 ? 00:00:00 hcid
4267 ? 00:00:00 sdpd
4277 ? 00:00:00 krfcommd
4311 ? 00:00:00 atd
4324 ? 00:00:00 cron
4419 ? 00:00:00 x-session-manag
4454 ? 00:00:00 ssh-agent
4457 ? 00:00:00 dbus-launch
4458 ? 00:00:00 dbus-daemon
4460 ? 00:00:00 gconfd-2
4463 ? 00:00:00 gnome-keyring-d
4466 ? 00:00:00 gnome-settings-
4482 ? 00:00:00 sh
4483 ? 00:00:00 esd
4490 ? 00:00:01 metacity
4495 ? 00:00:02 gnome-panel
4497 ? 00:00:01 nautilus
4501 ? 00:00:00 bonobo-activati
4503 ? 00:00:00 gnome-volume-ma
4516 ? 00:00:00 gnome-vfs-daemo
4518 ? 00:00:00 update-notifier
4524 ? 00:00:00 evolution-alarm
4536 ? 00:00:00 gnome-cups-icon
4539 ? 00:00:00 gnome-power-man
4563 ? 00:00:00 mapping-daemon
4579 ? 00:00:00 trashapplet
4595 ? 00:00:00 gnome-netstatus
4597 ? 00:00:00 mixer_applet2
4617 ? 00:00:00 gnome-screensav
4628 ? 00:00:00 dhclient3
4632 ? 00:00:00 dhclient3
4795 ? 00:00:00 logsave
4817 ? 00:00:00 gnome-terminal
4821 ? 00:00:00 gnome-pty-helpe
4822 pts/1 00:00:00 bash
4849 pts/1 00:00:00 sh
4875 pts/1 00:00:00 logsave
4876 pts/1 00:00:00 ps
Fri Apr 6 14:54:34 2007
----------------
Log of echo Edgy final release detected.
Fri Apr 6 14:54:34 2007
Edgy final release detected.
Fri Apr 6 14:54:34 2007
----------------
Log of rmmod ndiswrapper
Fri Apr 6 14:54:34 2007
ERROR: Module ndiswrapper does not exist in /proc/modules
rmmod died with exit status 1
Fri Apr 6 14:54:34 2007
----------------
Log of rmmod bcm43xx
Fri Apr 6 14:54:34 2007
Fri Apr 6 14:54:34 2007
----------------
Log of echo Edgy
Fri Apr 6 14:54:34 2007
Edgy
Fri Apr 6 14:54:34 2007
----------------
Log of apt-get --assume-yes install ndiswrapper-common ndiswrapper-utils-1.8
Fri Apr 6 14:54:34 2007
Reading package lists...
Building dependency tree...
Reading state information...
ndiswrapper-common is already the newest version.
ndiswrapper-utils-1.8 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Fri Apr 6 14:54:34 2007
----------------
Log of ndiswrapper -e bcmwl5
Fri Apr 6 14:54:34 2007
Driver bcmwl5 is not installed.Use -l to list installed drivers
Fri Apr 6 14:54:34 2007
----------------
Log of ndiswrapper -e bcmwl5a
Fri Apr 6 14:54:34 2007
Driver bcmwl5a is not installed.Use -l to list installed drivers
Fri Apr 6 14:54:34 2007
----------------
Log of ndiswrapper -l
Fri Apr 6 14:54:34 2007
No drivers installed
ndiswrapper died with exit status 1
Fri Apr 6 14:54:35 2007
----------------
Log of echo You appear to have a 64bit system...installing the 64bit drivers...
Fri Apr 6 14:54:35 2007
You appear to have a 64bit system...installing the 64bit drivers...
Fri Apr 6 14:54:35 2007
----------------
Log of tar -xf drivers-64.tar.gz
Fri Apr 6 14:54:35 2007
Fri Apr 6 14:54:35 2007
----------------
Log of ndiswrapper -i bcmwl5.inf
Fri Apr 6 14:54:35 2007
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Fri Apr 6 14:54:35 2007
----------------
Log of modprobe ndiswrapper
Fri Apr 6 14:54:35 2007
FATAL: Module ndiswrapper not found.
modprobe died with exit status 1
Fri Apr 6 14:54:35 2007
----------------
Log of iwconfig
Fri Apr 6 14:54:35 2007
lo no wireless extensions.
eth1 no wireless extensions.
sit0 no wireless extensions.
Fri Apr 6 14:54:35 2007
----------------
Log of ifconfig
Fri Apr 6 14:54:35 2007
eth1 Link encap:Ethernet HWaddr 00:03:25:28:B9:53
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:233
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:36 errors:0 dropped:0 overruns:0 frame:0
TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:2568 (2.5 KiB) TX bytes:2568 (2.5 KiB)
Fri Apr 6 14:54:35 2007
----------------
Log of iwlist scan
Fri Apr 6 14:54:35 2007
lo Interface doesn't support scanning.
eth1 Interface doesn't support scanning.
sit0 Interface doesn't support scanning.
Fri Apr 6 14:54:35 2007

I'm really desperate here...

I have a procedure to get 43xx cards working.

[http://www.stchman.com/install_ndis_broadcom.html](http://www.stchman.com/install_ndis_broadcom.html)

As long as there are no hardware errors this should work.

---

