---
title: "Replaced my wifi drivers, now wireless in Windows doesn't work anymore"
date: 2017-10-12
forum: Networking &amp; Wireless
---

### Post by iormungand on 2017-10-12
Dual booting with Windows 10. I've only installed Ubuntu 14.04 like last week. So basically the issue started with Ubuntu not having wireless internet. I found the issue described in this topic [https://askubuntu.com/questions/763080/no-wifi-in-qualcom-atheros-ubuntu-16-04-acer-aspire-e-15](https://askubuntu.com/questions/763080/no-wifi-in-qualcom-atheros-ubuntu-16-04-acer-aspire-e-15)

I could follow all the commands up until:

```
sudo mv firmware-5.bin_WLAN.TF.1.0-00267-1  firmware-5.bin
```

Since it couldn't find the file/directory. I looked further. I found this topic with a similar problem [https://ubuntuforums.org/showthread.php?t=2308578](https://ubuntuforums.org/showthread.php?t=2308578)

I executed these commands

```
sudo rm -r /lib/firmware/ath10k
sudo cp -r ath10k-firmware/ /lib/firmware/ath10k/
sudo mv /lib/firmware/ath10k/QCA6174/hw2.1/firmware-5.bin_SW_RM.1.1.1-00157-QCARMSWPZ-1 /lib/firmware/ath10k/QCA6174/hw2.1/firmware-5.bin
```

Oh now I have all the files in that git repository. Wireless still didn't work but I rebooted and went on my Windows. 

**PROBLEM:**

And I see now that after doing sudo rm and deleting my initial configuration I somehow messed up my wireless on the Windows side. Now I can't go wireless and it doesn't even detect my wireless adapter in the device manager, even when I scan. I tried re-installing the wireless adapter but nothing changes. Now I'm stuck without wireless. I'd rather have Windows wireless working than Ubuntu since that's the OS I use. But perhaps fixing Ubuntu's will fix Windows'? Long shot.

Maybe that this information helps

```
lspci -nnk | grep -iA2 net; dmesg | grep ath10k
    01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3854]
    Kernel driver in use: r8169
    02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Lenovo Device [17aa:4035]
    Kernel driver in use: ath10k_pci
    [   12.786686] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
    [   13.025131] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
    [   15.534724] ath10k_pci 0000:02:00.0: firmware crashed! (uuid bc1e1d0e-1081-4997-af24-68e082737f2e)
    [   15.534730] ath10k_pci 0000:02:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 17aa:4035) fw WLAN.TF.1.0-00002-QCATFSWPZ-5 fwapi 5 bdapi 2 htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
    [   15.534732] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
    [   15.536863] ath10k_pci 0000:02:00.0: firmware register dump:
    [   15.536865] ath10k_pci 0000:02:00.0: [00]: 0x05020000 0x00000000 0x000A091C 0x00000009
    [   15.536866] ath10k_pci 0000:02:00.0: [04]: 0x000A091C 0x00050730 0x00000010 0x00000003
    [   15.536868] ath10k_pci 0000:02:00.0: [08]: 0x00000001 0x004173B0 0x00400000 0x00421370
    [   15.536869] ath10k_pci 0000:02:00.0: [12]: 0x00000009 0x00000000 0x00952CD0 0x00952CE6
    [   15.536870] ath10k_pci 0000:02:00.0: [16]: 0x00952CC4 0x00914761 0x00000000 0x00000000
    [   15.536871] ath10k_pci 0000:02:00.0: [20]: 0x400A091C 0x0040EA28 0x00419980 0x004212E8
    [   15.536872] ath10k_pci 0000:02:00.0: [24]: 0x800A0D0A 0x0040EA88 0xFFFFFFFF 0xC00A091C
    [   15.536874] ath10k_pci 0000:02:00.0: [28]: 0x800A0614 0x0040EAA8 0x0041FA10 0x00420170
    [   15.536875] ath10k_pci 0000:02:00.0: [32]: 0x80910829 0x0040EAC8 0x00000000 0x00400600
    [   15.536876] ath10k_pci 0000:02:00.0: [36]: 0x80910927 0x0040EB08 0x00000000 0xFFF08041
    [   15.536877] ath10k_pci 0000:02:00.0: [40]: 0x8091114E 0x0040EB28 0x00400000 0x00400600
    [   15.536878] ath10k_pci 0000:02:00.0: [44]: 0x8091122D 0x0040EB48 0x00000000 0x00400600
    [   15.536879] ath10k_pci 0000:02:00.0: [48]: 0x40910024 0x0040EB78 0x0040AB98 0x0040AB98
    [   15.536880] ath10k_pci 0000:02:00.0: [52]: 0x00000000 0x0040EB98 0x009BB001 0x00040020
    [   15.536882] ath10k_pci 0000:02:00.0: [56]: 0x8091114E 0x0040EB28 0x00400000 0x00400600
    [   16.523695] ath10k_pci 0000:02:00.0: failed to receive control response completion, polling..
    [   17.523512] ath10k_pci 0000:02:00.0: ctl_resp never came in (-110)
    [   17.523515] ath10k_pci 0000:02:00.0: failed to connect to HTC: -110
    [   17.524004] ath10k_pci 0000:02:00.0: could not init core (-110)
    [   17.524034] ath10k_pci 0000:02:00.0: could not probe fw (-110)
    [   17.535587] ath10k_pci 0000:02:00.0: cannot restart a device that hasn't been started
```


My wireless-info.text. So right now in ath10k I have all the kvalo folders (8?). But before I did that I remember vaguely having only 3 folders? One of them being 9377. Matching the module infos

```
########## wireless info START ##########

Report from: 12 Oct 2017 14:12 CEST +0200

Booted last: 12 Oct 2017 13:49 CEST +0200

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.4.0-97-generic #120~14.04.1-Ubuntu SMP Wed Sep 20 15:53:13 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3854]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Lenovo Device [17aa:4035]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0cf3:e360 Atheros Communications, Inc. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 5986:06b1 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

ath10k_pci             40960  0 
ath10k_core           315392  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              733184  1 ath10k_core
cfg80211              561152  3 ath,mac80211,ath10k_core
ideapad_laptop         28672  0 
sparse_keymap          16384  1 ideapad_laptop
mxm_wmi                16384  1 nouveau
wmi                    20480  3 ideapad_laptop,mxm_wmi,nouveau
video                  40960  3 i915_bpo,ideapad_laptop,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:10.134.217.108  Bcast:10.134.217.255  Mask:255.255.254.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:512 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:305217 (305.2 KB)  TX bytes:63344 (63.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3783 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3783 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:301843 (301.8 KB)  TX bytes:301843 (301.8 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.134.216.1    0.0.0.0         UG    0      0        0 eth0
10.134.216.0    0.0.0.0         255.255.254.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1038     1  0 13:49 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.134.217.108
    Prefix:          23 (255.255.254.0)
    Gateway:         10.134.216.1

    DNS:             8.8.8.8

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

##### iw reg get ########################

Region: Europe/Brussels (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.4.0-97-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     5F58F07B355E62C1D93DF6E
depends:        ath10k_core
intree:         Y
vermagic:       4.4.0-97-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.4.0-97-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     FD7C356A1DE1780566F2B10
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-97-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.4.0-97-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-97-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-97-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     066D9B501A63401DBFCBF56
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-97-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-97-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     074D104BC98456ECCF3395E
depends:        
intree:         Y
vermagic:       4.4.0-97-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N

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

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   10.212695] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   13.110515] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 0136b74b-6713-4c71-885a-333bbba2f506)
[   13.110522] ath10k_pci 0000:02:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 17aa:4035) fw WLAN.TF.1.0-00002-QCATFSWPZ-5 fwapi 5 bdapi 2 htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[   13.110523] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   13.112656] ath10k_pci 0000:02:00.0: firmware register dump:
[   13.112658] ath10k_pci 0000:02:00.0: [00]: 0x05020000 0x00000000 0x00A0F774 0x00000000
[   13.112659] ath10k_pci 0000:02:00.0: [04]: 0x00A0F774 0x00060130 0x00000010 0xFFFFE000
[   13.112660] ath10k_pci 0000:02:00.0: [08]: 0x0042136C 0x00420660 0x00400000 0x00400000
[   13.112662] ath10k_pci 0000:02:00.0: [12]: 0x00000000 0x00000000 0x00952CD0 0x00952CE6
[   13.112663] ath10k_pci 0000:02:00.0: [16]: 0x00000002 0x01010101 0x00000003 0x0000000A
[   13.112664] ath10k_pci 0000:02:00.0: [20]: 0x00000328 0x00429880 0x009A37AC 0x00000032
[   13.112665] ath10k_pci 0000:02:00.0: [24]: 0x800A0D0A 0x0040EA88 0x00420170 0x004173B0
[   13.112666] ath10k_pci 0000:02:00.0: [28]: 0x00401F64 0x00401F68 0x00000000 0x00417550
[   13.112668] ath10k_pci 0000:02:00.0: [32]: 0x00401FC0 0x5BBFDF74 0x00406F55 0x00000003
[   13.112669] ath10k_pci 0000:02:00.0: [36]: 0x800A0907 0x00000001 0x0000085B 0x339011B2
[   13.112670] ath10k_pci 0000:02:00.0: [40]: 0x0000FFFE 0x0000000A 0x009BFE28 0x009BE0DC
[   13.112671] ath10k_pci 0000:02:00.0: [44]: 0x800A0D0A 0x0040EA88 0x00420170 0x004173B0
[   13.112672] ath10k_pci 0000:02:00.0: [48]: 0x00400000 0x00400000 0x00000001 0xFFFFFFFF
[   13.112673] ath10k_pci 0000:02:00.0: [52]: 0x800A0614 0x0040EAA8 0x0041FA10 0x00420170
[   13.112674] ath10k_pci 0000:02:00.0: [56]: 0x00400000 0x00421370 0x00419980 0x004212E8
[   14.100132] ath10k_pci 0000:02:00.0: failed to receive control response completion, polling..
[   15.104277] ath10k_pci 0000:02:00.0: ctl_resp never came in (-110)
[   15.104280] ath10k_pci 0000:02:00.0: failed to connect to HTC: -110
[   15.104733] ath10k_pci 0000:02:00.0: could not init core (-110)
[   15.104764] ath10k_pci 0000:02:00.0: could not probe fw (-110)
[   15.116130] ath10k_pci 0000:02:00.0: cannot restart a device that hasn't been started
[   20.242978] r8169 0000:01:00.0 eth0: link down
[   20.243031] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1187.792247] r8169 0000:01:00.0 eth0: link up
[ 1187.792273] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############
```

---

### Post by jeremy31 on 2017-10-13
Try the new firmware in the 16.04 repositories
```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157.12_all.deb
sudo dpkg -i linux-firmware_1.157.12_all.deb
```
Shutdown and try a cold boot

---

### Post by iormungand on 2017-10-13
Forgot to reply here but I "solved" it last night. I removed the kvalo files again and this time I used the ath10k files of the wkennington repository. My ubuntu wireless works now. But my primary problem still persists. Windows wireless doesn't work, it can't even detect the network adapter in device manager even after scanning. I'm not sure if Windows-related problems are relevant.

However I am 100% sure that after deleting my initial ath10k folder in ubuntu my wireless in Windows disappeared. Anyone know why? I had no idea that what you did in ubuntu also affected windows to such extent.

---

### Post by ajgreeny on 2017-10-13
I do not see how anything you have done for your wifi connection in Ubuntu could have affected the Windows connection, so I suspect the two problems are not related.

---

### Post by iormungand on 2017-10-13
I was constantly switching between Ubuntu and Windows (shutdown / boot, shutdown / boot). I went back to Windows (Windows wifi was still working then) to take a phone picture of my wireless adapter info, at this point I already did the commands of the first link in OP post so the problem wouldn't lie there. Then afterwards I went back to Ubuntu to execute the remove & replace commands (3 lines). It didn't work and I went back to Windows. Then wifi there suddenly doesn't work. I changed nothing with settings on the Windows side.

Maybe while I wasn't looking Windows Updates, while doing boots, bugged something out. However I have this laptop for over a year and I've never had problems with my wireless on Windows. It'd be one hell of a coincidence that the moment I fiddle with Ubuntu's lib ath10k folder that my Windows wireless starts failing. 

No matter what you do in Ubuntu it shouldn't affect anything in Windows?

---

### Post by ajgreeny on 2017-10-13
> **iormungand said:**
> No matter what you do in Ubuntu it shouldn't affect anything in Windows?
That's correct, providing, of course, that you do not delete or edit any files in the Windows partitions, and some say you should try not to write anything to the Windows partition at all from Ubuntu, as that may upset things.

---

