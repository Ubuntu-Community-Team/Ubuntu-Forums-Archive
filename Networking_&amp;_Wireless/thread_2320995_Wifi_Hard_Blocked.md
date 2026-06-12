---
title: "Wifi Hard Blocked"
date: 2016-04-19
forum: Networking &amp; Wireless
---

### Post by Brij_Raj_Kishore on 2016-04-19
i have Hp 15-s005tx
I have recently installed ubuntu.
My "enable wifi" option is greyed out and blutooth is not working.
I have tried ```
rfkill list
``` the output is ```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```.
When I press my Wireless Button and then do ```
rfkill list
``` the output is ```
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
```.
My bluetooth is also not working.
I have tried Everything i found but it got me no use. Please Help.
Thanks In Advance

---

### Post by howefield on 2016-04-19
Hello and welcome to the forums. 

Thread moved to the "*Networking & Wireless*" forum.

---

### Post by Brij_Raj_Kishore on 2016-04-19
Thanks For Reply.
Sir I am new here and you said Thread moved to the "*Networking & Wireless*" forum. Please tell me what i should do next.

---

### Post by jeremy31 on 2016-04-19
Follow the instructions from [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) to use the wireless script, then post the results from the wireless-info.txt file

---

### Post by Brij_Raj_Kishore on 2016-04-20
I have done all the updation of the system,
My pc is connected via ethernet cable with working INTERNET only through it. ANd the etherenet network option is also greyed out and it is showing only wired connection.
The output file created after running code```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

is wireless-info.txt is attached.
Please find the attachment.

---

### Post by Brij_Raj_Kishore on 2016-04-21
My pc is connected via ethernet cable with working INTERNET only through  it. ANd the etherenet network option is also greyed out and it is  showing only wired connection. I have Triple Booted System  with Windows 10, Ubuntu And Kali LInux. In Windows 10 Wifi and bluetooth works but in ubuntu and kali linux the same problem persists. (This Code is created at the time when i had a dual boot system. I just intalled kali liunux)
The output file created after running code     Code:
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info 
```

And The Output Is : 
```

########## wireless info START ##########

Report from: 20 Apr 2016 19:32 IST +0530

Booted last: 20 Apr 2016 19:30 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-35-generic #40~14.04.1-Ubuntu SMP Fri Mar 18 16:37:35 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:2212]
    Kernel driver in use: r8169

0a:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
    Kernel driver in use: rt2800pci

##### lsusb #############################

Bus 003 Device 003: ID 0bda:5776 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

rt2800pci              16384  0 
rt2800mmio             20480  1 rt2800pci
rt2800lib              90112  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              53248  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              741376  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              552960  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:145360 (145.3 KB)  TX bytes:61538 (61.5 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search domain.name

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root       789     1  0 19:30 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

[[/etc/NetworkManager/system-connections/Hotspot]] (600 root)
[connection] id=Hotspot | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=brij-Compaq-15-Notebook-PC | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     3497B3BA82AA313725A7F23
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CBFDB4F3C912C17CDD96BE2
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     900056C9CD8078BA66893D3
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512

[rt2x00pci]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     F2A3F87D3DBCA573A6F6E05
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     879F1B5CBAAA72A33F68B51
depends:        rt2x00lib
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D31088D761A4CE666692F67
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1E79C1BE23A29358B904F24
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

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

[/etc/modprobe.d/hp.conf]
options hp_wmi wireless=1

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x3290 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   17.381729] r8169 0000:08:00.0 eth0: link down (repeated 2 times)
[   17.381901] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.046202] r8169 0000:08:00.0 eth0: link up
[   19.046213] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

---

### Post by jeremy31 on 2016-04-21
What happens if you disable wireless in Windows and then boot into Ubuntu?

---

### Post by Brij_Raj_Kishore on 2016-04-21
i have activated airplane mode in my windows and then shut down it and then restart my pcin ubuntu but nothing changed here. And one thing i want to tell my all 3 OS are in UEFI.
Windows and Ubuntu in Secure boot on and kali linux 2 in secure boot off.

---

### Post by jeremy31 on 2016-04-21
What other modules are loaded, please post the result for ```
lsusb
```

---

### Post by Brij_Raj_Kishore on 2016-04-21
The output of the following code 
```
lsusb
``` is as follows :
```
Bus 003 Device 003: ID 0bda:5776 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 3938:1031  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by jeremy31 on 2016-04-22
Go into BIOS and choose reset to defaults.  See if wifi works in Ubuntu

---

### Post by Brij_Raj_Kishore on 2016-04-23
No changes occur.

---

### Post by jeremy31 on 2016-04-24
You could try the tape trick to mask a pin on the wifi card to fix the block
[https://youtu.be/yzAKcmlaH1M](https://youtu.be/yzAKcmlaH1M)

---

### Post by Brij_Raj_Kishore on 2016-04-25
Awesome Sir!  Thanks. Wifi problem is solved but the bluetooth is now also not working.

---

### Post by jeremy31 on 2016-04-25
> **Brij_Raj_Kishore said:**
> Awesome Sir!  Thanks. Wifi problem is solved but the bluetooth is now also not working.

Unfortunately the bluetooth might never work.  The last bug report that I read about that bluetooth said that is was some proprietary design and the manufacturer wasn't going to help with any code

---

### Post by Brij_Raj_Kishore on 2016-04-25
Thanks Sir. Thank you very much for the help. It meant a lot because I was ever stucked in this problem.

---

