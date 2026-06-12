---
title: "Wifi not working on Lenovo E10-30 Laptop"
date: 2015-09-05
forum: Networking &amp; Wireless
---

### Post by Panashe on 2015-09-05
Hi, I am a newbie to Ubuntu. I have just replaced Windows 8 with Ubuntu 14.04 on my Lenovo E10-30 net-book. My challenge now is that Wifi Network has disappeared. In the meantime I am able to make use of Ethernet connection though. Please assist me fix this problem.

```


########## wireless info START ##########

Report from: 05 Sep 2015 22:47 CAT +0200

Booted last: 05 Sep 2015 22:10 CAT +0200

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-48-generic #64~14.04.1-Ubuntu SMP Thu Aug 20 23:03:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Lenovo Device [17aa:3815]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo Device [17aa:0621]
    Kernel driver in use: bcma-pci-bridge

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 105b:e065  
Bus 001 Device 003: ID 058f:5608 Alcor Micro Corp. 
Bus 001 Device 002: ID 3938:1031  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              498458  0 
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104112  6 snd_soc_rt5640,snd_soc_core,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
bcma                   52320  0 
ideapad_laptop         18278  0 
sparse_keymap          13948  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.100.2  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2682 errors:0 dropped:47 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3245527 (3.2 MB)  TX bytes:364132 (364.1 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.1   0.0.0.0         UG    0      0        0 eth0
192.168.100.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       866     1  0 22:10 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
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
    Address:         192.168.100.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.100.1

    DNS:             192.168.100.1

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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi | type=802-11-wireless
[802-11-wireless] ssid=HUAWEI-2pEA | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Africa/Harare (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.16.0-48-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     046346857FD53951C911443
depends:        
intree:         Y
vermagic:       3.16.0-48-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A1:44:3F:3B:F3:4A:21:57:C7:23:F6:CD:E2:AE:9C:14:9E:CD:2A:6A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[bcma]
filename:       /lib/modules/3.16.0-48-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     D52E980A55E0AC3C372382C
depends:        
intree:         Y
vermagic:       3.16.0-48-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A1:44:3F:3B:F3:4A:21:57:C7:23:F6:CD:E2:AE:9C:14:9E:CD:2A:6A
sig_hashalgo:   sha512

##### module parameters #################

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[ 1246.834414] Modules linked in: bnep rfcomm bluetooth 6lowpan_iphc nls_iso8859_1 snd_hda_codec_realtek snd_hda_codec_generic uvcvideo snd_hda_intel snd_soc_rt5640 intel_rapl intel_soc_dts_thermal intel_powerclamp coretemp videobuf2_vmalloc videobuf2_memops snd_soc_rl6231 snd_hda_controller snd_soc_core i915 snd_hda_codec snd_compress snd_pcm_dmaengine snd_hwdep videobuf2_core kvm_intel snd_pcm dm_multipath snd_seq_midi snd_seq_midi_event snd_rawmidi v4l2_common kvm snd_seq bcma scsi_dh drm_kms_helper videodev media crct10dif_pclmul crc32_pclmul ghash_clmulni_intel cryptd rtsx_pci_ms memstick joydev snd_seq_device snd_timer serio_raw mei_txe drm snd mei ideapad_laptop intel_smartconnect sparse_keymap dw_dmac dw_dmac_core video i2c_hid soundcore snd_soc_sst_acpi i2c_designware_platform i2c_algo_bit i2c_designware_core shpchp spi_pxa2xx_platform iosf_mbi pwm_lpss lpc_ich 8250_dw mac_hid parport_pc ppdev lp parport hid_generic usbhid hid rtsx_pci_sdmmc psmouse r8169 rtsx_pci mii ahci libahci dm_mirror dm_region_hash dm_log sdhci_acpi sdhci

########## wireless info END ############

```

---

### Post by jeremy31 on 2015-09-06
According to the Broadcom sticky post in Networking and wireless, that chipset works with bcmwl 
```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```

It may need a reboot, then check ```
rfkill list all
``` And see if it still has Soft blocked: yes  If it does see if ```
rfkill unblock all
``` allows the wifi to work

---

### Post by Panashe on 2015-09-06
Hi Jeremy31

Many thanks for providing the solution for the WIFI problem. Greatly appreciated. The Wifi Network is now available and I am actually using it to post this message. 

I notice "Bluetooth" is shown as disabled. Is there  something that I can do to fix the bluetooth issue? Ive run the "rfkill list all" command and got the following:

```
panashe@panashe-Lenovo-E10-30:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

### Post by jeremy31 on 2015-09-07
Bug reports will have to be filed to get bluetooth working. [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
I know bluetooth worked on the 3.13 kernels for your chipset but a regression happened and btusb doesn't try to load the firmware in the newer kernels

---

### Post by Ben_Shaver on 2015-09-07
With the installation USB plugged in, go to Settings>Software&Updates>Additional Drivers, and then tick all (if any) boxes. Not entirely sure this would work, judging from what jeremy31 has said, but it's worth a shot I suppose.

---

### Post by howefield on 2015-09-07
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by jeremy31 on 2015-09-07
I just made a dkms update for the bluetooth,  Install [https://www.dropbox.com/s/6yau4ieg6iv47xo/btusb-dkms_3.0_all.deb?dl=0](https://www.dropbox.com/s/6yau4ieg6iv47xo/btusb-dkms_3.0_all.deb?dl=0)
```
wget http://www.gnebehay.com/blog/lenovo-flexpad-bluetooth-debian/BCM43142A0-105b-e065.hcd
sudo cp BCM43142A0-105b-e065.hcd /lib/firmware/brcm/
```


Reboot and post the results from ```
dmesg | egrep -i 'blue|firm'
```

---

### Post by Panashe on 2015-09-10
Hi
i have run the commands as instructed above, and got the following result:

[code]

panashe@panashe-Lenovo-E10-30:~$ dmesg | egrep -i 'blue|firm'
[    0.135487] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.486714] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    1.999831] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f00)
[   16.527426] Bluetooth: Core ver 2.19
[   16.527454] Bluetooth: HCI device and connection manager initialized
[   16.527463] Bluetooth: HCI socket layer initialized
[   16.527467] Bluetooth: L2CAP socket layer initialized
[   16.527482] Bluetooth: SCO socket layer initialized
[   16.553161] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.553166] Bluetooth: BNEP filters: protocol multicast
[   16.553178] Bluetooth: BNEP socket layer initialized
[   16.638959] Bluetooth: RFCOMM TTY layer initialized
[   16.638975] Bluetooth: RFCOMM socket layer initialized
[   16.638986] Bluetooth: RFCOMM ver 1.11
panashe@panashe-Lenovo-E10-30:~$ 

[code/]

---

### Post by jeremy31 on 2015-09-10
check ```
lsmod | grep btusb
``` to see if it is loaded, if not ```
sudo modprobe -v btusb
``` then see if there are any new messages from ```
dmesg | tail
```

---

### Post by Panashe on 2015-09-11
see the result after running the commands suggested:

```

panashe@panashe-Lenovo-E10-30:~$ wget http://www.gnebehay.com/blog/lenovo-flexpad-bluetooth-debian/BCM43142A0-105b-e065.hcd
--2015-09-11 07:47:00--  http://www.gnebehay.com/blog/lenovo-flexpad-bluetooth-debian/BCM43142A0-105b-e065.hcd
Resolving www.gnebehay.com (www.gnebehay.com)... 77.37.11.150
Connecting to www.gnebehay.com (www.gnebehay.com)|77.37.11.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 28681 (28K)
Saving to: ‘BCM43142A0-105b-e065.hcd.2’

100%[======================================>] 28,681       103KB/s   in 0.3s   

2015-09-11 07:47:01 (103 KB/s) - ‘BCM43142A0-105b-e065.hcd.2’ saved [28681/28681]

panashe@panashe-Lenovo-E10-30:~$ sudo cp BCM43142A0-105b-e065.hcd /lib/firmware/brcm/
panashe@panashe-Lenovo-E10-30:~$ dmesg | egrep -i 'blue|firm'
[    0.135137] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.486355] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    1.970329] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f00)
[   15.955216] Bluetooth: Core ver 2.19
[   15.955254] Bluetooth: HCI device and connection manager initialized
[   15.955264] Bluetooth: HCI socket layer initialized
[   15.955269] Bluetooth: L2CAP socket layer initialized
[   15.955291] Bluetooth: SCO socket layer initialized
[   15.961629] Bluetooth: RFCOMM TTY layer initialized
[   15.961645] Bluetooth: RFCOMM socket layer initialized
[   15.961653] Bluetooth: RFCOMM ver 1.11
[   16.089861] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.089866] Bluetooth: BNEP filters: protocol multicast
[   16.089877] Bluetooth: BNEP socket layer initialized
panashe@panashe-Lenovo-E10-30:~$ lsmod | grep btusb
btusb                  32497  0 
bluetooth             446409  11 bnep,btusb,rfcomm
panashe@panashe-Lenovo-E10-30:~$ sudo modprobe -v btusb
panashe@panashe-Lenovo-E10-30:~$ dmesg | tail
[  152.628081] cfg80211: Calling CRDA to update world regulatory domain
[  152.648832] cfg80211: World regulatory domain updated:
[  152.648853] cfg80211:  DFS Master region: unset
[  152.648862] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  152.648881] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  152.648896] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  152.648910] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[  152.648924] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  152.648938] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  388.575817] usbcore: registered new interface driver btusb

```

i've attached 2 screenshots to provide more information. Not sure if it'll help.

---

### Post by jeremy31 on 2015-09-11
Try ```
wget https://www.dropbox.com/s/6yau4ieg6iv47xo/btusb-dkms_3.0_all.deb
```
```
dpkg -i btusb-dkms_3.0_all.deb
```
```
sudo modprobe -r btusb
```
```
sudo modprobe btusb
```

---

### Post by Panashe on 2015-09-12
Error message as highlighted below:

```

panashe@panashe-Lenovo-E10-30:~$ wget https://www.dropbox.com/s/6yau4ieg6iv47xo/btusb-dkms_3.0_all.deb
--2015-09-12 12:29:01--  https://www.dropbox.com/s/6yau4ieg6iv47xo/btusb-dkms_3.0_all.deb
Resolving www.dropbox.com (www.dropbox.com)... 108.160.172.206, 108.160.172.238
Connecting to www.dropbox.com (www.dropbox.com)|108.160.172.206|:443... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: https://dl.dropboxusercontent.com/content_link/y9KiIopEu2iZcHRzVflMoYj3rfy1CV4X0sGATezA1lZpCYhHZneOjxDai33czGGo [following]
--2015-09-12 12:29:03--  https://dl.dropboxusercontent.com/content_link/y9KiIopEu2iZcHRzVflMoYj3rfy1CV4X0sGATezA1lZpCYhHZneOjxDai33czGGo
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 107.22.191.122, 54.243.96.35, 23.23.237.190, ...
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|107.22.191.122|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17194 (17K) [application/x-debian-package]
Saving to: ‘btusb-dkms_3.0_all.deb.1’

100%[======================================>] 17,194      --.-K/s   in 0.002s  

2015-09-12 12:29:05 (7.20 MB/s) - ‘btusb-dkms_3.0_all.deb.1’ saved [17194/17194]

[COLOR=#ff0000]panashe@panashe-Lenovo-E10-30:~$ dpkg -i btusb-dkms_3.0_all.deb
dpkg: error: requested operation requires superuser privilege[/COLOR]
panashe@panashe-Lenovo-E10-30:~$ sudo modprobe -r btusb
[sudo] password for panashe: 
panashe@panashe-Lenovo-E10-30:~$ sudo modprobe btusb
panashe@panashe-Lenovo-E10-30:~$ 

```

---

### Post by jeremy31 on 2015-09-12
```
sudo dpkg -i btusb-dkms_3.0_all.deb
```

---

### Post by Panashe on 2015-09-13
Done as recommended. I've encountered another error message highlighted below in red font:
```

panashe@panashe-Lenovo-E10-30:~$ sudo dpkg -i btusb-dkms_3.0_all.deb
(Reading database ... 213524 files and directories currently installed.)
Preparing to unpack btusb-dkms_3.0_all.deb ...

------------------------------
Deleting module version: 3.0
completely from the DKMS tree.
------------------------------
Done.
Unpacking btusb-dkms (3.0) over (3.0) ...
Setting up btusb-dkms (3.0) ...
Loading new btusb-3.0 DKMS files...
First Installation: checking all kernels...
Building only for 3.16.0-48-generic
Building for architecture x86_64
Building initial module for 3.16.0-48-generic
[COLOR=#ff0000]Error! Bad return status for module build on kernel: 3.16.0-48-generic (x86_64)
Consult /var/lib/dkms/btusb/3.0/build/make.log for more information.[/COLOR]
panashe@panashe-Lenovo-E10-30:~$ 

```

---

### Post by jeremy31 on 2015-09-13
Forgot you had the 3.16 kernel so this one should work
```
wget https://www.dropbox.com/s/84ep5hgbnwv5vz4/btusb-dkms_4.0_all.deb
sudo dpkg -i btusb-dkms_4.0_all.deb
```
Reboot

If you ever switch to the 3.19 kernel you will need to use the btusb-dkms_3.0_all.deb

---

### Post by Panashe on 2015-09-18
Hi JEREMY 31. I NOW HAVE BOTH WIFI AND BLUETOOTH FULLY FUNCTIONAL. MANY THANKS AND GREATLY APPRECIATED.

---

