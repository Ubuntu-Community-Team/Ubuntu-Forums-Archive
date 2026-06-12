---
title: "unable to connect to wireless network"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by phenrol on 2007-07-08
I need some help connecting to my wireless network.  I am using a netgear WAB501 and I have ndiswrapper installed.  Here is my ifconfig, iwconfig and lspci output:

ath0      Link encap:Ethernet  HWaddr 00:09:5B:2F:60:DB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4378 (4.2 KiB)  TX bytes:5165 (5.0 KiB)

ath0:avah Link encap:Ethernet  HWaddr 00:09:5B:2F:60:DB  
          inet addr:169.254.7.20  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:D0:59:93:0F:4D  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fe93:f4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:943052 (920.9 KiB)  TX bytes:184350 (180.0 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1164 (1.1 KiB)  TX bytes:1164 (1.1 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-09-5B-2F-60-DB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3464 errors:0 dropped:0 overruns:0 frame:823
          TX packets:887 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:283582 (276.9 KiB)  TX bytes:42067 (41.0 KiB)
          Interrupt:11 

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:"DONTTRYME"  Nickname:"DONTTRYME"
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:2441  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:04.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
00:09.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 09)
00:09.1 Serial controller: Agere Systems LT WinModem
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5211 802.11ab NIC (rev 01)

To install ndiswrapper I did the following commands:

$ndiswrapper -i netwab51.inf
(no output)
$ndiswrapper -l
netwab51 : driver installed
        device (168C:0012) present (alternate driver: ath_pci)
$sudo modprobe ndiswrapper
(no output)

When I try to use the wireless network drivers application in System->Administration->Windows Wireless Drivers it says "Hardware present:no" and won't let me remove it

When I use wifi radar, it sees my wireless network it shows a good signal strength but when I create a profile for it and connect it says that it is unable to get an ip address.  If I configure it for a static IP address (along with a valid DNS server) I can ping my router but nothing beyond the router.

Any help would be great.

---

### Post by kevdog on 2007-07-08
Can you post the following:

lshw -C network
sudo modprobe -l | grep ath_pci
sudo modinfo ath_pci

Thanks!

---

### Post by phenrol on 2007-07-08
Here you go:

$ lshw -C network
  *-network               
       description: NETGEAR WAB501 802.11a/b Wireless Adapter
       physical id: 0
       version: 0000000000000000000000000000000000
       slot: Socket 0
       resources: irq:11
  *-network
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth0
       version: 09
       serial: 00:d0:59:93:0f:4d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A ip=192.168.0.2 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: iomemory:41280000-41280fff ioport:3440-347f iomemory:41200000-4121ffff irq:11
  *-network
       description: Wireless interface
       product: AR5211 802.11ab NIC
       vendor: Atheros Communications, Inc.
       physical id: 3
       bus info: pci@02:00.0
       logical name: wifi0
       version: 01
       serial: 00:09:5b:2f:60:db
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.1) latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11a
       resources: iomemory:34000000-3400ffff irq:11

$ sudo modprobe -l | grep ath_pci
/lib/modules/2.6.20-16-generic/madwifi/ath_pci.ko

$ sudo modprobe -l | grep ath_pci
/lib/modules/2.6.20-16-generic/madwifi/ath_pci.ko
liam@armor:/tmp$ sudo modinfo ath_pci
filename:       /lib/modules/2.6.20-16-generic/madwifi/ath_pci.ko
license:        Dual BSD/GPL
version:        0.9.3.1
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     D33427613CC54A874D9A746
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           countrycode:Override default country code (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)

---

### Post by kevdog on 2007-07-08
First Im surprised this card doesnt work "out of the box" without ndiswrapper.   But anyway that's another discussion. 

First if you look at the output of lshw -C network, notice the following line:

configuration: broadcast=yes [COLOR="Red"]driver=ath_pci[/COLOR] driverversion=0.9.4.5 (0.9.3.1) latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11a

Despite installing ndiswrapper, your card is still associated with the ath_pci driver.  First you must blacklist this using the following method:
```

gksu gedit /etc/modprobe.d/blacklist
```

Add to end of file:
> blacklist ath_pci


Your card might work then if ndiswrapper is setup properly.  What I would do at this point is to reboot, and then check again with lshw -C network and sure your card is associated with ndiswrapper.  If it is, then we could debug ndiswrapper.

---

### Post by phenrol on 2007-07-08
Thanks for the suggestion; I tried it and it didn't work, however, I have figured out my issue.  Here is what I ended up doing:

First, I removed all traces of the ndiswrapper module:
$sudo modprobe -r ndiswrapper

Then I ran the uninstall script for madwifi (which I did not realize was installed)
[modwifi src folder]$sudo make uninstall

I dowloaded the lastest madwifi and patches into the /usr/src folder
$sudo svn checkout [http://svn.madwifi.org/trunk/](http://svn.madwifi.org/trunk/) madwifi-ng
$sudo wget [http://patches.aircrack-ng.org/madwifi-ng-r2277.patch](http://patches.aircrack-ng.org/madwifi-ng-r2277.patch)
$cd madwifi-ng
$sudo patch -Np1 -i ../madwifi-ng-r2277.patch

Then I ran make which is when I found another problem.  I was seeing a ton of errors, and found out that in order to compile device drivers I needed the build-essential package, so I ran:
$sudo apt-get install build-essential

After this, I ran the following without errors from the /usr/src/madwifi-ng folder:
$sudo make
$sudo make install

This installed the files, then I used modprobe to apply them:
$sudo modinfo ath_pci

After this command, I got an error due to the fact that I had blacklisted the driver, so I unblacklisted it and rebooted, ran the modprobe command again and everything worked.  

WOOT!

---

