---
title: "Ubuntu 18.04 new install, no ethernet or wifi"
date: 2018-08-18
forum: Networking &amp; Wireless
---

### Post by gshockxc2 on 2018-08-18
I completed a new install on a Dell Vostro 1520, and everything seems to be working fine, except for the network adapter.  I don't have Ethernet or WiFi.  It's an old laptop, so I figured I was missing a driver.  I did some research and found the post by bapoumba (thanks for this, it's very helpful).  The thread is closed, so I'm posting here for advice/suggestions.  Thank you in advance for any help you can offer.

I followed the instructions here by bapoumba:
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

The results of my text file are: 
```

########## wireless info START ##########

Report from: 17 Aug 2018 18:31 CDT -0500

Booted last: 17 Aug 2018 00:00 CDT -0500

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:02bc]
    Kernel driver in use: r8169

0e:00.0 Network controller [0280]: Broadcom Limited BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0718:063d Imation Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

dell_laptop            20480  0
dell_smbios            16384  2 dell_laptop,dell_smbios_smm
b43                   413696  0
bcma                   57344  1 b43
mac80211              778240  1 b43
cfg80211              622592  2 b43,mac80211
ssb                    57344  1 b43
video                  40960  2 dell_laptop,i915

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp8s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp8s0' [IF1]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

enp8s0    no wireless extensions.

##### route #############################

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       630     1  0 18:24 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp8s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp8s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp8s0    Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode42.fw
firmware:       b43/ucode40.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode30_mimo.fw
firmware:       b43/ucode33_lcn40.fw
firmware:       b43/ucode29_mimo.fw
firmware:       b43/ucode26_mimo.fw
firmware:       b43/ucode25_mimo.fw
firmware:       b43/ucode25_lcn.fw
firmware:       b43/ucode24_lcn.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode16_lp.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     9F0109CA3DBCBC74B77ACE8
depends:        mac80211,ssb,bcma,cfg80211
retpoline:      Y
intree:         Y
name:           b43
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F4DB57748318105D28C557A
depends:        
retpoline:      Y
intree:         Y
name:           bcma
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.15.0-20-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-20-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     12D8BAB8F43573B88998E25
depends:        
retpoline:      Y
intree:         Y
name:           ssb
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   13.758539] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[   14.075996] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   14.120787] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   14.120802] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2062, Revision 2, Version 0
[   14.137570] b43 ssb0:0: Direct firmware load for b43/ucode15.fw failed with error -2 (repeated 2 times)
[   14.137601] b43 ssb0:0: Direct firmware load for b43-open/ucode15.fw failed with error -2 (repeated 2 times)
[   14.137614] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   14.137618] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   14.137620] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   25.014728] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[   25.117482] r8169 0000:08:00.0 enp8s0: link down
[   25.117692] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready

########## wireless info END ############


```

---

### Post by jeremy31 on 2018-08-18
[https://ubuntuforums.org/showthread.php?t=2316978](https://ubuntuforums.org/showthread.php?t=2316978) should get wifi working

---

### Post by kc1di on 2018-08-18
Hello gshockxc2  and Welcome to Ubuntu forums.

Did you have Ethernet connection before you followed that guide?  Because for your wireless card it looks like you've installed the wrong driver.
the Broadcom 4312 should use the wl driver you have b43 installed.  

Since you have no internet at this point I would do a new install.  
When you get the live usb/dvd running before you install anything go to a terminal and type the following 
```
sudo apt install bcmwl-kernel-source
``` It will load the correct driver for your wireless card.  makesure it works then do the install.
.
once installed you will need to have a temporary ethernet cable connection and type the same command again get wifi working and you can disconnect the cable. 
If you have no access to Ethernet then it can be loaded from the live usb stick  by copying some files and installing them manually.
follow the instructions on[ this linuxmint]("https://forums.linuxmint.com/viewtopic.php?t=250094") page. it will work in ubuntu also. Good luck.

---

### Post by kc1di on 2018-08-18
> **jeremy31 said:**
> [https://ubuntuforums.org/showthread.php?t=2316978](https://ubuntuforums.org/showthread.php?t=2316978) should get wifi working

Hi Jeremy31,

I have the same card 4312 in two machines,  and I can say that the b43 driver though it may work is not as good with this card as the sta/wl driver.  In fact the recommended driver almost always comes up as bcmwl for this card.  b43 is intermittent at least on my dell machines.  Dell ships with sta driver also. for this card. 

Just my opinion.  -Dave

---

### Post by gshockxc2 on 2018-08-18
> **jeremy31 said:**
> [https://ubuntuforums.org/showthread.php?t=2316978](https://ubuntuforums.org/showthread.php?t=2316978) should get wifi working

Indeed, it did.  I still don't have an ethernet connection.  I recall that I had this problem previously with this laptop.  I had originally installed Ubuntu (17.04, I think), and then jumped over to Kubuntu for a while.  Recently, I switched back, but did a clean install of 18.04.  However, it's been so long that I don't recall what the fix was.  Now that I have WiFi, I'll update the software sources and download the latest packages to make sure I'm up to date.

Any other suggestions to troubleshoot?

Thanks Jeremy.

---

### Post by jeremy31 on 2018-08-18
The ethernet might work after ```
sudo apt update && sudo apt install r8168-dkms
```
Reboot

---

### Post by gshockxc2 on 2018-08-18
> **kc1di said:**
> Hello gshockxc2  and Welcome to Ubuntu forums.

Did you have Ethernet connection before you followed that guide?  Because for your wireless card it looks like you've installed the wrong driver.
the Broadcom 4312 should use the wl driver you have b43 installed.  

I did not.  It hasn't worked since I completed the install.

> Since you have no internet at this point I would do a new install.  
This was a new install, but I could do it again, if I had to ... though, I'd prefer not.  ;-)

> When you get the live usb/dvd running before you install anything go to a terminal and type the following 
```
sudo apt install bcmwl-kernel-source
``` It will load the correct driver for your wireless card.  makesure it works then do the install.

once installed you will need to have a temporary ethernet cable connection and type the same command again get wifi working and you can disconnect the cable. 
If you have no access to Ethernet then it can be loaded from the live usb stick  by copying some files and installing them manually.
follow the instructions on[ this linuxmint]("https://forums.linuxmint.com/viewtopic.php?t=250094") page. it will work in ubuntu also. Good luck.

Now that I have WiFi, (sorry for the dumb question) is there a separate driver for Ethernet?  It's the same card, right, so the b43 driver should work for both.  What would cause WiFi to work, but Ethernet not?

---

### Post by gshockxc2 on 2018-08-18
Using my wifi connection, I selected the best server and updated all the  packages.  Not unexpectedly, it must have updated the driver for the  Broadcom network adapter, so I lost my wifi again.  I re-ran Jeremy's  procedure, and wifi is working again.  How can I prevent the Update  Manager from overwriting this driver each time it runs?

Thanks for your help.

---

### Post by jeremy31 on 2018-08-18
Post results for ```
dkms status
```
Does [https://ubuntuforums.org/showthread.php?t=2398843&p=13793094#post13793094](https://ubuntuforums.org/showthread.php?t=2398843&p=13793094#post13793094) do anything for the ethernet?

---

### Post by gshockxc2 on 2018-08-18
dkms status

```

r8168, 8.045.08, 4.15.0-20-generic, x86_64: installed

```

Doesn't seem to affect the Ethernet, but I will reboot and see what happens.

---

### Post by ubucat2 on 2018-08-31
Some weeks ago I upgraded the second PC to Ubuntu 18.04, after the installation had worked fine on the first one. This second PC is a Gigabyte F2A88X-D3H with BIOS 08-19-2013, running ubuntu 18.04 - 4.15.0-30-generic ... and has an on-board ethernet RTL8111/8168/8411 PCI .... lsmod |grep 816 --> r8169 - 86016 - 0, mii - 16384 - 1 r8169.
The day before yesterday I could not connect to the Web. I could not even ping the router. I checked everything, but did not find a clue. At last I disabled the onboard ethernet and inserted a PCI-Network-Card. Same RTL-Chip, same driver. Network was now indicated as up, but the symbol on the top-line showed a question mark in the center of the three squares, ping didn't work, and no connection was possible.
After a lot of reading I discovered the tool mii-diag_2.11-3_amd64.deb, which I installed with sudo dpkg ... and ran as sudo mii-diag -v enp1s0. Well, I still can't believe it, but after that the network was suddenly up, and I write this message on this very PC. The previously upgraded PC runs  18.04 - 4.15.0-23 with the same ethernet hardware and drivers.

---

### Post by ubucat2 on 2018-09-03
Just updated the  Gigabyte F2A88X-D3H to 4.15.0.33 and network is still up. Considering that I had 4.15.0.30 running flawlessly for several weeks before the network out of the blue fell apart, the bug-hunt will be somewhat demanding, because a simple go-nogo-test will not suffice, and it is by no means clear, where the bug sits - in the Realtek chip, in the driver, or in the OS. For me, applying mii-diag was quite satisfying to regain network functionality.

---

### Post by cjklmnop on 2019-07-22
> **ubucat2 said:**
> Some weeks ago I upgraded the second PC to Ubuntu 18.04, after the installation had worked fine on the first one. This second PC is a Gigabyte F2A88X-D3H with BIOS 08-19-2013, running ubuntu 18.04 - 4.15.0-30-generic ... and has an on-board ethernet RTL8111/8168/8411 PCI .... lsmod |grep 816 --> r8169 - 86016 - 0, mii - 16384 - 1 r8169.
The day before yesterday I could not connect to the Web. I could not even ping the router. I checked everything, but did not find a clue. At last I disabled the onboard ethernet and inserted a PCI-Network-Card. Same RTL-Chip, same driver. Network was now indicated as up, but the symbol on the top-line showed a question mark in the center of the three squares, ping didn't work, and no connection was possible.
After a lot of reading I discovered the tool mii-diag_2.11-3_amd64.deb, which I installed with sudo dpkg ... and ran as sudo mii-diag -v enp1s0. Well, I still can't believe it, but after that the network was suddenly up, and I write this message on this very PC. The previously upgraded PC runs  18.04 - 4.15.0-23 with the same ethernet hardware and drivers.

Hello, i have the same problem and can not use or see my ethernet port on my laptop despite wifi is working, after reinstalling ubuntu desktop. Can you be a little bit more specific how you solved this problem after installing the mii-diag_2.11-3_amd64.deb? the command  sudo mii-diag -v enp1s0 does returns error: SIOCGMIIPHY on enp1s0 failed: No such device .

thank you!

---

