---
title: "Intel 7260 ac wireless card problem"
date: 2014-09-13
forum: Networking &amp; Wireless
---

### Post by kr4t0s2 on 2014-09-13
Hi guys I am new here, I recently purchased intel wireless card 7260hmw ac for my laptop which I had bcm4313 but it kept dropping connections after suspend. And I have to restart the router every time. To cut the story short I have installed the new wireless card and followed the instruction of loading the drivers to the firmware, I have also tried to use the additional software and I cant seem to find a good driver for it. I am getting the error message "Wifi is disabled by hardware switch". I am able to use the ethernet but I cant use the wifi. I have tried the rfkill commands and the output is "Hard blocked: yes" on phy0. So I am contemplaiting returning it but I dont want to send it back before I have troubleshoot it to the end. Thanks in advance I hope I can fix this.

---

### Post by jeremy31 on 2014-09-13
Follow the instructions to download, run, and post the results of the wireless_script [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
also post the results of ```
lsmod
```

It sounds like the same card as one of mine

---

### Post by kr4t0s2 on 2014-09-13
Here is the scripts output I did it with the ethernet port on
```

########## wireless info START ##########

Report from: 14 Sep 2014 07:55 MYT +0800

Script from: 05 Sep 2014 22:42 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:fd3c]
    Kernel driver in use: r8169

06:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 63)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4270]
    Kernel driver in use: iwlwifi

##### lsusb #####

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 8087:07dc Intel Corp. 
Bus 001 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd CNF9055 Toshiba Webcam
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #####

iwlmvm                189774  0 
mac80211              630653  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  1 toshiba_acpi

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ba70:f4ff:fe66:11f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8019498 (8.0 MB)  TX bytes:785322 (785.3 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr wlan0>

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
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.34
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             1.9.1.9
    DNS:             202.188.0.133

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

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

##### iwlist scan #####

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

##### module infos #####

[iwlmvm]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     478509C929B480278881B2A
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[iwlwifi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
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

##### module parameters #####

[iwlmvm]
init_dbg: N
power_scheme: 2

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

##### /etc/modules #####

lp
rtc

##### blacklists #####

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

##### rc.local #####

exit 0

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b2 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    5.010237] iwlwifi 0000:06:00.0: irq 43 for MSI/MSI-X
[    5.022835] iwlwifi 0000:06:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    5.065017] iwlwifi 0000:06:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    5.065093] iwlwifi 0000:06:00.0: L1 Enabled; Disabling L0S
[    5.065337] iwlwifi 0000:06:00.0: RF_KILL bit toggled to disable radio.
[    5.065365] iwlwifi 0000:06:00.0: L1 Enabled; Disabling L0S
[    5.093444] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    6.626235] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############]
```

Here is lsmod output
```
Module                  Size  Used by
snd_hda_codec_realtek    65580  1 
snd_hda_intel          56451  3 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
joydev                 17381  0 
arc4                   12608  2 
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
serio_raw              13462  0 
iwlmvm                189774  0 
mac80211              630653  1 iwlmvm
i915                  783805  3 
intel_ips              18664  0 
snd                    69322  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
iwlwifi               169932  1 iwlmvm
btusb                  32412  0 
lpc_ich                21080  0 
drm_kms_helper         53081  1 i915
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
drm                   303102  4 i915,drm_kms_helper
toshiba_acpi           22901  0 
mei_me                 18627  0 
i2c_algo_bit           13413  1 i915
sparse_keymap          13948  1 toshiba_acpi
soundcore              12680  1 snd
mei                    82276  1 mei_me
wmi                    19177  1 toshiba_acpi
rfcomm                 69160  8 
bnep                   19624  2 
bluetooth             391136  22 bnep,btusb,rfcomm
parport_pc             32701  0 
video                  19476  1 i915
mac_hid                13205  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
psmouse               106678  0 
ahci                   25819  2 
libahci                32716  1 ahci
r8169                  67581  0 
mii                    13934  1 r8169

```

---

### Post by jeremy31 on 2014-09-13
This might be one that needs toshiba_acpi to be blacklisted.  Try ```
echo "blacklist toshiba_acpi" | sudo tee -a /etc/modprobe.d/blacklist.conf
``` and reboot

---

### Post by kr4t0s2 on 2014-09-14
Nope it didnt work :(

---

### Post by praseodym on 2014-09-14
Your card is shut off. Any button, switch, key or key combination? Any possibility in your BIOS to turn it on?

---

### Post by kr4t0s2 on 2014-09-14
I have tried fn + f8 it does not work. I also have tried to reset bios to default but nothing changes. There is no other physical button :(

---

### Post by jeremy31 on 2014-09-14
> **kr4t0s2 said:**
> I have tried fn + f8 it does not work. I also have tried to reset bios to default but nothing changes. There is no other physical button :(

Does your Toshiba have another set of buttons like mine between the keyboard and display
[IMG]http://17c4dcd7f91259d8cc66-f5932f6db0039e8c02f89a70c334ff0e.r2.cf1.rackcdn.com/wp-content/uploads/sites/2/53069.jpg[/IMG]
The one with the wifi icon will hard block my wifi

---

### Post by kr4t0s2 on 2014-09-14
My toshiba is a bit old its a toshiba satellite c660. It doesn't have those buttons. Yours looks cool though

---

### Post by jeremy31 on 2014-09-14
Is your BIOS the latest version?  Have you gone into BIOS and reset to defaults?  

Mine might look cool but I can only use the wifi card that it came with, an Intel 6250 wireless-n + WiMax as any others I have tried haven't worked even in Windows

---

### Post by kr4t0s2 on 2014-09-14
Yes the bios is the latest version 2.00, That must be so annoying

---

### Post by praseodym on 2014-09-14
Reload that module:

```
sudo modprobe -v toshiba_acpi
```
and try the buttons again.

---

### Post by kr4t0s2 on 2014-09-14
Nothing changed after reload

---

### Post by praseodym on 2014-09-14
Try 
```

sudo rfkill unblock all
rfkill list
iwconfig
```
Unfortunately, the module shows no additional parameters:

```
modinfo toshiba_acpi 
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/toshiba_acpi.ko
license:        GPL
description:    Toshiba Laptop ACPI Extras Driver
author:         John Belmonte
srcversion:     8BEFA8D9409D0EACD8E7FFF
alias:          acpi*:TOS1900:*
alias:          acpi*:TOS6208:*
alias:          acpi*:TOS6200:*
depends:        wmi,sparse-keymap
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
```

---

### Post by kr4t0s2 on 2014-09-14
Nothing changed
```
maverix@Kratos:~$ sudo rfkill unblock all
[sudo] password for maverix: 
maverix@Kratos:~$ rfkill list
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
maverix@Kratos:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

```

---

### Post by praseodym on 2014-09-14
Ok, lets check:
```

sudo modprobe -rfv iwlwifi
sudo rfkill unblock all
sudo modprobe -v iwlwifi
rfkill list
iwconfig
grep iwl /etc/modprobe.d/*
dmesg | grep iwl
```

---

### Post by kr4t0s2 on 2014-09-14
Doesnt work :(
```
maverix@Kratos:~$ sudo modprobe -rfv iwlwifi
[sudo] password for maverix: 
remove (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) && /sbin/modprobe -r mac80211
rmmod mac80211
rmmod cfg80211
maverix@Kratos:~$ sudo rfkill unblock all
maverix@Kratos:~$ sudo modprobe -v iwlwifi
insmod /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 
maverix@Kratos:~$ rfkill list
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
5: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
maverix@Kratos:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
maverix@Kratos:~$ grep iwl /etc/modprobe.d/*
/etc/modprobe.d/iwlwifi.conf:# /etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/iwlwifi.conf:# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
/etc/modprobe.d/iwlwifi.conf:# microcode file installed on the system.  When removing iwlwifi, first
/etc/modprobe.d/iwlwifi.conf:# remove the iwl?vm module and then iwlwifi.
/etc/modprobe.d/iwlwifi.conf:remove iwlwifi \
/etc/modprobe.d/iwlwifi.conf:(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
maverix@Kratos:~$ dmesg | grep iwl
[    5.600347] iwlwifi 0000:06:00.0: irq 43 for MSI/MSI-X
[    5.615224] iwlwifi 0000:06:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    5.674727] iwlwifi 0000:06:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    5.674812] iwlwifi 0000:06:00.0: L1 Enabled; Disabling L0S
[    5.675057] iwlwifi 0000:06:00.0: RF_KILL bit toggled to disable radio.
[    5.675150] iwlwifi 0000:06:00.0: L1 Enabled; Disabling L0S
[    5.741412] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[ 1267.335567] iwlwifi 0000:06:00.0: RF_KILL bit toggled to disable radio.
[ 1844.886128] iwlwifi 0000:06:00.0: RF_KILL bit toggled to disable radio.
[ 1851.977816] iwlwifi 0000:06:00.0: RF_KILL bit toggled to disable radio.
[ 1903.375176] iwlwifi 0000:06:00.0: irq 43 for MSI/MSI-X
[ 1903.375924] iwlwifi 0000:06:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[ 1903.398672] iwlwifi 0000:06:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[ 1903.398750] iwlwifi 0000:06:00.0: L1 Enabled; Disabling L0S
[ 1903.398991] iwlwifi 0000:06:00.0: RF_KILL bit toggled to disable radio.
[ 1903.399018] iwlwifi 0000:06:00.0: L1 Enabled; Disabling L0S
[ 1903.408965] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
maverix@Kratos:~$ 

```

---

### Post by praseodym on 2014-09-14
Strange. Try to press the key combination permanently or repeatedly during boot-up

---

### Post by kr4t0s2 on 2014-09-14
Nothing. But I tried switching to windows and it still doesnt work even with the drivers installed before posting it here. The ethernet and bluetooth work but wifi doesnt. Does this mean that it is incompatible with my laptop?

---

### Post by praseodym on 2014-09-14
Thats possible. If it is not listed in the BIOS whitelist, there may be no chance. Broadcom 4313 works better. Please show the wireless script output with that card

---

### Post by kr4t0s2 on 2014-09-14
Ok here is the result of bcm4313
```

########## wireless info START ##########

Report from: 15 Sep 2014 01:42 MYT +0800

Script from: 05 Sep 2014 22:42 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:fd3c]
    Kernel driver in use: r8169

06:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7175]
    Kernel driver in use: bcma-pci-bridge

##### lsusb #####

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0930:0214 Toshiba Corp. 
Bus 001 Device 004: ID 04f2:b1d6 Chicony Electronics Co., Ltd CNF9055 Toshiba Webcam
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

brcmsmac              563041  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
b43                   387371  0 
mac80211              630653  2 b43,brcmsmac
cfg80211              484040  3 b43,brcmsmac,mac80211
ssb                    62379  1 b43
bcma                   52096  3 b43,brcmsmac

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr <MAC addr wlan1>  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e2ca:94ff:fe03:abb6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77912 (77.9 KB)  TX bytes:46236 (46.2 KB)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"streamyx_sarah_103"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC addr streamyx_sarah_103>   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:59   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan1
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan1  [streamyx_sarah_103] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        <MAC addr wlan1>

  Capabilities:
    Speed:           36 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    syimma13:        Infra, <MAC addr syimma13>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Streamyx_YUN:    Infra, <MAC addr Streamyx_YUN>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WEP
    Streamyx_montague: Infra, <MAC addr Streamyx_montague>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WEP
    *streamyx_sarah_103: Infra, <MAC addr streamyx_sarah_103>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WEP

  IPv4 Settings:
    Address:         192.168.1.33
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             1.9.1.9
    DNS:             202.188.0.133

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iw reg get #####

country SG:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5735 - 5835 @ 40), (N/A, 20)

##### iwlist channels #####

eth0      no frequency information.

lo        no frequency information.

wlan1     13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #####

Channel occupancy:

     2   WLAPs on   Frequency:2.412 GHz (Channel 1)
     2   WLAPs on   Frequency:2.437 GHz (Channel 6)

wlan1     Scan completed :
          Cell 01 - Address: <MAC addr streamyx_sarah_103>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-17 dBm  
                    Encryption key:on
                    ESSID:"streamyx_sarah_103"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014a5429a72
                    Extra: Last beacon: 20ms ago
          Cell 02 - Address: <MAC addr Streamyx_YUN>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Streamyx_YUN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000179529de24e
                    Extra: Last beacon: 172ms ago
          Cell 03 - Address: <MAC addr Streamyx_montague>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Streamyx_montague"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000090b7dacd84
                    Extra: Last beacon: 20ms ago
          Cell 04 - Address: <MAC addr syimma13>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"syimma13"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000018f4ea99177
                    Extra: Last beacon: 1548ms ago

lo        Interface doesn't support scanning.

00000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos #####

[brcmsmac]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     43D6897F7EB716081DF69BE
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512

[brcmutil]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512

[b43]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     7ABBDDCA84C087640B27AE6
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512
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

[ssb]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512

[bcma]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512

##### module parameters #####

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

##### /etc/modules #####

lp
rtc

##### blacklists #####

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
blacklist toshiba_acpi

##### rc.local #####

exit 0

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b2 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #####

[    5.626494] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[    5.626523] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[    5.626545] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[    5.626589] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[    5.639474] bcma: bus0: Bus registered
[    6.049194] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[    6.049198] b43: probe of bcma0:0 failed with error -524
[    6.075207] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[    6.088299] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[    6.115362] systemd-udevd[334]: renamed network interface wlan0 to wlan1
[    7.753116] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[    7.753127] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[    7.753298] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[   59.948880] wlan1: authenticate with <MAC addr streamyx_sarah_103>
[   59.950202] wlan1: send auth to <MAC addr streamyx_sarah_103> (try 1/3)
[   59.951663] wlan1: authenticated
[   59.951919] brcmsmac bcma0:0 wlan1: disabling HT/VHT due to WEP/TKIP use
[   59.951923] brcmsmac bcma0:0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[   59.951925] brcmsmac bcma0:0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[   59.952467] wlan1: associate with <MAC addr streamyx_sarah_103> (try 1/3)
[   59.955384] wlan1: RX AssocResp from <MAC addr streamyx_sarah_103> (capab=0x431 status=0 aid=2)
[   59.956289] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   59.956293] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   59.956301] wlan1: associated
[   59.956324] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   59.975031] wlan1: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC addr streamyx_sarah_103>
[   60.014291] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)

########## wireless info END ############
```

---

### Post by praseodym on 2014-09-14
There are 2 drivers loaded:
```

echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv b43 brcmsmac
sudo modprobe -v brcmsmac
```

---

### Post by kr4t0s2 on 2014-09-14
Ok Now I cant connect to the internet on the bcm4313. So should I  put back the intel card?

---

### Post by praseodym on 2014-09-14
Why not using this one?

---

### Post by kr4t0s2 on 2014-09-14
Well when I resume from suspend the wireless is usually down and I dont know a simple way to turn it on. Other than restarting my router every time and this is going to bother especially when the new semester starts and I use it as my main laptop. I have a mac air but I will use the toshiba for some time as my main laptop until I have enough money to replace the current mac air battery.

---

### Post by praseodym on 2014-09-14
Run these commands:

```
sudo touch /etc/pm/config.d/00sleep_module
sudo chmod +x /etc/pm/config.d/00sleep_module
echo 'SUSPEND_MODULES="$SUSPEND_MODULES brcmsmac"' | sudo tee  /etc/pm/config.d/00sleep_module
```
-

---

### Post by kr4t0s2 on 2014-09-15
This seems to have worked so far I wont close the topic yet I will give it a day or two of testing. Thanks :)

---

### Post by kr4t0s2 on 2014-09-19
Thanks to everybody who helped in fixing my wireless problem. It works perfectly now without worrying.

---

### Post by kr4t0s2 on 2014-09-19
How do I mark this as 'solved'? or can someone do that for me. Thanks again :)

---

### Post by jeremy31 on 2014-09-19
You need to go to the first post in the thread and click on edit post and just add [SOLVED] to the title if I remember correctly

---

### Post by kr4t0s2 on 2014-09-21
Hi guys I switched to ubuntu gnome and the above commands dont work anymore :(
```
maverix@Kratos:~$ sudo touch /etc/pm/config.d/00sleep_module
[sudo] password for maverix: 
touch: cannot touch ‘/etc/pm/config.d/00sleep_module’: No such file or directory
```

---

### Post by praseodym on 2014-09-21
Then create it via

```
gksudo gedit /etc/pm/config.d/00sleep_module
```
and add

```
SUSPEND_MODULES="$SUSPEND_MODULES brcmsmac"
```
Save, close the editor and run

```
sudo touch /etc/pm/config.d/00sleep_module
```

---

### Post by kr4t0s2 on 2014-09-21
There is no config.d directory in gnome. Should I just create it and save the sleep module in it?

---

### Post by praseodym on 2014-09-21
Yes

---

### Post by kr4t0s2 on 2014-09-24
Hi guys I went to back to campus today and I couldnt connect to the wifi. I took the laptop to the IT guys( who are not linux users, I wonder what servers they are running ). It took alot of time. But we couldnt come to a fix because the laptop was appearing in the network. But I could not surf the web with my browsers. We tried to ping but it was rejected by my laptop. What can be the problem now? Thanks in advance?

---

