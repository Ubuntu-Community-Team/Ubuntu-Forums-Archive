---
title: "Bluetooth error hci0: Connection timed out ubuntu 20.04"
date: 2020-05-13
forum: Networking &amp; Wireless
---

### Post by reisub83 on 2020-05-13
Hi

I have problems with my pc embedded bluetooth.

Here some commands outputs

cat /etc/lsb-release 

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04 LTS"

```
sudo hciconfig hci0 -a
```
hci0:    Type: Primary  Bus: USB
    BD Address: 3C:95:09:53:C8:74  ACL MTU: 1024:8  SCO MTU: 50:8
    DOWN 
    RX bytes:1282038 acl:107 sco:0 events:182462 errors:0
    TX bytes:112233020 acl:182140 sco:0 commands:233 errors:0
    Features: 0xff 0xfe 0x8f 0xfe 0xd8 0x3f 0x5b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT

```
cat /var/lib/bluetooth/3C\:95\:09\:53\:C8\:74/settings 
```
[General]
Discoverable=true
DiscoverableTimeout=0

```
dmesg | grep Blue
```


[    3.819608] Bluetooth: Core ver 2.22
[    3.819626] Bluetooth: HCI device and connection manager initialized
[    3.819630] Bluetooth: HCI socket layer initialized
[    3.819631] Bluetooth: L2CAP socket layer initialized
[    3.819634] Bluetooth: SCO socket layer initialized
[    7.073723] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    7.073724] Bluetooth: BNEP filters: protocol multicast
[    7.073727] Bluetooth: BNEP socket layer initialized
[   10.108821] Bluetooth: RFCOMM TTY layer initialized
[   10.108828] Bluetooth: RFCOMM socket layer initialized
[   10.108832] Bluetooth: RFCOMM ver 1.11

```

dmesg | grep ath |grep -v path
```


[    3.807455] ath10k_pci 0000:05:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    4.119028] ath10k_pci 0000:05:00.0: qca9377 hw1.1 target 0x05020001 chip_id 0x003821ff sub 17aa:0901
[    4.119031] ath10k_pci 0000:05:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    4.119504] ath10k_pci 0000:05:00.0: firmware ver WLAN.TF.2.1-00021-QCARMSWP-1 api 6 features wowlan,ignore-otp crc32 42e41877
[    4.200919] ath10k_pci 0000:05:00.0: board_file api 2 bmi_id N/A crc32 8aedfa4a
[    4.285988] ath10k_pci 0000:05:00.0: unsupported HTC service id: 1536
[    4.304496] ath10k_pci 0000:05:00.0: htt-ver 3.56 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    4.441729] ath: EEPROM regdomain: 0x6c
[    4.441730] ath: EEPROM indicates we should expect a direct regpair map
[    4.441732] ath: Country alpha2 being used: 00
[    4.441733] ath: Regpair used: 0x6c
[    5.118312] ath10k_pci 0000:05:00.0 wlp5s0: renamed from wlan0
[    8.596618] ath10k_pci 0000:05:00.0: unsupported HTC service id: 1536
[   16.662644] ath: EEPROM regdomain: 0x817c
[   16.662645] ath: EEPROM indicates we should expect a country code
[   16.662645] ath: doing EEPROM country->regdmn map search
[   16.662646] ath: country maps to regdmn code: 0x37
[   16.662646] ath: Country alpha2 being used: IT
[   16.662647] ath: Regpair used: 0x37
[   16.662648] ath: regdomain 0x817c dynamically updated by country element

```

lsusb
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 001 Device 004: ID 0bda:58db Realtek Semiconductor Corp. Integrated Camera
Bus 001 Device 003: ID 0cf3:e500 Qualcomm Atheros Communications 
Bus 001 Device 002: ID 062a:4106 MosArt Semiconductor Corp. 2.4G Wireless Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
sudo lsusb -v -d 0cf3:e500

```
Bus 001 Device 003: ID 0cf3:e500 Qualcomm Atheros Communications 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.01
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x0cf3 Qualcomm Atheros Communications
  idProduct          0xe500 
  bcdDevice            0.01
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x00b1
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength       0x000c
  bNumDeviceCaps          1
  USB 2.0 Extension Device Capability:
    bLength                 7
    bDescriptorType        16
    bDevCapabilityType      2
    bmAttributes   0x00000002
      HIRD Link Power Management (LPM) Supported
can't get debug descriptor: Resource temporarily unavailable
Device Status:     0x0001
  Self Powered

```
lsmod

```
Module                  Size  Used by
ppp_deflate            16384  0
bsd_comp               16384  0
ppp_async              20480  1
ccm                    20480  6
xt_conntrack           16384  1
xt_MASQUERADE          20480  1
nf_conntrack_netlink    45056  0
nfnetlink              16384  2 nf_conntrack_netlink
xfrm_user              36864  1
xfrm_algo              16384  1 xfrm_user
xt_addrtype            16384  2
iptable_filter         16384  1
iptable_nat            16384  1
nf_nat                 40960  2 iptable_nat,xt_MASQUERADE
nf_conntrack          139264  4 xt_conntrack,nf_nat,nf_conntrack_netlink,xt_MASQUERADE
nf_defrag_ipv6         24576  1 nf_conntrack
nf_defrag_ipv4         16384  1 nf_conntrack
libcrc32c              16384  2 nf_conntrack,nf_nat
bpfilter               32768  0
br_netfilter           28672  0
bridge                176128  1 br_netfilter
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               487424  2 vboxnetadp,vboxnetflt
rfcomm                 81920  16
aufs                  262144  0
cmac                   16384  4
algif_hash             16384  2
algif_skcipher         16384  2
af_alg                 24576  10 algif_hash,algif_skcipher
bnep                   24576  2
overlay               114688  0
intel_rapl_msr         20480  0
uvcvideo               98304  0
mei_hdcp               24576  0
videobuf2_vmalloc      20480  1 uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
nls_iso8859_1          16384  1
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_common       49152  2 videobuf2_v4l2,uvcvideo
videodev              225280  3 videobuf2_v4l2,uvcvideo,videobuf2_common
mc                     53248  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
btusb                  57344  0
btrtl                  24576  1 btusb
btbcm                  16384  1 btusb
btintel                24576  1 btusb
intel_rapl_common      24576  1 intel_rapl_msr
x86_pkg_temp_thermal    20480  0
bluetooth             581632  42 btrtl,btintel,btbcm,bnep,btusb,rfcomm
intel_powerclamp       20480  0
coretemp               20480  0
snd_seq_midi           20480  0
ath10k_pci             49152  0
snd_seq_midi_event     16384  1 snd_seq_midi
ath10k_core           475136  1 ath10k_pci
ecdh_generic           16384  1 bluetooth
ecc                    28672  1 ecdh_generic
snd_rawmidi            36864  1 snd_seq_midi
kvm_intel             286720  0
snd_hda_codec_hdmi     61440  1
snd_hda_codec_conexant    28672  1
ath                    36864  1 ath10k_core
kvm                   663552  1 kvm_intel
snd_hda_codec_generic    81920  1 snd_hda_codec_conexant
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
mac80211              843776  1 ath10k_core
intel_cstate           20480  0
snd_hda_intel          53248  3
intel_rapl_perf        20480  0
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 24576  0
input_leds             16384  0
snd_hwdep              20480  1 snd_hda_codec
cfg80211              704512  3 ath,mac80211,ath10k_core
thinkpad_acpi         110592  0
wmi_bmof               16384  0
nvram                  16384  1 thinkpad_acpi
serio_raw              20480  0
ledtrig_audio          16384  3 snd_hda_codec_generic,snd_hda_codec_conexant,thinkpad_acpi
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
ucsi_acpi              16384  0
snd_timer              36864  2 snd_seq,snd_pcm
libarc4                16384  1 mac80211
typec_ucsi             40960  1 ucsi_acpi
mei_me                 40960  1
intel_xhci_usb_role_switch    16384  0
roles                  16384  1 intel_xhci_usb_role_switch
mei                   106496  3 mei_hdcp,mei_me
intel_pch_thermal      16384  0
snd                    90112  18 snd_hda_codec_generic,snd_seq,snd_hda_codec_conexant,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,thinkpad_acpi,snd_pcm,snd_rawmidi
typec                  45056  1 typec_ucsi
soundcore              16384  1 snd
mac_hid                16384  0
sch_fq_codel           20480  3
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  2 iptable_filter,iptable_nat
x_tables               40960  5 xt_conntrack,iptable_filter,xt_addrtype,ip_tables,xt_MASQUERADE
autofs4                45056  2
hid_generic            16384  0
usbhid                 57344  0
hid                   131072  2 usbhid,hid_generic
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
i915                 1986560  60
nvme                   49152  4
ghash_clmulni_intel    16384  0
i2c_algo_bit           16384  1 i915
aesni_intel           372736  10
drm_kms_helper        184320  1 i915
psmouse               155648  0
nvme_core             102400  6 nvme
sdhci_pci              53248  0
syscopyarea            16384  1 drm_kms_helper
r8169                  90112  0
i2c_i801               32768  0
crypto_simd            16384  1 aesni_intel
cqhci                  28672  1 sdhci_pci
sdhci                  65536  1 sdhci_pci
cryptd                 24576  4 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
realtek                24576  1
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
ahci                   40960  0
fb_sys_fops            16384  1 drm_kms_helper
libahci                32768  1 ahci
drm                   491520  19 drm_kms_helper,i915
wmi                    32768  1 wmi_bmof
video                  49152  2 thinkpad_acpi,i915

```

modinfo ath3k

```
filename:       /lib/modules/5.4.0-29-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     76A3AF6F30098E6C760BCBB
alias:          usb:v0489pE03Cd*dc*dsc*dp*ic*isc*ip*in*
...
depends:        bluetooth
retpoline:      Y
intree:         Y
name:           ath3k
vermagic:       5.4.0-29-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        7A:CA:B9:D1:07:98:31:F8:B2:A4:1F:1E:7A:BD:54:D9:CB:6B:6C
sig_hashalgo:   sha512

```

bluetoothctl
```
Agent registered
[bluetooth]# power off
Changing power off succeeded
[bluetooth]# power on
[bluetooth]# scan on
Failed to start discovery: org.bluez.Error.NotReady
Failed to set power on: org.bluez.Error.Failed


```

---

