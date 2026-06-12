---
title: "WiFi suddenly disconnects and disappear the stations"
date: 2015-01-01
forum: Networking &amp; Wireless
---

### Post by melo2 on 2015-01-01
Hello.
Sorry if the issue is solved but I have tried differents fixes without success.
The problem is that when I connect with any AP, apparently all works fine. But after 5 mins, sometimes after 2 hours, suddenly it disconnects and doesn't reconnect. In the network applet, all the stations disappear and the only workaround is to disable wireless network and enable it again. Then automatically connects to the preferred APs. But after some minutes or hours, again it disconnects.
I had not this issue 2 months ago with 14.04, but after some updates (i don't remember which ones) the issue appeared. And now with 14.10, still is broken.
I have tried several options in /etc/modprobe.d/iwlwifi.conf like disable 11n and bt coexistence without success. Also I tried 11n_disable=8 and nothing changed.

Any sugestion?

wireless-info.txt
```

########## wireless info START ##########

Report from: 31 Dec 2014 14:32 ART -0300

Booted last: 31 Dec 2014 08:56 ART -0300

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic

##### kernel ############################

Linux 3.16.0-28-lowlatency #38-Ubuntu SMP PREEMPT Fri Dec 12 18:06:05 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, intel_pstate=disable, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0888] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4262]
    Kernel driver in use: iwlwifi

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:5008]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 005: ID 8087:07da Intel Corp.
Bus 002 Device 004: ID 5986:0299 Acer, Inc
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                236430  0
mac80211              672870  1 iwldvm
iwlwifi               187004  1 iwldvm
cfg80211              522506  3 iwlwifi,mac80211,iwldvm
wmi                    19193  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.249  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd37:9993:3de8:0:6a17:29ff:fe2c:5655/64 Scope:Global
          inet6 addr: fe80::6a17:29ff:fe2c:5655/64 Scope:Link
          inet6 addr: fd37:9993:3de8:0:bdfd:d858:f9f5:2e7d/64 Scope:Global
          inet6 addr: fd37:9993:3de8::da7/128 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:47052373 (47.0 MB)  TX bytes:32657936 (32.6 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"OpenWrt"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'OpenWrt' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10  Invalid misc:528   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [OpenWrt] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *OpenWrt:        Infra, <MAC 'OpenWrt' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 46

  IPv4 Settings:
    Address:         192.168.1.249
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

  IPv6 Settings:
    Address:         fd37:9993:3de8::da7
    Prefix:          128
    Gateway:         ::

    Address:         fd37:9993:3de8:0:bdfd:d858:f9f5:2e7d
    Prefix:          64
    Gateway:         ::

    Address:         fd37:9993:3de8:0:6a17:29ff:fe2c:5655
    Prefix:          64
    Gateway:         ::

    Address:         fe80::6a17:29ff:fe2c:5655
    Prefix:          64
    Gateway:         ::

    DNS:             fd37:9993:3de8::1

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

[[/etc/NetworkManager/system-connections/lasrosas.libre.social]] (600 root)
[connection] id=lasrosas.libre.social | type=802-11-wireless
[802-11-wireless] ssid=lasrosas.libre.social | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/OpenWrt]] (600 root)
[connection] id=OpenWrt | type=802-11-wireless
[802-11-wireless] ssid=OpenWrt | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/Argentina/Buenos_Aires (based on set time zone)

country US: DFS-UNSET
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'OpenWrt' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"OpenWrt"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005566f857b
                    Extra: Last beacon: 63ms ago

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.16.0-28-lowlatency/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     092C5F7885F1C7B9B99605B
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-28-lowlatency SMP preempt mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        F7:5F:5B:68:BC:24:EE:18:58:A0:90:DC:13:78:60:BE:E7:D3:B9:B4
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-28-lowlatency/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BEA0C6DE6572AE84C25CD77
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-28-lowlatency SMP preempt mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        F7:5F:5B:68:BC:24:EE:18:58:A0:90:DC:13:78:60:BE:E7:D3:B9:B4
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.16.0-28-lowlatency/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     BD7C2C63BC84182E21AF290
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-28-lowlatency SMP preempt mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        F7:5F:5B:68:BC:24:EE:18:58:A0:90:DC:13:78:60:BE:E7:D3:B9:B4
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: N) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.16.0-28-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-28-lowlatency SMP preempt mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        F7:5F:5B:68:BC:24:EE:18:58:A0:90:DC:13:78:60:BE:E7:D3:B9:B4
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
11n_disable: 1
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 1
uapsd_disable: N
wd_disable: 1

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
options iwlmvm power_scheme=1
options iwlwifi bt_coex_active=N swcrypto=1
options iwlwifi 11n_disable=8

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0888 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 4207.701874] wlan0: associated
[ 6211.111414] wlan0: deauthenticated from <MAC 'OpenWrt' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 6211.118367] wlan0: authenticate with <MAC 'OpenWrt' [AC1]>
[ 6211.121667] wlan0: send auth to <MAC 'OpenWrt' [AC1]> (try 1/3)
[ 6211.123802] wlan0: authenticated
[ 6211.124215] wlan0: associate with <MAC 'OpenWrt' [AC1]> (try 1/3)
[ 6211.127091] wlan0: RX AssocResp from <MAC 'OpenWrt' [AC1]> (capab=0x421 status=0 aid=1)
[ 6211.129631] wlan0: associated
[ 8342.382945] wlan0: deauthenticated from <MAC 'OpenWrt' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 8342.434386] wlan0: authenticate with <MAC 'OpenWrt' [AC1]>
[ 8342.437995] wlan0: send auth to <MAC 'OpenWrt' [AC1]> (try 1/3)
[ 8342.440259] wlan0: authenticated
[ 8342.441202] wlan0: associate with <MAC 'OpenWrt' [AC1]> (try 1/3)
[ 8342.444063] wlan0: RX AssocResp from <MAC 'OpenWrt' [AC1]> (capab=0x421 status=0 aid=1)
[ 8342.446542] wlan0: associated
[16671.978700] wlan0: deauthenticated from <MAC 'OpenWrt' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[19479.005376] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[19479.012962] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[19479.072209] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[19479.496780] wlan0: authenticate with <MAC 'OpenWrt' [AC1]>
[19479.500268] wlan0: send auth to <MAC 'OpenWrt' [AC1]> (try 1/3)
[19479.502407] wlan0: authenticated
[19479.502923] wlan0: associate with <MAC 'OpenWrt' [AC1]> (try 1/3)
[19479.505703] wlan0: RX AssocResp from <MAC 'OpenWrt' [AC1]> (capab=0x421 status=0 aid=3)
[19479.507964] wlan0: associated
[19479.508000] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

---

### Post by melo2 on 2015-01-02
I forgot to mention that the computer is a Lenovo E130

---

### Post by Hadaka on 2015-01-02
Hi, please open a terminal then COPY  and paste these commands
*Your current "country code" setting is for US, it should be AR
```
sudo iw reg set AR
sudo sed -i 's/^REG.*=$/&AR/' /etc/default/crda 
```    
also, please change your network manager setting,,,IPV6  to IGNORE
thanks

---

### Post by melo2 on 2015-01-02
Is it so important the country code?
Ok. I have changed both and I am testing. I will show the results.
Thanks :-)

---

### Post by melo2 on 2015-01-02
It doesn't worked. Less than one hour and the connection dropped.

Any other suggestion? Thanks :-)

---

### Post by melo2 on 2015-01-04
dmesg | grep iwl
```
[   11.175857] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   11.176014] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[   11.420430] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   11.440534] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   11.440538] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   11.440540] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   11.440542] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[   11.440640] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   11.464083] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.339694] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   14.347217] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   14.585837] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   14.593357] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[20595.211746] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[20595.219358] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[25726.037564] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[25726.045159] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
```

The 25726.037564 and 25726.045159 messages appeared after a disconnection and a manual reconnection.

Any other info that could help to solve the issue? 3 months ago, with the same computer, I was connected 24h/day wirelessly without problem.

Thanks :-)

---

### Post by Hadaka on 2015-01-04
Hi, boot your computer while holding down the SHIFT key
this will put you in the rcovery mode. Choose "boot to a previous kernel"
arrow down a few kernels and select an older one, If you boot to it and
you no longer have a wifi problem, then file a bug report for your current
kernel version and wireless failure,and yes.,country code does make a dfference.
This is about the extent of my knowledge for your wifi problem, perhaps someone
else may help you find a resolution. good luck

---

### Post by melo2 on 2015-01-05
> **Hadaka said:**
> Hi, boot your computer while holding down the SHIFT key
this will put you in the rcovery mode. Choose "boot to a previous kernel"
arrow down a few kernels and select an older one, If you boot to it and
you no longer have a wifi problem, then file a bug report for your current
kernel version and wireless failure,and yes.,country code does make a dfference.
This is about the extent of my knowledge for your wifi problem, perhaps someone
else may help you find a resolution. good luck

This won't work because the issue appeared 3 months ago when I had installed 14.04. Now I have 14.10 and the problem didn't dissapeared with the 14.10 original kernel neither with the updated one. I should come back to a kernel 3 or 4 months ago.

Anybody knows any other solution? Could I give you any other information in order to find the solution?

Thanks :-)

---

### Post by melo2 on 2015-01-10
I am not 100% sure. If anybody could confirm it, would be great, but 3 or 4 days ago an update was installed that updated the firmwares of devices and since them, when disconnects, reconnects automatically like should be.

Thanks :-)

---

### Post by melo2 on 2015-01-20
3 or 4 days ago, after an update, wireless stop working. I have a router at home and everybody can connect with another computers (windows and android) but I cannot connect from ubuntu.

wireless-info:
```

########## wireless info START ##########

Report from: 20 Jan 2015 10:17 ART -0300

Booted last: 20 Jan 2015 09:38 ART -0300

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic

##### kernel ############################

Linux 3.16.0-29-lowlatency #39-Ubuntu SMP PREEMPT Mon Dec 15 22:55:59 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, intel_pstate=disable, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0888] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4262]
    Kernel driver in use: iwlwifi

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:5008]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 005: ID 8087:07da Intel Corp. 
Bus 002 Device 004: ID 5986:0299 Acer, Inc 
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                236430  0 
mac80211              672870  1 iwldvm
iwlwifi               187133  1 iwldvm
cfg80211              522506  3 iwlwifi,mac80211,iwldvm
wmi                    19193  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.238  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fdfd:38de:9201:0:e533:87a1:4f4e:d1a2/64 Scope:Global
          inet6 addr: fe80::a9e:1ff:feb2:352/64 Scope:Link
          inet6 addr: fdfd:38de:9201:0:a9e:1ff:feb2:352/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11875 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5023450 (5.0 MB)  TX bytes:2419849 (2.4 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Mortadela:       Infra, <MAC 'Mortadela' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WPA2
    ChanchoLibre:    Infra, <MAC 'ChanchoLibre' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70

- Device: eth0  [Cableada automática] -----------------------------------------
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
    Address:         192.168.1.238
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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/lasrosas.libre.social]] (600 root)
[connection] id=lasrosas.libre.social | type=802-11-wireless
[802-11-wireless] ssid=lasrosas.libre.social | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/OpenWrt]] (600 root)
[connection] id=OpenWrt | type=802-11-wireless
[802-11-wireless] ssid=OpenWrt | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Mortadela]] (600 root)
[connection] id=Mortadela | type=802-11-wireless
[802-11-wireless] ssid=Mortadela | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ChanchoLibre]] (600 root)
[connection] id=ChanchoLibre | type=802-11-wireless
[802-11-wireless] ssid=ChanchoLibre | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/Argentina/Buenos_Aires (based on set time zone)

country AR: DFS-UNSET
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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

##### iwlist scan #######################

Channel occupancy:

      2   APs on   Frequency:2.437 GHz (Channel 6)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Mortadela' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Mortadela"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000647acaf8
                    Extra: Last beacon: 23ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ChanchoLibre' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"ChanchoLibre"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000647ad1e3
                    Extra: Last beacon: 23ms ago

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.16.0-29-lowlatency/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     092C5F7885F1C7B9B99605B
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-29-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        93:51:A1:B2:C7:2A:3E:BF:EB:47:EB:ED:F0:62:69:DA:C7:2E:9E:9E
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-29-lowlatency/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B3A65EB1DAE59CB6B5FD971
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-29-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        93:51:A1:B2:C7:2A:3E:BF:EB:47:EB:ED:F0:62:69:DA:C7:2E:9E:9E
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.16.0-29-lowlatency/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     D335B9FC08B25C4ADA0BD33
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-29-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        93:51:A1:B2:C7:2A:3E:BF:EB:47:EB:ED:F0:62:69:DA:C7:2E:9E:9E
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: N) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.16.0-29-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-29-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        93:51:A1:B2:C7:2A:3E:BF:EB:47:EB:ED:F0:62:69:DA:C7:2E:9E:9E
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
11n_disable: 1
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: N
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 1
uapsd_disable: N
wd_disable: 1

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
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlmvm power_scheme=1
options iwlwifi bt_coex_active=N swcrypto=1
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0888 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   15.263816] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   15.271328] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   15.509192] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   15.516744] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   15.577081] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2033.889783] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 2033.889966] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[ 2033.891005] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[ 2033.915885] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 2033.915891] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 2033.915893] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 2033.915898] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[ 2033.915982] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 2033.933441] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2033.940637] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 2033.948905] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[ 2034.187688] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 2034.195263] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[ 2034.260588] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2047.444617] wlan0: authenticate with <MAC 'Mortadela' [AC1]>
[ 2047.449604] wlan0: send auth to <MAC 'Mortadela' [AC1]> (try 1/3)
[ 2047.453638] wlan0: authenticated
[ 2052.453163] wlan0: aborting authentication with <MAC 'Mortadela' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2062.560483] wlan0: authenticate with <MAC 'Mortadela' [AC1]>
[ 2062.563856] wlan0: send auth to <MAC 'Mortadela' [AC1]> (try 1/3)
[ 2062.566140] wlan0: authenticated
[ 2067.565234] wlan0: aborting authentication with <MAC 'Mortadela' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2081.644244] wlan0: authenticate with <MAC 'ChanchoLibre' [AC2]>
[ 2081.647519] wlan0: send auth to <MAC 'ChanchoLibre' [AC2]> (try 1/3)
[ 2081.649779] wlan0: authenticated
[ 2097.152879] wlan0: authenticate with <MAC 'ChanchoLibre' [AC2]>
[ 2097.156143] wlan0: send auth to <MAC 'ChanchoLibre' [AC2]> (try 1/3)
[ 2097.159805] wlan0: authenticated
[ 2102.155347] wlan0: aborting authentication with <MAC 'ChanchoLibre' [AC2]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############
```

---

### Post by melo2 on 2015-01-20
I have changed the encryption to WPA2 AES and now I get this messages:

```

dmesg | grep iwl
[   11.011006] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   11.011159] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[   11.212623] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   11.243608] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   11.243612] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   11.243614] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   11.243617] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[   11.243711] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   11.265267] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   15.263816] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   15.271328] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   15.509192] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   15.516744] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[ 2033.889783] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 2033.889966] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[ 2033.891005] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[ 2033.915885] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 2033.915891] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 2033.915893] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 2033.915898] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[ 2033.915982] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 2033.933441] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2033.940637] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 2033.948905] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[ 2034.187688] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 2034.195263] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[ 3537.257476] iwlwifi 0000:03:00.0: Error sending REPLY_TX_LINK_QUALITY_CMD: time out after 2000ms.
[ 3537.257487] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 128 write_ptr 129
[ 3537.257844] iwlwifi 0000:03:00.0: Loaded firmware version: 18.168.6.1
[ 3537.258009] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[ 3537.258014] iwlwifi 0000:03:00.0: CSR values:
[ 3537.258018] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 3537.258033] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80b08
[ 3537.258062] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[ 3537.258090] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[ 3537.258119] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[ 3537.258147] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[ 3537.258176] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X00000002
[ 3537.258205] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[ 3537.258233] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 3537.258262] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X000000c8
[ 3537.258291] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X7ebe0ffd
[ 3537.258319] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000801
[ 3537.258348] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030001
[ 3537.258403] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[ 3537.258433] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X000025a8
[ 3537.258463] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000080
[ 3537.258501] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 3537.258529] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 3537.258542] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000040
[ 3537.258555] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X88116c38
[ 3537.258583] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X29800200
[ 3537.258596] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[ 3537.258625] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X53f7f757
[ 3537.258655] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 3537.258686] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0010
[ 3537.258708] iwlwifi 0000:03:00.0: FH register values:
[ 3537.258764] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X05015100
[ 3537.258804] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X005a63b0
[ 3537.258847] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f0
[ 3537.258897] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00801114
[ 3537.258937] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 3537.258977] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 3537.259018] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 3537.259058] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 3537.259099] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 3537.259129] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[ 3537.259140] iwlwifi 0000:03:00.0: Status: 0x0000204C, count: 6
[ 3537.259150] iwlwifi 0000:03:00.0: 0x00000066 | NMI_INTERRUPT_HOST          
[ 3537.259158] iwlwifi 0000:03:00.0: 0x00011DD4 | uPc
[ 3537.259164] iwlwifi 0000:03:00.0: 0x00011DA2 | branchlink1
[ 3537.259171] iwlwifi 0000:03:00.0: 0x00011E14 | branchlink2
[ 3537.259175] iwlwifi 0000:03:00.0: 0x0000EC7A | interruptlink1
[ 3537.259179] iwlwifi 0000:03:00.0: 0x00000424 | interruptlink2
[ 3537.259183] iwlwifi 0000:03:00.0: 0x00000001 | data1
[ 3537.259188] iwlwifi 0000:03:00.0: 0x07030000 | data2
[ 3537.259192] iwlwifi 0000:03:00.0: 0x00029B36 | line
[ 3537.259196] iwlwifi 0000:03:00.0: 0x00018ED0 | beacon time
[ 3537.259200] iwlwifi 0000:03:00.0: 0x00000130 | tsf low
[ 3537.259204] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[ 3537.259208] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[ 3537.259212] iwlwifi 0000:03:00.0: 0x01B791D5 | time gp2
[ 3537.259216] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[ 3537.259220] iwlwifi 0000:03:00.0: 0x754312A8 | uCode version
[ 3537.259224] iwlwifi 0000:03:00.0: 0x000000C8 | hw version
[ 3537.259228] iwlwifi 0000:03:00.0: 0x00C80B08 | board version
[ 3537.259232] iwlwifi 0000:03:00.0: 0x097F0018 | hcmd
[ 3537.259237] iwlwifi 0000:03:00.0: 0x27863080 | isr0
[ 3537.259244] iwlwifi 0000:03:00.0: 0x0189E000 | isr1
[ 3537.259249] iwlwifi 0000:03:00.0: 0x00000E02 | isr2
[ 3537.259256] iwlwifi 0000:03:00.0: 0x0143ECC2 | isr3
[ 3537.259261] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[ 3537.259266] iwlwifi 0000:03:00.0: 0x01000112 | isr_pref
[ 3537.259272] iwlwifi 0000:03:00.0: 0x00029B36 | wait_event
[ 3537.259280] iwlwifi 0000:03:00.0: 0x00001988 | l2p_control
[ 3537.259287] iwlwifi 0000:03:00.0: 0x0000013A | l2p_duration
[ 3537.259294] iwlwifi 0000:03:00.0: 0x000000BF | l2p_mhvalid
[ 3537.259301] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[ 3537.259308] iwlwifi 0000:03:00.0: 0x00000004 | lmpm_pmg_sel
[ 3537.259315] iwlwifi 0000:03:00.0: 0x13011054 | timestamp
[ 3537.259322] iwlwifi 0000:03:00.0: 0x0000F000 | flow_handler
[ 3537.259455] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[ 3537.259514] iwlwifi 0000:03:00.0: EVT_LOGT:0028807544:0x00000000:0663
[ 3537.259561] iwlwifi 0000:03:00.0: EVT_LOGT:0028807545:0x0000002a:1592
[ 3537.259596] iwlwifi 0000:03:00.0: EVT_LOGT:0028807548:0x097f0018:0401
[ 3537.259630] iwlwifi 0000:03:00.0: EVT_LOGT:0028807589:0x00000112:0611
[ 3537.259665] iwlwifi 0000:03:00.0: EVT_LOGT:0028807589:0x00000113:0595
[ 3537.259700] iwlwifi 0000:03:00.0: EVT_LOGT:0028807610:0x00000183:0591
[ 3537.259735] iwlwifi 0000:03:00.0: EVT_LOGT:0028807610:0x00000187:0596
[ 3537.259769] iwlwifi 0000:03:00.0: EVT_LOGT:0028807611:0x0000019c:0605
[ 3537.259804] iwlwifi 0000:03:00.0: EVT_LOGT:0028807612:0x000001a1:1621
[ 3537.259839] iwlwifi 0000:03:00.0: EVT_LOGT:0028807613:0x00018ee8:0605
[ 3537.259876] iwlwifi 0000:03:00.0: EVT_LOGT:0028807613:0x00288000:0605
[ 3537.259916] iwlwifi 0000:03:00.0: EVT_LOGT:0028807614:0xffffffff:0605
[ 3537.259956] iwlwifi 0000:03:00.0: EVT_LOGT:0028807614:0x00000054:0591
[ 3537.259992] iwlwifi 0000:03:00.0: EVT_LOGT:0028807615:0xffffffff:0605
[ 3537.260027] iwlwifi 0000:03:00.0: EVT_LOGT:0028807616:0x0000000a:1250
[ 3537.260061] iwlwifi 0000:03:00.0: EVT_LOGT:0028807616:0x00000001:1250
[ 3537.260096] iwlwifi 0000:03:00.0: EVT_LOGT:0028807623:0x0000004b:1100
[ 3537.260131] iwlwifi 0000:03:00.0: EVT_LOGT:0028807635:0x00000087:0591
[ 3537.260166] iwlwifi 0000:03:00.0: EVT_LOGT:0028807637:0x0000010c:0123
[ 3537.260201] iwlwifi 0000:03:00.0: EVT_LOGT:0028807637:0x00000000:0125
[ 3547.214924] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 3547.222473] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[ 3602.368671] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 3602.376214] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0


```

---

### Post by leolino-lam on 2015-01-27
I'm having the same issue. It's not working after I suspend the laptop, but I fixed it with `killall wpa_supplicant`.

Have you tried that?

---

### Post by danbebber on 2015-03-29
You have the dreaded Intel Centrino 2230 card. See the stress that it has caused [https://communities.intel.com/thread/38676](https://communities.intel.com/thread/38676)
I have it in my Dell Inspiron 17SE. The only thing that worked for me is disabling Bluetooth. Now my wifi is almost as fast as on my Macbook Air.

---

