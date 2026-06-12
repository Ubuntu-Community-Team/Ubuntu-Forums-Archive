---
title: "Broadcom BCM4366 PCI-e driver won't load"
date: 2016-09-15
forum: Networking &amp; Wireless
---

### Post by n3roj on 2016-09-15
[COLOR=#000000]Hi All, I've recently purchased an Asus PCE-AC88 dualband wifi card. Things haven't been going to well. I'll get right to it. (Yes I looked at the "How to install a driver for the Broadcom series of PCI wireless cards" sticky post).

[/COLOR]dmesg reports this:
```
[ 2755.750897] brcmfmac 0000:07:00.0: Direct firmware load for brcm/brcmfmac4366b-pcie.txt failed with error -2
[ 2758.086255] brcmf_pcie_download_fw_nvram: FW failed to initialize
```

That file doesn't exist on my system. I've looked everywhere and the "NVRAM from EFI" section from [https://wireless.wiki.kernel.org/en/users/drivers/brcm80211](https://wireless.wiki.kernel.org/en/users/drivers/brcm80211) doesn't help. I do not see that nvram file anywhere. Is there a special way to generate this?

So I looked online and tried to use a hack where you can specify just the macaddr=<mac_addr_of_card>. Still didn't work as I still see in dmesg.
```
[ 2758.086255] brcmf_pcie_download_fw_nvram: FW failed to initialize
```

Linux kernel and ubuntu are updated as of today.

Unsure as to how I should continue. Any help is greatly appreciated!!

```


########## wireless info START ##########


Report from: 15 Sep 2016 12:59 EDT -0400


Booted last: 15 Sep 2016 00:00 EDT -0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, text


##### desktop ###########################


/usr/share/xsessions/plasma


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1] (rev 05)
    DeviceName:  Onboard LAN
    Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I218-V [1043:85c4]


07:00.0 Network controller [0280]: Broadcom Limited Device [14e4:43c3] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:86fb]
    Kernel modules: brcmfmac


##### lsusb #############################


Bus 002 Device 002: ID 8087:8002 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:800a Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 05ac:024f Apple, Inc. 
Bus 003 Device 004: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 003 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 002: ID 174c:2074 ASMedia Technology Inc. ASM1074 High-Speed hub
Bus 003 Device 007: ID 0cf3:9170 Atheros Communications, Inc. AR9170 802.11n
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


brcmfmac              290816  0
brcmutil               16384  1 brcmfmac
carl9170               90112  0
ath                    32768  1 carl9170
mac80211              737280  1 carl9170
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
video                  40960  1 asus_wmi
mxm_wmi                16384  0
cfg80211              565248  4 ath,brcmfmac,mac80211,carl9170
wmi                    20480  2 mxm_wmi,asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fa100000-fa120000 


wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          inet addr:192.168.0.14  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e20:3bb:eaca:b9e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10053956 (10.0 MB)  TX bytes:1247255 (1.2 MB)


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


wlx<IF from MAC [IF2]>  IEEE 802.11abgn  ESSID:"XXX"  
          Mode:Managed  Frequency:5.785 GHz  Access Point: <XX>   
          Bit Rate=108 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:102  Invalid misc:120   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlx<IF from MAC [IF2]>
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlx<IF from MAC [IF2]>


##### resolv.conf #######################


nameserver 209.18.47.61


##### network managers ##################


Installed:


    NetworkManager


Running:


root       867     1  0 12:30 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############
<remove ssids>
##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=false


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########

<removed>
##### iw reg get ########################


Region: America/New_York (based on set time zone)


country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


eno1      no frequency information.


wlx<IF from MAC [IF2]>  32 channels in total; available frequencies :
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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Current Frequency:5.785 GHz


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


<removed wifi>


##### module infos ######################


[brcmfmac]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/brcm80211/brcmfmac/brcmfmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11 wireless LAN fullmac driver.
author:         Broadcom Corporation
firmware:       brcm/brcmfmac4354-sdio.txt
firmware:       brcm/brcmfmac4354-sdio.bin
firmware:       brcm/brcmfmac43455-sdio.txt
firmware:       brcm/brcmfmac43455-sdio.bin
firmware:       brcm/brcmfmac43430-sdio.txt
firmware:       brcm/brcmfmac43430-sdio.bin
firmware:       brcm/brcmfmac4339-sdio.txt
firmware:       brcm/brcmfmac4339-sdio.bin
firmware:       brcm/brcmfmac43362-sdio.txt
firmware:       brcm/brcmfmac43362-sdio.bin
firmware:       brcm/brcmfmac4335-sdio.txt
firmware:       brcm/brcmfmac4335-sdio.bin
firmware:       brcm/brcmfmac43340-sdio.txt
firmware:       brcm/brcmfmac43340-sdio.bin
firmware:       brcm/brcmfmac4334-sdio.txt
firmware:       brcm/brcmfmac4334-sdio.bin
firmware:       brcm/brcmfmac4330-sdio.txt
firmware:       brcm/brcmfmac4330-sdio.bin
firmware:       brcm/brcmfmac4329-sdio.txt
firmware:       brcm/brcmfmac4329-sdio.bin
firmware:       brcm/brcmfmac43241b5-sdio.txt
firmware:       brcm/brcmfmac43241b5-sdio.bin
firmware:       brcm/brcmfmac43241b4-sdio.txt
firmware:       brcm/brcmfmac43241b4-sdio.bin
firmware:       brcm/brcmfmac43241b0-sdio.txt
firmware:       brcm/brcmfmac43241b0-sdio.bin
firmware:       brcm/brcmfmac43143-sdio.txt
firmware:       brcm/brcmfmac43143-sdio.bin
firmware:       brcm/brcmfmac43569.bin
firmware:       brcm/brcmfmac43242a.bin
firmware:       brcm/brcmfmac43236b.bin
firmware:       brcm/brcmfmac43143.bin
firmware:       brcm/brcmfmac4371-pcie.txt
firmware:       brcm/brcmfmac4371-pcie.bin
firmware:       brcm/brcmfmac4366b-pcie.txt
firmware:       brcm/brcmfmac4366b-pcie.bin
firmware:       brcm/brcmfmac4365b-pcie.txt
firmware:       brcm/brcmfmac4365b-pcie.bin
firmware:       brcm/brcmfmac4358-pcie.txt
firmware:       brcm/brcmfmac4358-pcie.bin
firmware:       brcm/brcmfmac43570-pcie.txt
firmware:       brcm/brcmfmac43570-pcie.bin
firmware:       brcm/brcmfmac4356-pcie.txt
firmware:       brcm/brcmfmac4356-pcie.bin
firmware:       brcm/brcmfmac4350-pcie.txt
firmware:       brcm/brcmfmac4350-pcie.bin
firmware:       brcm/brcmfmac43602-pcie.txt
firmware:       brcm/brcmfmac43602-pcie.bin
srcversion:     394D104EE5D4CED7AA9D01D
depends:        brcmutil,cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           txglomsz:maximum tx packet chain size [SDIO] (int)
parm:           feature_disable:Disable features (int)
parm:           alternative_fw_path:string
parm:           debug:level of debug output (int)
parm:           p2pon:enable legacy p2p management functionality (int)
parm:           fcmode:mode of firmware signalled flow control (int)
parm:           roamoff:do not use internal roaming engine (int)


[brcmutil]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     AE9B4BBC6D82855B9265054
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 


[carl9170]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko
firmware:       carl9170-1.fw
description:    Atheros AR9170 802.11n USB wireless
license:        GPL
author:         Christian Lamparter <chunkeey@googlemail.com>
author:         Johannes Berg <johannes@sipsolutions.net>
srcversion:     0DE070463F621213D92166B
depends:        mac80211,ath,cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware crypto offload. (bool)
parm:           noht:Disable MPDU aggregation. (int)


[ath]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B10AF1CD828D26173EA0378
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


grep: /sys/module/brcmfmac/parameters/alternative_fw_path: Permission denied
grep: /sys/module/brcmfmac/parameters/debug: Permission denied
grep: /sys/module/brcmfmac/parameters/fcmode: Permission denied
grep: /sys/module/brcmfmac/parameters/roamoff: Permission denied
[brcmfmac]


[carl9170]
noht: 0
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
blacklist b43
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


##### dmesg #############################


[  113.856443] usb 3-1: firmware API: 1.9.6 2012-07-07
[  114.180459] ath: EEPROM regdomain: 0x0
[  114.180464] ath: EEPROM indicates default country code should be used
[  114.180466] ath: doing EEPROM country->regdmn map search
[  114.180469] ath: country maps to regdmn code: 0x3a
[  114.180471] ath: Country alpha2 being used: US
[  114.180472] ath: Regpair used: 0x3a
[  114.875689] carl9170 3-1:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[  114.902182] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 3 times)
[  120.512944] wlx<IF from MAC [IF2]>: authenticate with <MAC 'M<MAC 'M<MAC address>J-5G' [AN8]>J-5G' [AC1]>
[  120.571862] wlx<IF from MAC [IF2]>: send auth to <MAC 'M<MAC 'M<MAC address>J-5G' [AN8]>J-5G' [AC1]> (try 1/3)
[  120.572971] wlx<IF from MAC [IF2]>: authenticated
[  120.573136] wlx<IF from MAC [IF2]>: waiting for beacon from <MAC 'M<MAC 'M<MAC address>J-5G' [AN8]>J-5G' [AC1]>
[  120.629361] wlx<IF from MAC [IF2]>: associate with <MAC 'M<MAC 'M<MAC address>J-5G' [AN8]>J-5G' [AC1]> (try 1/3)
[  120.630604] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'M<MAC 'M<MAC address>J-5G' [AN8]>J-5G' [AC1]> (capab=0x1011 status=0 aid=2)
[  120.632559] wlx<IF from MAC [IF2]>: associated
[  120.632603] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready
[  157.215811] brcmf_pcie_download_fw_nvram: FW failed to initialize


########## wireless info END ############

```

---

### Post by wildmanne39 on 2016-09-15
I am sorry you removed information from the script and I need to see it in order to help.

---

### Post by n3roj on 2016-09-24
You need to see my connected wifi information in order to help?

What information do you need, I'll post it.

---

### Post by wildmanne39 on 2016-09-24
Just run the wireless script and post the complete file it creates in your home folder, the directions how to do it are in the link in my signature.
Thanks

---

### Post by jeremy31 on 2016-09-24
I think we have more issues than that with this card.  It is misidentified in the 4.4 kernel as a 4366b device when it is a 4366c device, see [kernel commit](http://git.kernel.org/cgit/linux/kernel/git/next/linux-next.git/commit/drivers/net/wireless/broadcom/brcm80211/brcmfmac?id=bc86fdb9ac02c77b9f55325f64fb70decc425962)
It seems that the commit is part of backports-20160324 but the firmware file bcrmfmac4366c-pcie.bin is not in linux-firmware-next, see [comment](https://bugzilla.kernel.org/show_bug.cgi?id=135321#c2) but it seems that they found something on Fedora forums [http://forums.fedoraforum.org/showthread.php?p=1769999#post1769999](http://forums.fedoraforum.org/showthread.php?p=1769999#post1769999)

---

### Post by quickk on 2016-12-11
I'm not sure if I should start a new thread or not, but I also am in the same situation.  I'm trying to get my Asus PCI AC-88 wireless adapter to work, and I've had no luck.  I just upgraded to the latest kernel (4.9) in the hopes that this would work, but no luck.  

Anyone have luck with this card?

---

### Post by olmightyg on 2016-12-13
Hi,

I am also interested in a solution. I have updated to the 4.8 kernel. I can find the firmware files in the /lib/firmware folder.
dmesg shows: brcmfmac 0000:02:00.0: Direct firmware load for brcm/brcmfmac4366c-pcie.bin failed with error -2

Any solution to this?

---

### Post by jeremy31 on 2016-12-13
Unfortunately it seems that no progress has been made for this chipset

---

### Post by olmightyg on 2016-12-13
What can we do? Its my first time I have a problem with hardware under Linux. I can live with the cable connection for some time but it would be great if we could achieve something since the firmware stuff seems to be there and the device is recognized. Some people made it (googled it) but I either could not understand and reproduce what they did or it did not work for me.
E.g. extracting the FW from an Asus router firmware file.
Found this: [https://wireless.wiki.kernel.org/en/users/Drivers/brcm80211](https://wireless.wiki.kernel.org/en/users/Drivers/brcm80211) but the provided files seem to be alredy in the designated folders, at least with the 4.8 kernel, did not check 4.4.

Any ideas?

---

### Post by n3roj2 on 2017-03-10
So I (original poster) figured this one out. It might help people in the future. I included steps for the latest firmware as of 03/10/17.

1.) Go to the Asus support page and download the "other" firmware for RT-AC88U. ([https://www.asus.com/us/Networking/RT-AC88U/HelpDesk_Download/](https://www.asus.com/us/Networking/RT-AC88U/HelpDesk_Download/))
- I'm using [COLOR=#333333][FONT=Arial]Version[/FONT][/COLOR][COLOR=#333333][FONT=Arial]3.0.0.4.380.7266[/FONT][/COLOR]
2.) Extract the firmware using binwalk: binwalk -e RT-AC88U_3.0.0.4_380_7266-g6439257.trx
3.) Enter the [FONT=monospace][COLOR=#000000]_RT-AC88U_3.0.0.4_380_7266-g6439257.trx.extracted/squashfs-root/lib/modules/2.6.36.4brcmarm/kernel/drivers/net/dhd/ directory
- You should see dhd.ko
4.) Use read elf and search for 4366c0: [/COLOR][/FONT]readelf -s dhd.ko | grep 4366c0

[FONT=monospace][COLOR=#000000]   219: 000fe818     4 OBJECT  GLOBAL DEFAULT   35 active_cons_[/COLOR][COLOR=#FF5454]**4366c0**[/COLOR]
   228: 000fe7ec    18 OBJECT  GLOBAL DEFAULT   35 dlimagever_[COLOR=#FF5454]**4366c0**[/COLOR]
   248: 000fe73c   175 OBJECT  GLOBAL DEFAULT   35 dlimagename_[COLOR=#FF5454]**4366c0**[/COLOR]
   348: 000fe814     1 OBJECT  GLOBAL DEFAULT   35 dlimagetag_[COLOR=#FF5454]**4366c0**[/COLOR]
   479: 000fe800    20 OBJECT  GLOBAL DEFAULT   35 dlimagedate_[COLOR=#FF5454]**4366c0**[/COLOR]
   518: 000fe81c 0xe6450 OBJECT  GLOBAL DEFAULT   35 dlarray_[COLOR=#FF5454]**4366c0**[/COLOR]
   625: 000022e4     4 OBJECT  GLOBAL DEFAULT   45 debug_params_[COLOR=#FF5454]**4366c0**[/COLOR]

[/FONT][FONT=monospace]5.) 0xe6450 is [/FONT]943184 in decimal (this is the bin file size)
[FONT=monospace]6.) Open up another brcmfmacXXXX.bin in bless to compare the start and stop tags for another firmware (I'm using [/FONT][FONT=monospace][COLOR=#000000]brcmfmac4366b-pcie.bin)
7.) We see a start hex of "[/COLOR][/FONT]00 F2 3E B8" as a starting point and "FWID: 01-c47a91a4...." as ending (4 bytes past the denoted as periods
8.) Search in dhd.ko using bless for [FONT=monospace][COLOR=#000000]"[/COLOR][/FONT]00 F2 3E B8"; Address at 0x137bbc which is 1276860 in decimal
9.) Copy out the firmware using dd: dd if=dhd.ko skip=1276860 ibs=1 count=943184 of=brcmfmac4366c-pcie.bin
10.) Open up the new brcmfmac4366c-pcie.bin file in Bless to check it out and ensure that we start with "00 F2 3E B8" and end with the FWID: "FWID: 01-fed440e1...."
- sha1sum is "[FONT=monospace][COLOR=#000000]9f97ebaf661631d6aa303d5e74a528cf1d95a016  brcmfmac4366c-pcie.bin"
[/COLOR][/FONT]11.) Put that in [FONT=monospace][COLOR=#000000]/lib/firmware/brcm and reaload the module.
[/COLOR][/FONT][FONT=monospace]12.) Check dmesg on your system and grep for errors.

This worked on my system and I now have perfect wi-fi using the [/FONT]ASUS PCE-AC88 4x4 Wireless AC3100 PCIe Adapter.[FONT=monospace]

[/FONT][FONT=monospace][COLOR=#000000]Linux x0 4.8.0-39-generic #42-Ubuntu SMP Mon Feb 20 11:47:27 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]DISTRIB_ID=Ubuntu[/COLOR]
DISTRIB_RELEASE=16.10
DISTRIB_CODENAME=yakkety
DISTRIB_DESCRIPTION="Ubuntu 16.10"

Credit to [/FONT]https://serialize.wordpress.com/2017/02/12/extract-4366c0-firmware/ for more detailed steps.[FONT=monospace]

Cheers.

[/FONT][FONT=monospace]
[/FONT]

---

### Post by chrismacp on 2017-03-19
Nice! That works and I have the WIFI card working. The connection doesn't seem so stable yet, but I'll have a play around.

I did have the card connecting to my router previously but could not get any data transferring for some reason, great to be able to use this card now.

Thanks a lot :)

> **n3roj2 said:**
> So I (original poster) figured this one out. It might help people in the future. I included steps for the latest firmware as of 03/10/17.

1.) Go to the Asus support page and download the "other" firmware for RT-AC88U. ([https://www.asus.com/us/Networking/RT-AC88U/HelpDesk_Download/](https://www.asus.com/us/Networking/RT-AC88U/HelpDesk_Download/))
- I'm using [COLOR=#333333][FONT=Arial]Version[/FONT][/COLOR][COLOR=#333333][FONT=Arial]3.0.0.4.380.7266[/FONT][/COLOR]
2.) Extract the firmware using binwalk: binwalk -e RT-AC88U_3.0.0.4_380_7266-g6439257.trx
3.) Enter the [FONT=monospace][COLOR=#000000]_RT-AC88U_3.0.0.4_380_7266-g6439257.trx.extracted/squashfs-root/lib/modules/2.6.36.4brcmarm/kernel/drivers/net/dhd/ directory
- You should see dhd.ko
4.) Use read elf and search for 4366c0: [/COLOR][/FONT]readelf -s dhd.ko | grep 4366c0

[FONT=monospace][COLOR=#000000]   219: 000fe818     4 OBJECT  GLOBAL DEFAULT   35 active_cons_[/COLOR][COLOR=#FF5454]**4366c0**[/COLOR]
   228: 000fe7ec    18 OBJECT  GLOBAL DEFAULT   35 dlimagever_[COLOR=#FF5454]**4366c0**[/COLOR]
   248: 000fe73c   175 OBJECT  GLOBAL DEFAULT   35 dlimagename_[COLOR=#FF5454]**4366c0**[/COLOR]
   348: 000fe814     1 OBJECT  GLOBAL DEFAULT   35 dlimagetag_[COLOR=#FF5454]**4366c0**[/COLOR]
   479: 000fe800    20 OBJECT  GLOBAL DEFAULT   35 dlimagedate_[COLOR=#FF5454]**4366c0**[/COLOR]
   518: 000fe81c 0xe6450 OBJECT  GLOBAL DEFAULT   35 dlarray_[COLOR=#FF5454]**4366c0**[/COLOR]
   625: 000022e4     4 OBJECT  GLOBAL DEFAULT   45 debug_params_[COLOR=#FF5454]**4366c0**[/COLOR]

[/FONT][FONT=monospace]5.) 0xe6450 is [/FONT]943184 in decimal (this is the bin file size)
[FONT=monospace]6.) Open up another brcmfmacXXXX.bin in bless to compare the start and stop tags for another firmware (I'm using [/FONT][FONT=monospace][COLOR=#000000]brcmfmac4366b-pcie.bin)
7.) We see a start hex of "[/COLOR][/FONT]00 F2 3E B8" as a starting point and "FWID: 01-c47a91a4...." as ending (4 bytes past the denoted as periods
8.) Search in dhd.ko using bless for [FONT=monospace][COLOR=#000000]"[/COLOR][/FONT]00 F2 3E B8"; Address at 0x137bbc which is 1276860 in decimal
9.) Copy out the firmware using dd: dd if=dhd.ko skip=1276860 ibs=1 count=943184 of=brcmfmac4366c-pcie.bin
10.) Open up the new brcmfmac4366c-pcie.bin file in Bless to check it out and ensure that we start with "00 F2 3E B8" and end with the FWID: "FWID: 01-fed440e1...."
- sha1sum is "[FONT=monospace][COLOR=#000000]9f97ebaf661631d6aa303d5e74a528cf1d95a016  brcmfmac4366c-pcie.bin"
[/COLOR][/FONT]11.) Put that in [FONT=monospace][COLOR=#000000]/lib/firmware/brcm and reaload the module.
[/COLOR][/FONT][FONT=monospace]12.) Check dmesg on your system and grep for errors.

This worked on my system and I now have perfect wi-fi using the [/FONT]ASUS PCE-AC88 4x4 Wireless AC3100 PCIe Adapter.[FONT=monospace]

[/FONT][FONT=monospace][COLOR=#000000]Linux x0 4.8.0-39-generic #42-Ubuntu SMP Mon Feb 20 11:47:27 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]DISTRIB_ID=Ubuntu[/COLOR]
DISTRIB_RELEASE=16.10
DISTRIB_CODENAME=yakkety
DISTRIB_DESCRIPTION="Ubuntu 16.10"

Credit to [/FONT]https://serialize.wordpress.com/2017/02/12/extract-4366c0-firmware/ for more detailed steps.[FONT=monospace]

Cheers.

[/FONT][FONT=monospace]
[/FONT]

---

### Post by mariuswiik on 2017-03-25
So I followed the guide and seem to have gotten the firmware installed. I can finally scan for networks and connect.
However, the connection is not really there... 

Connection info shows 12 Mb\s (I have a 1Gbit connection), and I cannot open any pages.

I fear I might have broken something when trying to install this card.
dmesg shows alot of brcmf related errors:
```

&#10140;  ~ dmesg | grep brcmf
[    2.613289] usbcore: registered new interface driver brcmfmac
[    2.730533] brcmfmac 0000:04:00.0: Direct firmware load for brcm/brcmfmac4366c-pcie.txt failed with error -2
[    3.470636] brcmf_c_preinit_dcmds: Firmware version = wl0: Sep 12 2016 13:26:44 version 10.10.69.6908 (r658761) FWID 01-fed440e1
[    3.477287] brcmf_cfg80211_reg_notifier: not a ISO3166 code (0x30 0x30)
[    3.479859] brcmfmac 0000:04:00.0 wlp4s0: renamed from wlan0
[    4.837398] brcmf_p2p_set_firmware: failed to update device address ret -23
[    4.837607] brcmf_p2p_create_p2pdev: set p2p_disc error
[    4.837609] brcmf_cfg80211_add_iface: add iface p2p-dev-wlp4s0 type 10 failed: err=-23
[   95.450904] brcmf_cfg80211_reg_notifier: not a ISO3166 code (0x30 0x30)
[  104.019109] brcmf_inetaddr_changed: fail to get arp ip table err:-23
[  109.349073] brcmf_inetaddr_changed: fail to get arp ip table err:-23
[  109.349086] brcmf_cfg80211_reg_notifier: not a ISO3166 code (0x30 0x30)
[  111.223303] brcmf_inetaddr_changed: fail to get arp ip table err:-23
[  329.507209] brcmf_cfg80211_reg_notifier: not a ISO3166 code (0x30 0x30)
[  439.721682] brcmf_cfg80211_reg_notifier: not a ISO3166 code (0x30 0x30)
[  620.070268] brcmf_cfg80211_reg_notifier: not a ISO3166 code (0x30 0x30)
[  715.254178] brcmf_cfg80211_reg_notifier: not a ISO3166 code (0x30 0x30)
[  820.457706] brcmf_cfg80211_reg_notifier: not a ISO3166 code (0x30 0x30)


```

But the firmware file is there:
```

ls /lib/firmware/brcm 
bcm4329-fullmac-4.bin   brcmfmac43236b.bin        brcmfmac4329-sdio.bin   brcmfmac43362-sdio.bin   brcmfmac4354-sdio.bin      brcmfmac43602-pcie.bin
bcm43xx-0.fw            brcmfmac43241b0-sdio.bin  brcmfmac4330-sdio.bin   brcmfmac4339-sdio.bin    brcmfmac43569.bin          brcmfmac4366b-pcie.bin
bcm43xx_hdr-0.fw        brcmfmac43241b4-sdio.bin  brcmfmac43340-sdio.bin  brcmfmac43455-sdio.bin   brcmfmac4356-pcie.bin      brcmfmac4366c-pcie.bin
brcmfmac43143.bin       brcmfmac43241b5-sdio.bin  brcmfmac4334-sdio.bin   brcmfmac4350c2-pcie.bin  brcmfmac43570-pcie.bin     brcmfmac4371-pcie.bin
brcmfmac43143-sdio.bin  brcmfmac43242a.bin        brcmfmac4335-sdio.bin   brcmfmac4350-pcie.bin    brcmfmac43602-pcie.ap.bin


```

~ lspci -vvnn | grep -A 10 Network gives:
```

04:00.0 Network controller [0280]: Broadcom Limited Device [14e4:43c3] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:86fb]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 53
    Region 0: Memory at fb000000 (64-bit, non-prefetchable) [size=32K]
    Region 2: Memory at fa800000 (64-bit, non-prefetchable) [size=8M]
    Region 4: Memory at d2400000 (64-bit, prefetchable) [size=4M]
    Capabilities: <access denied>
    Kernel driver in use: brcmfmac


```

Any tips here are appreciated :)

---

### Post by nhine on 2017-03-31
> **n3roj2 said:**
> So I (original poster) figured this one out. It might help people in the future. I included steps for the latest firmware as of 03/10/17.

1.) Go to the Asus support page and download the "other" firmware for RT-AC88U. ([https://www.asus.com/us/Networking/RT-AC88U/HelpDesk_Download/](https://www.asus.com/us/Networking/RT-AC88U/HelpDesk_Download/))
- I'm using [COLOR=#333333][FONT=Arial]Version[/FONT][/COLOR][COLOR=#333333][FONT=Arial]3.0.0.4.380.7266[/FONT][/COLOR]
2.) Extract the firmware using binwalk: binwalk -e RT-AC88U_3.0.0.4_380_7266-g6439257.trx
3.) Enter the [FONT=monospace][COLOR=#000000]_RT-AC88U_3.0.0.4_380_7266-g6439257.trx.extracted/squashfs-root/lib/modules/2.6.36.4brcmarm/kernel/drivers/net/dhd/ directory
- You should see dhd.ko
4.) Use read elf and search for 4366c0: [/COLOR][/FONT]readelf -s dhd.ko | grep 4366c0

[FONT=monospace][COLOR=#000000]   219: 000fe818     4 OBJECT  GLOBAL DEFAULT   35 active_cons_[/COLOR][COLOR=#FF5454]**4366c0**[/COLOR]
   228: 000fe7ec    18 OBJECT  GLOBAL DEFAULT   35 dlimagever_[COLOR=#FF5454]**4366c0**[/COLOR]
   248: 000fe73c   175 OBJECT  GLOBAL DEFAULT   35 dlimagename_[COLOR=#FF5454]**4366c0**[/COLOR]
   348: 000fe814     1 OBJECT  GLOBAL DEFAULT   35 dlimagetag_[COLOR=#FF5454]**4366c0**[/COLOR]
   479: 000fe800    20 OBJECT  GLOBAL DEFAULT   35 dlimagedate_[COLOR=#FF5454]**4366c0**[/COLOR]
   518: 000fe81c 0xe6450 OBJECT  GLOBAL DEFAULT   35 dlarray_[COLOR=#FF5454]**4366c0**[/COLOR]
   625: 000022e4     4 OBJECT  GLOBAL DEFAULT   45 debug_params_[COLOR=#FF5454]**4366c0**[/COLOR]

[/FONT][FONT=monospace]5.) 0xe6450 is [/FONT]943184 in decimal (this is the bin file size)
[FONT=monospace]6.) Open up another brcmfmacXXXX.bin in bless to compare the start and stop tags for another firmware (I'm using [/FONT][FONT=monospace][COLOR=#000000]brcmfmac4366b-pcie.bin)
7.) We see a start hex of "[/COLOR][/FONT]00 F2 3E B8" as a starting point and "FWID: 01-c47a91a4...." as ending (4 bytes past the denoted as periods
8.) Search in dhd.ko using bless for [FONT=monospace][COLOR=#000000]"[/COLOR][/FONT]00 F2 3E B8"; Address at 0x137bbc which is 1276860 in decimal
9.) Copy out the firmware using dd: dd if=dhd.ko skip=1276860 ibs=1 count=943184 of=brcmfmac4366c-pcie.bin
10.) Open up the new brcmfmac4366c-pcie.bin file in Bless to check it out and ensure that we start with "00 F2 3E B8" and end with the FWID: "FWID: 01-fed440e1...."
- sha1sum is "[FONT=monospace][COLOR=#000000]9f97ebaf661631d6aa303d5e74a528cf1d95a016  brcmfmac4366c-pcie.bin"
[/COLOR][/FONT]11.) Put that in [FONT=monospace][COLOR=#000000]/lib/firmware/brcm and reaload the module.
[/COLOR][/FONT][FONT=monospace]12.) Check dmesg on your system and grep for errors.

This worked on my system and I now have perfect wi-fi using the [/FONT]ASUS PCE-AC88 4x4 Wireless AC3100 PCIe Adapter.[FONT=monospace]

[/FONT][FONT=monospace][COLOR=#000000]Linux x0 4.8.0-39-generic #42-Ubuntu SMP Mon Feb 20 11:47:27 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]DISTRIB_ID=Ubuntu[/COLOR]
DISTRIB_RELEASE=16.10
DISTRIB_CODENAME=yakkety
DISTRIB_DESCRIPTION="Ubuntu 16.10"

Credit to [/FONT]https://serialize.wordpress.com/2017/02/12/extract-4366c0-firmware/ for more detailed steps.[FONT=monospace]

Cheers.

[/FONT][FONT=monospace]
[/FONT]


Hello,
I'm new user of Ubuntu and has same wifi card. Could you please explain with more details steps 6 to 12 please ? I'm lost, how to get [FONT=monospace] brcmfmacXXXX.bin file ?

Thank you for your help ![/FONT]

---

### Post by chrismacp on 2017-04-09
> **nhine said:**
> Hello,
I'm new user of Ubuntu and has same wifi card. Could you please explain with more details steps 6 to 12 please ? I'm lost, how to get [FONT=monospace] brcmfmacXXXX.bin file ?

Thank you for your help ![/FONT]

You can probably try just doing steps 9 and 11. The other steps between 6 - 12 are verifying the created file is correct.

If it doesn't work then you will then need to recreate the file using the instructions and use those steps 6, 7, 8, 10 to confirm you did it correctly. 

When I followed the instructions it worked perfectly.

P.S. I don't get stable connections on 5Ghz but 2.4GHz works really well.

---

### Post by nhine on 2017-04-15
Hi,

thanks, I solved the problem and describe and share it to french ubuntu community.

[https://forum.ubuntu-fr.org/viewtopic.php?pid=21705625](https://forum.ubuntu-fr.org/viewtopic.php?pid=21705625)

---

### Post by hal9k2 on 2017-06-25
I got similar issue as @mariuswiik

```

$ demesg
[nie cze 25 12:55:34 2017] brcmfmac: brcmf_p2p_set_firmware: failed to update device address ret -23
[nie cze 25 12:55:34 2017] brcmfmac: brcmf_p2p_create_p2pdev: set p2p_disc error
[nie cze 25 12:55:34 2017] brcmfmac: brcmf_cfg80211_add_iface: add iface p2p-dev-wlp5s0 type 10 failed: err=-23

```

Anyone have ideas how to resolve it?

What I found is only this: **[https://www.mail-archive.com/linux-wireless@vger.kernel.org/msg10342.html](https://www.mail-archive.com/linux-wireless@vger.kernel.org/msg10342.html) **but this not getting me to resolve that issue.


 > **mariuswiik said:**
> So I followed the guide and seem to have gotten the firmware installed. I can finally scan for networks and connect.
However, the connection is not really there... 

Connection info shows 12 Mb\s (I have a 1Gbit connection), and I cannot open any pages.

I fear I might have broken something when trying to install this card.
dmesg shows alot of brcmf related errors:
```

&#10140;  ~ dmesg | grep brcmf
[    2.613289] usbcore: registered new interface driver brcmfmac
[    2.730533] brcmfmac 0000:04:00.0: Direct firmware load for brcm/brcmfmac4366c-pcie.txt failed with error -2
[    3.470636] brcmf_c_preinit_dcmds: Firmware version = wl0: Sep 12 2016 13:26:44 version 10.10.69.6908 (r658761) FWID 01-fed440e1
[    3.477287] brcmf_cfg80211_reg_notifier: not a ISO3166 code (0x30 0x30)
[    3.479859] brcmfmac 0000:04:00.0 wlp4s0: renamed from wlan0
[    4.837398] brcmf_p2p_set_firmware: failed to update device address ret -23
[    4.837607] brcmf_p2p_create_p2pdev: set p2p_disc error
[    4.837609] brcmf_cfg80211_add_iface: add iface p2p-dev-wlp4s0 type 10 failed: err=-23
[   95.450904] brcmf_cfg80211_reg_notifier: not a ISO3166 code (0x30 0x30)
[  104.019109] brcmf_inetaddr_changed: fail to get arp ip table err:-23
[  109.349073] brcmf_inetaddr_changed: fail to get arp ip table err:-23
[  109.349086] brcmf_cfg80211_reg_notifier: not a ISO3166 code (0x30 0x30)
[  111.223303] brcmf_inetaddr_changed: fail to get arp ip table err:-23
[  329.507209] brcmf_cfg80211_reg_notifier: not a ISO3166 code (0x30 0x30)
[  439.721682] brcmf_cfg80211_reg_notifier: not a ISO3166 code (0x30 0x30)
[  620.070268] brcmf_cfg80211_reg_notifier: not a ISO3166 code (0x30 0x30)
[  715.254178] brcmf_cfg80211_reg_notifier: not a ISO3166 code (0x30 0x30)
[  820.457706] brcmf_cfg80211_reg_notifier: not a ISO3166 code (0x30 0x30)


```

But the firmware file is there:
```

ls /lib/firmware/brcm 
bcm4329-fullmac-4.bin   brcmfmac43236b.bin        brcmfmac4329-sdio.bin   brcmfmac43362-sdio.bin   brcmfmac4354-sdio.bin      brcmfmac43602-pcie.bin
bcm43xx-0.fw            brcmfmac43241b0-sdio.bin  brcmfmac4330-sdio.bin   brcmfmac4339-sdio.bin    brcmfmac43569.bin          brcmfmac4366b-pcie.bin
bcm43xx_hdr-0.fw        brcmfmac43241b4-sdio.bin  brcmfmac43340-sdio.bin  brcmfmac43455-sdio.bin   brcmfmac4356-pcie.bin      brcmfmac4366c-pcie.bin
brcmfmac43143.bin       brcmfmac43241b5-sdio.bin  brcmfmac4334-sdio.bin   brcmfmac4350c2-pcie.bin  brcmfmac43570-pcie.bin     brcmfmac4371-pcie.bin
brcmfmac43143-sdio.bin  brcmfmac43242a.bin        brcmfmac4335-sdio.bin   brcmfmac4350-pcie.bin    brcmfmac43602-pcie.ap.bin


```

~ lspci -vvnn | grep -A 10 Network gives:
```

04:00.0 Network controller [0280]: Broadcom Limited Device [14e4:43c3] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:86fb]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 53
    Region 0: Memory at fb000000 (64-bit, non-prefetchable) [size=32K]
    Region 2: Memory at fa800000 (64-bit, non-prefetchable) [size=8M]
    Region 4: Memory at d2400000 (64-bit, prefetchable) [size=4M]
    Capabilities: <access denied>
    Kernel driver in use: brcmfmac


```

Any tips here are appreciated :)

---

### Post by HTF1 on 2017-09-07
> **n3roj2 said:**
> 
8.) Search in dhd.ko using bless for [FONT=monospace][COLOR=#000000]"[/COLOR][/FONT]00 F2 3E B8"; Address at 0x137bbc which is 1276860 in decimal[FONT=monospace]
[/FONT]

Could you please help me to understand how did you get the offset? Why this is a third match here?!

```
# xxd dhd.ko | grep -i "00F2 3EB8"
003d980: **00f2 3eb8** 05f2 c2b9 05f2 cdb9 05f2 d8b9  ..>.............
003d9a0: **00f2 3eb8** 05f2 c2b9 05f2 cdb9 05f2 d8b9  ..>.............
0137bb0: 3a31 3200 0000 0000 68c8 2000 [COLOR=#ff0000]**00f2 3eb8**[/COLOR]  :12.....h. ...>.
0137bd0: 05f2 74b9 05f2 82b9 05f2 8eb9 **00f2 3eb8**  ..t...........>.
```

I'm trying to extract the latest one (Version 3.0.0.4.382.15850), size seems to be 1087985 (0x1099f1) but I'm not sure how to get the offset:

 ```
# readelf -s dhd.ko | grep dlarray
   525: 00004448 0x1099f1 OBJECT  GLOBAL DEFAULT   35 dlarray_4366c0
```

```
# xxd dhd.ko | grep -i "00F2 3EB8"
003e800: 0000 0000 9cca 2000 **00f2 3eb8** 04f2 26bf  ...... ...>...&.
003e820: 04f2 66bf 04f2 72bf **00f2 3eb8** 04f2 26bf  ..f...r...>...&.
```

---

### Post by mikelojkovic on 2017-10-24
> **n3roj2 said:**
> So I (original poster) figured this one out. It might help people in the future. I included steps for the latest firmware as of 03/10/17.

1.) Go to the Asus support page and download the "other" firmware for RT-AC88U. ([https://www.asus.com/us/Networking/RT-AC88U/HelpDesk_Download/](https://www.asus.com/us/Networking/RT-AC88U/HelpDesk_Download/))
- I'm using [COLOR=#333333][FONT=Arial]Version[/FONT][/COLOR][COLOR=#333333][FONT=Arial]3.0.0.4.380.7266[/FONT][/COLOR]
2.) Extract the firmware using binwalk: binwalk -e RT-AC88U_3.0.0.4_380_7266-g6439257.trx
3.) Enter the [FONT=monospace][COLOR=#000000]_RT-AC88U_3.0.0.4_380_7266-g6439257.trx.extracted/squashfs-root/lib/modules/2.6.36.4brcmarm/kernel/drivers/net/dhd/ directory
- You should see dhd.ko
4.) Use read elf and search for 4366c0: [/COLOR][/FONT]readelf -s dhd.ko | grep 4366c0

[FONT=monospace][COLOR=#000000]   219: 000fe818     4 OBJECT  GLOBAL DEFAULT   35 active_cons_[/COLOR][COLOR=#FF5454]**4366c0**[/COLOR]
   228: 000fe7ec    18 OBJECT  GLOBAL DEFAULT   35 dlimagever_[COLOR=#FF5454]**4366c0**[/COLOR]
   248: 000fe73c   175 OBJECT  GLOBAL DEFAULT   35 dlimagename_[COLOR=#FF5454]**4366c0**[/COLOR]
   348: 000fe814     1 OBJECT  GLOBAL DEFAULT   35 dlimagetag_[COLOR=#FF5454]**4366c0**[/COLOR]
   479: 000fe800    20 OBJECT  GLOBAL DEFAULT   35 dlimagedate_[COLOR=#FF5454]**4366c0**[/COLOR]
   518: 000fe81c 0xe6450 OBJECT  GLOBAL DEFAULT   35 dlarray_[COLOR=#FF5454]**4366c0**[/COLOR]
   625: 000022e4     4 OBJECT  GLOBAL DEFAULT   45 debug_params_[COLOR=#FF5454]**4366c0**[/COLOR]

[/FONT][FONT=monospace]5.) 0xe6450 is [/FONT]943184 in decimal (this is the bin file size)
[FONT=monospace]6.) Open up another brcmfmacXXXX.bin in bless to compare the start and stop tags for another firmware (I'm using [/FONT][FONT=monospace][COLOR=#000000]brcmfmac4366b-pcie.bin)
7.) We see a start hex of "[/COLOR][/FONT]00 F2 3E B8" as a starting point and "FWID: 01-c47a91a4...." as ending (4 bytes past the denoted as periods
8.) Search in dhd.ko using bless for [FONT=monospace][COLOR=#000000]"[/COLOR][/FONT]00 F2 3E B8"; Address at 0x137bbc which is 1276860 in decimal
9.) Copy out the firmware using dd: dd if=dhd.ko skip=1276860 ibs=1 count=943184 of=brcmfmac4366c-pcie.bin
10.) Open up the new brcmfmac4366c-pcie.bin file in Bless to check it out and ensure that we start with "00 F2 3E B8" and end with the FWID: "FWID: 01-fed440e1...."
- sha1sum is "[FONT=monospace][COLOR=#000000]9f97ebaf661631d6aa303d5e74a528cf1d95a016  brcmfmac4366c-pcie.bin"
[/COLOR][/FONT]11.) Put that in [FONT=monospace][COLOR=#000000]/lib/firmware/brcm and reaload the module.
[/COLOR][/FONT][FONT=monospace]12.) Check dmesg on your system and grep for errors.

This worked on my system and I now have perfect wi-fi using the [/FONT]ASUS PCE-AC88 4x4 Wireless AC3100 PCIe Adapter.[FONT=monospace]

[/FONT][FONT=monospace][COLOR=#000000]Linux x0 4.8.0-39-generic #42-Ubuntu SMP Mon Feb 20 11:47:27 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]DISTRIB_ID=Ubuntu[/COLOR]
DISTRIB_RELEASE=16.10
DISTRIB_CODENAME=yakkety
DISTRIB_DESCRIPTION="Ubuntu 16.10"

Credit to [/FONT]https://serialize.wordpress.com/2017/02/12/extract-4366c0-firmware/ for more detailed steps.[FONT=monospace]

Cheers.

[/FONT][FONT=monospace]
[/FONT]

I have a solution that kind of works with the wl drivers, but has issues with meeting my internet speed. What speeds are you able to get in a speedtest?

---

