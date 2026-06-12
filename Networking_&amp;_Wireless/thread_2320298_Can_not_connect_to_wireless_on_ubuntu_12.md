---
title: "Can not connect to wireless on ubuntu 12"
date: 2016-04-12
forum: Networking &amp; Wireless
---

### Post by roya2 on 2016-04-12
Hi ,
Can anyone help me why I can not connect to a wireless network on ubuntu? It does not detect the wireless network.
The output of some of the commands that might help for understanding the issue. I really appreciate your help. Thank you.

```
eth0      no wireless extensions.
lo        no wireless extensions.
```
```
ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
```
rfkill list all shows nothing
```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr f8:bc:12:7e:f0:78  
          inet addr:192.168.0.30  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::fabc:12ff:fe7e:f078/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27553145 (27.5 MB)  TX bytes:1926369 (1.9 MB)
          Interrupt:44 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:245375 (245.3 KB)  TX bytes:245375 (245.3 KB)
```
```
lsusb :
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 413c:2107 Dell Computer Corp. 
Bus 003 Device 003: ID 046d:c077 Logitech, Inc. 
Bus 003 Device 004: ID 0c45:64d8 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 4242:ee02 USB Design by Example 

```
```
lspci -nn | grep 028003:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
```
```
dmesg | grep -e wlan -e b43

[ 1641.157756] b43: disagrees about version of symbol ieee80211_get_response_rate
[ 1641.157759] b43: Unknown symbol ieee80211_get_response_rate (err -22)
[ 1641.157790] b43: disagrees about version of symbol ieee80211_free_hw
[ 1641.157791] b43: Unknown symbol ieee80211_free_hw (err -22)
[ 1641.157797] b43: disagrees about version of symbol ieee80211_alloc_hw
[ 1641.157798] b43: Unknown symbol ieee80211_alloc_hw (err -22)
[ 1641.157805] b43: disagrees about version of symbol ieee80211_register_hw
[ 1641.157806] b43: Unknown symbol ieee80211_register_hw (err -22)
[ 1641.157811] b43: disagrees about version of symbol __ieee80211_get_radio_led_name
[ 1641.157812] b43: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[ 1641.157814] b43: disagrees about version of symbol ieee80211_generic_frame_duration
[ 1641.157816] b43: Unknown symbol ieee80211_generic_frame_duration (err -22)
[ 1641.157819] b43: disagrees about version of symbol ieee80211_wake_queue
[ 1641.157820] b43: Unknown symbol ieee80211_wake_queue (err -22)
[ 1641.157826] b43: disagrees about version of symbol __ieee80211_get_tx_led_name
[ 1641.157827] b43: Unknown symbol __ieee80211_get_tx_led_name (err -22)
[ 1641.157837] b43: disagrees about version of symbol wiphy_rfkill_set_hw_state
[ 1641.157838] b43: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[ 1641.157847] b43: disagrees about version of symbol __ieee80211_get_rx_led_name
[ 1641.157848] b43: Unknown symbol __ieee80211_get_rx_led_name (err -22)
[ 1641.157858] b43: disagrees about version of symbol ieee80211_queue_delayed_work
[ 1641.157859] b43: Unknown symbol ieee80211_queue_delayed_work (err -22)
[ 1641.157863] b43: disagrees about version of symbol ieee80211_ctstoself_get
[ 1641.157864] b43: Unknown symbol ieee80211_ctstoself_get (err -22)
[ 1641.157890] b43: Unknown symbol ieee80211_rx (err 0)
[ 1641.157896] b43: disagrees about version of symbol ieee80211_wake_queues
[ 1641.157897] b43: Unknown symbol ieee80211_wake_queues (err -22)
[ 1641.157899] b43: disagrees about version of symbol ieee80211_free_txskb
[ 1641.157900] b43: Unknown symbol ieee80211_free_txskb (err -22)
[ 1641.157909] b43: disagrees about version of symbol ieee80211_tx_status
[ 1641.157910] b43: Unknown symbol ieee80211_tx_status (err -22)
[ 1641.157911] b43: disagrees about version of symbol ieee80211_stop_queue
[ 1641.157913] b43: Unknown symbol ieee80211_stop_queue (err -22)
[ 1641.157920] b43: disagrees about version of symbol __ieee80211_get_assoc_led_name
[ 1641.157921] b43: Unknown symbol __ieee80211_get_assoc_led_name (err -22)
[ 1641.157923] b43: disagrees about version of symbol wiphy_rfkill_start_polling
[ 1641.157924] b43: Unknown symbol wiphy_rfkill_start_polling (err -22)
[ 1641.157930] b43: disagrees about version of symbol ieee80211_unregister_hw
[ 1641.157931] b43: Unknown symbol ieee80211_unregister_hw (err -22)
[ 1641.157934] b43: disagrees about version of symbol ieee80211_beacon_get_tim
[ 1641.157935] b43: Unknown symbol ieee80211_beacon_get_tim (err -22)
[ 1641.157940] b43: disagrees about version of symbol ieee80211_rts_get
[ 1641.157941] b43: Unknown symbol ieee80211_rts_get (err -22)
[ 1641.157946] b43: disagrees about version of symbol ieee80211_queue_work
[ 1641.157947] b43: Unknown symbol ieee80211_queue_work (err -22)
```

---

### Post by ajgreeny on 2016-04-12
Which version 12 are you running?

12.04 is supported for another year but 12.10 lost support a long time ago and will be very risky to keep using now with no security updates for several years, so I hope it is 12.04.

In view of your wifi adapter, have you looked at the thread at [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110) and tried all it suggests.

However, none of that will work if you are using 12.10 as the repos will now be unavailable, so you will need to upgrade to a supported version, currently 14.04 or 15.10, though you could try 16.04, which even though still a beta release, has been working well for me, and will be fully released in only 10 days.

---

### Post by roya2 on 2016-04-12
Thank you so much for your reply. I am using ubuntu 12.04 . I will consider your point about support for this version.
Unfortunately I have tried that solution and it did not help to connect to the wireless. Is there any other suggestion?

---

### Post by Hadaka on 2016-04-12
Your wireless card BCM43228 PCI-ID is..[14e4:4359]

From a working wired connection,Please open a terminal ctrl/alt/t
Copy and paste the following commands one at a time.

```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```

If you are still having difficulties,please COPY the following command to a terminal.
A file will be written to your home directory.The file name is wireless-info.txt

```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
Next..
Please copy and post the wireless-info.txt file
Thanks.

---

### Post by roya2 on 2016-04-13
Thank you so much for your time.
When I enter the command : 
```
sudo modprobe wl
```
The result is:
```
 FATAL: Error inserting wl (/lib/modules/3.5.0-61-generic/updates/dkms/wl.ko): Invalid argument 
```

```
And here is the wireless-info.txt content:
########## wireless info START ##########

last: /var/log/wtmp: No such file or directory
Perhaps this file was removed by the operator to prevent logging last info.
Report from: 14 Apr 2016 01:52 NZST +1200

Booted last: 14 Apr 2016 00:00 NZST +1200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.5.0-61-generic #90-Ubuntu SMP Sun Apr 26 11:23:53 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, acpi=force, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Dell Device [1028:05c2]
    Kernel driver in use: r8168

03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Dell Device [1028:0014]
    Kernel modules: wl

##### lsusb #############################

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 413c:2107 Dell Computer Corp. 
Bus 003 Device 003: ID 046d:c077 Logitech, Inc. 
Bus 003 Device 004: ID 0c45:64d8 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              589941  0 
compat                 34179  1 cfg80211
dell_wmi_aio           12653  0 
sparse_keymap          13891  1 dell_wmi_aio
wmi                    19257  1 dell_wmi_aio

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.30  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:120510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34267508 (34.2 MB)  TX bytes:2761225 (2.7 MB)
          Interrupt:44 Base address:0x2000 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.0.1
search rochester.rr.com

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1284     1  0 Apr13 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.30
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             209.18.47.62
    DNS:             209.18.47.61

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Cas_Wireless]] (600 root)
[connection] id=Cas_Wireless | type=802-11-wireless
[802-11-wireless] ssid=Cas_Wireless
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Pacific/Auckland (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
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
filename:       /lib/modules/3.5.0-61-generic/updates/dkms/cfg80211.ko
version:        backported from Linux (v3.15.1-0-g41b67d8) using backports v3.15.1-1-0-gfcc5f19
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1A9723940BDABC83F7695E3
depends:        compat
vermagic:       3.5.0-61-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
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

[/etc/modprobe.d/blacklist-local.conf]
blacklist wl

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/dkms.conf]
blacklist r8169

##### rc.local ##########################

logger "wmm rc.local ran as $USER"
/etc/init.d/doCASUpdateFromCD

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[69438.750949] wl: disagrees about version of symbol wiphy_register
[69438.750950] wl: Unknown symbol wiphy_register (err -22)
[69438.750953] wl: disagrees about version of symbol wiphy_new
[69438.750954] wl: Unknown symbol wiphy_new (err -22)
[69438.751007] wl: disagrees about version of symbol wiphy_unregister
[69438.751008] wl: Unknown symbol wiphy_unregister (err -22)
[69438.751015] wl: disagrees about version of symbol __ieee80211_get_channel
[69438.751016] wl: Unknown symbol __ieee80211_get_channel (err -22)
[69438.751028] wl: disagrees about version of symbol ieee80211_channel_to_frequency
[69438.751028] wl: Unknown symbol ieee80211_channel_to_frequency (err -22)
[69438.751047] wl: disagrees about version of symbol wiphy_free
[69438.751048] wl: Unknown symbol wiphy_free (err -22)
[69461.774328] wl: disagrees about version of symbol wiphy_register
[69461.774330] wl: Unknown symbol wiphy_register (err -22)
[69461.774335] wl: disagrees about version of symbol wiphy_new
[69461.774337] wl: Unknown symbol wiphy_new (err -22)
[69461.774430] wl: disagrees about version of symbol wiphy_unregister
[69461.774432] wl: Unknown symbol wiphy_unregister (err -22)
[69461.774448] wl: disagrees about version of symbol __ieee80211_get_channel
[69461.774449] wl: Unknown symbol __ieee80211_get_channel (err -22)
[69461.774470] wl: disagrees about version of symbol ieee80211_channel_to_frequency
[69461.774472] wl: Unknown symbol ieee80211_channel_to_frequency (err -22)
[69461.774510] wl: disagrees about version of symbol wiphy_free
[69461.774511] wl: Unknown symbol wiphy_free (err -22)
[69479.241608] wl: disagrees about version of symbol wiphy_register
[69479.241609] wl: Unknown symbol wiphy_register (err -22)
[69479.241612] wl: disagrees about version of symbol wiphy_new
[69479.241613] wl: Unknown symbol wiphy_new (err -22)
[69479.241667] wl: disagrees about version of symbol wiphy_unregister
[69479.241668] wl: Unknown symbol wiphy_unregister (err -22)
[69479.241676] wl: disagrees about version of symbol __ieee80211_get_channel
[69479.241677] wl: Unknown symbol __ieee80211_get_channel (err -22)
[69479.241689] wl: disagrees about version of symbol ieee80211_channel_to_frequency
[69479.241690] wl: Unknown symbol ieee80211_channel_to_frequency (err -22)
[69479.241709] wl: disagrees about version of symbol wiphy_free
[69479.241710] wl: Unknown symbol wiphy_free (err -22)

########## wireless info END ############
```

---

### Post by slickymaster on 2016-04-13
@roya2:
When posting code please[ use code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168"). Output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

### Post by roya2 on 2016-04-13
Thanks for the points. I will do that. I am just waiting for a response yet.

---

### Post by Hadaka on 2016-04-14
Hi, please do.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rf wl
sudo apt-get install  bcmwl-kernel-source
sudo modprobe -vv wl
```
then do and post the output of.,,
```
dmesg | grep wl
```
I also found this, so you may need to load Ubuntu 14.04
```
www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2016.../threads.html
Jan 31, 2016 - [Bug 1539937] [NEW] kernel *3.5.0-61*-*generic* is not supported on Ubuntu 12.04.1*
```*
thanks

---

### Post by roya2 on 2016-04-15
Thank you . The modeprobe commands did not work and the output of dmesg | grep wl is :
```

[66302.397172] wl: module license 'MIXED/Proprietary' taints kernel.
[66302.399520] wl: disagrees about version of symbol cfg80211_scan_done
[66302.399523] wl: Unknown symbol cfg80211_scan_done (err -22)
[66302.399546] wl: disagrees about version of symbol cfg80211_disconnected
[66302.399547] wl: Unknown symbol cfg80211_disconnected (err -22)
[66302.399559] wl: disagrees about version of symbol wiphy_register
[66302.399560] wl: Unknown symbol wiphy_register (err -22)
[66302.399563] wl: disagrees about version of symbol wiphy_new
[66302.399564] wl: Unknown symbol wiphy_new (err -22)
[66302.399566] wl: disagrees about version of symbol cfg80211_put_bss
[66302.399567] wl: Unknown symbol cfg80211_put_bss (err -22)
[66302.399568] wl: disagrees about version of symbol cfg80211_roamed
[66302.399569] wl: Unknown symbol cfg80211_roamed (err -22)
[66302.399600] wl: Unknown symbol cfg80211_inform_bss (err 0)
[66302.399604] wl: disagrees about version of symbol cfg80211_gtk_rekey_notify
[66302.399605] wl: Unknown symbol cfg80211_gtk_rekey_notify (err -22)
[66302.399608] wl: disagrees about version of symbol cfg80211_ibss_joined
[66302.399609] wl: Unknown symbol cfg80211_ibss_joined (err -22)
[66302.399614] wl: disagrees about version of symbol cfg80211_michael_mic_failure
[66302.399615] wl: Unknown symbol cfg80211_michael_mic_failure (err -22)
[66302.399617] wl: disagrees about version of symbol cfg80211_connect_result
[66302.399618] wl: Unknown symbol cfg80211_connect_result (err -22)
[66302.399625] wl: disagrees about version of symbol wiphy_unregister
[66302.399625] wl: Unknown symbol wiphy_unregister (err -22)
[66302.399629] wl: disagrees about version of symbol cfg80211_get_bss
[66302.399630] wl: Unknown symbol cfg80211_get_bss (err -22)
[66302.399633] wl: disagrees about version of symbol __ieee80211_get_channel
[66302.399633] wl: Unknown symbol __ieee80211_get_channel (err -22)
[66302.399644] wl: disagrees about version of symbol ieee80211_channel_to_frequency
[66302.399645] wl: Unknown symbol ieee80211_channel_to_frequency (err -22)
[66302.399657] wl: Unknown symbol cfg80211_inform_bss_frame (err 0)
[66302.399664] wl: disagrees about version of symbol wiphy_free
[66302.399664] wl: Unknown symbol wiphy_free (err -22)
[66366.814506] wl: disagrees about version of symbol cfg80211_scan_done
[66366.814510] wl: Unknown symbol cfg80211_scan_done (err -22)
[66366.814534] wl: disagrees about version of symbol cfg80211_disconnected
[66366.814535] wl: Unknown symbol cfg80211_disconnected (err -22)
[66366.814548] wl: disagrees about version of symbol wiphy_register
[66366.814549] wl: Unknown symbol wiphy_register (err -22)
[66366.814552] wl: disagrees about version of symbol wiphy_new
[66366.814553] wl: Unknown symbol wiphy_new (err -22)
[66366.814555] wl: disagrees about version of symbol cfg80211_put_bss
[66366.814556] wl: Unknown symbol cfg80211_put_bss (err -22)
[66366.814557] wl: disagrees about version of symbol cfg80211_roamed
[66366.814558] wl: Unknown symbol cfg80211_roamed (err -22)
[66366.814581] wl: Unknown symbol cfg80211_inform_bss (err 0)
[66366.814585] wl: disagrees about version of symbol cfg80211_gtk_rekey_notify
[66366.814586] wl: Unknown symbol cfg80211_gtk_rekey_notify (err -22)
[66366.814590] wl: disagrees about version of symbol cfg80211_ibss_joined
[66366.814591] wl: Unknown symbol cfg80211_ibss_joined (err -22)
[66366.814598] wl: disagrees about version of symbol cfg80211_michael_mic_failure
[66366.814599] wl: Unknown symbol cfg80211_michael_mic_failure (err -22)
[66366.814600] wl: disagrees about version of symbol cfg80211_connect_result
[66366.814601] wl: Unknown symbol cfg80211_connect_result (err -22)
[66366.814609] wl: disagrees about version of symbol wiphy_unregister
[66366.814610] wl: Unknown symbol wiphy_unregister (err -22)
[66366.814614] wl: disagrees about version of symbol cfg80211_get_bss
[66366.814615] wl: Unknown symbol cfg80211_get_bss (err -22)
[66366.814618] wl: disagrees about version of symbol __ieee80211_get_channel
[66366.814618] wl: Unknown symbol __ieee80211_get_channel (err -22)
[66366.814631] wl: disagrees about version of symbol ieee80211_channel_to_frequency
[66366.814632] wl: Unknown symbol ieee80211_channel_to_frequency (err -22)
[66366.814649] wl: Unknown symbol cfg80211_inform_bss_frame (err 0)
[66366.814657] wl: disagrees about version of symbol wiphy_free
[66366.814658] wl: Unknown symbol wiphy_free (err -22)

```

---

### Post by Hadaka on 2016-04-15
Hi, please open a terminal then copy and paste..
```
sudo iw reg set NZ
sudo sed -i 's/^REG.*=$/&NZ/' /etc/default/crda
```
Please post the output of..
```
locate wl.ko
uname -r
```
thanks

---

### Post by roya2 on 2016-04-15
Thank you. I am glad you replied soon. 
The output of locate wl.ko
```
/lib/modules/3.5.0-61-generic/updates/dkms/wl.ko
/var/lib/dkms/bcmwl/6.30.223.248+bdcom/3.5.0-61-generic/x86_64/module/wl.ko
/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/.wl.ko.cmd
```
and uname -r is 
3.5.0-61-generic

---

### Post by Hadaka on 2016-04-15
Hi, the errors you are getting when you attempt to load the wl module..
```
FATAL: Error inserting wl (/lib/modules/3.5.0-61-generic/updates/dkms/wl.ko)
```
and this bug...
```
www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2016.../threads.html
Jan 31, 2016 - [Bug 1539937] [NEW] kernel *3.5.0-61*-*generic* is not supported on Ubuntu 12.04.1
```
along with your dmesg output , The only suggest I have is to load Ubuntu 14.04
 you can try ,but im doubfull it will solve the issue to do..
```
sudo apt-get update
sudo apt-get dist-upgrade #This does NOT upgrade to 14.04
```
then do and post again..
```
arch
uname -r
```
thanks.

---

### Post by roya2 on 2016-04-15
Thank you so much. It did not upgrade anything. 
There are some reason that I can not yet upgrade to ubuntu 14. Everything was working a few days ago with the same ubuntu and I was able to connect to wireless. I just reinstalled it and this issue happened.

---

### Post by Hadaka on 2016-04-15
Ok, Since you cannot load 14.04 i suggest then that you reload 12.04
and do NOT do the updates. Once it is loaded, hopefully with a kernel
that is not  "kernel 3.5.0.61-generic" and the wireless works, we can
then go backand prevent it from loading 3.5.0.61
thanks.

---

### Post by roya2 on 2016-04-15
Thank you . I will do that.

---

### Post by QLee on 2016-04-16
@ Hadaka,
Did you notice this from the results of the wireless info? 

> [/etc/modprobe.d/blacklist-local.conf]
blacklist wl

---

### Post by Hadaka on 2016-04-16
Hi,a file has been brought to my attention that
I didnt see in your wireless report, please open a terminal and do..
```
sudo rm -rf etc/modprobe.d/blacklist-local.conf
```
then do..
```
sudo sed -i "/^rtc/ d" /etc/modules
sudo sed -i "/^lp/ d" /etc/modules
echo -e "lp\nrtc" | sudo tee -a /etc/modules
```
and..
```
sudo iw reg set NZ
sudo sed -i 's/^REG.*=$/&NZ/' /etc/default/crda
```

@QLee, Thank you for bringing that to my attention, good catch !

---

### Post by roya2 on 2016-04-19
Thank you again. 
Unfortunately the command : 
```
 sudo iw reg set NZ 
``` 
is not working and printing : nl80211 not found.

---

### Post by QLee on 2016-04-19
roya2,

Did you do the reinstall of 12.04 that you said you were going to do in post 15? If you did, your system has changed and likely no longer looks the same as we were looking at previously because now it would be back to a system without the needed module loaded. 

You can give Hadaka the needed information on the state of your system currently, by running the wireless script again and posting the results.

Always post the results of commands that are given to you to try, as the output gives information on what did happen. When you run several commands and just write that the last one is not working, not as much information is obtained.

If you have done the reinstall, probably all that has to happen is to load the correct module for your wireless card but the wireless info script would show the current state of your system and make it easier for Hadaka to help you.

---

### Post by roya2 on 2016-04-19
Thank you Qlee,
No I have not changed the system yet.
Other commands did not have an output except ```
echo -e "lp\nrtc" | sudo tee -a /etc/modules
``` which printed :

lp
rtc

---

### Post by Hadaka on 2016-04-19
Hi, Let's take a look at what has and hasn't changed.
Please open a terminal ctrl/alt/t then Copy and paste the following commandand press enter.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
Next.
From your directory please copy,paste and post the ***wireless-info.txt***
thanks.

---

### Post by roya2 on 2016-04-20
Hi, thank you for looking into this for me :
```

########## wireless info START ##########

last: /var/log/wtmp: No such file or directory
Perhaps this file was removed by the operator to prevent logging last info.
Report from: 21 Apr 2016 01:08 NZST +1200

Booted last: 21 Apr 2016 00:00 NZST +1200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.5.0-61-generic #90-Ubuntu SMP Sun Apr 26 11:23:53 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, acpi=force, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Dell Device [1028:05c2]
    Kernel driver in use: r8168

03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Dell Device [1028:0014]
    Kernel modules: wl

##### lsusb #############################

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 413c:2107 Dell Computer Corp. 
Bus 003 Device 003: ID 046d:c077 Logitech, Inc. 
Bus 003 Device 004: ID 0c45:64d8 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

dell_wmi_aio           12653  0 
sparse_keymap          13891  1 dell_wmi_aio
wmi                    19257  1 dell_wmi_aio

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.30  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15483 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12981677 (12.9 MB)  TX bytes:2133338 (2.1 MB)
          Interrupt:45 Base address:0x4000 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.0.1
search rochester.rr.com

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1275     1  0 Apr20 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.30
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             209.18.47.62
    DNS:             209.18.47.61

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Cas_Wireless]] (600 root)
[connection] id=Cas_Wireless | type=802-11-wireless
[802-11-wireless] ssid=Cas_Wireless
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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

[/etc/modprobe.d/blacklist-local.conf]
blacklist wl

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/dkms.conf]
blacklist r8169

##### rc.local ##########################

logger "wmm rc.local ran as $USER"
/etc/init.d/doCASUpdateFromCD

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[15493.784348] r8168: eth0: link down
[15498.466091] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[74111.446036] r8168: eth0: link up
[74111.446435] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

---

### Post by Hadaka on 2016-04-20
Hi, your wireless driver..wl..is still blacklisted..
```
[/etc/modprobe.d/blacklist-local.conf]
blacklist wl
```
Please open a terminal and do..
```
sudo rm -rf /etc/modprobe.d/blacklist-local.conf
```
boot..then do..
```
sudo modprobe -r wl
sudo modprobe -vv wl
```
next..do..and post the output of..
```
dmesg | grep wl
```
thanks.

---

### Post by roya2 on 2016-04-21
Thank you. Here is what I did:
```

casadmin@ubuntu:~$ sudo rm -rf /etc/modprobe.d/blacklist-local.conf
[sudo] password for casadmin: 
casadmin@ubuntu:~$ sudo modprobe -r wl
casadmin@ubuntu:~$ sudo modprobe -vv wl
insmod /lib/modules/3.5.0-61-generic/updates/dkms/compat.ko 
insmod /lib/modules/3.5.0-61-generic/updates/dkms/cfg80211.ko 
insmod /lib/modules/3.5.0-61-generic/updates/dkms/wl.ko 
FATAL: Error inserting wl (/lib/modules/3.5.0-61-generic/updates/dkms/wl.ko): Invalid argument
casadmin@ubuntu:~$ dmesg | grep wl
[160944.285944] wl: module license 'MIXED/Proprietary' taints kernel.
[160944.288402] wl: disagrees about version of symbol cfg80211_scan_done
[160944.288406] wl: Unknown symbol cfg80211_scan_done (err -22)
[160944.288434] wl: disagrees about version of symbol cfg80211_disconnected
[160944.288435] wl: Unknown symbol cfg80211_disconnected (err -22)
[160944.288452] wl: disagrees about version of symbol wiphy_register
[160944.288453] wl: Unknown symbol wiphy_register (err -22)
[160944.288456] wl: disagrees about version of symbol wiphy_new
[160944.288457] wl: Unknown symbol wiphy_new (err -22)
[160944.288460] wl: disagrees about version of symbol cfg80211_put_bss
[160944.288461] wl: Unknown symbol cfg80211_put_bss (err -22)
[160944.288463] wl: disagrees about version of symbol cfg80211_roamed
[160944.288464] wl: Unknown symbol cfg80211_roamed (err -22)
[160944.288491] wl: Unknown symbol cfg80211_inform_bss (err 0)
[160944.288495] wl: disagrees about version of symbol cfg80211_gtk_rekey_notify
[160944.288497] wl: Unknown symbol cfg80211_gtk_rekey_notify (err -22)
[160944.288502] wl: disagrees about version of symbol cfg80211_ibss_joined
[160944.288503] wl: Unknown symbol cfg80211_ibss_joined (err -22)
[160944.288510] wl: disagrees about version of symbol cfg80211_michael_mic_failure
[160944.288512] wl: Unknown symbol cfg80211_michael_mic_failure (err -22)
[160944.288513] wl: disagrees about version of symbol cfg80211_connect_result
[160944.288514] wl: Unknown symbol cfg80211_connect_result (err -22)
[160944.288524] wl: disagrees about version of symbol wiphy_unregister
[160944.288525] wl: Unknown symbol wiphy_unregister (err -22)
[160944.288530] wl: disagrees about version of symbol cfg80211_get_bss
[160944.288531] wl: Unknown symbol cfg80211_get_bss (err -22)
[160944.288535] wl: disagrees about version of symbol __ieee80211_get_channel
[160944.288536] wl: Unknown symbol __ieee80211_get_channel (err -22)
[160944.288550] wl: disagrees about version of symbol ieee80211_channel_to_frequency
[160944.288551] wl: Unknown symbol ieee80211_channel_to_frequency (err -22)
[160944.288567] wl: Unknown symbol cfg80211_inform_bss_frame (err 0)
[160944.288576] wl: disagrees about version of symbol wiphy_free
[160944.288577] wl: Unknown symbol wiphy_free (err -22)



```
----------------------
Output of 
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
```


########## wireless info START ##########

last: /var/log/wtmp: No such file or directory
Perhaps this file was removed by the operator to prevent logging last info.
Report from: 22 Apr 2016 04:35 NZST +1200

Booted last: 22 Apr 2016 00:00 NZST +1200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.5.0-61-generic #90-Ubuntu SMP Sun Apr 26 11:23:53 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, acpi=force, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Dell Device [1028:05c2]
    Kernel driver in use: r8168

03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Dell Device [1028:0014]
    Kernel modules: wl

##### lsusb #############################

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 413c:2107 Dell Computer Corp. 
Bus 003 Device 003: ID 046d:c077 Logitech, Inc. 
Bus 003 Device 004: ID 0c45:64d8 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              589941  0 
compat                 34179  1 cfg80211
dell_wmi_aio           12653  0 
sparse_keymap          13891  1 dell_wmi_aio
wmi                    19257  1 dell_wmi_aio

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.24  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2821 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1570747 (1.5 MB)  TX bytes:301448 (301.4 KB)
          Interrupt:44 Base address:0x8000 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.0.1
search rochester.rr.com

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1310     1  0 04:21 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.24
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             209.18.47.62
    DNS:             209.18.47.61

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Cas_Wireless]] (600 root)
[connection] id=Cas_Wireless | type=802-11-wireless
[802-11-wireless] ssid=Cas_Wireless
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Pacific/Auckland (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
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
filename:       /lib/modules/3.5.0-61-generic/updates/dkms/cfg80211.ko
version:        backported from Linux (v3.15.1-0-g41b67d8) using backports v3.15.1-1-0-gfcc5f19
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1A9723940BDABC83F7695E3
depends:        compat
vermagic:       3.5.0-61-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

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

##### rc.local ##########################

logger "wmm rc.local ran as $USER"
/etc/init.d/doCASUpdateFromCD

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   14.045146] wl: Unknown symbol wiphy_register (err -22)
[   14.045149] wl: disagrees about version of symbol wiphy_new
[   14.045150] wl: Unknown symbol wiphy_new (err -22)
[   14.045199] wl: disagrees about version of symbol wiphy_unregister
[   14.045199] wl: Unknown symbol wiphy_unregister (err -22)
[   14.045207] wl: disagrees about version of symbol __ieee80211_get_channel
[   14.045208] wl: Unknown symbol __ieee80211_get_channel (err -22)
[   14.045220] wl: disagrees about version of symbol ieee80211_channel_to_frequency
[   14.045220] wl: Unknown symbol ieee80211_channel_to_frequency (err -22)
[   14.045238] wl: disagrees about version of symbol wiphy_free
[   14.045239] wl: Unknown symbol wiphy_free (err -22)
[   16.950078] eth0: 0xffffc900050a8000, <MAC 'eth0' [IF]>, IRQ 44
[   17.000675] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[  126.877819] wl: disagrees about version of symbol wiphy_register
[  126.877821] wl: Unknown symbol wiphy_register (err -22)
[  126.877827] wl: disagrees about version of symbol wiphy_new
[  126.877829] wl: Unknown symbol wiphy_new (err -22)
[  126.877919] wl: disagrees about version of symbol wiphy_unregister
[  126.877921] wl: Unknown symbol wiphy_unregister (err -22)
[  126.877936] wl: disagrees about version of symbol __ieee80211_get_channel
[  126.877938] wl: Unknown symbol __ieee80211_get_channel (err -22)
[  126.877959] wl: disagrees about version of symbol ieee80211_channel_to_frequency
[  126.877961] wl: Unknown symbol ieee80211_channel_to_frequency (err -22)
[  126.877999] wl: disagrees about version of symbol wiphy_free
[  126.878000] wl: Unknown symbol wiphy_free (err -22)
[  701.259284] r8168: eth0: link up
[  701.259679] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############



```
--I just noticed you mentioned booting after removing the file. I did reboot but the output was the same.
FYI, right now I run the same ubuntu (12.04) (same kernel) on another device (a little newer Dell) and there is no problem with the wireless. 
The output of the wirelessInfo in the system that **does not** have a problem is : 
```
########## wireless info START ##########

last: /var/log/wtmp: No such file or directory
Perhaps this file was removed by the operator to prevent logging last info.
Report from: 21 Apr 2016 12:28 EDT -0400

Booted last: 21 Apr 2016 00:00 EDT -0400

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.5.0-61-generic #90-Ubuntu SMP Sun Apr 26 11:23:53 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)
    Subsystem: Intel Corporation Dual Band Wireless-N 7260 [8086:c420]
    Kernel driver in use: iwlwifi

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Dell Device [1028:0623]
    Kernel driver in use: r8168

##### lsusb #############################

Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 009: ID 0781:5530 SanDisk Corp. Cruzer
Bus 003 Device 002: ID 0c45:670a Microdia 
Bus 003 Device 003: ID 046d:c077 Logitech, Inc. 
Bus 003 Device 004: ID 413c:2107 Dell Computer Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                217873  0 
mac80211              684943  1 iwlmvm
dell_wmi_aio           12653  0 
sparse_keymap          13891  1 dell_wmi_aio
iwlwifi               189443  1 iwlmvm
cfg80211              589941  3 iwlmvm,mac80211,iwlwifi
compat                 34179  4 iwlmvm,mac80211,iwlwifi,cfg80211
wmi                    19257  1 dell_wmi_aio

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44765 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41298371 (41.2 MB)  TX bytes:7438150 (7.4 MB)
          Interrupt:46 Base address:0xe000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:489342 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:210928025 (210.9 MB)  TX bytes:14638881 (14.6 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Cas_Wireless"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Cas_Wireless' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:110   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.0.1
search rochester.rr.com

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1334     1  0 Apr19 ?        00:00:19 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.13
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             209.18.47.62
    DNS:             209.18.47.61

- Device: wlan0  [Cas_Wireless] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    HP-Print-7E-Photosmart 7520: Infra, <MAC 'HP-Print-7E-Photosmart 7520' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 95
    *Cas_Wireless:   Infra, <MAC 'Cas_Wireless' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 66 WPA2
    jaybwireless:    Infra, <MAC 'jaybwireless' [AC2]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             209.18.47.62
    DNS:             209.18.47.61

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Cas_Wireless]] (600 root)
[connection] id=Cas_Wireless | type=802-11-wireless
[802-11-wireless] ssid=Cas_Wireless | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)

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
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Cas_Wireless' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Cas_Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000016f506712
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'jaybwireless' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"jaybwireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000037b4adab
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HP-Print-7E-Photosmart 7520' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-7E-Photosmart 7520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000016f4dcc57
                    Extra: Last beacon: 72ms ago

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.5.0-61-generic/updates/dkms/iwlmvm.ko
version:        backported from Linux (v3.15.1-0-g41b67d8) using backports v3.15.1-1-0-gfcc5f19
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     D24668786B91C7C40F0C1A1
depends:        iwlwifi,mac80211,compat,cfg80211
vermagic:       3.5.0-61-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.5.0-61-generic/updates/dkms/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.15.1-0-g41b67d8) using backports v3.15.1-1-0-gfcc5f19
srcversion:     2F5666D6DE6CCC5E7A3F811
depends:        cfg80211,compat
vermagic:       3.5.0-61-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.5.0-61-generic/updates/dkms/iwlwifi.ko
version:        backported from Linux (v3.15.1-0-g41b67d8) using backports v3.15.1-1-0-gfcc5f19
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265-8.ucode
firmware:       iwlwifi-3160-8.ucode
firmware:       iwlwifi-7260-8.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     7DC3C9D053999B45C4F8296
depends:        compat,cfg80211
vermagic:       3.5.0-61-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.5.0-61-generic/updates/dkms/cfg80211.ko
version:        backported from Linux (v3.15.1-0-g41b67d8) using backports v3.15.1-1-0-gfcc5f19
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1A9723940BDABC83F7695E3
depends:        compat
vermagic:       3.5.0-61-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2

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
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
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

[/etc/modprobe.d/blacklist-local.conf]
blacklist wl

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/dkms.conf]
blacklist r8169

##### rc.local ##########################

logger "wmm rc.local ran as $USER"
/etc/init.d/doCASUpdateFromCD

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0 (r8168)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[175237.323957] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[175241.926460] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S (repeated 2 times)
[175241.940092] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[175250.219559] wlan0: authenticate with <MAC 'Cas_Wireless' [AC1]>
[175250.221766] wlan0: send auth to <MAC 'Cas_Wireless' [AC1]> (try 1/3)
[175250.223800] wlan0: authenticated
[175250.227069] wlan0: associate with <MAC 'Cas_Wireless' [AC1]> (try 1/3)
[175250.236243] wlan0: RX AssocResp from <MAC 'Cas_Wireless' [AC1]> (capab=0xc11 status=0 aid=6)
[175250.237402] wlan0: associated
[175250.237947] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[177226.296025] wlan0: AP <MAC 'Cas_Wireless' [AC1]> changed bandwidth, new config is 2462 MHz, width 2 (2452/0 MHz)
[180623.371312] wlan0: AP <MAC 'Cas_Wireless' [AC1]> changed bandwidth, new config is 2462 MHz, width 1 (2462/0 MHz)

########## wireless info END ############


```

Thanks.

---

### Post by roya2 on 2016-04-21
I do not know much about the commands but I just typed
```
 sudo modprobe iwlwifi 
```
Now the wired connection also  is disconnected and not recognized. The wireless icon at the top right is blinking sometimes and nothing happens.

---

### Post by Hadaka on 2016-04-21
Hi there are some big differences between the  wireless report of the machine that works
and the one that doesnt. to begin...
```
" sudo modprobe iwlwifi"
``` is to activate an intel driver
the machine not working does not have an intel wifi card.
The machine that works shows a region of USA
The machine that does not work shows a region of NZ
which is it?? It makes a difference.
you are activating this on boot..
```
##### rc.local ##########################
     logger "wmm rc.local ran as $USER"
     /etc/init.d/doCASUpdateFromCD
```
I have no idea what "doCASUpdateFromCD" does.
are you loading a driver from. "additional drivers"??

I suggest you reload 12.04 and not add things like..
"doCASUpdateFromCD" or attempt to load additional drivers
rigt now, noting is loading on this machine,, the udev list is blank
```
 ##### udev rules ########################
    grep: /etc/udev/rules.d/*net*.rules: No such file or directory
```
let me know what you decide.
thanks.

---

### Post by roya2 on 2016-04-22
Thank you. So I have to install the ubuntu 12.04 and another software together on the machine.There is a partition of 51200 and "/" is the mount point and there is one of size 40960 and /usr/local .... is the mount point and 10240 for the swap area. and the remaining is for /var/lib/mysql .
doCASUpdateFromCD is for the other mount point.

---

### Post by roya2 on 2016-05-19
Dear Hadka,
Based on your suggestion I have a fresh install of ubuntu 16 now that is not loading anything else. Still I am not able to connect to wifi .
```
sudo wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && sudo chmod +x wireless-info && sudo ./wireless-info
 
```
Wireless.info output :
```


########## wireless info START ##########

Report from: 19 May 2016 14:16 EDT -0400

Booted last: 19 May 2016 00:00 EDT -0400

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu (from ~/.dmrc)

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:05c2]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Dell BCM43228 802.11a/b/g/n [1028:0014]
    Kernel driver in use: bcma-pci-bridge

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 003: ID 413c:2107 Dell Computer Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0c45:64d8 Microdia 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

b43                   417792  0
mac80211              737280  1 b43
cfg80211              565248  2 b43,mac80211
ssb                    65536  1 b43
dell_wmi_aio           16384  0
sparse_keymap          16384  1 dell_wmi_aio
bcma                   53248  1 b43
wmi                    20480  1 dell_wmi_aio

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          inet addr:192.168.0.205  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2541:2913:8554:8059/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:163756 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85958 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:229747936 (229.7 MB)  TX bytes:6819710 (6.8 MB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       668     1  0 13:46 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       e3dcec7a-3516-4d7f-80c9-ab3a814ff627
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e3dcec7a-3516-4d7f-80c9-ab3a814ff627 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.205/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             209.18.47.61
IP4.DNS[2]:                             209.18.47.62
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 209.18.47.61 209.18.47.62
DHCP4.OPTION[5]:                        ip_address = 192.168.0.205
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1463685028
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.0.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::2541:2913:8554:8059/64
IP6.GATEWAY:                            

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

Region: America/New_York (based on set time zone)

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

enp2s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
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
srcversion:     6046FCC9190ABD5D296D2D2
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
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

[mac80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A882F4FE63500846E1C859E
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

[bcma]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C5CB08F60A0C6A00FBF57B0
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    6.649881] bcma: bus0: Found chip with id 43228, rev 0x00 and package 0x08
[    6.649912] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[    6.649938] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1E, class 0x0)
[    6.649992] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x12, class 0x0)
[    6.650018] bcma: bus0: Core 3 found: SDIO Device (manuf 0x4BF, id 0x829, rev 0x07, class 0x0)
[    6.661508] bcma: bus0: Bus registered
[    7.720076] b43-phy0: Broadcom 43228 WLAN found (core revision 30)
[    7.720502] b43-phy0: Found PHY: Analog 9, Type 4 (N), Revision 16
[    7.720513] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2057, Revision 9, Version 1
[    7.813598] b43 bcma0:1: Direct firmware load for b43/ucode30_mimo.fw failed with error -2 (repeated 2 times)
[    7.813635] b43 bcma0:1: Direct firmware load for b43-open/ucode30_mimo.fw failed with error -2 (repeated 2 times)
[    7.813650] b43-phy0 ERROR: Firmware file "b43/ucode30_mimo.fw" not found
[    7.813652] b43-phy0 ERROR: Firmware file "b43-open/ucode30_mimo.fw" not found
[    7.813654] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   15.056825] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   15.128008] r8169 0000:02:00.0 enp2s0: link down (repeated 2 times)
[   15.128066] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   17.898209] r8169 0000:02:00.0 enp2s0: link up
[   17.898222] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready

########## wireless info END ############


```

Can any one help me with that? 
Thanks.

---

### Post by roya2 on 2016-05-20
This was not ubuntu 12 problem or partitions. The solution is posted [here]("http://ubuntuforums.org/showthread.php?t=2325227"):

---

