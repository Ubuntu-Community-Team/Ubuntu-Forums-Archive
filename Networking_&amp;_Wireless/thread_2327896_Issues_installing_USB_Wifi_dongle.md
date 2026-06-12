---
title: "Issues installing USB Wifi dongle"
date: 2016-06-15
forum: Networking &amp; Wireless
---

### Post by ken55 on 2016-06-15
Not showing any wireless connections at all, not sure what to do (Tested on windows PC, works fine)...

Unit I purchased - [https://www.amazon.com/Adapter-Wireless-Internet-Including-demountable/dp/B01DJ6H7PM?ie=UTF8&ref_=zg_bs_13983791_2](https://www.amazon.com/Adapter-Wireless-Internet-Including-demountable/dp/B01DJ6H7PM?ie=UTF8&ref_=zg_bs_13983791_2)

Tried the guide in this thread for the 8192CU to no avail - [https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8192EU-chipset-0bda:818b-](https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8192EU-chipset-0bda:818b-)

*lspci -nnk | grep -iA2 net* -

```
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: Foxconn International, Inc. MCP61 Ethernet [105b:0d15]
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth
```



*lsusb* -

```
Bus 001 Device 003: ID 1058:1021 Western Digital Technologies, Inc. Elements Desktop (WDBAAU)
Bus 001 Device 002: ID **0bda:818b Realtek Semiconductor Corp.** 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```



*lsmod* -

```
Module                  Size  Used by
mac80211              659456  0
appletalk              36864  0
ipx                    28672  0
p8023                  16384  1 ipx
p8022                  16384  1 ipx
psnap                  16384  2 ipx,appletalk
llc                    16384  2 p8022,psnap
wl                   6152192  0
cfg80211              499712  2 wl,mac80211
ip6table_filter        16384  1
ip6_tables             20480  1 ip6table_filter
x_tables               24576  2 ip6table_filter,ip6_tables
nls_utf8               16384  1
isofs                  40960  1
ppdev                  20480  0
snd_hda_codec_realtek    73728  1
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     49152  1
snd_hda_intel          36864  5
snd_hda_codec         118784  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           61440  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
serio_raw              16384  0
edac_mce_amd           24576  0
snd_hwdep              16384  1 snd_hda_codec
k8temp                 16384  0
edac_core              49152  0
snd_pcm                94208  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
joydev                 20480  0
snd_seq_midi           16384  0
input_leds             16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            28672  1 snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    69632  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  1 snd
shpchp                 32768  0
8250_fintek            16384  0
parport_pc             32768  0
i2c_nforce2            16384  0
parport                45056  2 ppdev,parport_pc
mac_hid                16384  0
autofs4                40960  2
hid_logitech_hidpp     20480  0
hid_logitech_dj        20480  0
usbhid                 49152  0
hid                    98304  4 usbhid,hid_logitech_dj,hid_logitech_hidpp
uas                    20480  0
usb_storage            57344  2 uas
pata_acpi              16384  0
radeon               1466368  2
i2c_algo_bit           16384  1 radeon
ttm                    90112  1 radeon
drm_kms_helper        131072  1 radeon
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   311296  5 ttm,drm_kms_helper,radeon
psmouse               118784  0
sata_nv                24576  3
forcedeth              65536  0
pata_amd               16384  1
fjes                   28672  0
```



*iwconfig* -

```
enp0s7    no wireless extensions.

tun0      no wireless extensions.

lo        no wireless extensions.

```

Any help is appreciated.

Thanks,
Ken

---

### Post by Hadaka on 2016-06-15
Hi Ken,before we load the driver for your usb wifi, Let's see why
your internal card is not working or showing any wifi with ubuntu.
Please remove the USB wifi
You currently have the wifi "wl" driver loaded, that is for a broadcom card
let's remove that dirver. Please open a terminal ctrl/alt/t and do..
*The 2nd line may fail..that is ok..ignore
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
Next,please run this diagnostic wireless report.
Copy and paste
Open a terminal ctrl/alt/t then Copy and paste the following command
and press enter.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is **wireless-info.txt**
Next.
From your directory please copy,paste and post the **wireless-info.txt**

source..[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
thanks.

---

### Post by ken55 on 2016-06-15
> **Hadaka said:**
> Hi Ken,before we load the driver for your usb wifi, Let's see why
your internal card is not working or showing any wifi with ubuntu.
Please remove the USB wifi
You currently have the wifi "wl" driver loaded, that is for a broadcom card
let's remove that dirver. Please open a terminal ctrl/alt/t and do..
*The 2nd line may fail..that is ok..ignore
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
Next,please run this diagnostic wireless report.
Copy and paste
Open a terminal ctrl/alt/t then Copy and paste the following command
and press enter.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is **wireless-info.txt**
Next.
From your directory please copy,paste and post the **wireless-info.txt**

source..[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
thanks.

Hi Hadaka, Thanks for the response!

This is a desktop PC, It doesn't have internal wifi ;)

The 2nd command above did indeed fail...

Here is the wireless-info.txt:


```
########## wireless info START ##########

Report from: 15 Jun 2016 13:03 EDT -0400

Booted last: 15 Jun 2016 00:00 EDT -0400

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:25:16 UTC 2016 i686 athlon i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: Foxconn International, Inc. MCP61 Ethernet [105b:0d15]
    Kernel driver in use: forcedeth

##### lsusb #############################

Bus 001 Device 003: ID 1058:1021 Western Digital Technologies, Inc. Elements Desktop (WDBAAU)
Bus 001 Device 002: ID 0bda:818b Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

##### lsmod #############################

mac80211              659456  0
wl                   6152192  0
cfg80211              499712  2 wl,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s7    Link encap:Ethernet  HWaddr <MAC 'enp0s7' [IF1]>  
          inet addr:192.168.0.110  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:788938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:756512 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:255555775 (255.5 MB)  TX bytes:381893019 (381.8 MB)

tun0      Link encap:UNSPEC  HWaddr <MAC 'tun0' [IF2]>  
          inet addr:10.105.1.6  P-t-P:10.105.1.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:119577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:22997087 (22.9 MB)  TX bytes:54805369 (54.8 MB)

##### iwconfig ##########################

enp0s7    no wireless extensions.

tun0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.105.1.5      128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 enp0s7
10.105.1.1      10.105.1.5      255.255.255.255 UGH   0      0        0 tun0
10.105.1.5      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
128.0.0.0       10.105.1.5      128.0.0.0       UG    0      0        0 tun0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 enp0s7
208.167.254.234 192.168.0.1     255.255.255.255 UGH   0      0        0 enp0s7

##### resolv.conf #######################

nameserver 209.222.18.222
nameserver 209.222.18.218

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

    None found.

##### NetworkManager info ###############

Error: NetworkManager is not running.

Error: NetworkManager is not running.

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: America/Toronto (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp0s7    no frequency information.

tun0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp0s7    Interface doesn't support scanning.

tun0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[mac80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

modinfo: ERROR: Module wl not found.
[wl]

[cfg80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
install rtl8192cu /bin/false
install rtl8192c_common /bin/false
install rtlwifi /bin/false
install rtl8xxxu /bin/false

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

ethtool -A eth0 autoneg off
exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   35.409016] IPv6: ADDRCONF(NETDEV_UP): enp0s7: link is not ready
[   35.409585] forcedeth 0000:00:07.0 enp0s7: MSI enabled
[67503.070929] wl: module license 'MIXED/Proprietary' taints kernel.
[67503.096069] wl: module verification failed: signature and/or required key missing - tainting kernel
[68341.005540] forcedeth 0000:00:07.0 enp0s7: MSI enabled (repeated 3 times)

########## wireless info END ############
```

Thanks!
Ken

---

### Post by Hadaka on 2016-06-15
Ok, first i know nothing about tunneling so your routes and tunnels may
or may not be correct,
the wl dirver is still loaded? it is the driver that is in Additional drivers, proprietary
dirver...do not load that. please do again..
```
sudo apt-get remove --purge bcmwl-kernel-source
```

you also have both network managers loaded...Network Manager and Wcid
you cannot have both...only one.

your country code is not defined,...country 00: DFS-UNSET
Please copy and paste..
```
sudo iw reg set CA
sudo sed -i 's/^REG.*=$/&CA/' /etc/default/crda
```
Insert your USB wifi and do..
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
boot and test wireless
*If wireless fails run a new wireless report with the usb inserted
thanks.

---

### Post by ken55 on 2016-06-15
> **Hadaka said:**
> Ok, first i know nothing about tunneling so your routes and tunnels may
or may not be correct,
the wl dirver is still loaded? it is the driver that is in Additional drivers, proprietary
dirver...do not load that. please do again..
```
sudo apt-get remove --purge bcmwl-kernel-source
```

you also have both network managers loaded...Network Manager and Wcid
you cannot have both...only one.

your country code is not defined,...country 00: DFS-UNSET
Please copy and paste..
```
sudo iw reg set CA
sudo sed -i 's/^REG.*=$/&CA/' /etc/default/crda
```
Insert your USB wifi and do..
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
boot and test wireless
*If wireless fails run a new wireless report with the usb inserted
thanks.
As far as I know, WCID is the only network manager running...


```
##### NetworkManager info ###############

Error: NetworkManager is not running.
```

Broadcom driver was supposedly uninstalled...

```
Package 'bcmwl-kernel-source' is not installed, so not removed
```

Error when running - *sudo dkms install 8192cu/1.9*

```
htpc@htpchtpc:~$ sudo dkms install 8192cu/1.9
Error! Could not find module source directory.
Directory: /usr/src/8192cu-1.9 does not exist.


```

[I]Changed 1.9 to 1.10

[/I]```
htpc@htpchtpc:~$ sudo dkms install 8192cu/1.10
[sudo] password for htpc: 
Module 8192cu/1.10 already installed on kernel 4.4.0-24-generic/i686
```

---

### Post by ken55 on 2016-06-18
Still no wifi and could use some more guidance.

Thanks,
Ken

---

### Post by gordintoronto on 2016-06-18
[https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8192EU-chipset-0bda:818b-](https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8192EU-chipset-0bda:818b-)

---

### Post by jeremy31 on 2016-06-18
Is secure boot enabled?

---

### Post by ken55 on 2016-06-19
> **gordintoronto said:**
> [https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8192EU-chipset-0bda:818b-](https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8192EU-chipset-0bda:818b-)

That was the very 1st thing I tried, to no avail. :(

---

### Post by ken55 on 2016-06-19
> **jeremy31 said:**
> Is secure boot enabled?

I have no idea :confused: How do I check? Should it be?

---

### Post by jeremy31 on 2016-06-20
> **ken55 said:**
> I have no idea :confused: How do I check? Should it be?

It is a setting in BIOS and it will need to be disabled or it will prevent your compiled driver from loading.  See what happens when trying to manually load
```
sudo modprobe -v 8192cu
```

---

### Post by ken55 on 2016-06-20
> **jeremy31 said:**
> It is a setting in BIOS and it will need to be disabled or it will prevent your compiled driver from loading.  See what happens when trying to manually load
```
sudo modprobe -v 8192cu
```

Here is the output:
```
insmod /lib/modules/4.4.0-24-generic/updates/dkms/8192cu.ko rtw_power_mgnt=0 rtw_enusbss=0 


```

Not seeing the "Secure Boot" Option.. This is an older PC ([http://www.newegg.com/Product/Product.aspx?Item=N82E16883114036](http://www.newegg.com/Product/Product.aspx?Item=N82E16883114036)) not sure if that makes any difference.

Thanks,
Ken

---

### Post by jeremy31 on 2016-06-21
The pvaret driver doesn't have support for this chip as it seems to be a rtl8723eu and there is a driver on github that appears to be patched for 16.04
```
git clone https://github.com/feedcafe/rtl8192eu.git
sudo dkms add ./rtl8192eu
sudo dkms build -m rtl8192eu -v 0.1.0
sudo dkms install -m rtl8192eu -v 0.1.0
```

Reboot

---

### Post by ken55 on 2016-06-21
Edit: Works now!! Thanks, Jeremy!!

Only 1 issue is the speed. I am getting <2mbps download speed of my 100mb connection, tested thru speedtest.net


I read this thread here, but not sure how to edit the commands to fit for my wifi driver: [http://ubuntuforums.org/showthread.php?t=2175345](http://ubuntuforums.org/showthread.php?t=2175345)

Thanks again!
Ken

---

### Post by jeremy31 on 2016-06-21
Run the wireless script again and post the new results

---

### Post by ken55 on 2016-06-21
> **jeremy31 said:**
> Run the wireless script again and post the new results

```


########## wireless info START ##########


Report from: 21 Jun 2016 10:54 EDT -0400


Booted last: 21 Jun 2016 00:00 EDT -0400


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:25:16 UTC 2016 i686 athlon i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
	Subsystem: Foxconn International, Inc. MCP61 Ethernet [105b:0d15]
	Kernel driver in use: forcedeth


##### lsusb #############################


Bus 001 Device 002: ID 1058:1021 Western Digital Technologies, Inc. Elements Desktop (WDBAAU)
Bus 001 Device 004: ID 0bda:818b Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


'pccardctl' is not installed (package "pcmciautils").


##### rfkill ############################


##### lsmod #############################


cfg80211              499712  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp0s7    Link encap:Ethernet  HWaddr <MAC 'enp0s7' [IF1]>  
          inet addr:192.168.0.110  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:682545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:571360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:763632647 (763.6 MB)  TX bytes:160579976 (160.5 MB)


enx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'enx<IF from MAC [IF2]>' [IF2]>  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3cee:d3dc:772f:a498/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9087 errors:0 dropped:5 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1291544 (1.2 MB)  TX bytes:46438 (46.4 KB)


##### iwconfig ##########################


enp0s7    no wireless extensions.


lo        no wireless extensions.


enx<IF from MAC [IF2]>  IEEE 802.11bgn  ESSID:"TP-LINK_2.4GHz_EC07E1"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'TP-LINK_2.4GHz_EC07E1' [AC1]>   
          Bit Rate:144.4 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp0s7
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 enx<IF from MAC [IF2]>
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s7
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 enx<IF from MAC [IF2]>


##### resolv.conf #######################


nameserver 209.222.18.222
nameserver 209.222.18.218


##### network managers ##################


Installed:


	NetworkManager
	Wicd


Running:


root       623     1  0 08:50 ?        00:00:04 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp0s7
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         NVIDIA Corporation
GENERAL.PRODUCT:                        MCP61 Ethernet
GENERAL.DRIVER:                         forcedeth
GENERAL.DRIVER-VERSION:                 0.64
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp0s7' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:07.0/net/enp0s7
GENERAL.IP-IFACE:                       enp0s7
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       8543f278-2803-4f03-9af1-cdcf50110d7c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{29}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8543f278-2803-4f03-9af1-cdcf50110d7c | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.110/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             192.168.0.1
IP4.DNS[2]:                             8.8.8.8
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1466526807
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.110
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n NIC
GENERAL.DRIVER:                         rtl8192eu
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2:1.0/net/enx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       enx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     TP-LINK_2.4GHz_EC07E1
GENERAL.CON-UUID:                       6226b91f-d02e-46c7-af79-d0012d596c5a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{38}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6226b91f-d02e-46c7-af79-d0012d596c5a | TP-LINK_2.4GHz_EC07E1
IP4.ADDRESS[1]:                         192.168.0.106/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1466528037
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.106
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::3cee:d3dc:772f:a498/64
IP6.GATEWAY:                            


SSID                   BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
TP-LINK_2.4GHz_EC07E1  <MAC 'TP-LINK_2.4GHz_EC07E1' [AC1]>  Infra  1     2412 MHz  44 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     * 
xfinitywifi            <MAC 'xfinitywifi' [AC3]>  Infra  6     2437 MHz  44 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --         no        
--                     <MAC '' [AC2]>  Infra  6     2437 MHz  44 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
--                     <MAC '--' [AN4]>  Infra  9     2452 MHz  14 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
--                     <MAC '--' [AN5]>  Infra  9     2452 MHz  14 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
HOME-1F68              <MAC 'HOME-1F68' [AC5]>  Infra  9     2452 MHz  14 Mbit/s  48      &#9602;&#9604;__  WPA1 WPA2  no        


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/TP-LINK_2.4GHz_EC07E1]] (600 root)
[connection] id=TP-LINK_2.4GHz_EC07E1 | type=wifi | permissions=user:htpc:;
[wifi] mac-address=<MAC 'enx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=TP-LINK_2.4GHz_EC07E1
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Toronto (based on set time zone)


country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


enp0s7    no frequency information.


lo        no frequency information.


enx<IF from MAC [IF2]>  13 channels in total; available frequencies :
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
          Current Frequency=2.412 GHz (Channel 1)


##### iwlist scan #######################


enp0s7    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.452 GHz (Channel 9)


enx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'TP-LINK_2.4GHz_EC07E1' [AC1]>
                    ESSID:"TP-LINK_2.4GHz_EC07E1"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=100/100  
                    Extra:fm=0003
          Cell 02 - Address: <MAC '' [AC2]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=20/100  Signal level=100/100  
                    Extra:fm=0001
          Cell 03 - Address: <MAC 'xfinitywifi' [AC3]>
                    ESSID:"xfinitywifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:300 Mb/s
                    Quality=61/100  Signal level=100/100  
                    Extra:fm=0003
          Cell 04 - Address: <MAC '' [AC4]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Quality=90/100  Signal level=74/100  
                    Extra:fm=0001
          Cell 05 - Address: <MAC 'HOME-1F68' [AC5]>
                    ESSID:"HOME-1F68"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Quality=32/100  Signal level=47/100  
                    Extra:fm=0003


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


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
blacklist rtl8192cu


[/etc/modprobe.d/blacklist-native-rtl8192.conf]
install rtl8192cu /bin/false
install rtl8192c_common /bin/false
install rtlwifi /bin/false
install rtl8xxxu /bin/false


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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


ethtool -A eth0 autoneg off
exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   36.856445] IPv6: ADDRCONF(NETDEV_UP): enp0s7: link is not ready
[   36.857023] forcedeth 0000:00:07.0 enp0s7: MSI enabled
[ 1626.620370] RTL871X: rtl8192eu v4.3.1.1_11320.20140505
[ 1626.785847] RTL871X: rtw_ndev_init(wlan0)
[ 1626.908832] rtl8192eu 1-2:1.0 enx<IF from MAC [IF2]>: renamed from wlan0
[ 1626.939778] IPv6: ADDRCONF(NETDEV_UP): enx<IF from MAC [IF2]>: link is not ready (repeated 4 times)
[ 1920.995536] IPv6: ADDRCONF(NETDEV_CHANGE): enx<IF from MAC [IF2]>: link becomes ready


########## wireless info END ############



```

---

### Post by jeremy31 on 2016-06-21
post the result for ```
modinfo -p 8192eu
```
See if this works

---

### Post by ken55 on 2016-06-21
> **jeremy31 said:**
> post the result for ```
modified -p rtl8723eu
```

```
modified: command not found
```

```
modprobe: invalid option -- 'p'
```

Not sure if you meant "modprobe -v" but here is the output of that:

```
modprobe: FATAL: Module rtl8723eu not found in directory /lib/modules/4.4.0-24-generic
```

---

### Post by jeremy31 on 2016-06-21
stupid new phone
I will try editing the other post

---

### Post by ken55 on 2016-06-21
> **jeremy31 said:**
> post the result for ```
modinfo -p rtl8723eu
```
```
htpc@htpchtpc:~$ modinfo -p rtl8723eu
modinfo: ERROR: Module rtl8723eu not found.

```

In case you meant "8192eu":

```
htpc@htpchtpc:~$ modinfo -p rtl8192eu
modinfo: ERROR: Module rtl8192eu not found.
```

---

### Post by jeremy31 on 2016-06-21
I got home and compiled the driver myself, the module is 8192eu.ko and we should be able to use the same commands as the 8192cu to disable power management
```
echo "options 8192eu rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/rtl8192eu.conf
```
Reboot

---

### Post by ken55 on 2016-06-21
> **jeremy31 said:**
> I got home and compiled the driver myself, the module is 8192eu.ko and we should be able to use the same commands as the 8192cu to disable power management
```
echo "options options 8192eu rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/rtl8192eu.conf
```
Reboot

Output:

```
options options 8192eu rtw_power_mgnt=0 rtw_enusbss=0
```

I am currently connected to my home pc via teamviewer and if I restart it, I wont be able to reconnect (some buggy issue with teamviewer, or ports or something). Is there a service i can restart to mimic whatever needs to happen with the reboot?

Thanks,
Ken

---

### Post by jeremy31 on 2016-06-21
I messed up that command too, it should be
```
echo "options 8192eu rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/rtl8192eu.conf
```

The option will disconnect your internet for a little bit
```
sudo modprobe -r 8192eu
sudo modprobe 8192eu rtw_power_mgnt=0 rtw_enusbss=0
```

---

### Post by ken55 on 2016-06-21
> **jeremy31 said:**
> I messed up that command too, it should be
```
echo "options 8192eu rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/rtl8192eu.conf
```

The option will disconnect your internet for a little bit
```
sudo modprobe -r 8192eu
sudo modprobe 8192eu rtw_power_mgnt=0 rtw_enusbss=0
```

I'm home now :)

```
options 8192eu rtw_power_mgnt=0 rtw_enusbss=0


```

I'm getting 17mbps down now on the linux desktop, sitting right next to my router. My windows laptop, also next to the router using the same dongle is getting 70mbps. So something still seems to be a bit off :-/

Thanks,
Ken

---

### Post by jeremy31 on 2016-06-22
Having Network Manager and WICD running may cause problems.  I would also change the settings for the wireless connection in Network Manager for IPv6 to ignore.  Set the country code with ```
sudo iw reg set CA
sudo sed -i 's/^REG.*=$/&CA/' /etc/default/crda
```

See if the wifi router will allow you to change the encryption to WPA2 only as it has WPA/WPA2 enabled

---

### Post by ken55 on 2016-06-22
> **jeremy31 said:**
> Having Network Manager and WICD running may cause problems.  I would also change the settings for the wireless connection in Network Manager for IPv6 to ignore.  Set the country code with ```
sudo iw reg set CA
sudo sed -i 's/^REG.*=$/&CA/' /etc/default/crda
```

See if the wifi router will allow you to change the encryption to WPA2 only as it has WPA/WPA2 enabled

I uninstalled WICD the other day, I can't figure out why it still shows as they are both installed.

```
htpc@htpchtpc:~$ sudo apt-get remove wicd wicd-gtk
[sudo] password for htpc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'wicd' is not installed, so not removed
Package 'wicd-gtk' is not installed, so not removed

```
[x] change the settings for the wireless connection in Network Manager for IPv6 to ignore
[x] Set the country code
[x] wifi router changed the encryption to WPA2 only

Speeds still between 15-20mbps :(

```
 

########## wireless info START ##########


Report from: 22 Jun 2016 10:19 EDT -0400


Booted last: 22 Jun 2016 00:00 EDT -0400


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:25:16 UTC 2016 i686 athlon i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
	Subsystem: Foxconn International, Inc. MCP61 Ethernet [105b:0d15]
	Kernel driver in use: forcedeth


##### lsusb #############################


Bus 001 Device 004: ID 0bda:818b Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 1058:1021 Western Digital Technologies, Inc. Elements Desktop (WDBAAU)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


'pccardctl' is not installed (package "pcmciautils").


##### rfkill ############################


##### lsmod #############################


cfg80211              499712  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp0s7    Link encap:Ethernet  HWaddr <MAC 'enp0s7' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


enx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'enx<IF from MAC [IF2]>' [IF2]>  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7076 errors:0 dropped:119 overruns:0 frame:0
          TX packets:11725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3934373 (3.9 MB)  TX bytes:6837161 (6.8 MB)


tun0      Link encap:UNSPEC  HWaddr <MAC 'tun0' [IF3]>  
          inet addr:10.120.1.6  P-t-P:10.120.1.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:3809 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6791 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:851169 (851.1 KB)  TX bytes:5348813 (5.3 MB)


##### iwconfig ##########################


enp0s7    no wireless extensions.


tun0      no wireless extensions.


lo        no wireless extensions.


enx<IF from MAC [IF2]>  IEEE 802.11bgn  ESSID:"TP-LINK_2.4GHz_EC07E1"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'TP-LINK_2.4GHz_EC07E1' [AC1]>   
          Bit Rate:144.4 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=72/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.120.1.5      128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 enx<IF from MAC [IF2]>
10.120.1.1      10.120.1.5      255.255.255.255 UGH   0      0        0 tun0
10.120.1.5      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
108.61.152.250  192.168.0.1     255.255.255.255 UGH   0      0        0 enx<IF from MAC [IF2]>
128.0.0.0       10.120.1.5      128.0.0.0       UG    0      0        0 tun0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 enx<IF from MAC [IF2]>


##### resolv.conf #######################


nameserver 209.222.18.222
nameserver 209.222.18.218


##### network managers ##################


Installed:


	NetworkManager
	Wicd


Running:


root       581     1  0 10:15 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         tun0
GENERAL.TYPE:                           tun
GENERAL.NM-TYPE:                        NMDeviceTun
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         tun
GENERAL.DRIVER-VERSION:                 1.6
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/tun0
GENERAL.IP-IFACE:                       tun0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     tun0
GENERAL.CON-UUID:                       f24ad372-52fc-49f1-8f4d-61aa42489f9d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{38}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f24ad372-52fc-49f1-8f4d-61aa42489f9d | tun0
IP4.ADDRESS[1]:                         10.120.1.6/32
IP4.GATEWAY:                            
IP4.ROUTE[1]:                           dst = 0.0.0.0/1, nh = 10.120.1.5, mt = 0
IP4.ROUTE[2]:                           dst = 10.120.1.1/32, nh = 10.120.1.5, mt = 0
IP4.ROUTE[3]:                           dst = 128.0.0.0/1, nh = 10.120.1.5, mt = 0
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n NIC
GENERAL.DRIVER:                         rtl8192eu
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.1/usb1/1-7/1-7:1.0/net/enx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       enx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     TP-LINK_2.4GHz_EC07E1
GENERAL.CON-UUID:                       6226b91f-d02e-46c7-af79-d0012d596c5a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     144 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{15}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6226b91f-d02e-46c7-af79-d0012d596c5a | TP-LINK_2.4GHz_EC07E1
IP4.ADDRESS[1]:                         192.168.0.106/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 108.61.152.250/32, nh = 192.168.0.1, mt = 0
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1466612169
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.106
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp0s7
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         NVIDIA Corporation
GENERAL.PRODUCT:                        MCP61 Ethernet
GENERAL.DRIVER:                         forcedeth
GENERAL.DRIVER-VERSION:                 0.64
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp0s7' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:07.0/net/enp0s7
GENERAL.IP-IFACE:                       
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
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID                   BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
--                     <MAC '' [AC2]>  Infra  6     2437 MHz  44 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
xfinitywifi            <MAC 'xfinitywifi' [AC3]>  Infra  6     2437 MHz  44 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --         no        
--                     <MAC '' [AC5]>  Infra  9     2452 MHz  14 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2       no        
--                     <MAC '' [AC6]>  Infra  9     2452 MHz  14 Mbit/s  73      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
TP-LINK_2.4GHz_EC07E1  <MAC 'TP-LINK_2.4GHz_EC07E1' [AC1]>  Infra  1     2412 MHz  44 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
--                     <MAC '' [AC4]>  Infra  9     2452 MHz  14 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
HOME-1F68              <MAC 'HOME-1F68' [AC7]>  Infra  9     2452 MHz  14 Mbit/s  52      &#9602;&#9604;__  WPA1 WPA2  no        


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/TP-LINK_2.4GHz_EC07E1]] (600 root)
[connection] id=TP-LINK_2.4GHz_EC07E1 | type=wifi | permissions=user:htpc:;
[wifi] mac-address=<MAC 'enx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=TP-LINK_2.4GHz_EC07E1
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: America/Toronto (based on set time zone)


country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


enp0s7    no frequency information.


tun0      no frequency information.


lo        no frequency information.


enx<IF from MAC [IF2]>  13 channels in total; available frequencies :
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
          Current Frequency=2.412 GHz (Channel 1)


##### iwlist scan #######################


enp0s7    Interface doesn't support scanning.


tun0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.452 GHz (Channel 9)


enx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'TP-LINK_2.4GHz_EC07E1' [AC1]>
                    ESSID:"TP-LINK_2.4GHz_EC07E1"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=72/100  Signal level=100/100  
                    Extra:fm=0003
          Cell 02 - Address: <MAC '' [AC2]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=100/100  
                    Extra:fm=0001
          Cell 03 - Address: <MAC 'xfinitywifi' [AC3]>
                    ESSID:"xfinitywifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:300 Mb/s
                    Quality=78/100  Signal level=100/100  
                    Extra:fm=0003
          Cell 04 - Address: <MAC '' [AC4]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=70/100  
                    Extra:fm=0001
          Cell 05 - Address: <MAC '' [AC5]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=20/100  Signal level=74/100  
                    Extra:fm=0001
          Cell 06 - Address: <MAC '' [AC6]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Quality=16/100  Signal level=73/100  
                    Extra:fm=0001
          Cell 07 - Address: <MAC 'HOME-1F68' [AC7]>
                    ESSID:"HOME-1F68"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Quality=55/100  Signal level=52/100  
                    Extra:fm=0003


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


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
blacklist rtl8192cu


[/etc/modprobe.d/blacklist-native-rtl8192.conf]
install rtl8192cu /bin/false
install rtl8192c_common /bin/false
install rtlwifi /bin/false
install rtl8xxxu /bin/false


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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/rtl8192eu.conf]
options 8192eu rtw_power_mgnt=0 rtw_enusbss=0


##### rc.local ##########################


ethtool -A eth0 autoneg off
exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   17.697895] RTL871X: rtl8192eu v4.3.1.1_11320.20140505
[   17.854570] RTL871X: rtw_ndev_init(wlan0)
[   17.956706] rtl8192eu 1-7:1.0 enx<IF from MAC [IF2]>: renamed from wlan0
[   37.500751] IPv6: ADDRCONF(NETDEV_UP): enp0s7: link is not ready
[   37.501332] forcedeth 0000:00:07.0 enp0s7: MSI enabled
[   37.501549] forcedeth 0000:00:07.0 enp0s7: no link during initialization
[   37.501842] IPv6: ADDRCONF(NETDEV_UP): enp0s7: link is not ready
[   38.003018] IPv6: ADDRCONF(NETDEV_UP): enx<IF from MAC [IF2]>: link is not ready (repeated 3 times)
[   51.692525] IPv6: ADDRCONF(NETDEV_CHANGE): enx<IF from MAC [IF2]>: link becomes ready


########## wireless info END ############

```

---

### Post by jeremy31 on 2016-06-22
That bit rate is pretty high and may be part of the problem but I haven't had any luck changing the bit rate on my wifi card

---

### Post by ken55 on 2016-06-22
> **jeremy31 said:**
> That bit rate is pretty high and may be part of the problem but I haven't had any luck changing the bit rate on my wifi card

Should I mark this as "solved" and open a different thread about the speed issue?

Thanks again Jeremy!
Ken

---

### Post by jeremy31 on 2016-06-22
I think that would be acceptable

---

