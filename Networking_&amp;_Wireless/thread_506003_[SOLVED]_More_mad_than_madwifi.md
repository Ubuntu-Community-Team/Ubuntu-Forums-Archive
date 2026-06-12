---
title: "[SOLVED] More mad than madwifi"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2007-07-21
Per a [Solved] post titled: Atheros restricted drivers or madwifi or windows

mark@Lexington:~$ uname -r
2.6.20-16-386

mark@Lexington:~$ lspci
01:0b.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

mark@Lexington:~$ lshw
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR5212 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: b
                bus info: pci@01:0b.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64 maxlatency=28 mingnt=10
                resources: iomemory:ff8f0000-ff8fffff irq:3

mark@Lexington:~$ iwconfig
lo        no wireless extensions.

mark@Lexington:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 b)  TX bytes:600 (600.0 b)

mark@Lexington:~$ cat /etc/network/interfaces
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

iface ppp0 inet ppp
provider ppp0

mark@Lexington:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

mark@Lexington:~$ iwlist scan
lo        Interface doesn't support scanning.

mark@Lexington:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper

mark@Lexington:~$ cat etc/resolv.conf
cat: etc/resolv.conf: No such file or directory

sumark@Lexington:~$ sudo apt-cache search madwifi
Password:
linux-restricted-modules-2.6.20-15-386 - Non-free Linux 2.6.20 modules on 386
linux-restricted-modules-2.6.20-15-generic - Non-free Linux 2.6.20 modules on x86/x86_64
hostapd - user space IEEE 802.11 AP and IEEE 802.1X/WPA/WPA2/EAP Authenticator
madwifi-tools - tools for the Multiband Atheros Driver for WiFi
linux-restricted-modules-2.6.20-15-lowlatency - Non-free Linux 2.6.20 modules on x86/x86_64
xen-restricted-modules-2.6.17-6-generic-xen0 - Non-free Linux 2.6.17 modules on x86_64 generic-xen0
linux-restricted-modules-2.6.20-16-386 - Non-free Linux 2.6.20 modules on 386
linux-restricted-modules-2.6.20-16-generic - Non-free Linux 2.6.20 modules on x86/x86_64
linux-restricted-modules-2.6.20-16-lowlatency - Non-free Linux 2.6.20 modules on x86/x86_64

mark@Lexington:~$ sudo uname -r
2.6.20-16-386

mark@Lexington:~$ sudo aptitude install linux-restricted-modules-2.6.20-16.386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find package "linux-restricted-modules-2.6.20-16.386".  However, the following
packages contain "linux-restricted-modules-2.6.20-16.386" in their name:
  linux-restricted-modules-2.6.20-16-386 
The following packages have been automatically kept back:
  clamav-freshclam 
The following packages have been kept back:
  clamav clamav-base clamav-daemon clamav-docs libclamav2 
0 packages upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
mark@Lexington:~$ 

mark@Lexington:~$ sudo ifconfig
Password:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)

mark@Lexington:~$ sudo ifconfig wlan0
wlan0: error fetching interface information: Device not found

mark@Lexington:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub [8086:1130] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82815 815 Chipset AGP Bridge [8086:1131] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 01)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 [8086:244b] (rev 01)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB (Hub #1) [8086:2442] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus [8086:2443] (rev 01)
01:0b.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5212 802.11abg NIC [168c:0013] (rev 01)
01:0c.0 Multimedia audio controller [0401]: Ensoniq ES1371 [AudioPCI-97] [1274:1371] (rev 06)
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS [1002:5046]
mark@Lexington:~$ 

mark@Lexington:~$ modinfo acx_pci
modinfo: could not find module acx_pci

mark@Lexington:~$ modinfo ath_pci
filename:       /lib/modules/2.6.20-16-386/madwifi/ath_pci.ko
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
vermagic:       2.6.20-16-386 mod_unload 486 
parm:           countrycode:Override default country code (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)
mark@Lexington:~$ 

mark@Lexington:~$ sudo apt-cache search madwifi
linux-restricted-modules-2.6.20-15-386 - Non-free Linux 2.6.20 modules on 386
linux-restricted-modules-2.6.20-15-generic - Non-free Linux 2.6.20 modules on x86/x86_64
hostapd - user space IEEE 802.11 AP and IEEE 802.1X/WPA/WPA2/EAP Authenticator
madwifi-tools - tools for the Multiband Atheros Driver for WiFi
linux-restricted-modules-2.6.20-15-lowlatency - Non-free Linux 2.6.20 modules on x86/x86_64
xen-restricted-modules-2.6.17-6-generic-xen0 - Non-free Linux 2.6.17 modules on x86_64 generic-xen0
linux-restricted-modules-2.6.20-16-386 - Non-free Linux 2.6.20 modules on 386
linux-restricted-modules-2.6.20-16-generic - Non-free Linux 2.6.20 modules on x86/x86_64
linux-restricted-modules-2.6.20-16-lowlatency - Non-free Linux 2.6.20 modules on x86/x86_64
mark@Lexington:~$ 

mark@Lexington:~$ sudo uname -r
2.6.20-16-386

mark@Lexington:~$ sudo aptitude install linux-restricted-modules-2.6.20-16-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  clamav-freshclam 
The following packages have been kept back:
  clamav clamav-base clamav-daemon clamav-docs libclamav2 
0 packages upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
mark@Lexington:~$ 

mark@Lexington:~$ sudo aptitude install linux-restricted-modules-2.6.20-16-386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  clamav-freshclam 
The following packages have been kept back:
  clamav clamav-base clamav-daemon clamav-docs libclamav2 
0 packages upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
mark@Lexington:~$ 

after adding the restricted module above, I rebooted and:

root@Lexington:/home/mark# lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: b
       bus info: pci@01:0b.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
       resources: iomemory:ff8f0000-ff8fffff irq:3
root@Lexington:/home/mark# 

still nothing but the dial up modem in Gnome net. mgr.

any suggestion appreciated.

---

### Post by spd106 on 2007-07-22
Have you tried enabling it through the Restricted Drivers Manager?

Also try these commands
```
sudo modprobe ath_pci
```
```
lsmod | grep ath
```
```
dmesg | grep ath
```

I have read that there can be an IRQ or ACPI problem on some laptops, particularly the IBM Thinkpads. I can't remember the thread exactly, but you should be able to search for it.

---

### Post by Mark_in_Hollywood on 2007-07-23
output of dmesg | grep ath


[  163.888136] wlan: 0.8.4.2 (0.9.3.1)
[  163.963545] ath_pci: Unknown symbol _ath_hal_attach
[  163.964019] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  163.965405] ath_pci: Unknown symbol ath_hal_computetxtime
[  163.966595] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  163.967039] ath_pci: Unknown symbol ath_hal_detach
[  163.969046] ath_pci: Unknown symbol ath_hal_probe
[  163.971595] ath_pci: Unknown symbol ath_hal_init_channels
[  163.972569] ath_pci: Unknown symbol ath_hal_getwirelessmodes

---

### Post by spd106 on 2007-07-23
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/60938](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/60938) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It might be worth having a read through the bug report.

Basically it suggests running depmod in order to refresh the module dependencies list. After this it should work.

---

### Post by Mark_in_Hollywood on 2007-07-23
> **spd106 said:**
> **This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/60938](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/60938) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It might be worth having a read through the bug report.

Basically it suggests running depmod in order to refresh the module dependencies list. After this it should work.

The link you provide, shows that the kernel they are using is "old" compared to mine, e.g., their's is 17 and mine is 20. And they say it had been resolved as to that. My problem lies elsewhere. Thanks.

---

### Post by spd106 on 2007-07-23
Yes, you are right, but I still thought it might be worth trying.

I see you're already familiar with ndiswrapper, so it's not worth going over that again. It might be worth trying to build madwifi from the latest svn snapshot. Otherwise I don't know what else to suggest. Does it work from a live CD? Have you tried a Gutsy Tribe 3 desktop cd or some other distro like Knoppix or Fedora 7?

Another long shot would be to try madwifi-old.

---

### Post by Mark_in_Hollywood on 2007-07-24
The output of dmesg:

[  163.888136] wlan: 0.8.4.2 (0.9.3.1)
[  163.963545] ath_pci: Unknown symbol _ath_hal_attach
[  163.964019] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  163.965405] ath_pci: Unknown symbol ath_hal_computetxtime
[  163.966595] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  163.967039] ath_pci: Unknown symbol ath_hal_detach
[  163.969046] ath_pci: Unknown symbol ath_hal_probe
[  163.971595] ath_pci: Unknown symbol ath_hal_init_channels
[  163.972569] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[  164.005374] drivers/usb/class/usblp.c: usblp0: USB Bidirectional p

and 

usr/src

has nothing madwifi in it; which from reading another post, seems that madwifi-ng should be there. Meanwhile, I'm trying to learn how to install "from source when the kernel isn't mounted"

Any ideas?

---

### Post by Mark_in_Hollywood on 2007-07-25
Per another's advice, i'm reinstalling Feisty.

THREAD CLOSED.

---

