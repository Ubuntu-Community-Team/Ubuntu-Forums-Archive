---
title: "No ethernet connection"
date: 2021-01-26
forum: Networking &amp; Wireless
---

### Post by visiblepotato on 2021-01-26
Ubuntu won't recognize my ethernet. I have no wifi in my PC so this means I have no internet connection.

---

### Post by CelticWarrior on 2021-01-26
Welcome.

Please post the results of the following commands:
```
[COLOR=#000000][FONT=&quot]sudo lshw -C network; lsb_release -a; uname -a[/FONT][/COLOR]
```[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]

---

### Post by TheFu on 2021-01-26
If you have a chicken-egg problem with lshw not already existing, **either** of these commands should provide some network device information:
```
lspci -vk |egrep --after-context=8 'Ethernet|Network'
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/'
```
The first is probably easier to type, but I'd just save the commands to a flash drive connect that do the Ubuntu system, then copy/paste the commands into a terminal or use normal output redirection.

The output ... copy paste that into a new text file, move it back to the internet-connected system, and post here ... wrapped in "code tags" so it is readable.
[https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) explains how to do 'code tags' in these forums.

BTW, running these commands may be even easier and work if you boot into a "Try Ubuntu" environment off the USB flash drive used to perform the installation. Often, networking is fine in that environment even if it isn't ok post-install.  The "Try Ubuntu" environment can be used to fix almost any problems with any Ubuntu install, so it is worth knowing and having handy.

---

### Post by vvons on 2021-01-31
I am having same problem, ethernet is not detected in ubuntu 20.04.1. It worked fine in windows.
output of above commads is :
mohit@mohit--System:~$ sudo lshw -C network
  *-network                 
       description: Wireless interface
       product: Centrino Wireless-N 1030 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 34
       serial: bc:77:37:28:64:41
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.8.0-41-generic firmware=18.168.6.1 6000g2b-6.ucode ip=192.168.1.8 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:36 memory:f1a00000-f1a01fff
mohit@mohit--System:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal
mohit@mohit--System:~$ uname -a
Linux mohit--System 5.8.0-41-generic #46~20.04.1-Ubuntu SMP Mon Jan 18 17:52:23 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
mohit@mohit--System:~$ lspci -vk |egrep --after-context=8 'Ethernet|Network'
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 36
    Memory at f1a00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
mohit@mohit--System:~$ lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/'
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 36
    Memory at f1a00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

---

### Post by praseodym on 2021-02-07
> ```
lspci -vk |egrep --after-context=8 'Ethernet|Network'
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] (rev 34)
Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN
Flags: bus master, fast devsel, latency 0, IRQ 36
Memory at f1a00000 (64-bit, non-prefetchable) [size=8K]
Capabilities: <access denied>
Kernel driver in use: iwlwifi
Kernel modules: iwlwifi
```
Obviously, you have wifi, bot no ethernet?! Please show
```
lspci -nnk
iwconfig
rfkill list
dmesg | egrep 'firm|iwl'
sudo iwlist scan
```

---

