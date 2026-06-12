---
title: "Enabling 5GHz On Wifi Card"
date: 2017-07-02
forum: Networking &amp; Wireless
---

### Post by Darth4212 on 2017-07-02
My wireless card on my laptop is capable of using 5GHz but I am not seeing them on my list of wifi networks. Now using natural logic I assume that 5GHz capability on my wifi card is disabled. How would I go about enabling this?

---

### Post by praseodym on 2017-07-02
Lets "guess" which card it is ;)
```

lspci -nnk
lsusb
lsmod
```

---

### Post by Darth4212 on 2017-07-02
> **praseodym said:**
> Lets "guess" which card it is ;)
Lol it is a Broadcom 802.11n

---

### Post by praseodym on 2017-07-02
Please show the outputs of the first and 3rd command

---

### Post by vocx on 2017-07-02
> **Darth4212 said:**
> Lol it is a Broadcom 802.11n
Please provide the full information that you are being asked.

You already mentioned a problem in another thread [https://ubuntuforums.org/showthread.php?t=2364857](https://ubuntuforums.org/showthread.php?t=2364857)

In that thread you already ran "lshw -c network". If you don't want to specify again your hardware in this thread, the minimum you should do is link to your previous thread so people don't have to ask the same questions again. Just paste the text in "```
" tags. You should not use pictures to document something that can be described in plain text.
[CODE]
*-network
    description: Wireless interface
    product: BCM43225 802.11b/g/n
    vendor: Broadcom Limited
    ...

```

By the way, saying a card is a "Broadcom 802.11n" is not good enough. That is like saying "I have an Intel x86_64 processor". It does not give you details. It justs tells you the brand "Intel", and the generic information "x86_64", which is an architecture which has existed since the early 1990s. Basically all desktop processors are "x86_64" nowadays, so giving this information is not helpful. Or it's like saying "I have a Hyundai 2016 car". Well, again, it only tells you the brand "Hyundai", and the year of the car, but it does not tell you which model it is. Is it electric, does it use diesel, is it automatic, does it have 4x4 traction? These are important details that you need if you want to fix a problem with it.

 For your wireless card "Broadcom" is the brand and "802.11n" is a generic description. Essentially, all wireless cards, all Wi-Fi routers, all cellphones, etc., are "802.11n". The 802.11 number indicates an IEEE standard for wireless communication. If you say that you have a 802.11 device, that is not helpful information to troubleshoot your problems.

The real model of your card is the other number, BCM43225. There are many devices in the market from the same manufacturer, so giving the specific number is important if you ever want to find solutions to any issues, as different devices could use different, sometimes incompatible, kernel modules. So please, give the full information whenever you are asked.

---

### Post by Darth4212 on 2017-07-02
> **vocx said:**
> By the way, saying a card is a "Broadcom 802.11n" is not good enough. That is like saying "I have an Intel x86_64 processor". It does not give you details. It justs tells you the brand "Intel", and the generic information "x86_64", which is an architecture which has existed since the early 1990s. Basically all desktop processors are "x86_64" nowadays, so giving this information is not helpful. Or it's like saying "I have a Hyundai 2016 car". Well, again, it only tells you the brand "Hyundai", and the year of the car, but it does not tell you which model it is. Is it electric, does it use diesel, is it automatic, does it have 4x4 traction? These are important details that you need if you want to fix a problem with it.

 For your wireless card "Broadcom" is the brand and "802.11n" is a generic description. Essentially, all wireless cards, all Wi-Fi routers, all cellphones, etc., are "802.11n". The 802.11 number indicates an IEEE standard for wireless communication. If you say that you have a 802.11 device, that is not helpful information to troubleshoot your problems.

The real model of your card is the other number, BCM43225. There are many devices in the market from the same manufacturer, so giving the specific number is important if you ever want to find solutions to any issues, as different devices could use different, sometimes incompatible, kernel modules. So please, give the full information whenever you are asked.

Thanks for the explanation. Not sure if you are meaning to be but it seems like you are being a bit rude? I apologize for being so nooby I am learning so I try my best.

---

### Post by praseodym on 2017-07-02
Ok, lets see which driver version is in use
```

lsmod
dmesg | egrep 'wl|brcm|Broadcom'
```

---

### Post by Darth4212 on 2017-07-02
> **praseodym said:**
> Please show the outputs of the first and 3rd command
First command
```
root@The-Meme-Machine-2:~# lspci -nnk00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] RS880 Host Bridge [1022:9601]
    Subsystem: Acer Incorporated [ALI] RS880 Host Bridge [1025:036e]
00:01.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (int gfx) [1022:9602]
    Kernel modules: shpchp
00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0) [1022:9604]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:05.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) [1022:9605]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
    Subsystem: Acer Incorporated [ALI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1025:036e]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Acer Incorporated [ALI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1025:036e]
    Kernel driver in use: ohci-pci
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Acer Incorporated [ALI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1025:036e]
    Kernel driver in use: ehci-pci
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Acer Incorporated [ALI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1025:036e]
    Kernel driver in use: ohci-pci
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Acer Incorporated [ALI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1025:036e]
    Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 41)
    Subsystem: Acer Incorporated [ALI] SBx00 SMBus Controller [1025:036e]
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco
00:14.1 IDE interface [0101]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40)
    Subsystem: Acer Incorporated [ALI] SB7x0/SB8x0/SB9x0 IDE Controller [1025:036e]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp, pata_acpi
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: Acer Incorporated [ALI] SBx00 Azalia (Intel HDA) [1025:036e]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
    Subsystem: Acer Incorporated [ALI] SB7x0/SB8x0/SB9x0 LPC host controller [1025:036e]
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
    Subsystem: Acer Incorporated [ALI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1025:036e]
    Kernel driver in use: ohci-pci
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250] [1002:9712]
    Subsystem: Acer Incorporated [ALI] RS880M [Mobility Radeon HD 4225/4250] [1025:036e]
    Kernel driver in use: radeon
    Kernel modules: radeon
01:05.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series] [1002:970f]
    Subsystem: Acer Incorporated [ALI] RS880 HDMI Audio [Radeon HD 4200 Series] [1025:036e]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
02:00.0 Ethernet controller [0200]: Broadcom Limited NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] NetLink BCM57780 Gigabit Ethernet PCIe [1025:036e]
    Kernel driver in use: tg3
    Kernel modules: tg3
08:00.0 Network controller [0280]: Broadcom Limited BCM43225 802.11b/g/n [14e4:4357] (rev 01)
    Subsystem: Foxconn International, Inc. T77H103.00 Wireless Half-size Mini PCIe Card [105b:e021]
    Kernel driver in use: wl
    Kernel modules: bcma, wl

```

Third command:
```

root@The-Meme-Machine-2:~# lsmod
Module                  Size  Used by
uas                    24576  0
usb_storage            69632  2 uas
iptable_mangle         16384  0
ipt_REJECT             16384  0
nf_reject_ipv4         16384  1 ipt_REJECT
iptable_filter         16384  0
xt_REDIRECT            16384  0
nf_nat_redirect        16384  1 xt_REDIRECT
xt_tcpudp              16384  0
xt_owner               16384  0
xt_conntrack           16384  0
iptable_nat            16384  0
nf_conntrack_ipv4      20480  1
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_redirect,nf_nat_ipv4
nf_conntrack          131072  5 nf_conntrack_ipv4,xt_conntrack,nf_nat_ipv4,xt_REDIRECT,nf_nat
libcrc32c              16384  1 nf_nat
snd_hrtimer            16384  1
acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
edac_mce_amd           28672  0
snd_hda_codec_realtek    90112  1
snd_hda_codec_hdmi     49152  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
edac_core              53248  0
snd_hda_intel          36864  4
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
uvcvideo               90112  0
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
kvm_amd              2183168  0
snd_hwdep              16384  1 snd_hda_codec
videobuf2_vmalloc      16384  1 uvcvideo
kvm                   593920  1 kvm_amd
snd_pcm               102400  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
irqbypass              16384  1 kvm
snd_seq_midi           16384  0
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
joydev                 20480  0
input_leds             16384  0
serio_raw              16384  0
snd_seq                65536  3 snd_seq_midi_event,snd_seq_midi
k10temp                16384  0
wl                   6447104  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  3 snd_seq,snd_hrtimer,snd_pcm
snd                    77824  20 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
soundcore              16384  1 snd
cfg80211              610304  1 wl
shpchp                 36864  0
mac_hid                16384  0
i2c_piix4              24576  0
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  3 iptable_mangle,iptable_filter,iptable_nat
x_tables               36864  8 ipt_REJECT,xt_owner,iptable_mangle,ip_tables,iptable_filter,xt_tcpudp,xt_conntrack,xt_REDIRECT
autofs4                40960  2
pata_acpi              16384  0
amdkfd                139264  1
amd_iommu_v2           20480  1 amdkfd
radeon               1507328  4
i2c_algo_bit           16384  1 radeon
ttm                    98304  1 radeon
drm_kms_helper        151552  1 radeon
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
broadcom               20480  1
bcm_phy_lib            16384  1 broadcom
fb_sys_fops            16384  1 drm_kms_helper
psmouse               139264  0
drm                   352256  7 radeon,ttm,drm_kms_helper
pata_atiixp            16384  0
ahci                   36864  1
tg3                   163840  0
libahci                32768  1 ahci
ptp                    20480  1 tg3
pps_core               20480  1 ptp
wmi                    16384  1 acer_wmi
video                  40960  1 acer_wmi
fjes                   77824  0

```

Jeez that is alot of text. Also how "good" is the hardware on my laptop as you seem to be good with hardware. Forgive me if I am out of line.

---

### Post by praseodym on 2017-07-02
Deactivate the firewall:

```
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

Which driver version is it? 248 or 271?

---

### Post by Darth4212 on 2017-07-02
> **praseodym said:**
> Which driver version is it? 248 or 271?
I don't know how do I check? This is the info under additional drivers.
[IMG]https://sg9krg.bn1301.livefilestore.com/y4mkhcEsCrL5Dtb8iOLjQhCaotv2Ohfb6wZOOG2aiH1-D0GnsaphTPSyrMajaPfkoi0uHbKWz9_2Oq7HEepzW4PkRa3LA0kG_lbBcp2BeFseogVTqLj8j7ehFmAq7um1jN7xzq-Qqo_AnO0kt4-vmNumHR7GmyB6Gi2SsZ0gEEWoQkSjV4QinTgZwTcukkVRHTrgyvdg4O_0tik1SbD2gtMgw?width=632&height=108&cropmode=none[/IMG]

---

### Post by chili555 on 2017-07-02
You can check the version with:```
sudo dpkg -s bcmwl-kernel-source
```We hope we see: > Version: 6.30.223.[COLOR="#FF0000"]271[/COLOR]+bdcom-0ubuntu2
We'd also like to see:```
sudo iwlist chan
sudo nmcli dev wifi list
```

---

### Post by Darth4212 on 2017-07-06
> **praseodym said:**
> Ok, lets see which driver version is in use
```

lsmod
dmesg | egrep 'wl|brcm|Broadcom'
```

I ran that and I got this output:
```
wlan0: Broadcom BCM4357 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)

```

---

### Post by praseodym on 2017-07-06
Please show also the "lsmod" output, maybe we need to blacklist some other native drivers

---

