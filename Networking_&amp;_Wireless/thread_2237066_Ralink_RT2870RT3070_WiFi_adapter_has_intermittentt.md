---
title: "Ralink RT2870/RT3070 WiFi adapter has intermittent/temporamental connection"
date: 2014-07-30
forum: Networking &amp; Wireless
---

### Post by chris271 on 2014-07-30
Hi ive recently started using ubuntu and it is the only OS installed on the system, even though my wifi is at full bar when i try to connect after a few seconds "Disconnect - You are now offline appears".

It has worked before and the adapter works fine on Windows AND KALI!

Adapter: RT2870/RT3070

Please help ive also tried 3 different wifis and they keep dropping me out.

p.s. been working through tutorials for the past 3 days trying to fix this so this forum post is my last hope :(


Thank you!!

---

### Post by praseodym on 2014-07-30
Please show
```

lsusb
lsmod
iwconfig
ifconfig -a
cat /etc/resolv.conf
sudo iwlist scan
```

---

### Post by chris271 on 2014-07-30
```
user@user-Latitude-E4310:~$ lsusb
Bus 002 Device 005: ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor
Bus 002 Device 008: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@user-Latitude-E4310:~$ lsmod
Module                  Size  Used by
rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              12707  1 rt2800lib
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   19624  2 
rfcomm                 69160  0 
arc4                   12608  4 
iwldvm                232285  0 
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
snd_hda_codec_hdmi     46207  1 
snd_hda_codec_idt      54645  1 
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
snd_hda_intel          52355  3 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
ath9k_htc              95963  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ath9k_common           13551  1 ath9k_htc
btusb                  32412  0 
ath9k_hw              453856  2 ath9k_common,ath9k_htc
bluetooth             395423  11 bnep,btusb,rfcomm
ath                    28698  3 ath9k_common,ath9k_htc,ath9k_hw
mac80211              626557  5 rt2x00lib,rt2x00usb,rt2800lib,iwldvm,ath9k_htc
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
kvm                   451511  1 kvm_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
joydev                 17381  0 
snd                    69238  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
serio_raw              13462  0 
iwlwifi               169932  1 iwldvm
intel_ips              18664  0 
cfg80211              484040  6 ath,iwlwifi,mac80211,rt2x00lib,iwldvm,ath9k_htc
lpc_ich                21080  0 
soundcore              12680  1 snd
mei_me                 18627  0 
mei                    82276  1 mei_me
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
dm_crypt               23177  1 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  2 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
i915                  783703  8 
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  4 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse               102222  0 
e1000e                254433  0 
i2c_algo_bit           13413  1 i915
ahci                   25819  2 
drm_kms_helper         53081  1 i915
ptp                    18933  1 e1000e
libahci                32168  1 ahci
drm                   303102  4 i915,drm_kms_helper
pps_core               19382  1 ptp
sdhci_pci              23172  0 
sdhci                  43015  1 sdhci_pci
wmi                    19177  1 dell_wmi
video                  19476  1 i915
user@user-Latitude-E4310:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan3     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
user@user-Latitude-E4310:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 5c:26:0a:3a:51:4a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f5400000-f5420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5553 (5.5 KB)  TX bytes:5553 (5.5 KB)

wlan0     Link encap:Ethernet  HWaddr 58:94:6b:cc:72:9c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan3     Link encap:Ethernet  HWaddr 00:c0:ca:59:cc:9d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

user@user-Latitude-E4310:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
user@user-Latitude-E4310:~$ sudo iwlist scan
```

---

### Post by chris271 on 2014-07-30
Sorry about the smileys :s

---

### Post by praseodym on 2014-07-30
First: You need nameservers in your /etc/resolv.conf:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```
Second: There is an Atheros driver loaded (ath9k_htc). Unload it:
```

sudo modprobe -rfv rt2800usb ath9k_htc
sudo modprobe -v rt2800usb
```
Replug the stick.

Third: Do you have an internal Intel card? There is the driver iwlwifi loaded. Lets check:
```

lspci -nnk | grep -iA2 net
cat /etc/udev/rules.d/70-persistent-net.rules
```
I think there is one, because there is also an Intel LAN driver loaded (e1000e). But we will see later...

---

### Post by chris271 on 2014-07-30
Yes i do have an internal card, i run the commands and wifi still acts the same.. trys to connect then brings up the "Disconnected" message

I think its a problem with the built in driver that comes with ubuntu, i checked kali with the adapter again and it all works fine and also switched to a weaker adapter i have and tried that on ubuntu which also worked fine.

So the two definitely dont go together well! :/

Thanks for the help.

---

### Post by chris271 on 2014-07-30
I followed instructions from here [http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385), hopefully this helps.


```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

user-Latitude-E4310 3.13.0-30-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5 CPU       M 560  @ 2.67GHz
Memory : 3753 MB
Uptime : 04:44:14 up  6:40,  1 user,  load average: 0.05, 0.08, 0.06


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 05)
    Subsystem: Dell Device [1028:0410]
    Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1321]
    Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 005: ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor
Bus 002 Device 027: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 025: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan3     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=30 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface               Soft blocked  Hard blocked
1: dell-wifi: Wireless LAN        no            no
2: dell-bluetooth: Bluetooth      yes           no
3: phy0: Wireless LAN             no            no
12: phy9: Wireless LAN            no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k_htc              95963  0 
ath9k_common           13551  1 ath9k_htc
ath9k_hw              453856  2 ath9k_common,ath9k_htc
ath                    28698  3 ath9k_common,ath9k_htc,ath9k_hw
rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              12707  1 rt2800lib
iwldvm                232285  0 
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
mac80211              626557  5 rt2x00lib,rt2x00usb,rt2800lib,iwldvm,ath9k_htc
iwlwifi               169932  1 iwldvm
cfg80211              484040  6 ath,iwlwifi,mac80211,rt2x00lib,iwldvm,ath9k_htc
wmi                    19177  1 dell_wmi


module parameters ~~~~~~~~~~~~~~~~~~

ath9k_htc     (3): btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800usb     (1): nohwcrypt=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
================o=============o===========o==============o=========o===========o==============o===========
 wlan3          | 802.11 WiFi | rt2800usb | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan3>

*WIRELESS NETWORK INFO REMOVED*

----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | iwlwifi   | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    *WIRELESS NETWORK INFO REMOVED*

----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | e1000e    | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 8.8.8.8
nameserver 8.8.4.4


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_GB.UTF-8")
country BO:
    (2402 - 2482 @ 40), (N/A, 30)
    (5735 - 5835 @ 40), (N/A, 30)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan3     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          wlan0     18 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan3     Scan completed :
          *WIRELESS NETWORK INFO REMOVED*
wlan0     Scan completed :
          *WIRELESS NETWORK INFO REMOVED*


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k_htc]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
srcversion:     76D0CC269ACAA11EA825B93
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

[ath]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[rt2800usb]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
firmware:       rt2870.bin
version:        2.3.0
srcversion:     D6F814DAF78F2BEA3DA12CB
depends:        rt2x00lib,rt2800lib,rt2x00usb
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
version:        2.3.0
srcversion:     44768071492503F8EFE1EED
depends:        rt2x00lib,mac80211

[rt2800lib]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
version:        2.3.0
srcversion:     9BD0087B6943A41E7FD8EDA
depends:        rt2x00lib,mac80211,crc-ccitt

[rt2x00lib]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     C57F87A3569F5363E79FD42
depends:        mac80211,cfg80211

[crc_ccitt]
filename:       /lib/modules/3.13.0-30-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        

[iwldvm]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
version:        in-tree:
srcversion:     C000699B57577A9A45666BA
depends:        iwlwifi,mac80211,cfg80211

[dell_wmi]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/platform/x86/dell-wmi.ko
srcversion:     0ED3A43A5709CF19B7DFD19
depends:        wmi,sparse-keymap

[mac80211]
filename:       /lib/modules/3.13.0-30-generic/kernel/net/mac80211/mac80211.ko
srcversion:     6F23437712851B1B0563BCB
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
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
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     1E6912E109D5A43B310FB34
depends:        cfg80211
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
filename:       /lib/modules/3.13.0-30-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x10ea (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x422c (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan2>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan3>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan3"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/vmlinuz-3.13.0-30-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.157287] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.157651] audit: initializing netlink socket (disabled)
[    1.646584] wmi: Mapper loaded
[   23.660698] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   23.660901] iwlwifi 0000:02:00.0: irq 44 for MSI/MSI-X
[   23.710013] iwlwifi 0000:02:00.0: Direct firmware load failed with error -2
[   23.710020] iwlwifi 0000:02:00.0: Falling back to user helper
[   23.773271] usb 2-1.1.4: ath9k_htc: Firmware htc_9271.fw requested
[   23.773384] usbcore: registered new interface driver ath9k_htc
[   23.857584] iwlwifi 0000:02:00.0: Direct firmware load failed with error -2
[   23.857589] iwlwifi 0000:02:00.0: Falling back to user helper
[   23.911123] iwlwifi 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[   23.915712] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   23.915715] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   23.915717] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   23.915719] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   23.915814] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   23.935069] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   24.148254] usb 2-1.1.4: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   24.384762] ath9k_htc 2-1.1.4:1.0: ath9k_htc: HTC initialized with 33 credits
[   24.615248] ath9k_htc 2-1.1.4:1.0: ath9k_htc: FW Version: 1.3
[   24.615255] ath: EEPROM regdomain: 0x809c
[   24.615257] ath: EEPROM indicates we should expect a country code
[   24.615260] ath: doing EEPROM country->regdmn map search
[   24.615263] ath: country maps to regdmn code: 0x52
[   24.615265] ath: Country alpha2 being used: CN
[   24.615267] ath: Regpair used: 0x52
[   24.635970] systemd-udevd[454]: renamed network interface wlan1 to wlan2
[   26.588508] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.182795] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   29.189506] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
[   29.402234] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   29.408934] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
[   29.534405] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.534736] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.840085] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   29.841176] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   32.138849] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   57.501347] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   87.504700] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   93.550397] ath: phy1: RX failed to go idle in 10 ms RXSM=0xb892f0cc
[   93.754713] ath: phy1: RX failed to go idle in 10 ms RXSM=0xb892f0cc
[   93.864221] usb 2-1.1.4: ath9k_htc: USB layer deinitialized
[  196.854458] ieee80211 phy2: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  196.885316] ieee80211 phy2: rt2x00_set_rf: Info - RF chipset 0005 detected
[  196.923683] systemd-udevd[2479]: renamed network interface wlan1 to wlan3
[  196.924888] ieee80211 phy2: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  196.934201] ieee80211 phy2: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  197.234541] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[  197.235224] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[  198.715420] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[  224.473168] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[  227.489682] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[  253.480788] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[  256.480047] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[  282.478742] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[  285.498934] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[  311.489417] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[  314.489384] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[  321.706686] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[  583.962400] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  583.962412] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[ 2109.192500] ieee80211 phy2: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[ 4148.708455] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 4148.708702] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 4148.800573] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4283.696247] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4284.291704] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 4284.291917] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 4284.386841] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4284.387295] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4348.471596] usbcore: deregistering interface driver ath9k_htc
[ 4348.471613] ath9k_htc: Driver unloaded
[ 4479.991919] ieee80211 phy3: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[ 4480.022148] ieee80211 phy3: rt2x00_set_rf: Info - RF chipset 0005 detected
[ 4480.364924] systemd-udevd[3830]: renamed network interface wlan1 to wlan3
[ 4480.366854] ieee80211 phy3: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[ 4480.366919] ieee80211 phy3: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[ 4480.668028] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 4480.668717] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 4482.112150] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 4507.878374] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 4510.858517] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 4515.722930] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 4520.131601] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 4545.861723] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 4548.865807] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 4552.590807] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 4552.938464] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 4555.126922] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 4557.811624] ieee80211 phy3: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[ 4558.770598] ieee80211 phy4: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[ 4558.800935] ieee80211 phy4: rt2x00_set_rf: Info - RF chipset 0005 detected
[ 4558.851925] systemd-udevd[3846]: renamed network interface wlan1 to wlan3
[ 4558.853259] ieee80211 phy4: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[ 4558.853300] ieee80211 phy4: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[ 4559.131035] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 4559.131772] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 4560.587165] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 4563.948229] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 4572.132932] ieee80211 phy4: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[ 4910.002881] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 4910.003151] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 4910.094687] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5013.383090] usb 2-1.1.4: ath9k_htc: Firmware htc_9271.fw requested
[ 5013.383262] usbcore: registered new interface driver ath9k_htc
[ 5013.530163] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 5013.530469] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 5013.627884] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5013.673205] usb 2-1.1.4: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[ 5013.911867] ath9k_htc 2-1.1.4:1.0: ath9k_htc: HTC initialized with 33 credits
[ 5014.181759] ath9k_htc 2-1.1.4:1.0: ath9k_htc: FW Version: 1.3
[ 5014.181764] ath: EEPROM regdomain: 0x809c
[ 5014.181767] ath: EEPROM indicates we should expect a country code
[ 5014.181770] ath: doing EEPROM country->regdmn map search
[ 5014.181772] ath: country maps to regdmn code: 0x52
[ 5014.181775] ath: Country alpha2 being used: CN
[ 5014.181777] ath: Regpair used: 0x52
[ 5014.204066] systemd-udevd[4694]: renamed network interface wlan1 to wlan2
[ 5014.512748] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 5014.513480] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 5016.822497] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 5042.909442] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 5140.864879] ath: phy5: RX failed to go idle in 10 ms RXSM=0x60decb
[ 5141.072631] ath: phy5: RX failed to go idle in 10 ms RXSM=0xa822b59c
[ 5141.279332] ath: phy5: RX failed to go idle in 10 ms RXSM=0xa822b59c
[ 5141.480993] ath: phy5: RX failed to go idle in 10 ms RXSM=0xa822b59c
[ 5141.690140] ath: phy5: RX failed to go idle in 10 ms RXSM=0xa822b59c
[ 5141.892148] ath: phy5: RX failed to go idle in 10 ms RXSM=0x60decb
[ 5142.097612] ath: phy5: Chip reset failed
[ 5142.097619] ath: phy5: Unable to reset channel (2412 Mhz) reset status -22
[ 5142.097657] ath: phy5: Unable to set channel
[ 5142.198525] ath: phy5: RX failed to go idle in 10 ms RXSM=0xeaffffff
[ 5142.198610] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 5142.405811] ath: phy5: RX failed to go idle in 10 ms RXSM=0xe4fd30cd
[ 5142.416071] ath: phy5: Failed to wakeup in 500us
[ 5142.518117] ath: phy5: RX failed to go idle in 10 ms RXSM=0xe4fd30cd
[ 5142.737138] ath: phy5: RX failed to go idle in 10 ms RXSM=0xb852facc
[ 5142.947592] ath: phy5: RX failed to go idle in 10 ms RXSM=0xb852facc
[ 5143.241455] usb 2-1.1.4: ath9k_htc: USB layer deinitialized
[ 5146.533734] usb 2-1.1.4: ath9k_htc: Firmware htc_9271.fw requested
[ 5146.824715] usb 2-1.1.4: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[ 5147.062591] ath9k_htc 2-1.1.4:1.0: ath9k_htc: HTC initialized with 33 credits
[ 5147.331142] ath9k_htc 2-1.1.4:1.0: ath9k_htc: FW Version: 1.3
[ 5147.331147] ath: EEPROM regdomain: 0x809c
[ 5147.331149] ath: EEPROM indicates we should expect a country code
[ 5147.331152] ath: doing EEPROM country->regdmn map search
[ 5147.331155] ath: country maps to regdmn code: 0x52
[ 5147.331157] ath: Country alpha2 being used: CN
[ 5147.331159] ath: Regpair used: 0x52
[ 5147.356173] systemd-udevd[5333]: renamed network interface wlan1 to wlan2
[ 5147.664275] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 5147.664954] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 5149.758439] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 5152.607286] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 5180.985669] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 5206.979245] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 5209.975059] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 5222.125749] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 5240.562025] ath: phy6: RX failed to go idle in 10 ms RXSM=0xb852b0a4
[ 5240.770963] ath: phy6: RX failed to go idle in 10 ms RXSM=0xb852b0a4
[ 5240.892951] usb 2-1.1.4: ath9k_htc: USB layer deinitialized
[ 9066.252922] usb 2-1.1.4: ath9k_htc: Firmware htc_9271.fw requested
[ 9066.544999] usb 2-1.1.4: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[ 9066.782930] ath9k_htc 2-1.1.4:1.0: ath9k_htc: HTC initialized with 33 credits
[ 9067.051454] ath9k_htc 2-1.1.4:1.0: ath9k_htc: FW Version: 1.3
[ 9067.051460] ath: EEPROM regdomain: 0x809c
[ 9067.051462] ath: EEPROM indicates we should expect a country code
[ 9067.051465] ath: doing EEPROM country->regdmn map search
[ 9067.051467] ath: country maps to regdmn code: 0x52
[ 9067.051470] ath: Country alpha2 being used: CN
[ 9067.051472] ath: Regpair used: 0x52
[ 9067.075068] systemd-udevd[5505]: renamed network interface wlan1 to wlan2
[ 9067.377921] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 9067.378515] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 9069.487601] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 9077.370008] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 9124.103915] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 9167.813489] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 9221.338290] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 9225.895658] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 9232.731433] ath: phy7: RX failed to go idle in 10 ms RXSM=0xb832b0a4
[ 9232.937971] ath: phy7: RX failed to go idle in 10 ms RXSM=0xb832b0a4
[ 9233.091706] usb 2-1.1.4: ath9k_htc: USB layer deinitialized
[ 9238.401678] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 9238.401917] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 9238.496527] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9875.467630] usb 2-1.1.4: ath9k_htc: Firmware htc_9271.fw requested
[ 9875.759741] usb 2-1.1.4: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[ 9875.997356] ath9k_htc 2-1.1.4:1.0: ath9k_htc: HTC initialized with 33 credits
[ 9876.265893] ath9k_htc 2-1.1.4:1.0: ath9k_htc: FW Version: 1.3
[ 9876.265899] ath: EEPROM regdomain: 0x809c
[ 9876.265902] ath: EEPROM indicates we should expect a country code
[ 9876.265905] ath: doing EEPROM country->regdmn map search
[ 9876.265907] ath: country maps to regdmn code: 0x52
[ 9876.265910] ath: Country alpha2 being used: CN
[ 9876.265912] ath: Regpair used: 0x52
[ 9876.289684] systemd-udevd[7294]: renamed network interface wlan1 to wlan2
[ 9876.594593] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 9876.595227] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 9878.684175] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 9887.200681] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 9909.444125] ath: phy8: RX failed to go idle in 10 ms RXSM=0xb832b0a4
[ 9909.596912] usb 2-1.1.4: ath9k_htc: USB layer deinitialized
[ 9921.612659] ieee80211 phy9: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[ 9921.644011] ieee80211 phy9: rt2x00_set_rf: Info - RF chipset 0005 detected
[ 9921.693815] systemd-udevd[7348]: renamed network interface wlan1 to wlan3
[ 9921.695675] ieee80211 phy9: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[ 9921.695714] ieee80211 phy9: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[ 9922.017241] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 9922.017977] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 9946.443316] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 9947.545117] wlan3: authenticate with <*WIRELESS NETWORK INFO REMOVED*>
[ 9947.611840] ieee80211 phy9: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[ 9947.611847] ieee80211 phy9: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[ 9947.657588] wlan3: direct probe to <*WIRELESS NETWORK INFO REMOVED*> (try 1/3)
[ 9947.859963] wlan3: send auth to <*WIRELESS NETWORK INFO REMOVED*> (try 2/3)
[ 9947.861946] wlan3: authenticated
[ 9952.658888] wlan3: deauthenticating from <*WIRELESS NETWORK INFO REMOVED*> by local choice (reason=3)
[ 9952.659260] wlan3: authenticate with <*WIRELESS NETWORK INFO REMOVED*>
[ 9952.663289] wlan3: send auth to <*WIRELESS NETWORK INFO REMOVED*> (try 1/3)
[ 9952.665352] wlan3: authenticated
[ 9957.668849] wlan3: deauthenticating from <*WIRELESS NETWORK INFO REMOVED*> by local choice (reason=3)
[ 9959.230052] wlan3: authenticate with <*WIRELESS NETWORK INFO REMOVED*>
[ 9959.250572] wlan3: send auth to <*WIRELESS NETWORK INFO REMOVED*> (try 1/3)
[ 9959.252440] wlan3: authenticated
[ 9964.253441] wlan3: deauthenticating from <*WIRELESS NETWORK INFO REMOVED*> by local choice (reason=3)
[ 9966.306207] wlan3: authenticate with <*WIRELESS NETWORK INFO REMOVED*>
[ 9966.327249] wlan3: send auth to <*WIRELESS NETWORK INFO REMOVED*> (try 1/3)
[ 9966.328935] wlan3: authenticated
[ 9971.330084] wlan3: deauthenticating from <*WIRELESS NETWORK INFO REMOVED*> by local choice (reason=3)
[ 9972.349589] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 9973.018312] ieee80211 phy9: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[ 9973.018357] ieee80211 phy9: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[ 9973.018370] ieee80211 phy9: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[ 9975.370713] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 9975.443764] wlan3: authenticate with <*WIRELESS NETWORK INFO REMOVED*>
[ 9975.446926] wlan3: send auth to <*WIRELESS NETWORK INFO REMOVED*> (try 1/3)
[ 9975.448779] wlan3: authenticated
[ 9977.278132] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[ 9978.434611] ieee80211 phy9: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[ 9978.434617] ieee80211 phy9: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0

    ======== Done ========

```

---

### Post by praseodym on 2014-07-31
```
[ 9971.330084] wlan3: deauthenticating from <*WIRELESS NETWORK INFO REMOVED*> by local choice (reason=3)
```
Obviously, a network-manager issue.. Deactivate IPv6 there. Did you chose the wlan interface in your profile? If yes, change it to wlan3. If no, chose wlan3

---

### Post by chris271 on 2014-07-31
What do you mean did i change wlan interface?

How to deactivate IPv6?

Still pretty confused

---

### Post by praseodym on 2014-07-31
Open the network-manager applet->Edit connections->Wifi ->Edit->IPv6 settings, set it to "Ignore", reconnect. You should be able to choose wlan3 in the profile there.

---

### Post by chris271 on 2014-07-31
I done all of that, set ignore on ipv6 and chose wlan3, it still drops me out instantly when trying to connect.

---

### Post by praseodym on 2014-08-01
Try to deactivate the hardware encryption of the driver:

On-the fly:
```

sudo modprobe -rfv rt2800usb
sudo modprobe -v rt2800usb nohwcrypt=1
```
If it works make it permanent:
```

echo "options rt2800usb nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800usb.conf
```

---

### Post by chris271 on 2014-08-01
Nope :'( this isnt a fix either, i dont understand why it works perfectly on kali but not ubuntu.

How would i go about updating the driver?

---

### Post by praseodym on 2014-08-01
Can you show on Kali:
```

lsmod
uname -a
modinfo rt2800usb | egrep 'versi|filen'
```
and on Ubuntu

```

uname -a
modinfo rt2800usb | egrep 'versi|filen'
```

---

### Post by chris271 on 2014-08-01
Ubuntu:
```
user@user-Latitude-E4310:~$ lsmod
Module                  Size  Used by
rt2800usb              27034  0
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              12707  1 rt2800lib
ath9k_htc              95963  0
ath9k_common           13551  1 ath9k_htc
ath9k_hw              453856  2 ath9k_common,ath9k_htc
ath                    28698  3 ath9k_common,ath9k_htc,ath9k_hw
pci_stub               12622  1
bnep                   19624  2
rfcomm                 69160  0
arc4                   12608  4
iwldvm                232285  0
mac80211              626557  5 rt2x00lib,rt2x00usb,rt2800lib,iwldvm,ath9k_htc
dell_wmi               12761  0
sparse_keymap          13948  1 dell_wmi
snd_hda_codec_hdmi     46207  1
snd_hda_codec_idt      54645  1
dell_laptop            18168  0
dcdbas                 14928  1 dell_laptop
snd_hda_intel          52355  3
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
intel_powerclamp       14705  0
snd_seq_midi           13324  0
snd_seq_midi_event     14899  1 snd_seq_midi
coretemp               13435  0
btusb                  32412  0
bluetooth             395423  11 bnep,btusb,rfcomm
snd_rawmidi            30144  1 snd_seq_midi
kvm_intel             143060  0
kvm                   451511  1 kvm_intel
joydev                 17381  0
serio_raw              13462  0
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
intel_ips              18664  0
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
lpc_ich                21080  0
iwlwifi               169932  1 iwldvm
cfg80211              484040  6 ath,iwlwifi,mac80211,rt2x00lib,iwldvm,ath9k_htc
snd                    69238  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
mei_me                 18627  0
mei                    82276  1 mei_me
mac_hid                13205  0
parport_pc             32701  0
ppdev                  17671  0
lp                     17759  0
parport                42348  3 lp,ppdev,parport_pc
dm_crypt               23177  1
crct10dif_pclmul       14289  0
crc32_pclmul           13113  0
ghash_clmulni_intel    13216  0
i915                  783703  8
aesni_intel            55624  2
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  4 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse               102222  0
i2c_algo_bit           13413  1 i915
ahci                   25819  2
sdhci_pci              23172  0
drm_kms_helper         53081  1 i915
e1000e                254433  0
libahci                32168  1 ahci
sdhci                  43015  1 sdhci_pci
drm                   303102  4 i915,drm_kms_helper
ptp                    18933  1 e1000e
pps_core               19382  1 ptp
wmi                    19177  1 dell_wmi
video                  19476  1 i915
user@user-Latitude-E4310:~$ uname -a
Linux user-Latitude-E4310 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
user@user-Latitude-E4310:~$ modinfo rt2800usb | egrep 'versi|filen'
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
version:        2.3.0
srcversion:     D6F814DAF78F2BEA3DA12CB
vermagic:       3.13.0-30-generic SMP mod_unload modversions


```

Kali:
```
root@kali:~# uname -a
Linux kali 3.14-kali1-686-pae #1 SMP Debian 3.14.5-1kali1 (2014-06-07) i686 GNU/Linux
root@kali:~# modinfo rt2800usb | egrep 'versi|filen'
filename:       /lib/modules/3.14-kali1-686-pae/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
version:        2.3.0
srcversion:     8D709655B6AD993F0D5ACC4
vermagic:       3.14-kali1-686-pae SMP mod_unload modversions 686 
root@kali:~# 


```

---

### Post by praseodym on 2014-08-02
Obviously, another driver version in Kali. You can try the latest stable mainline kernel 3.15:
```

sudo apt-get install build-essential dkms
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/linux-headers-3.15.0-031500-generic_3.15.0-031500.201406131105_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/linux-headers-3.15.0-031500_3.15.0-031500.201406131105_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/linux-image-3.15.0-031500-generic_3.15.0-031500.201406131105_amd64.deb
sudo dpkg -i linux-*.deb
```
Reboot and check:

```
uname -a
modinfo rt2800usb | egrep 'versi|filen'
dmesg | grep rt2
iwconfig
rfkill list
lsmod
```

---

### Post by chris271 on 2014-08-02
Anyway to update it without a connection?

---

### Post by praseodym on 2014-08-02
Download the files from that links ([http://whatsoever](http://whatsoever)...)

---

### Post by chris271 on 2014-08-02
```
user@user-Latitude-E4310:~$ uname -a
Linux user-Latitude-E4310 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
user@user-Latitude-E4310:~$ 
user@user-Latitude-E4310:~$ modinfo rt2800usb | egrep 'versi|filen'
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
version:        2.3.0
srcversion:     D6F814DAF78F2BEA3DA12CB
vermagic:       3.13.0-30-generic SMP mod_unload modversions 
user@user-Latitude-E4310:~$ 
user@user-Latitude-E4310:~$ dmesg | grep rt2
user@user-Latitude-E4310:~$ 
user@user-Latitude-E4310:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"----------"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: *Removed mac*   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:3   Missed beacon:0

user@user-Latitude-E4310:~$ 
user@user-Latitude-E4310:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
user@user-Latitude-E4310:~$ 
user@user-Latitude-E4310:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
pci_stub               12622  1 
bnep                   19624  2 
rfcomm                 69160  0 
arc4                   12608  2 
iwldvm                232285  0 
mac80211              626557  1 iwldvm
btusb                  32412  0 
bluetooth             395423  11 bnep,btusb,rfcomm
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
snd_hda_codec_hdmi     46207  1 
dcdbas                 14928  1 dell_laptop
snd_hda_codec_idt      54645  1 
snd_hda_intel          52355  3 
intel_powerclamp       14705  0 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
coretemp               13435  0 
snd_hwdep              13602  1 snd_hda_codec
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
joydev                 17381  0 
serio_raw              13462  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
intel_ips              18664  0 
iwlwifi               169932  1 iwldvm
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
lpc_ich                21080  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
snd                    69238  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                 18627  0 
soundcore              12680  1 snd
mei                    82276  1 mei_me
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
dm_crypt               23177  1 
usb_storage            62209  1 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  2 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
i915                  783703  8 
ablk_helper            13597  1 aesni_intel
cryptd                 20359  4 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse               102222  0 
i2c_algo_bit           13413  1 i915
ahci                   25819  2 
drm_kms_helper         53081  1 i915
e1000e                254433  0 
sdhci_pci              23172  0 
libahci                32168  1 ahci
sdhci                  43015  1 sdhci_pci
drm                   303102  4 i915,drm_kms_helper
ptp                    18933  1 e1000e
pps_core               19382  1 ptp
wmi                    19177  1 dell_wmi
video                  19476  1 i915
user@user-Latitude-E4310:~$
```

---

### Post by chris271 on 2014-08-02
Still not working updated and post results, this i really annoying. I dont want to change my mane OS to kali :(


Thanks for all your help so far praseodym, its appreciated

---

### Post by praseodym on 2014-08-02
Download these files and save them in "Downloads":

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/linux-headers-3.15.0-031500-generic_3.15.0-031500.201406131105_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/linux-headers-3.15.0-031500-generic_3.15.0-031500.201406131105_amd64.deb)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/linux-headers-3.15.0-031500_3.15.0-031500.201406131105_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/linux-headers-3.15.0-031500_3.15.0-031500.201406131105_all.deb)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/linux-image-3.15.0-031500-generic_3.15.0-031500.201406131105_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/linux-image-3.15.0-031500-generic_3.15.0-031500.201406131105_amd64.deb)

Installation:

```
sudo dpkg -i ~/Downloads/linux-*.deb
```
Reboot

---

### Post by chris271 on 2014-08-02
Done but there's no difference still

---

### Post by praseodym on 2014-08-02
```
modinfo rt2800usb | egrep 'versi|filen'
```
again

---

### Post by chris271 on 2014-08-02
```
user@user-Latitude-E4310:~$ modinfo rt2800usb | egrep 'versi|filen'
filename:       /lib/modules/3.15.0-031500-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
version:        2.3.0
srcversion:     7E5A910B4F8BAC527A57F26
vermagic:       3.15.0-031500-generic SMP mod_unload modversions 
user@user-Latitude-E4310:~$ 


```

---

### Post by praseodym on 2014-08-03
Thats another driver version, strange.

Reboot, hold the SHIFT-button and chose "previous ubuntu versions". Boot into kernel 3.13 and uninstall 3.15:
```

sudo apt-get remove --purge linux-image-3.15* linux-headers-3.15*
``` 
Install kernel 3.14 instead and reboot:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.15-utopic/linux-headers-3.14.15-031415-generic_3.14.15-031415.201407311853_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.15-utopic/linux-headers-3.14.15-031415-generic_3.14.15-031415.201407311853_amd64.deb)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.15-utopic/linux-headers-3.14.15-031415_3.14.15-031415.201407311853_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.15-utopic/linux-headers-3.14.15-031415_3.14.15-031415.201407311853_all.deb)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.15-utopic/linux-image-3.14.15-031415-generic_3.14.15-031415.201407311853_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.15-utopic/linux-image-3.14.15-031415-generic_3.14.15-031415.201407311853_amd64.deb)

---

### Post by chris271 on 2014-08-03
Its started connecting, it will take a few attempts and still feels unstable but it connects! Not sure whether to download older kernel like you said, what do you think?

Dont want to leave it then further down the line i get buggered..

---

### Post by praseodym on 2014-08-04
You can try kernel 3.14 in parallel, if it works better.

---

### Post by chris271 on 2014-08-06
I forgot to say thank you, the 3.15 kernel upgrade definitely done the job. Thanks so much for the help man you stopped me reverting to windows!

---

