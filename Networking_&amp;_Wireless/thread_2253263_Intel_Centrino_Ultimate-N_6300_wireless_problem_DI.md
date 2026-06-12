---
title: "Intel Centrino Ultimate-N 6300 wireless problem: DISABLED"
date: 2014-11-18
forum: Networking &amp; Wireless
---

### Post by Prognatus on 2014-11-18
Hello all,

I'm stuck with this wireless problem ... I've searched the Internet for a couple of days and tried lots of things, but to no avail. I've also tried to search this forum but didn't find anything. If you know a thread with the solution I'd be happy!

I have a Dell Latitude E5500 laptop where I've replaced the stock wireless card with an Intel Centrino Ultimate-N 6300. Now, this card worked right after I installed it, with the old drivers for the stock card, but when I install a new linux version the Intel card stops working.

To see if there's an IRQ conflict I've disabled some things in the BIOS - parallell printer, internal modem, serial ports, and internal Bluetooth - but no luck there either.

I've tried the tips here: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices)

When I use the command **lshw -C network** it's listed but with the message DISABLED. Trying to enable it with the Network Manager doesn't work.

Here's the relevant output from the lshw command:

*-network DISABLED      
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 3e
       serial: 24:77:03:ad:36:9c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-39-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:f69fe000-f69fffff

It says it uses the latest firmware driver so that's loaded anyway.

Any ideas what to try now?

Thanks!

---

### Post by weatherman2 on 2014-11-18
What's the output of the terminal command

```

rfkill list all

```

?

If you have a hard block, look for a hardware switch or function key to enable the wireless card.

If you have a soft block, try

```

sudo rfkill unblock all

```

---

### Post by jeremy31 on 2014-11-18
If nothing else, look at the sticky post before posting in networking and wireless and use the wireless script to gather info on your system- it does conceal personal info and post the resulting wireless-info file

---

### Post by Prognatus on 2014-11-18
> **weatherman2 said:**
> What's the output of the terminal command

```

rfkill list all

```

?
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
	
> **weatherman2 said:**
> If you have a hard block, look for a hardware switch or function key to enable the wireless card.
Ok, I'll look for that then! Don't know where it can be, or why it's suddenly is off, but it's finally a lead. Thanks!

> **jeremy31 said:**
> If nothing else, look at the sticky post before posting in networking and wireless and use the wireless script to gather info on your system- it does conceal personal info and post the resulting wireless-info file
Thanks for the tip, I'll do that and return her with the data output.


Best,
Prognatus

---

### Post by Prognatus on 2014-11-20
Ok, here's the output of the wireless script from the sticky post. See below.

I'm also going to update the BIOS version on that laptop from version 15 to 19, but the BIOS file is in a Windows self-extracting program and I don't have Windows installed on that PC so I have to install that first (with VirtualBox), but before that I'll have to find a Windows CD to install ... which I don't have either. It aint easy ...


Edit: I actually had to buy a Windows XP Pro SP3 CD on eBay today, just for this BIOS upgrade operation ... It didn't cost much but it's annoying extra trouble. LOL


```

########## wireless info START ##########

Report from: 20 Nov 2014 10:22 CET +0100

Booted last: 19 Nov 2014 23:52 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	LinuxMint
Description:	Linux Mint 17.1 Rebecca
Release:	17.1
Codename:	rebecca

##### kernel ############################

Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

default

##### lspci #############################

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe [14e4:1680] (rev 10)
	Subsystem: Dell Device [1028:0263]
	Kernel driver in use: tg3

0c:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:422b] (rev 3e)
	Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN [8086:1101]
	Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 08ff:2810 AuthenTec, Inc. AES2810
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

##### lsmod #############################

iwldvm                232285  0 
mac80211              630653  1 iwldvm
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  1 dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe59:b58a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11616 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16676771 (16.6 MB)  TX bytes:645115 (645.1 KB)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.66
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Olstad]] (600 root)
[connection] id=Olstad | type=802-11-wireless
[802-11-wireless] ssid=Olstad
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Oslo (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     CC4D1BA11C1EF73A6ABDE53
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     C2D0F3DFCA289585C100E36
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

fstrim -v /
exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x1680 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x422b (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    5.607034] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[    5.617423] iwlwifi 0000:0c:00.0: irq 45 for MSI/MSI-X
[    5.628272] iwlwifi 0000:0c:00.0: Direct firmware load failed with error -2
[    5.628277] iwlwifi 0000:0c:00.0: Falling back to user helper
[    6.745975] iwlwifi 0000:0c:00.0: Direct firmware load failed with error -2
[    6.745980] iwlwifi 0000:0c:00.0: Falling back to user helper
[    6.915916] iwlwifi 0000:0c:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[    6.989646] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    6.989652] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    6.989655] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    6.989658] iwlwifi 0000:0c:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[    6.989878] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[    6.996618] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[    7.058097] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    7.306840] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```

---

### Post by jeremy31 on 2014-11-20
If you don't find a hardware switch you can try ```
sudo modprobe -r dell_wmi
``````
sudo rfkill unblock all
``` and see if wifi gets unblocked

---

### Post by Prognatus on 2014-11-20
Thanks, Jeremy, but it didn't work. Still blocked. I think the BIOS is a prime suspect since it's older than the wireless Intel card and therefore lacks support for the card. So I'll update the BIOS and report back here within a few days.

---

### Post by weatherman2 on 2014-11-20
For future reference, you can download a free (legal) evaluation version of Windows 7 that will work for 30 days without a product key, if you are just trying to update a BIOS.  ISOs are available on DigitalRiver I believe.  Google for it, you can find the legit downloads.

But I don't think you'll be able to update the BIOS through Windows on a virtual machine.  I certainly wouldn't attempt it that way - seems very risky.

---

### Post by chili555 on 2014-11-20
Please try a wild guess for old Chili:```
sudo modprobe -r dell_laptop 
sudo modprobe dell_laptop force_rfkill=Y
```Now does the switch or key combination work?```
rfkill list all
```

---

### Post by Prognatus on 2014-11-25
> **weatherman2 said:**
> For future reference, you can download a free (legal) evaluation version of Windows 7 that will work for 30 days without a product key, if you are just trying to update a BIOS.  ISOs are available on DigitalRiver I believe.  Google for it, you can find the legit downloads.
Thanks for the tip. I'll look for this then (my purchased Windows CD hasn't arrived yet).

> **weatherman2 said:**
> But I don't think you'll be able to update the BIOS through Windows on a virtual machine.  I certainly wouldn't attempt it that way - seems very risky.
Thanks, you may be right about that. I'll try to install Windows in a Dual Boot instead.

> **chili555 said:**
> Please try a wild guess for old Chili:```
sudo modprobe -r dell_laptop 
sudo modprobe dell_laptop force_rfkill=Y
```Now does the switch or key combination work?```
rfkill list all
```
Nope, sorry. Still no change.

The more I look into this, the more it looks like a BIOS issue. The blue WiFi LED indicator doesn't light up or blink at all during the boot process.

---

### Post by jeremy31 on 2014-11-25
This model has a switch, see if it works
[http://en.community.dell.com/support-forums/laptop/f/3518/t/19364845](http://en.community.dell.com/support-forums/laptop/f/3518/t/19364845)

---

### Post by Prognatus on 2014-11-26
You found it, Jeremy! That was it! Thank you, thank you.

The wireless worked as soon as I slided the switch. I didn't even know it was there and I must've touched it unvolunterily when I turned the PC around to open it when I installed the wireless card.

Thanks again. Much appreciated.

---

