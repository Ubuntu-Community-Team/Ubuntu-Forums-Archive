---
title: "Lenovo 11IBY bluetooth device not found"
date: 2018-11-10
forum: Networking &amp; Wireless
---

### Post by playgamemy on 2018-11-10
Disclaimer: I am new to Linux so please help me if I get something fundamentally wrong.

I have Lenovo Ideapad 100S 11IBY which its 32GB eMMc storage filled up quickly thanks to constant update from Windows 10, and it ran really slow. Decided to give it a second chance by installing Ubuntu 18.04 instead, following the guides below, which now resolved the audio issue on this laptop

[https://www.linkedin.com/pulse/installing-ubuntu-1804-lenovo-100s-jose-ramon-huerga-ayuso](https://www.linkedin.com/pulse/installing-ubuntu-1804-lenovo-100s-jose-ramon-huerga-ayuso)
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/671323](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/671323)

There are other issues including the laptop keyboard and trackpad does not work occasionally after booting into Ubuntu and has to resolve by rebooting (sometimes rebooting few times). But once it works it will works fully for the whole time until reboot, I can bear with that. Another issue is it freeze occasionally but I think it happens only when I am using chromium, will leave that for now. (let me know if you have any ideas with these issues though)

My current issue is the bluetooth adapter is not recognised, In Settings -> Bluetooth it indicates "No Bluetooth Found - Plug in a dongle to use bluetooth" which I am sure I used bluetooth before on this laptop with windows 10. A quick search on the spec of the laptop also indicate it has bluetooth buildin. However, I cannot find any information on what the chip is, except one of the post suggest it is a rtl8723bs, and in fact, Ubuntu kernel module r8723 was loaded initially, and I have changed it to r8723bs instead but that does not help, rfkill list still show no bluetooth devices. On top of that bluetooth service is not enabled at start, even after I enabled it with systemctl, but thats properly because no bluetooth device is detected at startup?

If I understand correctly and the chip is indeed rtl8723bs (or rtl8723 variants), it is a combine wifi/bluetooth chip, and I can connect to wifi with no issue. I cannot find the device with lspci or lsusb so I don't know what to do next, any help is appreciated. Thanks in advance.

below are some diagnostic output

uname -r
```
4.15.0-38-generic
```

lspci -nnk; lsusb
```
00:00.0 Host bridge [0600]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register [8086:0f00] (rev 0f)
    Subsystem: Lenovo Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register [17aa:390c]
    Kernel driver in use: iosf_mbi_pci
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display [8086:0f31] (rev 0f)
    Subsystem: Lenovo Atom Processor Z36xxx/Z37xxx Series Graphics & Display [17aa:390c]
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI [8086:0f35] (rev 0f)
    Subsystem: Lenovo Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI [17aa:390c]
    Kernel driver in use: xhci_hcd
00:1a.0 Encryption controller [1080]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine [8086:0f18] (rev 0f)
    Subsystem: Lenovo Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine [17aa:390c]
    Kernel driver in use: mei_txe
    Kernel modules: mei_txe
00:1f.0 ISA bridge [0601]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit [8086:0f1c] (rev 0f)
    Subsystem: Lenovo Atom Processor Z36xxx/Z37xxx Series Power Control Unit [17aa:390c]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 5986:0673 Acer, Inc 
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

rfkill list
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

lsmod
```
Module                  Size  Used by
nls_iso8859_1          16384  1
snd_soc_sst_bytcr_rt5640    24576  1
gpio_keys              20480  0
axp288_adc             16384  0
axp288_fuel_gauge      20480  0
axp288_charger         20480  0
axp20x_pek             16384  0
industrialio           69632  2 axp288_adc,axp288_fuel_gauge
extcon_axp288          16384  0
intel_rapl             20480  0
intel_soc_dts_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             212992  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
punit_atom_debug       16384  0
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
uvcvideo               86016  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
aesni_intel           188416  0
videobuf2_v4l2         24576  1 uvcvideo
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
videodev              184320  3 videobuf2_core,videobuf2_v4l2,uvcvideo
media                  40960  2 videodev,uvcvideo
joydev                 24576  0
input_leds             16384  0
snd_intel_sst_acpi     16384  1
snd_soc_rt5670        131072  0
snd_intel_sst_core     53248  1 snd_intel_sst_acpi
snd_soc_rt5645        143360  0
snd_soc_sst_atom_hifi2_platform   102400  3 snd_intel_sst_core
snd_soc_rt5640        118784  2 snd_soc_sst_bytcr_rt5640
snd_soc_rl6231         16384  3 snd_soc_rt5670,snd_soc_rt5640,snd_soc_rt5645
lpc_ich                24576  0
mei_txe                20480  0
snd_soc_acpi           16384  2 snd_soc_sst_bytcr_rt5640,snd_intel_sst_acpi
snd_soc_acpi_intel_match    20480  1 snd_intel_sst_acpi
mei                    90112  1 mei_txe
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
mac_hid                16384  0
snd_soc_core          241664  5 snd_soc_sst_bytcr_rt5640,snd_soc_rt5670,snd_soc_rt5640,snd_soc_sst_atom_hifi2_platform,snd_soc_rt5645
snd_rawmidi            32768  1 snd_seq_midi
r8723bs               606208  0
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_pcm                98304  7 snd_soc_sst_bytcr_rt5640,snd_soc_rt5670,snd_soc_rt5640,snd_soc_sst_atom_hifi2_platform,snd_soc_core,snd_soc_rt5645,snd_pcm_dmaengine
soc_button_array       16384  0
dw_dmac                16384  0
int3406_thermal        16384  0
dw_dmac_core           24576  1 dw_dmac
dptf_power             16384  0
cfg80211              622592  1 r8723bs
int3400_thermal        16384  0
processor_thermal_device    16384  0
int3403_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
intel_int0002_vgpio    16384  0
int340x_thermal_zone    16384  2 int3403_thermal,processor_thermal_device
intel_soc_dts_iosf     16384  2 intel_soc_dts_thermal,processor_thermal_device
intel_cht_int33fe      16384  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
axp20x_i2c             16384  0
snd_timer              32768  2 snd_seq,snd_pcm
axp20x                 24576  1 axp20x_i2c
snd                    81920  10 snd_seq,snd_seq_device,snd_timer,snd_compress,snd_soc_sst_atom_hifi2_platform,snd_soc_core,snd_pcm,snd_rawmidi
acpi_pad              180224  0
pwm_lpss_platform      16384  0
pwm_lpss               16384  1 pwm_lpss_platform
soundcore              16384  1 snd
8250_dw                16384  0
sch_fq_codel           20480  5
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
mmc_block              36864  5
i915                 1617920  14
i2c_algo_bit           16384  1 i915
drm_kms_helper        172032  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   401408  6 drm_kms_helper,i915
video                  45056  2 int3406_thermal,i915
i2c_hid                20480  0
hid                   118784  2 i2c_hid,hid_generic
sdhci_acpi             16384  0
sdhci                  49152  1 sdhci_acpi
```

---

### Post by chili555 on 2018-11-10
May we see the result of:```
dmesg | grep -i sdio
```Thanks.

---

### Post by playgamemy on 2018-11-10
dmesg | grep -i sdio

```
[    3.793007] mmc0: new high speed SDIO card at address 0001
```

which likely is the sd card that I plugged into my laptop as storage

---

### Post by chili555 on 2018-11-11
Very interesting. I had hoped we'd see more about your wifi device which is also an SDIO device. The module that is loaded, r8723bs, is for SDIO devices:```

chili@T440p:~$ modinfo r8723bs
filename:       /lib/modules/4.18.0-10-generic/kernel/drivers/staging/rtl8723bs/r8723bs.ko
version:        v4.3.5.5_12290.20140916_BTCOEX20140507-4E40
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     5163DF8A4B772DE086A0F89
alias:          [COLOR="#FF0000"]sdio[/COLOR]:c*v024CdB723*
alias:          [COLOR="#FF0000"]sdio[/COLOR]:c*v024Cd0626*
alias:          [COLOR="#FF0000"]sdio[/COLOR]:c*v024Cd0623*
alias:          [COLOR="#FF0000"]sdio[/COLOR]:c*v024Cd0523*
alias:          acpi*:OBDA8723:*
depends:        cfg80211
staging:        Y
retpoline:      Y
intree:         Y
<snip>

```Notice that your wifi device also doesn't appear in lspci nor lsusb.

Any clues here?```
cat /var/log/syslog | grep -i sdio
```

Possibly discouraging news: [https://askubuntu.com/questions/1049547/problem-with-audio-device-es8316-and-bluetooth-r8723bs-ubuntu-18-04-installed-i#1068653](https://askubuntu.com/questions/1049547/problem-with-audio-device-es8316-and-bluetooth-r8723bs-ubuntu-18-04-installed-i#1068653)

> The r8723bs driver in the 18.04 staging area doesn't include bluetooth. 

---

### Post by playgamemy on 2018-11-12
cat /var/log/syslog | grep -i sdio
```
Nov 12 22:08:57 nick-Lenovo-ideapad-100S-11IBY kernel: [    3.741054] mmc0: new high speed SDIO card at address 0001
Nov 12 22:16:33 nick-Lenovo-ideapad-100S-11IBY kernel: [  465.966202] audit: type=1400 audit(1542023193.895:62): apparmor="DENIED" operation="open" profile="snap.chromium.chromium" name="/run/udev/data/+sdio:mmc0:0001:1" pid=1960 comm="TaskSchedulerFo" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov 12 22:42:30 nick-Lenovo-ideapad-100S-11IBY kernel: [    3.847149] mmc0: new high speed SDIO card at address 0001


```

see lshw which of course showed I have a wireless device but no info on the bus it use

sudo lshw -c netowrk

```
  *-network                 
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 60:6d:c7:91:e9:f5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723bs ip=192.168.1.107 multicast=yes wireless=IEEE 802.11bgn
```

keep in mind the default loaded driver was r8723, i moprobe it to r8723bs because I found a post saying the chip used on this device is r8723bs, but I have no way to confirm it (thought I can confirm this using lspci, lsusb or lshw, but none of this give me the information I need)

Maybe I can try to get the old driver from kernel 4.4-LTS? if so, can you guide me on where and how to do it?

(Sorry i did not subscribe to the post, sorry for a late reply, please don't abandon me :(

---

### Post by chili555 on 2018-11-12
> Maybe I can try to get the old driver from kernel 4.4-LTS? if so, can you guide me on where and how to do it?
I don't know of any way to simply do a surgical transplant; I think you'd need the entire 4.4.0-xx kernel and associated packages. I'm not sure it would reliably work even if you took that big backwards step.

Please see: [https://github.com/lwfinger/rtl8723bs_bt/issues/28](https://github.com/lwfinger/rtl8723bs_bt/issues/28)> I analyzed the commits on the r8723bs driver in staging tree, and it seems there is little to no work being done on it, sooo... So you are probably not going to see it anytime soon, unless you are C guru and willing to move throught the commit submitting hassle.

It is suggested, at the link above, that kernel version 4.19.1 has the fix. I f you are willing to try it, I am willing to help.

Could you use a USB bluetooth adapter?

---

### Post by playgamemy on 2018-11-12
USB dongle is always an option. For my own education purpose, however, i want to know how to identify the hardware on my computer, in this case, the model number of the wireless/Bluetooth chip.

Isn’t it a bit unusual that there are no info to be find with all the lspci lsusb and lshw commands? Are there anything else I can try in order to identify the piece of hardware?

---

### Post by playgamemy on 2018-11-13
After upgrading to kernel to 4.19.1 using ukuu, The bluetooth device is showing up but still fail to turn on. dmesg | grep blue indicate it has failed to load the required firmware, which is missing from the /lib/firmware/rtl_bt folder.

[https://github.com/lwfinger/rtl8723bs_bt](https://github.com/lwfinger/rtl8723bs_bt)

Cloned the git and compiled from above, and renamed the firmware and configuration files in /lib/firmware/rtl_bt/ correctly according to the error shown in dmesg | bluetooth

Finally, get the bluetooth workin, but when bluetooth is turned on wifi signal stability is greatly affected.... guess thats the caveat for now :(

---

