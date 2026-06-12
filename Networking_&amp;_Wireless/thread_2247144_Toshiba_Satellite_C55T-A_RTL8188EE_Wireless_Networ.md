---
title: "Toshiba Satellite C55T-A RTL8188EE Wireless Network Adapter hardware switch"
date: 2014-10-05
forum: Networking &amp; Wireless
---

### Post by torinn232 on 2014-10-05
In a nutshell... 
Computer: Toshiba Satellite C55T-A
OS: Ubuntu 14.04 LTS 64bit
Problem: WI-Fi recognized, however is disabled by the hardware switch. (wifi toggle is "Fn+F12")
WI-FI Adapter: 01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)

> $ rfkill list all
0: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes



> $ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation ValleyView SSA-CUnit [8086:0f00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation ValleyView Gen7 [8086:0f31] (rev 0c)
00:13.0 SATA controller [0106]: Intel Corporation ValleyView 6-Port SATA AHCI Controller [8086:0f23] (rev 0c)
00:14.0 USB controller [0c03]: Intel Corporation ValleyView USB xHCI Host Controller [8086:0f35] (rev 0c)
00:1a.0 Encryption controller [1080]: Intel Corporation ValleyView SEC [8086:0f18] (rev 0c)
00:1b.0 Audio device [0403]: Intel Corporation ValleyView High Definition Audio Controller [8086:0f04] (rev 0c)
00:1c.0 PCI bridge [0604]: Intel Corporation ValleyView PCI Express Root Port [8086:0f48] (rev 0c)
00:1c.1 PCI bridge [0604]: Intel Corporation ValleyView PCI Express Root Port [8086:0f4a] (rev 0c)
00:1c.2 PCI bridge [0604]: Intel Corporation ValleyView PCI Express Root Port [8086:0f4c] (rev 0c)
00:1c.3 PCI bridge [0604]: Intel Corporation ValleyView PCI Express Root Port [8086:0f4e] (rev 0c)
00:1f.0 ISA bridge [0601]: Intel Corporation ValleyView Power Control Unit [8086:0f1c] (rev 0c)
00:1f.3 SMBus [0c05]: Intel Corporation ValleyView SMBus Controller [8086:0f12] (rev 0c)
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)

> $ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr=2347 B   Fragment thr: off
          Power Management: off



Links that I have tried with no luck:

[http://askubuntu.com/questions/452315/problems-with-realtek-rtl8188ee-on-14-04](http://askubuntu.com/questions/452315/problems-with-realtek-rtl8188ee-on-14-04)

[http://ubuntuforums.org/showthread.php?t=2218962](http://ubuntuforums.org/showthread.php?t=2218962)

Waking the computer from suspend mode doesn't help either.

Any and all help welcome...bear in mind I'm noobISH ^^

Thanx everyone! =)

---

### Post by varunendra on 2014-10-06
Please follow the instructions in this post to download and run 'wireless_script' (alternative version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by torinn232 on 2014-10-06
My apologies! Thank you for introducing me to the "code" tag. 

And my output

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Lizzie-Satellite-C55t-A 3.14.0-031400-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Celeron(R) CPU  N2820  @ 2.13GHz
Memory : 3836 MB
Uptime : 12:52:40 up 39 min,  2 users,  load average: 0.91, 0.61, 0.49


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0191]
    Kernel driver in use: rtl8188ee
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 10f1:1a52 Importek 
Bus 001 Device 004: ID 04f3:0142 Elan Microelectronics Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            yes


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8188ee              96048  0 
rtl_pci                27261  1 rtl8188ee
rtlwifi                64281  2 rtl_pci,rtl8188ee
mac80211              676864  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              531467  2 mac80211,rtlwifi
wmi                    19363  1 toshiba_acpi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8188ee     (5): debug=0 | fwlps=Y | ips=Y | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
============================o=============o===========o=============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | r8169     | connected   | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.107
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             75.75.75.75
    DNS:             75.75.76.76
----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | rtl8188ee | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


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

nameserver 127.0.1.1
search hsd1.ma.comcast.net


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.945/0.967/0.990/0.038 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.040/0.054/0.069/0.016 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8188ee]
filename:       /lib/modules/3.14.0-031400-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
srcversion:     9294C4318714C04CF9E0321
depends:        rtlwifi,rtl_pci,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.14.0-031400-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     B07D1002FC86501951333AE
depends:        mac80211,rtlwifi

[rtlwifi]
filename:       /lib/modules/3.14.0-031400-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     BACE38460F5E5294FE27C59
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.14.0-031400-generic/kernel/net/mac80211/mac80211.ko
srcversion:     AF71C11DB75127119B9AB7B
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.14.0-031400-generic/kernel/net/wireless/cfg80211.ko
srcversion:     0739D3437930A94073358B8
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.14.0-031400-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rtl8187)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# USB device 0x:0x (rtl8187)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"


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
modprobe.conf     : options rtl8192ce ips=1
                    options rtl8192ce fwlps=0
                    options rtl8192ce swenc=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.14.0-031400-generic root=UUID=fee9e490-4376-49d2-81b6-ab07e50154b8 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.878799] audit: initializing netlink subsys (disabled)
[    1.135748] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   10.478483] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.580597] wmi: Mapper loaded
[   12.377591] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   12.418855] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   12.626508] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.626914] rtlwifi: wireless switch is on
[   18.348033] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  435.759746] rtlwifi: wireless switch is on
[  438.727603] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  445.426244] rtlwifi: wireless switch is on
[  448.462719] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========

```

---

### Post by torinn232 on 2014-10-06
Side note!

I connected my trendnet usb wifi adapter I am confronted with the same issue, "WI-FI disabled by hardware switch." 
To be clear this adapter has no such switch that I can find.
numbers( TA-2007/680    TEW-424UB H/W:3.1R )

My updated lsusb output:
p.s. I underlined the wifi adaper.
```
$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 10f1:1a52 Importek 
Bus 001 Device 004: ID 04f3:0142 Elan Microelectronics Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
**_Bus 001 Device 006: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter_**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by varunendra on 2014-10-07
> **torinn232 said:**
> ```
module parameters ~~~~~~~~~~~~~~~~~~
....
rtl8188ee     (5): debug=0 | **[COLOR="#FF0000"]fwlps=Y[/COLOR]** | ips=Y | swenc=N | swlps=N
....
modprobe.conf     : options rtl8192ce ips=1
                    options rtl8192ce fwlps=0
                    options rtl8192ce swenc=1

```
Even though you seem to have set the parameter "fwlps" to "0", it is loaded with its default value "Y" which means "1". Did you run the script immediately after creating the conf file?

By the way, it is recommended to set all the power saving features to "N", that is "0". Also, I personally prefer to pass the values directly as "Y" or "N" when the modinfo says it has to be a 'bool' value. As such, please delete the above conf file you have created, and create a new one with recommended parameters with following commands -
```
sudo rm /etc/modprobe.d/modprobe.conf
echo "options rtl8192ce fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```

Did it come with Windows 8 preinstalled? Are you still dualbooting with it? If so, make sure to disable "fastboot" and "secure boot" from within windows8/BIOS. If you are not dualbooting, resetting the BIOS may also be an option worth trying.

And have you checked that there are no physical switches to toggle it on/off?

---

### Post by torinn232 on 2014-10-07
The OS is dedicated ubuntu 14.04. The computer came with Win8, and i searched all over, and a physical HW switch isn't to be found, the bios doesn't have an option to control the wireless card. I will run the commands soon and report back, also as far as I know, the bios is set to default settings. Should the cammands not work, I will reset my bios and retrace my steps.

Thank for your help thus far!

---

### Post by torinn232 on 2014-10-07
just tried the commands with no luck =/ 

I still get the "WI-FI disabled by hardware switch" mumbo, and in the wifi settings the airplane mode is on and can't be turned off, also some "Fn+F" combos don't work and or function correctly. This my affect my "hardware switch."

Tis being tricky ^^

---

### Post by varunendra on 2014-10-07
Did you try BIOS reset? Did it have no effect? Please post the outputs of -
```
lsmod
egrep -i 'switch|rfkill|network|wlan|rtl81' /var/log/syslog
```

---

### Post by torinn232 on 2014-10-10
Sorry I took a bit.

The output of  
```
egrep -i 'switch|rfkill|network|wlan|rtl81' /var/log/syslog
```
can be found here --> [https://www.dropbox.com/s/dm0sd516iq0uwlt/egrepout-toshiba_satellite_C55T-A.txt?dl=0](https://www.dropbox.com/s/dm0sd516iq0uwlt/egrepout-toshiba_satellite_C55T-A.txt?dl=0)
I had trouble submitting it to the forum directly.

lsmod output

```
Module                  Size  Used by
usb_storage            66714  1 
snd_hda_codec_hdmi     47124  1 
snd_hda_codec_realtek    66644  1 
snd_hda_codec_generic    69424  1 snd_hda_codec_realtek
intel_rapl             19228  0 
coretemp               17768  0 
arc4                   12573  2 
kvm_intel             148674  0 
kvm                   471679  1 kvm_intel
uvcvideo               82247  0 
crct10dif_pclmul       14250  0 
crc32_pclmul           13160  0 
ghash_clmulni_intel    13259  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
cryptd                 20531  1 ghash_clmulni_intel
videobuf2_core         45465  1 uvcvideo
snd_hda_intel          57222  5 
rts5139               318332  0 
snd_hda_codec         142651  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
videodev              149340  2 uvcvideo,videobuf2_core
rtl8188ee              96048  0 
snd_hwdep              13613  1 snd_hda_codec
hid_multitouch         17645  0 
rtl_pci                27261  1 rtl8188ee
rtlwifi                64281  2 rtl_pci,rtl8188ee
mac80211              676864  3 rtl_pci,rtlwifi,rtl8188ee
i915                  826549  3 
snd_pcm               108860  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
microcode              24391  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              531467  2 mac80211,rtlwifi
drm_kms_helper         53224  1 i915
drm                   308197  4 i915,drm_kms_helper
snd_rawmidi            30465  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi_event,snd_seq_midi
joydev                 17575  0 
serio_raw              13462  0 
toshiba_acpi           22950  0 
bnep                   19884  2 
sparse_keymap          13890  1 toshiba_acpi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              30038  2 snd_pcm,snd_seq
i2c_algo_bit           13564  1 i915
toshiba_bluetooth      12852  0 
snd                    73979  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
wmi                    19363  1 toshiba_acpi
intel_smartconnect     12619  0 
dw_dmac                12814  0 
video                  19914  1 i915
dw_dmac_core           28517  1 dw_dmac
soundcore              12680  1 snd
i2c_hid                19022  0 
8250_dw                13395  0 
i2c_designware_platform    13006  0 
i2c_designware_core    14990  1 i2c_designware_platform
mac_hid                13253  0 
spi_pxa2xx_platform    23279  0 
rfcomm                 74734  0 
bluetooth             426845  10 bnep,rfcomm
6lowpan_iphc           18968  1 bluetooth
parport_pc             32866  0 
ppdev                  17711  0 
lp                     17799  0 
nls_iso8859_1          12713  2 
parport                42481  3 lp,ppdev,parport_pc
usbhid                 53067  0 
hid                   106254  3 i2c_hid,hid_multitouch,usbhid
r8169                  73299  0 
psmouse               108839  0 
mii                    13981  1 r8169
sdhci_acpi             13420  0 
sdhci                  43409  1 sdhci_acpi
ahci                   30066  3 
libahci                32191  1 ahci
```

---

