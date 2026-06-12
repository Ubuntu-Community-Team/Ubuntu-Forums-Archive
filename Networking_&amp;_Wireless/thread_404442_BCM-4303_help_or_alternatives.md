---
title: "BCM-4303 help or alternatives"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by prophet9 on 2007-04-08
I've been working on this for longer than I care to admit.  All I'm trying ot do is get on my wireless network.  Unfortunately I seem to have the singularly most diffcult hardware to set up.  I have a Linksys WMP11, which turns out to actually be a BM-4303.  I'm trying to connect to my Linksys WRT54GS router.  

I've been up and down the entire forums and I've found dozens, if not hundreds of post about this problem.  All of them keep pointing me to guides for the BM-4313, which I followed.  Tried to install ndiswrapper but I was met with complete an utter failure.  So I went out and I talked to someone more knowledgeable than myself (or so I thought) and they got me to buy a WAP, which turned out to be entirely the wrong thing for my problem.  So I returned that and I got a brdige that was made for the X-Box, but said it would work with computers too.  It was the DGL-3420.  It should have done exactly what I needed, but it doesn't work.

**So heres my questions:**  I want on my f-ing network.  I'm completely willing to by new hardware if someone knows a wireless PCI card that wont be a multi-day-marathon/pain-in-my-*** to setup.   If anyone can help me figure out how ot use my BCM-4303 that would work too.  

I followed this guide to set up my card [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")  and heres the log file it created:

```
Log of echo Script version: 0.1.2 
Sun Apr  8 12:08:01 2007

Script version: 0.1.2

Sun Apr  8 12:08:01 2007
----------------
Log of lspci 
Sun Apr  8 12:08:02 2007

00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 945G/GZ/P/PL Express PCI Express Root Port (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:01.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
01:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
01:02.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 08)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
04:00.0 VGA compatible controller: nVidia Corporation Unknown device 0291 (rev a1)

Sun Apr  8 12:08:02 2007
----------------
Log of echo /etc/issue MD5 sum: 11046fbe3787d2ba4fc5821d5a41617e 
Sun Apr  8 12:08:02 2007

/etc/issue MD5 sum: 11046fbe3787d2ba4fc5821d5a41617e

Sun Apr  8 12:08:02 2007
----------------
Log of cat /etc/issue 
Sun Apr  8 12:08:02 2007

Ubuntu 6.10 \n \l


Sun Apr  8 12:08:02 2007
----------------
Log of ps -e 
Sun Apr  8 12:08:02 2007

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 migration/1
    6 ?        00:00:00 ksoftirqd/1
    7 ?        00:00:00 watchdog/1
    8 ?        00:00:00 events/0
    9 ?        00:00:00 events/1
   10 ?        00:00:00 khelper
   11 ?        00:00:00 kthread
   14 ?        00:00:00 kblockd/0
   15 ?        00:00:00 kblockd/1
   16 ?        00:00:00 kacpid
   17 ?        00:00:00 kacpi_notify
  114 ?        00:00:00 kseriod
  153 ?        00:00:00 pdflush
  154 ?        00:00:00 pdflush
  155 ?        00:00:00 kswapd0
  156 ?        00:00:00 aio/0
  157 ?        00:00:00 aio/1
  789 ?        00:00:00 kirqd
 1720 ?        00:00:00 ata/0
 1721 ?        00:00:00 ata/1
 1724 ?        00:00:00 scsi_eh_0
 1725 ?        00:00:00 scsi_eh_1
 1840 ?        00:00:00 khubd
 1923 ?        00:00:00 kjournald
 2007 ?        00:00:00 logd
 2153 ?        00:00:00 udevd
 2958 ?        00:00:00 shpchpd
 3061 ?        00:00:00 kpsmoused
 3136 ?        00:00:00 scsi_eh_2
 3137 ?        00:00:00 usb-storage
 3157 ?        00:00:00 kgameportd
 3881 tty1     00:00:00 getty
 3882 tty2     00:00:00 getty
 3884 tty3     00:00:00 getty
 3886 tty4     00:00:00 getty
 3887 tty5     00:00:00 getty
 3888 tty6     00:00:00 getty
 4119 ?        00:00:00 acpid
 4227 ?        00:00:00 syslogd
 4253 ?        00:00:00 dd
 4255 ?        00:00:00 klogd
 4329 ?        00:00:00 gdm
 4330 ?        00:00:00 gdm
 4347 tty7     00:00:03 Xorg
 4367 ?        00:00:00 cupsd
 4384 ?        00:00:00 hpiod
 4387 ?        00:00:00 python
 4439 ?        00:00:00 dbus-daemon
 4454 ?        00:00:02 hald
 4455 ?        00:00:00 hald-runner
 4461 ?        00:00:00 hald-addon-acpi
 4471 ?        00:00:00 hald-addon-keyb
 4475 ?        00:00:00 hald-addon-keyb
 4478 ?        00:00:00 hald-addon-keyb
 4493 ?        00:00:00 hald-addon-stor
 4502 ?        00:00:00 hald-addon-stor
 4504 ?        00:00:00 hald-addon-stor
 4519 ?        00:00:00 perl
 4591 ?        00:00:00 hcid
 4595 ?        00:00:00 sdpd
 4615 ?        00:00:00 krfcommd
 4634 ?        00:00:00 anacron
 4648 ?        00:00:00 atd
 4661 ?        00:00:00 cron
 4752 ?        00:00:00 x-session-manag
 4787 ?        00:00:00 ssh-agent
 4790 ?        00:00:00 dbus-launch
 4791 ?        00:00:00 dbus-daemon
 4793 ?        00:00:00 gconfd-2
 4796 ?        00:00:00 gnome-keyring-d
 4799 ?        00:00:00 gnome-settings-
 4816 ?        00:00:00 sh
 4817 ?        00:00:00 esd
 4822 ?        00:00:00 metacity
 4827 ?        00:00:01 gnome-panel
 4829 ?        00:00:01 nautilus
 4833 ?        00:00:00 bonobo-activati
 4837 ?        00:00:00 gnome-vfs-daemo
 4838 ?        00:00:00 gnome-volume-ma
 4862 ?        00:00:00 update-notifier
 4866 ?        00:00:00 evolution-alarm
 4876 ?        00:00:00 gnome-cups-icon
 4885 ?        00:00:00 gnome-power-man
 4889 ?        00:00:00 trashapplet
 4940 ?        00:00:00 mapping-daemon
 4956 ?        00:00:00 mixer_applet2
 4975 ?        00:00:00 gnome-screensav
 5023 ?        00:00:02 firefox-bin
 5036 ?        00:00:01 gnome-terminal
 5038 ?        00:00:00 gnome-pty-helpe
 5039 pts/0    00:00:00 bash
 5069 ?        00:00:00 netstat <defunct>
 5109 pts/0    00:00:00 sh
 5133 pts/0    00:00:00 logsave
 5134 pts/0    00:00:00 ps

Sun Apr  8 12:08:02 2007
----------------
Log of echo Edgy final release detected. 
Sun Apr  8 12:08:02 2007

Edgy final release detected.

Sun Apr  8 12:08:02 2007
----------------
Log of rmmod ndiswrapper 
Sun Apr  8 12:08:02 2007

ERROR: Module ndiswrapper does not exist in /proc/modules
rmmod died with exit status 1

Sun Apr  8 12:08:02 2007
----------------
Log of rmmod bcm43xx 
Sun Apr  8 12:08:02 2007


Sun Apr  8 12:08:02 2007
----------------
Log of echo Edgy 
Sun Apr  8 12:08:02 2007

Edgy

Sun Apr  8 12:08:02 2007
----------------
Log of apt-get --assume-yes install ndiswrapper-common ndiswrapper-utils-1.8 
Sun Apr  8 12:08:02 2007

Reading package lists...
Building dependency tree...
Reading state information...
E: Couldn't find package ndiswrapper-common
apt-get died with exit status 100

Sun Apr  8 12:08:02 2007
----------------
Log of ndiswrapper -e bcmwl5 
Sun Apr  8 12:08:02 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Sun Apr  8 12:08:02 2007
----------------
Log of ndiswrapper -e bcmwl5a 
Sun Apr  8 12:08:02 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Sun Apr  8 12:08:02 2007
----------------
Log of ndiswrapper -l 
Sun Apr  8 12:08:02 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Sun Apr  8 12:08:02 2007
----------------
Log of echo You appear to have an i386 system...installing the i386 drivers... 
Sun Apr  8 12:08:02 2007

You appear to have an i386 system...installing the i386 drivers...

Sun Apr  8 12:08:02 2007
----------------
Log of tar -xf drivers-32.tar.gz 
Sun Apr  8 12:08:02 2007


Sun Apr  8 12:08:02 2007
----------------
Log of ndiswrapper -i bcmwl5.inf 
Sun Apr  8 12:08:02 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Sun Apr  8 12:08:02 2007
----------------
Log of modprobe ndiswrapper 
Sun Apr  8 12:08:02 2007


Sun Apr  8 12:08:02 2007
----------------
Log of iwconfig 
Sun Apr  8 12:08:02 2007

lo        no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.


Sun Apr  8 12:08:02 2007
----------------
Log of ifconfig 
Sun Apr  8 12:08:02 2007

eth1      Link encap:Ethernet  HWaddr 00:17:31:C3:CE:24  
          inet addr:192.168.0.31  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23924 (23.3 KiB)  TX bytes:23924 (23.3 KiB)


Sun Apr  8 12:08:02 2007
----------------
Log of iwlist scan 
Sun Apr  8 12:08:02 2007

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


Sun Apr  8 12:08:02 2007
----------------


```


If you've made it this far, thanks for reading and thanks for any help you can provide.
--Ryan

---

### Post by Floppyjoe on 2007-04-08
The link you are following is for a Broadcom 4318 card. You should be following one for a Broadcom 4303 card.

You probably have the wrong driver installed.

This is what is on the ndiswrapper list site about your cards chipset:
> # Card: Broadcom BCM4301 built-in Compaq nx9110 laptop

    * Chipset: Broadcom 4301
    * pciid: **14e4:4301 (rev 02)**
    * Driver: Downloaded Windows 2000 driver from Compaq site. FilenameSP28538.exe.
    * Other: Debian with 2.6.8 kernel. NdisWrapper 0.10 built deb and installed. Use bcmwl5.inf. 

# Card: Broadcom BCM4301 built-in HP Pavillion zv5142EA (zv5000 series)

    * Chipset: Broadcom 4301
    * pciid: **14e4:4301 (rev 02)**
    * Driver: Downloading latest XP driver for the zv5142EA will surely be ok - as of 2004-10, this is SP27952A. Use driver bcmwl5a.inf here!#*Other: SuSE 9.1 with 2.6.4.52-default kernel. NdisWrapper? installed via YaST. 

# Card: Broadcom BCM4301 built-in HP Compaq nx9010 laptop

    * Chipset: Broadcom 4301 802.11b (rev 02)
    * pciid: **14e4:4301 (rev 02)**
    * Driver: bcmwl5.inf from the HP.com Windows XP update file SP28537.exe, using Ndiswrapper 1.1 and wpa_supplicant, everything including WPA-PSK works following installation instructions and using the WPA config file on the wiki. 

# Card: Broadcom BCM4303 built-in HP Pavilion zv5265EA (zv5200 series)

    * Chipset: **Broadcom 4303**
    * pciid: **14e4:4301 (rev 02**)
    * Driver: Works with driver from "Driver Recovery CD" Disc 1 - SWSetup/WLAN/bcmwl5.inf / bcmwl5.sys 


And this:
> # Card: Linksys #[WMP11 v2.7] 802.11b -- [link here|List#WMP11 v27]

    * Chipset: Broadcom BCM4301
    * Driver: Downloaded Windows 2000 driver from Compaq site. FilenameSP28538.exe.
    * Other: Mandrake 10.1 with 2.6.8.1 kernel. NdisWrapper 0.90 built and installed. Use bcmwl5.inf. If you're having trouble getting card into Managed mode, put it auto mode first, then change to managed. 

# Card: Linksys #[WMP11 v2.7] 802.11b -- [link here|List#WMP11 v27]

    * ndiswrapper version: 0.8
    * Chipset: Broadcom Corporation BCM4301 802.11b (rev 02)
    * pciid: **14e4:4301**
    * Driver: Version 3.8.28.0, Release Date: 11/15/02 from ownloads
    * Other: Knoppix Linux 3.7 (2.4.27). Interface doesn't always come up, but easily fixed by root command ifup wlan0 



---

### Post by prophet9 on 2007-04-08
...Ok.  I knew I was following instructions for the thw wrong BCM but every site I went to linked back to the post on the 4318, and I really do mean everything.  It said that was the best automated ndiswrapper installer there was.  

So, I see the stuff you've quoted, but I dont know what to do with it.  I have a linksys wmp11, which is listed in the second quote you put up, but that quote also says the BCM-4301 chipster, I have the BCM-4303.

:) Thanks for responding, but I still don't know what to do.  :(

---

### Post by lildragon1202 on 2007-05-23
any new info on this? i did the exact same thing prohet9 did. :(

---

