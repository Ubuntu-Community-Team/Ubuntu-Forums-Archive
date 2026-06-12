---
title: "WiFi card not enabled on Elyssa"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by marianogedisman on 2008-11-17
Hello all,

I have Mint Elyssa and I can see the net5211 windows driver on the system (HAL and support for Atheros LAN cards is checked on the Hardware drivers window) however, I cannot see it on the Network settings window.  

Quite weird, since I was able to install it with no problem before, but I forgot how I did it!  

Help will be much appreciated.

Cheers. :)

---

### Post by pytheas22 on 2008-11-17
I don't use Mint but assuming that it's pretty much the same as Ubuntu (I think Mint is just Ubuntu with more proprietary stuff included by default?), if you post the output of the following commands I'll try to figure out what's wrong:
```

lshw -C Network
lspci -nn
dmesg | grep -e ndis -e wlan -e ath
sudo iwlist scan
```

---

### Post by marianogedisman on 2008-11-17
Right away!

```
marianox@compax ~ $ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:64:d9:8f
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.2 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

marianox@compax ~ $ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7000M (rev a2) [10de:0533] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
marianox@compax ~ $ 


marianox@compax ~ $ dmesg | grep -e ndis -e wlan -e ath
[  586.824060] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[ 1182.614775] wlan: 0.9.4
[ 1182.644426] ath_pci: 0.9.4

marianox@compax ~ $ sudo iwlist scan
[sudo] password for marianox: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

marianox@compax ~ $ 
```

---

### Post by pytheas22 on 2008-11-17
Please try following the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=798485") to compile the latest version of madwifi from source.  Then reboot.  This will hopefully do the trick.

If the wireless still doesn't work after rebooting, please post the output of:
```

lshw -C Network
modinfo ath_pci
dmesg | grep -e ath -e wlan
lsmod | grep ath
sudo iwlist scan
```

---

### Post by marianogedisman on 2008-11-18
Jesus Christ! Last time Mint didn't give me so many problems, I just installed the Windows drivers and that's it! I wonder why is this happening, because it's the same CD...

Here you have:
```
marianox@compax ~ $ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:64:d9:8f
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.2 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
marianox@compax ~ $  

marianox@compax ~ $ modinfo ath_pci
filename:       /lib/modules/2.6.24-16-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        svn r3873
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     168B1DC259AAD65A2454E21
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
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
vermagic:       2.6.24-16-generic SMP mod_unload 586 
parm:           beacon_cal:int
parm:           countrycode:Override default country code.  Default is 0. (int)
parm:           maxvaps:Maximum VAPs.  Default is 4. (int)
parm:           outdoor:Enable/disable outdoor use.  Default is 0. (int)
parm:           xchanmode:Enable/disable extended channel mode. (int)
parm:           rfkill:Enable/disable RFKILL capability.  Default is 0. (int)
parm:           hal_tpc:Disables manual per-packet transmit power control and lets this be managed by the HAL.  Default is OFF. (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           intmit:Enable interference mitigation by default.  Default is 0. (int)
parm:           ath_debug:Load-time driver debug output enable (int)
parm:           ieee80211_debug:Load-time 802.11 debug output enable (int)
marianox@compax ~ $ ~

marianox@compax ~ $ modinfo ath_pci
filename:       /lib/modules/2.6.24-16-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        svn r3873
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     168B1DC259AAD65A2454E21
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
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
vermagic:       2.6.24-16-generic SMP mod_unload 586 
parm:           beacon_cal:int
parm:           countrycode:Override default country code.  Default is 0. (int)
parm:           maxvaps:Maximum VAPs.  Default is 4. (int)
parm:           outdoor:Enable/disable outdoor use.  Default is 0. (int)
parm:           xchanmode:Enable/disable extended channel mode. (int)
parm:           rfkill:Enable/disable RFKILL capability.  Default is 0. (int)
parm:           hal_tpc:Disables manual per-packet transmit power control and lets this be managed by the HAL.  Default is OFF. (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           intmit:Enable interference mitigation by default.  Default is 0. (int)
parm:           ath_debug:Load-time driver debug output enable (int)
parm:           ieee80211_debug:Load-time 802.11 debug output enable (int)
marianox@compax ~ $ ~

marianox@compax ~ $ dmesg | grep -e ath -e wlan
[   35.661432] ath_pci: HAL doesn't support MAC revision 0xe2
marianox@compax ~ $ 

marianox@compax ~ $ lsmod | grep ath
ath_pci               248376  0 
wlan                  235504  1 ath_pci
ath_hal               252512  1 ath_pci
marianox@compax ~ $ 

marianox@compax ~ $ sudo iwlist scan
[sudo] password for marianox: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

marianox@compax ~ $ 

```


Thanks so much!!

---

### Post by pytheas22 on 2008-11-18
If you installed the driver using that script, it doesn't seem to have done anything.  However, that script would have installed madwifi, a native driver, not a Windows driver.  If you want to go the Windows route, you should make sure first that ndiswrapper is installed by typing:

```
sudo apt-get install ndiswrapper*
```

Then blacklist the native Linux driver so it won't interfere with ndiswrapper:

```
echo 'blacklist ath_pci' | sudo tee -a /etc/modules
```

Then install your Windows .inf file into ndiswrapper, and reboot.  This should do it.  If not, what is the output of:
```

dmesg | grep -e wlan -e ndis
lshw -C Network
ndiswrapper -l
uname -m
```

Also, where are you getting the Windows .inf file from?  Are you positive it's the right one?

---

### Post by marianogedisman on 2008-11-18
Thanks!

Should I change anything on the propietary drivers? Both *Atheros HAL* and *Support for Atheros 802.11 Wireless LAN cards* are checked.

---

### Post by marianogedisman on 2008-11-18
The driver's /usr/lib/linuxmint/mintWifi/drivers/i386/Atheros_AR5007eg/net5211.inf and it was there since I've installed Linux. If I'm not wrong is the same one I've used when I had the same previous Linux install.

Cheers.

---

### Post by marianogedisman on 2008-11-18
Well, I rebooted the system and nothing... Geez, I'm thinking of re-installing Linux.

---

### Post by pytheas22 on 2008-11-18
Try running:

```
sudo ndiswrapper -i /usr/lib/linuxmint/mintWifi/drivers/i386/Atheros_AR5007eg/net5211.inf
```

The driver may be there, but ndiswrapper may not know about it.  I'm not sure how Mint works, but on Ubuntu, just having the .inf in that directory wouldn't make the card work.

> Should I change anything on the propietary drivers? Both Atheros HAL and Support for Atheros 802.11 Wireless LAN cards are checked. 

Yes, you should uncheck those boxes if you want to use ndiswrapper+Windows drivers.

If you still can't get it to work, please post the output of these commands, which will help to give a more precise idea of what's wrong:
```

dmesg | grep -e wlan -e ndis
lshw -C Network
ndiswrapper -l
uname -m
```

---

### Post by marianogedisman on 2008-11-18
HAHA, I'm laughing in despair! It's either laugh or cry for me!:confused:

](*,)

I just don't understand why Linux recognises the driver and yet I can't see the WLAN card on the manual network config. list!

Is there a way to un-unclaim the wifi card?

Here's the code: (thanks so much!)

```
marianox@compax ~ $ dmesg | grep -e wlan -e ndis
(DIDN'T SHOW ANYTHING)

marianox@compax ~ $ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:64:d9:8f
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.2 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
marianox@compax ~ $ 

marianox@compax ~ $ ndiswrapper -l
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)
marianox@compax ~ $ uname -m
i686
marianox@compax ~ $ 


```

---

### Post by marianogedisman on 2008-11-18
And I don't know how to use the alternative "ath_pci" driver. Someone kill me please!

---

### Post by pytheas22 on 2008-11-18
hmmm, ndiswrapper detects the device, which is good.  It's possible that the ndiswrapper module is simply not loaded.  Try typing:

```
sudo modprobe -r ndiswrapper ath_pci ath9k ath5k
sudo modprobe ndiswrapper
```

Then wait a few seconds and see if the wireless interface pops up.

If not, please post the output of these commands so that we can figure out why ndiswrapper doesn't want to work:
```

dmesg | grep -e ndis -e wlan
sudo iwlist scan
lsmod | grep ndis
```

Don't worry about ath_pci for now.  If you use ndiswrapper, you can ignore ath_pci.

---

### Post by marianogedisman on 2008-11-18
GENIUS!!

```
marianox@compax ~ $ sudo modprobe -r ndiswrapper ath_pci ath9k ath5k
[sudo] password for marianox: 
FATAL: Module ath9k not found.
marianox@compax ~ $ sudo modprobe ndiswrapper
marianox@compax ~ $ 

```

After this, the Wifi interface popped up! :D
I'm not able to test it now though, but I have Wifi at work (the main reason why I need it) and I will let you know. Man I owe you BIG TIME!

Thanks so much!
:popcorn:

---

### Post by pytheas22 on 2008-11-19
Glad that did it.  It may not work automatically after rebooting, however.  To solve this problem, run this command once:
```

echo ndiswrapper | sudo tee -a /etc/modules
```

Thereafter, it should work automatically.  If not, please let me know.

---

### Post by marianogedisman on 2008-11-19
Yup! It's working! I'm at work now. Thanks so much pytheas22!! =)

---

