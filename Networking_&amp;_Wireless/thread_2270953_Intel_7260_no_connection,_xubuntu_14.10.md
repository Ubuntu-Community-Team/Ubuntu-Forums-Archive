---
title: "Intel 7260 no connection, xubuntu 14.10"
date: 2015-03-26
forum: Networking &amp; Wireless
---

### Post by Krillo on 2015-03-26
Hi all

I can't get wifi working on my laptop HP Spectre 13 x2 13-h275eo, which has the infamous Intel 7260.
I've been reading alot of threads on this matter and I was reluctant to start yet another one, but I'm getting nowhere :(

Any help would be much appreciated, thanks!

```

########## wireless info START ##########

Report from: 26 Mar 2015 17:41 CET +0100

Booted last: 26 Mar 2015 17:12 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic

##### kernel ############################

Linux 3.16.0-33-generic #44-Ubuntu SMP Thu Mar 12 12:19:35 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

07:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 001 Device 008: ID 04f3:0217 Elan Microelectronics Corp. 
Bus 001 Device 006: ID 0bda:5777 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 06cb:5711 Synaptics, Inc. 
Bus 001 Device 004: ID 8087:07dc Intel Corp. 
Bus 001 Device 003: ID 0483:91d1 STMicroelectronics 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: nfc0: NFC
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

iwlmvm                255316  0 
mac80211              578037  1 iwlmvm
hp_wmi                 14109  0 
acer_wmi               32522  0 
sparse_keymap          13948  2 acer_wmi,hp_wmi
iwlwifi               186159  1 iwlmvm
cfg80211              508913  3 iwlwifi,mac80211,iwlmvm
compat                 14427  4 cfg80211,iwlwifi,mac80211,iwlmvm
wmi                    19193  2 acer_wmi,hp_wmi
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104102  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
video                  20128  2 i915,acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### nm-tool ###########################

NetworkManager Tool

State: disconnected

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

##### iw reg get ########################

Region: Europe/Stockholm (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR

##### iwlist channels ###################

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

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.16.0-33-generic/updates/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     D67AF5074A61978919B7356
depends:        iwlwifi,mac80211,compat,cfg80211
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.16.0-33-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
srcversion:     A9C2E81BFFB8CD560F6A03B
depends:        cfg80211,compat
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.16.0-33-generic/updates/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:d
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
firmware:       iwlwifi-3165-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     3F79E6B9DBC4489492CABD9
depends:        compat,cfg80211
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
parm:           debug:debug output mask (uint)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.16.0-33-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     07F008E2B6279F6399E5939
depends:        compat
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2

[mac80211]
beacon_loss_count: 7
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
debug: 0
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
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
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

rfkill block bluetooth
exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   12.846039] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[   12.857696] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.033829] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   14.046904] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.845054] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   15.858307] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.842829] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   17.855413] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.840882] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   19.854346] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.840388] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   21.853523] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.849574] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   23.863001] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.837909] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   25.850631] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.838265] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   27.850936] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.834051] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   29.847104] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.833538] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   31.846281] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.842774] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   33.856009] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.828188] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   35.840720] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.829457] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   37.842955] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.839386] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   39.852820] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.824810] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   41.837510] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.836332] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   43.849283] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.822909] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   45.835934] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   47.820859] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   47.835916] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   49.831725] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   49.845006] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.816899] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   51.831806] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   53.827696] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   53.841099] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   55.814365] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   55.828490] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   57.813628] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   57.829125] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   59.811177] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[   59.824648] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   61.760414] iwlwifi 0000:07:00.0: RF_KILL bit toggled to disable radio.

########## wireless info END ############


```

---

### Post by jeremy31 on 2015-03-26
Try ```
sudo modprobe -r acer_wmi
``````
sudo rfkill unblock all
``` and see if wifi works

---

### Post by Krillo on 2015-03-26
> **jeremy31 said:**
> Try ```
sudo modprobe -r acer_wmi
``````
sudo rfkill unblock all
``` and see if wifi works

Thanks, tried it, no errors, but no change either.

---

### Post by jeremy31 on 2015-03-26
I would try ```
echo "blacklist acer_wmi" | sudo tee /etc/modprobe.d/acer_wmi.conf
``` and reboot and see if the hard block is gone

---

### Post by Krillo on 2015-03-27
> **jeremy31 said:**
> I would try ```
echo "blacklist acer_wmi" | sudo tee /etc/modprobe.d/acer_wmi.conf
``` and reboot and see if the hard block is gone

Hell yeah :D
Now I just need to read up on what that did :-k

Thanks a ton!!

[ATTACH=CONFIG]260919[/ATTACH]

---

### Post by jeremy31 on 2015-03-27
We just prevented an unneeded module from loading, why an acer module would be loaded on a HP laptop is beyond me

---

### Post by Krillo on 2015-03-27
Yeah, that puzzled me too!

---

### Post by Krillo on 2015-04-11
So a summary of how to get wifi working on HP Spectre X2:
(copied partly from [http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63](http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63))

Get: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2)

Right-click it and select 'Extract Here.' Now open a terminal and do:

```

cd Desktop/backports-3.11-rc3-1/
make defconfig-iwlwifi
make
sudo make install
```

Get: [https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode](https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode)

Do:

```
sudo cp ~/Desktop/iwlwifi-7260-7.ucode /lib/firmware/  <--or wherever you downloaded it
sudo modprobe -r iwldvm  <--If it is not loaded, OK, please proceed
sudo modprobe -r iwlwifi <--If it is not loaded, OK, please proceed
sudo modprobe iwlwifi
```

And lastly:

```
echo "blacklist acer_wmi" | sudo tee /etc/modprobe.d/acer_wmi.conf
```

Now you should have working wifi on HP Spectre X2

---

### Post by Krillo on 2015-04-11
When attempting this on Ubuntu Mate, I get

```
user@laptop:~/Desktop/backports-3.11-rc3-1$ make defconfig-iwlwifi
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
make[2]: cc: Command not found
<builtin>: recipe for target 'conf.o' failed
make[2]: *** [conf.o] Error 127
Makefile.real:36: recipe for target 'defconfig-iwlwifi' failed
make[1]: *** [defconfig-iwlwifi] Error 2
Makefile:40: recipe for target 'defconfig-iwlwifi' failed
make: *** [defconfig-iwlwifi] Error 2
user@laptop:~/Desktop/backports-3.11-rc3-1$ 


```

I have no clue to what's going on. :-k

---

### Post by jeremy31 on 2015-04-11
It might be easier to go into system settings, software and updates, and click next to source code so you can download the source code for your kernel and modify it so you can use the older firmware.  Once source code is enabled and the updates are refreshed, you can open terminal and
```
apt-get source linux-lts-utopic
```

Then ```
gedit ~/linux-lts-utopic-3.16.0/drivers/net/wireless/iwlwifi/iwl-7000.c
```

Go to line 77 and you should see ```
/* Lowest firmware API version supported */
#define IWL7260_UCODE_API_MIN    8
#define IWL3160_UCODE_API_MIN    8
```
And make it be ```
/* Lowest firmware API version supported */
#define IWL7260_UCODE_API_MIN    7
```

Save and exit
```
cd ~/linux-lts-utopic-3.16.0/drivers/net/wireless/iwlwifi
```
```
cp /boot/config-$(uname -r) .config
```
```
cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
```
```
make -C /lib/modules/$(uname -r)/build M=$PWD modules
```
```
sudo mv /lib/modules/$(uname -r)/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko.bak
```
```
sudo cp iwlwifi.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/iwlwifi/
```

Reboot, you are likely going to have to rename any iwlwifi-7260 ucode files that are higher than 7 to keep them from loading

---

### Post by Krillo on 2015-04-11
Thanks for the detailed post :)

Please note that I installed Ubuntu Mate. Maybe I should move my post to the appropriate sub-forum?

*Edit:* So I did this
```
sudo modprobe -r acer_wmi

sudo rfkill unblock all
 
 
echo "blacklist acer_wmi" | sudo tee /etc/modprobe.d/acer_wmi.conf
```

again, and it works. So it was simpler than I initially thought!
Problem now is that it doesn't connect automatically, even though it is set to do so.

---

