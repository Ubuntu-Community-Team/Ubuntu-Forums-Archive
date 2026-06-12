---
title: "Wireless disconnection after 1minute, strange error."
date: 2014-03-10
forum: Networking &amp; Wireless
---

### Post by nick85x on 2014-03-10
Hello everyone,

I have two modem-routher, they are working very well with my old netbook, but when I installed linux in my new netbook, I don't know why, but in only one of the two modem-routher, after a minute my new netbook disconnects and does not see the wifi line, until I turn it off or suspend him.
These are excerpts from the response of the command dmesg 

```
[15124.975471] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[15109.912727] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15110.965959] wlan0: authenticate with --:--:--:--:--:--
[15111.132898] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[15111.292912] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15111.301056] wlan0: send auth to --:--:--:--:--:-- (try 1/3)
[15112.321167] wlan0: send auth to --:--:--:--:--:-- (try 2/3)
[15113.321314] wlan0: send auth to --:--:--:--:--:-- (try 3/3)
[15114.321535] wlan0: authentication with --:--:--:--:--:-- timed out
[15114.497477] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[15114.657536] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15114.917619] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[15115.077667] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15123.315066] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[15123.475137] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15124.754573] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15124.975471] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[15123.475137] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
```

```
[15528.462526] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[15528.462526] Please file bug report to http://rt2x00.serialmonkey.com
```

```
[  636.290536] alx 0000:03:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [--:--:--:--:--:--]
[  636.524141] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  636.526266] alx 0000:03:00.0: irq 46 for MSI/MSI-X
[  636.526379] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  636.527437] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  636.663690]  sda: sda1
[  638.695613] wlan0: authenticate with --:--:--:--:--:--
[  638.703435] wlan0: send auth to --:--:--:--:--:-- (try 1/3)
[  638.704846] wlan0: authenticated
[  638.705134] rt2800pci 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  638.705142] rt2800pci 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  638.705146] rt2800pci 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  638.707141] wlan0: associate with --:--:--:--:--:-- (try 1/3)
[  638.709220] wlan0: RX AssocResp from --:--:--:--:--:-- (capab=0x411 status=0 aid=1)
[  638.709687] wlan0: associated
[  638.709736] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  662.803512] mei_me 0000:00:16.0: reset: init clients timeout hbm_state = 1.
[  662.803530] mei_me 0000:00:16.0: unexpected reset: dev_state = RESETTING
```

I did some research on the internet, but unfortunately to no avail.
Somebody know some solution to write on the terminal or some pacage to install, to solve this problem?
Thank you
Sincerelly

---

### Post by varunendra on 2014-03-10
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by nick85x on 2014-03-10
Please No Scripts. Just commands. 
Thanks

---

### Post by varunendra on 2014-03-10
```
lsb_release -d
uname -mr
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list all
iw reg get
nm-tool
sudo iwlist scan
egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules
dmesg | egrep 'wlan|rt2'
```
..should be sufficient. :p

Sorry, I've got too used to seeing the script report, the above are just those commands whose output may shed some light on the frequent disconnection issue.

By the way, some of the above outputs will show the MAC addresses of your router/access-points and local NICs. You may wish to obscure them, since you seem to be seriously concerned about security (understandable). The script does that automatically, but anyway..

---

### Post by nick85x on 2014-03-10
Thank you very much,
This is it:

```
lsb_release -d
uname -mr
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list all
iw reg get
nm-tool
sudo iwlist scan
egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules
dmesg | egrep 'wlan|rt2'


lsb_release -d
Description:    Linux Mint 16 Petra

uname -mr
3.11.0-12-generic x86_64


lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Foxconn International, Inc. Device [105b:e055]
    Kernel driver in use: rt2800pci
--
03:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8172 Fast Ethernet [1969:10a0] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: alx


lsmod
Module                  Size  Used by
alx                    32255  0 
mdio                   13807  1 alx
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  0 
bnep                   19564  2 
bluetooth             371874  10 bnep,rfcomm
binfmt_misc            17468  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
cryptd                 20329  1 ghash_clmulni_intel
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
joydev                 17377  0 
dm_multipath           22843  0 
scsi_dh                14882  1 dm_multipath
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     41276  1 
snd_hda_codec_conexant    56945  1 
microcode              23518  0 
snd_hda_intel          48171  3 
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
psmouse                97626  0 
arc4                   12608  2 
serio_raw              13413  0 
rt2800pci              18690  0 
rt2800lib              79963  1 rt2800pci
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  1 rt2800pci
rt2x00lib              55238  4 rt2x00pci,rt2800lib,rt2800pci,rt2x00mmio
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
mac80211              596969  3 rt2x00lib,rt2x00pci,rt2800lib
lpc_ich                21080  0 
cfg80211              479757  2 mac80211,rt2x00lib
snd                    69141  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
soundcore              12680  1 snd
hid_multitouch         17407  0 
mei_me                 18421  0 
mei                    77692  1 mei_me
mac_hid                13205  0 
ext2                   72832  1 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
dm_mirror              22056  0 
dm_region_hash         20784  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101512  3 hid_multitouch,hid_generic,usbhid
usb_storage            62062  0 
wmi                    19070  1 asus_wmi
i915                  655752  2 
i2c_algo_bit           13413  1 i915
drm_kms_helper         52651  1 i915
video                  19318  2 i915,asus_wmi
drm                   296739  3 i915,drm_kms_helper
ahci                   25819  3 
libahci                31898  1 ahci


iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on


rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


iw reg get
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        --:--:--:--:--:--

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        --:--:--:--:--:--

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


iwlist scan
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     No scan results


egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules

# PCI device 0x1969:0x10a0 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="--:--:--:--:--:--", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:0x3290 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="--:--:--:--:--:--", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


dmesg | egrep 'wlan|rt2'
[   11.737019] rt2800pci 0000:02:00.0: irq 44 for MSI/MSI-X
[   11.737114] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0013 detected
[   11.745717] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   17.261871] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[   17.297408] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[   17.342505] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.342856] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.558348] wlan0: authenticate with --:--:--:--:--:--
[   19.573804] wlan0: send auth to --:--:--:--:--:-- (try 1/3)
[   19.575670] wlan0: authenticated
[   19.577610] wlan0: associate with --:--:--:--:--:-- (try 1/3)
[   19.581001] wlan0: RX AssocResp from --:--:--:--:--:-- (capab=0x411 status=0 aid=1)
[   19.581123] wlan0: associated
[   19.581163] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   22.984564] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   23.144504] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   23.516388] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   23.676276] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   23.936255] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   24.096199] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   24.256119] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   24.416102] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   25.468181] wlan0: authenticate with --:--:--:--:--:--
[   25.635722] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   25.795669] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   25.803785] wlan0: send auth to --:--:--:--:--:-- (try 1/3)
[   26.815672] wlan0: send auth to --:--:--:--:--:-- (try 2/3)
[   27.815031] wlan0: send auth to --:--:--:--:--:-- (try 3/3)
[   28.814708] wlan0: authentication with d8:fe:e3:e0:45:ea timed out
[   28.990617] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   29.150582] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   29.410472] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   29.570439] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   29.730407] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   29.890361] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   31.109916] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   31.269922] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   36.104353] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   36.264295] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   36.424228] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   36.584165] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   37.803799] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   37.963751] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   42.798199] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   42.958141] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   43.118100] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   43.278065] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   44.497685] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   44.657620] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   47.333628] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   47.528690] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   47.688715] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   47.848652] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   48.008596] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   49.228217] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   49.388147] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   51.163597] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   51.323551] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   51.483483] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   51.643444] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   52.863062] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   53.023011] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   74.088312] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   74.248260] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   83.501262] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   85.672752] wlan0: authenticate with --:--:--:--:--:--
[   85.688442] wlan0: send auth to --:--:--:--:--:-- (try 1/3)
[   85.690249] wlan0: authenticated
[   85.692318] wlan0: associate with --:--:--:--:--:-- (try 1/3)
[   85.695684] wlan0: RX AssocResp from --:--:--:--:--:-- (capab=0x411 status=0 aid=1)
[   85.695806] wlan0: associated
[   85.695846] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  144.210980] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  144.975120] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  145.515220] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  145.675250] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  145.935364] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  146.095382] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  146.255417] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  146.415440] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  147.635617] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  147.795665] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  152.632576] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  152.792604] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  152.952617] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  153.112627] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  154.332884] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  154.492923] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  159.329799] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  159.489826] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  159.649861] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  159.809887] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  161.030068] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  161.190138] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  161.303496] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  161.494156] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  161.654207] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  161.814231] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  161.974246] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  163.194499] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  163.354529] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  165.166807] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  165.326829] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  165.486862] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  165.646887] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  166.867164] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  167.027221] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  188.170998] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  188.331038] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  188.491065] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  188.651097] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  189.871354] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  190.031390] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  221.181055] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  221.341095] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  221.501126] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  221.661143] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  222.881372] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  223.041400] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  264.188871] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  264.348920] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  264.508955] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  264.668976] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  265.889204] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  266.049229] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  317.198502] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  317.358573] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  317.518611] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  317.678633] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  318.898860] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  319.058896] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  380.177670] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  380.337602] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  380.497540] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  380.657489] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  380.693518] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  381.877113] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  382.037081] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  443.161640] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  443.321581] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  443.481538] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  443.641480] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  443.677490] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  444.861100] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  445.021041] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  506.137609] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  506.297554] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  506.457510] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  506.617454] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  506.653461] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  507.837068] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  507.997009] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  569.121573] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  569.281528] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  569.441482] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  569.601419] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  569.637429] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  570.821036] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  570.980982] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  632.097551] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  632.257493] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  632.417452] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  632.577405] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  632.613394] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  633.797009] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  633.956961] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  695.081513] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  695.241473] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  695.401413] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  695.561370] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  695.597370] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  696.780970] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  696.940919] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  758.057492] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  758.217432] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  758.377379] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  758.537331] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  758.573344] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  759.756951] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  759.916894] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  821.041464] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  821.201404] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  821.361361] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  821.521287] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  821.557306] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  822.740912] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  822.900862] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  881.450244] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  881.610202] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  881.770121] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  881.930093] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  881.966097] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  883.149711] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  883.309651] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  884.017434] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  884.177377] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  884.337336] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  884.497274] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  884.533263] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  885.716896] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  885.876836] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  947.001404] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  947.161355] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  947.321287] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  947.481242] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  947.517210] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  948.700859] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  948.860788] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1009.977375] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1010.137326] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1010.297270] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1010.457224] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1010.493227] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1011.676835] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1011.836776] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1072.961345] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1073.121288] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1073.281223] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1073.441168] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1073.477194] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1074.660806] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1074.820749] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush


```

---

### Post by varunendra on 2014-03-10
Let's start from the trivial - please try -
```
sudo iwconfig wlan0 power off
```
If it accepts the command without errors, check -
```
iwconfig
```
Does the Power Management turn off? It may turn on again after sometime, so keep checking it to see if it happens. If it does, we may try extra steps to make sure it remains turned off.

However, if it does not accept the command, or if it doesn't help the stability, please try -
```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
It'll be a temporary change and we'll make it permanent only if it seems to help. If not, we may have to try a different driver. Post back how it goes and we'll proceed if needed.

---

### Post by nick85x on 2014-03-12
I apologize for the delay.
When I try the first your option, it doesn't work, but when I try your second:
```
sudo modprobe -rv rt2800pci 
sudo modprobe -v rt2800pci nohwcrypt=Y
```
it is reconnecting but only for 1 minute, and than stop.
Then I copied this:
```
[ 3668.141044] rt2800pci 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 3668.143237] wlan0: associate with --:--:--:--:--:-- (try 1/3)
[ 3668.145338] wlan0: RX AssocResp from --:--:--:--:--:-- (capab=0x411 status=0 aid=1)
[ 3668.145636] wlan0: associated
[ 3668.145673] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4233.310012] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4233.470078] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4233.838155] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4233.998184] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4234.258192] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4234.418250] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4234.578278] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4234.738303] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4235.791059] wlan0: authenticate with --:--:--:--:--:--
[ 4235.958487] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4236.118546] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4236.118709] wlan0: send auth to --:--:--:--:--:-- (try 1/3)
[ 4237.150760] wlan0: send auth to --:--:--:--:--:-- (try 2/3)
[ 4238.150934] wlan0: send auth to --:--:--:--:--:-- (try 3/3)
[ 4239.162968] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4239.330993] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4239.490978] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4239.750897] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4239.910848] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4240.070745] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4240.230747] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4241.450355] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4241.610298] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4246.444762] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4246.604710] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4246.764646] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4246.924610] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4248.144221] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4248.304173] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4249.582045] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4249.779657] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4249.939656] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4250.099571] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4250.259564] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4251.479163] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4251.639117] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4253.502473] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4253.662475] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4253.822426] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4253.982376] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4255.205981] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4255.365924] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4269.569420] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 4269.729329] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4276.211624] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4276.271309] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4276.271309] Please file bug report to http://rt2x00.serialmonkey.com
[ 4277.354889] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4277.354889] Please file bug report to http://rt2x00.serialmonkey.com
[ 4278.371174] wlan0: authenticate with --:--:--:--:--:--
[ 4278.378836] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4278.378855] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4278.378855] Please file bug report to http://rt2x00.serialmonkey.com
[ 4278.582556] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4278.786429] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4278.990423] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4278.998623] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4278.998623] Please file bug report to http://rt2x00.serialmonkey.com
[ 4279.082409] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4279.082409] Please file bug report to http://rt2x00.serialmonkey.com
[ 4280.106180] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4280.106180] Please file bug report to http://rt2x00.serialmonkey.com
[ 4280.142070] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4280.142070] Please file bug report to http://rt2x00.serialmonkey.com
[ 4281.158295] wlan0: authenticate with --:--:--:--:--:--
[ 4281.165945] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4281.165965] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4281.165965] Please file bug report to http://rt2x00.serialmonkey.com
[ 4281.369667] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4281.573593] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4281.777537] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4281.781739] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4281.781739] Please file bug report to http://rt2x00.serialmonkey.com
[ 4281.917501] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4281.917501] Please file bug report to http://rt2x00.serialmonkey.com
[ 4282.941243] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4282.941243] Please file bug report to http://rt2x00.serialmonkey.com
[ 4287.967579] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4287.967579] Please file bug report to http://rt2x00.serialmonkey.com
[ 4294.021648] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4294.021648] Please file bug report to http://rt2x00.serialmonkey.com
[ 4300.075736] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4300.075736] Please file bug report to http://rt2x00.serialmonkey.com
[ 4304.366360] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4304.366360] Please file bug report to http://rt2x00.serialmonkey.com
[ 4307.389394] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4307.389394] Please file bug report to http://rt2x00.serialmonkey.com
[ 4308.405732] wlan0: authenticate with --:--:--:--:--:--
[ 4308.413283] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4308.413303] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4308.413303] Please file bug report to http://rt2x00.serialmonkey.com
[ 4308.616999] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4308.820934] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4309.024867] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4309.029086] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4309.029086] Please file bug report to http://rt2x00.serialmonkey.com
[ 4309.164819] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4309.164819] Please file bug report to http://rt2x00.serialmonkey.com
[ 4310.188615] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4310.188615] Please file bug report to http://rt2x00.serialmonkey.com
[ 4315.218904] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4315.218904] Please file bug report to http://rt2x00.serialmonkey.com
[ 4321.272995] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4321.272995] Please file bug report to http://rt2x00.serialmonkey.com
[ 4327.323059] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4327.323059] Please file bug report to http://rt2x00.serialmonkey.com
[ 4332.357431] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4332.357431] Please file bug report to http://rt2x00.serialmonkey.com
[ 4335.372499] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4335.372499] Please file bug report to http://rt2x00.serialmonkey.com
[ 4336.388742] wlan0: authenticate with --:--:--:--:--:--
[ 4336.396401] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4336.396421] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4336.396421] Please file bug report to http://rt2x00.serialmonkey.com
[ 4336.600100] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4336.804035] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4337.007971] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4337.016147] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4337.016147] Please file bug report to http://rt2x00.serialmonkey.com
[ 4337.151938] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4337.151938] Please file bug report to http://rt2x00.serialmonkey.com
[ 4338.175709] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4338.175709] Please file bug report to http://rt2x00.serialmonkey.com
[ 4343.206008] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4343.206008] Please file bug report to http://rt2x00.serialmonkey.com
[ 4344.222227] wlan0: authenticate with --:--:--:--:--:--
[ 4344.229899] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4344.229918] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4344.229918] Please file bug report to http://rt2x00.serialmonkey.com
[ 4344.433563] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4344.637547] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4344.841431] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4344.845680] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4344.845680] Please file bug report to http://rt2x00.serialmonkey.com
[ 4344.981449] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4344.981449] Please file bug report to http://rt2x00.serialmonkey.com
[ 4345.997682] wlan0: authenticate with --:--:--:--:--:--
[ 4346.005222] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4346.005222] Please file bug report to http://rt2x00.serialmonkey.com
[ 4346.005346] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4346.209076] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4346.412985] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4346.616911] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4346.625113] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4346.625113] Please file bug report to http://rt2x00.serialmonkey.com
[ 4346.760887] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4346.760887] Please file bug report to http://rt2x00.serialmonkey.com
[ 4347.784650] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4347.784650] Please file bug report to http://rt2x00.serialmonkey.com
[ 4352.810965] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4352.810965] Please file bug report to http://rt2x00.serialmonkey.com
[ 4353.827194] wlan0: authenticate with --:--:--:--:--:--
[ 4353.834729] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4353.834729] Please file bug report to http://rt2x00.serialmonkey.com
[ 4353.834846] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4354.038546] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4354.242488] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4354.446404] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4354.450628] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4354.450628] Please file bug report to http://rt2x00.serialmonkey.com
[ 4354.586347] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4354.586347] Please file bug report to http://rt2x00.serialmonkey.com
[ 4355.602634] wlan0: authenticate with --:--:--:--:--:--
[ 4355.610166] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4355.610166] Please file bug report to http://rt2x00.serialmonkey.com
[ 4355.610281] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4355.813948] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4356.017925] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4356.221859] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4356.230060] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4356.230060] Please file bug report to http://rt2x00.serialmonkey.com
[ 4356.365822] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4356.365822] Please file bug report to http://rt2x00.serialmonkey.com
[ 4357.382043] wlan0: authenticate with --:--:--:--:--:--
[ 4357.389533] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4357.389533] Please file bug report to http://rt2x00.serialmonkey.com
[ 4357.389640] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4357.593386] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4357.797318] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4358.001292] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4358.009493] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4358.009493] Please file bug report to http://rt2x00.serialmonkey.com
[ 4358.145255] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4358.145255] Please file bug report to http://rt2x00.serialmonkey.com
[ 4359.169044] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4359.169044] Please file bug report to http://rt2x00.serialmonkey.com
[ 4360.348553] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4360.348553] Please file bug report to http://rt2x00.serialmonkey.com
[ 4361.372340] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4361.372340] Please file bug report to http://rt2x00.serialmonkey.com
[ 4363.343608] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4363.343608] Please file bug report to http://rt2x00.serialmonkey.com
[ 4364.367375] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4364.367375] Please file bug report to http://rt2x00.serialmonkey.com
[ 4386.340261] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4386.340261] Please file bug report to http://rt2x00.serialmonkey.com
[ 4387.364059] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4387.364059] Please file bug report to http://rt2x00.serialmonkey.com
[ 4419.325797] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4419.325797] Please file bug report to http://rt2x00.serialmonkey.com
[ 4462.316123] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4462.316123] Please file bug report to http://rt2x00.serialmonkey.com
[ 4515.295287] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4515.295287] Please file bug report to http://rt2x00.serialmonkey.com
[ 4578.279247] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4578.279247] Please file bug report to http://rt2x00.serialmonkey.com
[ 4641.259220] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4641.259220] Please file bug report to http://rt2x00.serialmonkey.com
[ 4660.273173] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4660.273173] Please file bug report to http://rt2x00.serialmonkey.com
[ 4661.289513] wlan0: authenticate with --:--:--:--:--:--
[ 4661.297060] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4661.297080] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4661.297080] Please file bug report to http://rt2x00.serialmonkey.com
[ 4661.500765] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4661.704703] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4661.908626] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4661.916812] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4661.916812] Please file bug report to http://rt2x00.serialmonkey.com
[ 4662.052595] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4662.052595] Please file bug report to http://rt2x00.serialmonkey.com
[ 4663.076378] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4663.076378] Please file bug report to http://rt2x00.serialmonkey.com
[ 4668.102694] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4668.102694] Please file bug report to http://rt2x00.serialmonkey.com
[ 4674.156766] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4674.156766] Please file bug report to http://rt2x00.serialmonkey.com
[ 4675.173057] wlan0: authenticate with --:--:--:--:--:--
[ 4675.180644] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4675.180664] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4675.180664] Please file bug report to http://rt2x00.serialmonkey.com
[ 4675.384367] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4675.588294] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4675.792227] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4675.800425] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4675.800425] Please file bug report to http://rt2x00.serialmonkey.com
[ 4675.936193] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4675.936193] Please file bug report to http://rt2x00.serialmonkey.com
[ 4676.952432] wlan0: authenticate with --:--:--:--:--:--
[ 4676.959920] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4676.959920] Please file bug report to http://rt2x00.serialmonkey.com
[ 4676.960022] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4677.163788] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4677.367722] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4677.571654] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4677.579865] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4677.579865] Please file bug report to http://rt2x00.serialmonkey.com
[ 4677.715633] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4677.715633] Please file bug report to http://rt2x00.serialmonkey.com
[ 4678.739408] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4678.739408] Please file bug report to http://rt2x00.serialmonkey.com
[ 4683.769656] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4683.769656] Please file bug report to http://rt2x00.serialmonkey.com
[ 4684.793483] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4684.793483] Please file bug report to http://rt2x00.serialmonkey.com
[ 4685.245230] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4685.245230] Please file bug report to http://rt2x00.serialmonkey.com
[ 4689.819751] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4689.819751] Please file bug report to http://rt2x00.serialmonkey.com
[ 4690.836020] wlan0: authenticate with --:--:--:--:--:--
[ 4690.843660] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4690.843680] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4690.843680] Please file bug report to http://rt2x00.serialmonkey.com
[ 4691.047369] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4691.251301] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4691.455211] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4691.459553] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4691.459553] Please file bug report to http://rt2x00.serialmonkey.com
[ 4691.595220] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4691.595220] Please file bug report to http://rt2x00.serialmonkey.com
[ 4692.611443] wlan0: authenticate with --:--:--:--:--:--
[ 4692.618986] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4692.618986] Please file bug report to http://rt2x00.serialmonkey.com
[ 4692.619101] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4692.822803] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4693.026715] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4693.230681] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4693.238853] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4693.238853] Please file bug report to http://rt2x00.serialmonkey.com
[ 4693.374645] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4693.374645] Please file bug report to http://rt2x00.serialmonkey.com
[ 4694.398418] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4694.398418] Please file bug report to http://rt2x00.serialmonkey.com
[ 4699.424728] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4699.424728] Please file bug report to http://rt2x00.serialmonkey.com
[ 4700.448496] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4700.448496] Please file bug report to http://rt2x00.serialmonkey.com
[ 4705.478796] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4705.478796] Please file bug report to http://rt2x00.serialmonkey.com
[ 4711.532871] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4711.532871] Please file bug report to http://rt2x00.serialmonkey.com
[ 4712.549187] wlan0: authenticate with --:--:--:--:--:--
[ 4712.556767] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4712.556788] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4712.556788] Please file bug report to http://rt2x00.serialmonkey.com
[ 4712.760462] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4712.964399] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4713.168341] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4713.176536] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4713.176536] Please file bug report to http://rt2x00.serialmonkey.com
[ 4713.232327] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4713.232327] Please file bug report to http://rt2x00.serialmonkey.com
[ 4714.256094] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4714.256094] Please file bug report to http://rt2x00.serialmonkey.com
[ 4716.255369] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4716.255369] Please file bug report to http://rt2x00.serialmonkey.com
[ 4717.271380] wlan0: authenticate with --:--:--:--:--:--
[ 4717.279260] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4717.279279] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4717.279279] Please file bug report to http://rt2x00.serialmonkey.com
[ 4717.482970] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4717.686866] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4717.890839] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4717.899044] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4717.899044] Please file bug report to http://rt2x00.serialmonkey.com
[ 4718.034801] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4718.034801] Please file bug report to http://rt2x00.serialmonkey.com
[ 4719.051034] wlan0: authenticate with --:--:--:--:--:--
[ 4719.058576] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4719.058576] Please file bug report to http://rt2x00.serialmonkey.com
[ 4719.058686] wlan0: direct probe to --:--:--:--:--:-- (try 1/3)
[ 4719.262350] wlan0: direct probe to --:--:--:--:--:-- (try 2/3)
[ 4719.298410] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4719.298410] Please file bug report to http://rt2x00.serialmonkey.com
[ 4720.322135] wlan0: direct probe to --:--:--:--:--:-- (try 3/3)
[ 4720.526001] wlan0: authentication with --:--:--:--:--:-- timed out
[ 4720.534206] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4720.534206] Please file bug report to http://rt2x00.serialmonkey.com
[ 4722.229466] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4722.229466] Please file bug report to http://rt2x00.serialmonkey.com
[ 4723.253198] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4723.253198] Please file bug report to http://rt2x00.serialmonkey.com
[ 4745.226162] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4745.226162] Please file bug report to http://rt2x00.serialmonkey.com
[ 4746.249937] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4746.249937] Please file bug report to http://rt2x00.serialmonkey.com
[ 4778.211674] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4778.211674] Please file bug report to http://rt2x00.serialmonkey.com
[ 4821.201999] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4821.201999] Please file bug report to http://rt2x00.serialmonkey.com
[ 4874.181146] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4874.181146] Please file bug report to http://rt2x00.serialmonkey.com
[ 4937.165122] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 4937.165122] Please file bug report to http://rt2x00.serialmonkey.com
[ 5000.141092] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 5000.141092] Please file bug report to http://rt2x00.serialmonkey.com
[ 5063.125063] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 0
[ 5063.125063] Please file bug report to http://rt2x00.serialmonkey.com
[ 5131.595082] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5133.726698] wlan0: authenticate with --:--:--:--:--:--
[ 5133.734326] wlan0: send auth to --:--:--:--:--:-- (try 1/3)
[ 5133.735740] wlan0: authenticated
[ 5133.735959] rt2800pci 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 5133.735966] rt2800pci 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 5133.735969] rt2800pci 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 5133.738101] wlan0: associate with --:--:--:--:--:-- (try 1/3)
[ 5133.740205] wlan0: RX AssocResp from --:--:--:--:--:-- (capab=0x411 status=0 aid=1)
[ 5133.740501] wlan0: associated
[ 5133.740538] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10410.484527] wlan0: deauthenticating from --:--:--:--:--:-- by local choice (reason=3)
[10418.157514] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10420.301198] wlan0: authenticate with --:--:--:--:--:--
[10420.316720] wlan0: send auth to --:--:--:--:--:-- (try 1/3)
[10420.318568] wlan0: authenticated
[10420.320616] wlan0: associate with --:--:--:--:--:-- (try 1/3)
[10420.324377] wlan0: RX AssocResp from --:--:--:--:--:-- (capab=0x411 status=0 aid=2)
[10420.324516] wlan0: associated
[10420.324549] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10482.545814] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10482.705847] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10483.069912] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10483.229934] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10483.489991] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10483.650017] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10483.810051] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10483.970074] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10485.190300] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10485.350321] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10490.183209] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10490.343231] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10490.503269] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10490.663292] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10491.883518] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10492.043539] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10496.880427] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10497.040448] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10497.200491] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10497.360478] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10498.580737] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10498.740735] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10498.891002] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10499.080791] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10499.240858] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10499.400911] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10499.560884] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10500.781137] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10500.941134] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10502.749493] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10502.909491] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10503.069514] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10503.229544] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10504.449760] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10504.609834] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10525.753692] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10525.913674] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10526.073750] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10526.233769] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10527.454002] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10527.613985] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10558.759706] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10558.919724] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10559.079762] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10559.239784] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10560.460002] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10560.620019] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10601.747669] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10601.907611] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10602.067567] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10602.227505] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10603.447070] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10603.607032] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10654.730819] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10654.890761] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10655.050719] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10655.210659] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10656.430277] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10656.590219] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10663.380091] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10663.540019] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10685.942264] rt2800pci 0000:02:00.0: irq 44 for MSI/MSI-X
[10685.942354] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0013 detected
[10685.946179] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[10685.952996] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[10685.953030] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[10686.001125] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10686.001625] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10686.061837] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 2, dropping
[10686.125791] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 2, dropping
[10686.189776] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 2, dropping
[10686.253777] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 2, dropping
[10686.317751] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 0, dropping
[10686.381716] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 0, dropping
[10686.445701] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 0, dropping
[10686.509688] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 0, dropping
[10686.573654] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 0, dropping
[10686.637639] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 0, dropping
[10686.701613] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 0, dropping
[10687.141541] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 0, dropping
[10687.145661] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 0, dropping
[10687.205525] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 0, dropping
[10687.209804] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 0, dropping
[10688.156773] wlan0: authenticate with --:--:--:--:--:--
[10688.172345] wlan0: send auth to --:--:--:--:--:-- (try 1/3)
[10688.174066] wlan0: authenticated
[10688.176187] wlan0: associate with --:--:--:--:--:-- (try 1/3)
[10688.179612] wlan0: RX AssocResp from --:--:--:--:--:-- (capab=0x411 status=0 aid=2)
[10688.179733] wlan0: associated
[10688.179775] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10718.515531] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10718.675386] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10719.035074] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10719.194954] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10719.454753] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10719.614623] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10719.774455] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10719.934330] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10720.986075] wlan0: authenticate with --:--:--:--:--:--
[10721.153372] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10721.313233] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10721.321338] wlan0: send auth to --:--:--:--:--:-- (try 1/3)
[10722.352342] wlan0: send auth to --:--:--:--:--:-- (try 2/3)
[10723.351535] wlan0: send auth to --:--:--:--:--:-- (try 3/3)
[10724.350770] wlan0: authentication with --:--:--:--:--:-- timed out
[10724.526608] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10724.686471] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10724.946256] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10725.106128] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10725.266002] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10725.425819] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10726.644876] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10726.804737] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10731.636785] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10731.796663] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10731.956533] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10732.116393] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10733.335396] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10733.495272] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10734.830972] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10735.022014] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10735.181887] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10735.341781] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10735.501623] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10736.720567] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10736.880459] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10738.683028] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10738.842844] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10739.002689] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10739.162617] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10740.381636] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10740.541498] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10761.668208] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10761.828043] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10761.987902] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10762.147788] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10763.367015] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10763.526921] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10775.119270] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10775.279227] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10787.418052] rt2800pci 0000:02:00.0: irq 44 for MSI/MSI-X
[10787.418146] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0013 detected
[10787.421855] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[10787.431250] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[10787.431325] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[10787.483619] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10787.484146] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10787.548312] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 2, dropping
[10787.612271] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 2, dropping
[10787.676260] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 2, dropping
[10787.740229] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 2, dropping
[10787.804215] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 2, dropping
[10787.868182] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 2, dropping
[10787.932168] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 2, dropping
[10787.996131] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 2, dropping
[10788.060120] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 2, dropping
[10788.124107] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 2, dropping
[10788.188072] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 2, dropping
[10788.730939] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10788.890903] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10789.050839] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10789.087861] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 2, dropping
[10789.092086] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 0, dropping
[10789.151849] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 0, dropping
[10789.156088] ieee80211 phy0: rt2800pci_txdone: Warning - Got TX status for an empty queue 0, dropping
[10790.103060] wlan0: authenticate with --:--:--:--:--:--
[10790.118614] wlan0: send auth to --:--:--:--:--:-- (try 1/3)
[10790.122499] wlan0: authenticated
[10790.126526] wlan0: associate with --:--:--:--:--:-- (try 1/3)
[10790.130027] wlan0: RX AssocResp from --:--:--:--:--:-- (capab=0x411 status=0 aid=2)
[10790.130143] wlan0: associated
[10790.130181] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10816.467143] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10816.627132] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10816.987234] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10817.147259] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10817.407291] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10817.567348] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10817.727367] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10817.887350] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10818.940179] wlan0: authenticate with --:--:--:--:--:--
[10819.107577] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10819.267644] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10819.275711] wlan0: send auth to --:--:--:--:--:-- (try 1/3)
[10820.299845] wlan0: send auth to --:--:--:--:--:-- (try 2/3)
[10821.300027] wlan0: send auth to --:--:--:--:--:-- (try 3/3)
[10822.300199] wlan0: authentication with --:--:--:--:--:-- timed out
[10822.476174] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10822.636269] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10822.896288] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10823.056336] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10823.216366] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10823.376394] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10824.596588] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10824.756650] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10829.589532] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10829.749556] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10829.909540] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10830.069614] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10831.289795] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10831.449868] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10832.809369] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10833.001814] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10833.161764] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10833.321711] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10833.481624] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10834.701271] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10834.861223] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10836.656654] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10836.816611] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10836.976555] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10837.136509] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10838.356109] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10838.516038] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10859.653336] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10859.813295] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10859.973239] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10860.133195] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10861.352747] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10861.512753] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10892.642855] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10892.802798] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10892.962754] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10893.122700] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10894.342315] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10894.502257] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10935.629183] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10935.789127] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10935.949083] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10936.109023] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10937.328644] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10937.488587] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10988.612327] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10988.772284] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10988.932224] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10989.092182] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[10990.311794] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[10990.471736] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[11051.592304] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[11051.752246] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[11051.912204] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[11052.072145] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[11052.108153] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[11053.291763] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[11053.451705] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[11114.572268] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[11114.732224] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[11114.892173] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[11115.052120] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[11115.088127] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[11116.271734] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[11116.431684] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush


```

---

### Post by chili555 on 2014-03-12
@Varun-- It seems to be a known bug: [https://bugzilla.kernel.org/show_bug.cgi?id=61621](https://bugzilla.kernel.org/show_bug.cgi?id=61621) I am working on a very similar thread here: [http://ubuntuforums.org/showthread.php?t=2210708](http://ubuntuforums.org/showthread.php?t=2210708) I suspect a 3,12 or even 3.13 kernel might fix it.

---

### Post by varunendra on 2014-03-12
> **chili555 said:**
> I suspect a 3,12 or even 3.13 kernel might fix it.

Yup, I don't trust the ralink drivers of kernel 3.10/11 anymore anyway, I try those parameters just for the kicks :p

Thanks for the thread link, I didn't remember whether the sta driver builds or not on the latest kernels, I think some of the latest ones do, but probably none related to this card, so..

**@nick85x,**

When you say - "***When I try the first your option, it doesn't work..***" - do you mean it couldn't keep the power management off or that it did but that did not help?

Because if the power management turned off, but automatically turned on again after a few minutes, we may try some other tweaks to keep it off. This can be important, please confirm in detail what happened with the first command.

IF (and for now I'd say "Only IF"), the power management remained off, but did not help, then please follow the instructions in this post to try a newer driver : [http://ubuntuforums.org/showthread.php?t=2204912&p=12927696#post12927696](http://ubuntuforums.org/showthread.php?t=2204912&p=12927696#post12927696)

We'd be curious to see your report about the performance after trying above, but please also confirm what I asked about the Power Management.

---

### Post by nick85x on 2014-03-12
```

--@-- ~ $ iwconfig 
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"--"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: --:--:--:--:--:--   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:95   Missed beacon:0

--@-- ~ $ sudo iwconfig wlan0 power off

--@-- ~ $ iwconfig 
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"--"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: --:--:--:--:--:--   
          Bit Rate=57.8 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10  Invalid misc:106   Missed beacon:0

**After about 30 seconds or some more, the opening of Firefox:**

--@-- ~ $ iwconfig 
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

--@-- ~ $ sudo iwconfig wlan0 power off
--@-- ~ $ iwconfig 
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

Indeed, the command "sudo iwconfig wlan0 power off" does not happen anything like you said.
Then I noticed that the connection remains active until the moment that does not use the opening Mozilla Firefox or any other application that uses the line.
Then you advise me to install this new driver?
My fear is that I can not even connect to the internet from the other modem-routher (from which I'm writing).

---

### Post by varunendra on 2014-03-12
Yes, my advice for now IS to follow the link I gave and try the newer driver. That driver has been tested many times by different users here on the forums and it usually (read - almost 'always') works better. In any case, it won't make anything worse.

However, like you can't 'Guarantee' that your computer will even power on again after shutting down this time (nobody knows when a software/hardware may fail), similarly I can't 'Guarantee' that changing the driver will only improve things and _can not_ break anything.

Don't worry, I'm saying this just to stay 'Clean' in case something wrong happens during or after running the installation procedure, and you start claiming the 'Guaranty'.., the driver itself and the procedure to install it are completely safe and quite easy. :p

If you want to play extra safe, create a Live bootable USB and install the proposed driver on that instead. If successful (I'm not sure if it can install on Live session or not), check the performance yourself and then proceed. I don't know a safer way to test that. :)

---

### Post by nick85x on 2014-03-15
Hi Varunendra, 
It works very well, with both modem! :D
I love Linux, it is so fast, powerful, simple, and is the most secure OS in the world ;)
(Although sometimes you have to lose a little bit of time to set it up in a workmanlike :) )
Thank you so much!!!!!!!!! :D

---

