---
title: "Both bluetooth and wifi not connecting"
date: 2014-05-29
forum: Networking &amp; Wireless
---

### Post by raffaele2 on 2014-05-29
Hi,
I'm having problems both with bluetooth and wifi, my pc is a Lenovo B5400.
The BT can do a scan, but it isn't able to find any devices; I don't see any wifi network (but I have a working Ethernet connection).
I read many topics on the internet but before trying different solutions and make some changes (I just installed Ubuntu 14.04) I would firstly try to understand what could the problem depend on.

What are the commands I can use to see what's going on? 


Thank you in advance

---

### Post by praseodym on 2014-05-29
Hi,

lets check for Bluetooth:

```
sudo apt-get install bluez-utils libopenobex1 gnome-bluetooth 
lsusb | grep Bluetooth 
hciconfig --all 
```
For wireless:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
```

---

### Post by raffaele2 on 2014-06-03
hi, thank you for the commands.

```
lsusb | grep Bluetooth
```
returns nothing

```
hciconfig --all:
 
    BD Address: A4:DB:30:9E:43:BB  ACL MTU: 820:8  SCO MTU: 255:16
    UP RUNNING PSCAN ISCAN 
    RX bytes:901 acl:0 sco:0 events:42 errors:0
    TX bytes:994 acl:0 sco:0 commands:42 errors:0
    Features: 0xff 0xff 0xff 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'ubuntu-0'
    Class: 0x700100
    Service Classes: Object Transfer, Audio, Telephony
    Device Class: Computer, Uncategorized
    HCI Version: 4.0 (0x6)  Revision: 0xb
    LMP Version: 4.0 (0x6)  Subversion: 0x8723
    Manufacturer: Realtek Semiconductor Corporation (93)


```


For wireless
```
lspci -nnk | grep -iA2 net

04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b728]
    Kernel driver in use: rtl8723be
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:5024]
    Kernel driver in use: r8169


```


```
lsusb

Bus 002 Device 003: ID 04f2:b2fa Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 045e:0748 Microsoft Corp. 
Bus 003 Device 005: ID 152b:0015  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```


```
lsmod

Module                  Size  Used by
rfcomm                 69160  12 
bnep                   19624  2 
nls_iso8859_1          12713  1 
snd_hda_codec_realtek    61438  1 
snd_hda_codec_hdmi     46207  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
cryptd                 20359  1 ghash_clmulni_intel
joydev                 17381  0 
serio_raw              13462  0 
thinkpad_acpi          80973  1 
nvram                  14411  1 thinkpad_acpi
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_hda_intel          52355  7 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_pcm               102099  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
i915                  783485  5 
rtl8723be              85042  0 
btusb                  32412  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
bluetooth             395423  22 bnep,btusb,rfcomm
rtl_pci                26690  1 rtl8723be
rtlwifi                63475  2 rtl_pci,rtl8723be
mac80211              626511  3 rtl_pci,rtlwifi,rtl8723be
drm_kms_helper         52758  1 i915
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
lpc_ich                21080  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29482  2 snd_pcm,snd_seq
drm                   302817  4 i915,drm_kms_helper
cfg80211              484040  2 mac80211,rtlwifi
mei_me                 18627  0 
mei                    82274  1 mei_me
snd                    69238  25 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
i2c_algo_bit           13413  1 i915
wmi                    19177  0 
soundcore              12680  1 snd
video                  19476  1 i915
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
psmouse               102222  0 
ahci                   25819  2 
r8169                  67581  0 
libahci                32168  1 ahci
mii                    13934  1 r8169


```


```
iwconfig

eth0      no wireless extensions.

lo        no wireless extensions.


```


```
rfkill list

1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```


```

resolv.conf

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.1.2
nameserver 127.0.1.1
search timprogetti.local


```

---

### Post by raffaele2 on 2014-06-04
please,
can anyone help me to understand if there are anomalies?

Thanks

---

### Post by bunker2 on 2014-06-28
I have Lenovo B5400. There was a problem with wifi too. The problem was solved by installing kernel 3.16.0 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

