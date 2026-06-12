---
title: "New d-link lan card dge-528t not working"
date: 2019-06-22
forum: Networking &amp; Wireless
---

### Post by AnupamMitra on 2019-06-22
My O/S in desktop is UBUNTU 19.04 64 bit. Due to lightning, the embedded LAN Card in the M/B became ineffective. Therefore, I purchased the above mentioned LAN card. My source of network connection is "wired". In the NETWORK of SETTINGS it is shown that D-Link System Ethernet is "connected". But in fact I'm not getting any connection. Need help.

---

### Post by praseodym on 2019-06-22
Please show
```

lspci -nnk
lsmod
```

---

### Post by AnupamMitra on 2019-06-22
> **praseodym said:**
> Please show
```

lspci -nnk
lsmod
```

Thanks. I'm giving the output hereunder.

```

[FONT=Times]anupam@anupam-ubuntu:~$ lspci -nnk[/FONT]
[FONT=Times]00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers [8086:190f] (rev 07)[/FONT]
[FONT=Times]    Subsystem: Gigabyte Technology Co., Ltd Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers [1458:5000][/FONT]
[FONT=Times]    Kernel driver in use: skl_uncore[/FONT]
[FONT=Times]00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 510 [8086:1902] (rev 06)[/FONT]
[FONT=Times]    Subsystem: Gigabyte Technology Co., Ltd HD Graphics 510 [1458:d000][/FONT]
[FONT=Times]    Kernel driver in use: i915[/FONT]
[FONT=Times]    Kernel modules: i915[/FONT]
[FONT=Times]00:14.0 USB controller [0c03]: Intel Corporation 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller [8086:a12f] (rev 31)[/FONT]
[FONT=Times]    Subsystem: Gigabyte Technology Co., Ltd 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller [1458:5007][/FONT]
[FONT=Times]    Kernel driver in use: xhci_hcd[/FONT]
[FONT=Times]00:14.2 Signal processing controller [1180]: Intel Corporation 100 Series/C230 Series Chipset Family Thermal Subsystem [8086:a131] (rev 31)[/FONT]
[FONT=Times]    Subsystem: Gigabyte Technology Co., Ltd 100 Series/C230 Series Chipset Family Thermal Subsystem [1458:8888][/FONT]
[FONT=Times]    Kernel driver in use: intel_pch_thermal[/FONT]
[FONT=Times]    Kernel modules: intel_pch_thermal[/FONT]
[FONT=Times]00:16.0 Communication controller [0780]: Intel Corporation 100 Series/C230 Series Chipset Family MEI Controller #1 [8086:a13a] (rev 31)[/FONT]
[FONT=Times]    Subsystem: Gigabyte Technology Co., Ltd 100 Series/C230 Series Chipset Family MEI Controller [1458:1c3a][/FONT]
[FONT=Times]    Kernel driver in use: mei_me[/FONT]
[FONT=Times]    Kernel modules: mei_me[/FONT]
[FONT=Times]00:17.0 SATA controller [0106]: Intel Corporation Q170/Q150/B150/H170/H110/Z170/CM236 Chipset SATA Controller [AHCI Mode] [8086:a102] (rev 31)[/FONT]
[FONT=Times]    Subsystem: Gigabyte Technology Co., Ltd Q170/Q150/B150/H170/H110/Z170/CM236 Chipset SATA Controller [AHCI Mode] [1458:b005][/FONT]
[FONT=Times]    Kernel driver in use: ahci[/FONT]
[FONT=Times]    Kernel modules: ahci[/FONT]
[FONT=Times]00:1c.0 PCI bridge [0604]: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #5 [8086:a114] (rev f1)[/FONT]
[FONT=Times]    Kernel driver in use: pcieport[/FONT]
[FONT=Times]00:1c.5 PCI bridge [0604]: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #6 [8086:a115] (rev f1)[/FONT]
[FONT=Times]    Kernel driver in use: pcieport[/FONT]
[FONT=Times]00:1d.0 PCI bridge [0604]: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #9 [8086:a118] (rev f1)[/FONT]
[FONT=Times]    Kernel driver in use: pcieport[/FONT]
[FONT=Times]00:1f.0 ISA bridge [0601]: Intel Corporation H110 Chipset LPC/eSPI Controller [8086:a143] (rev 31)[/FONT]
[FONT=Times]    Subsystem: Gigabyte Technology Co., Ltd H110 Chipset LPC/eSPI Controller [1458:5001][/FONT]
[FONT=Times]00:1f.2 Memory controller [0580]: Intel Corporation 100 Series/C230 Series Chipset Family Power Management Controller [8086:a121] (rev 31)[/FONT]
[FONT=Times]    Subsystem: Gigabyte Technology Co., Ltd 100 Series/C230 Series Chipset Family Power Management Controller [1458:5001][/FONT]
[FONT=Times]00:1f.3 Audio device [0403]: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller [8086:a170] (rev 31)[/FONT]
[FONT=Times]    Subsystem: Gigabyte Technology Co., Ltd 100 Series/C230 Series Chipset Family HD Audio Controller [1458:a182][/FONT]
[FONT=Times]    Kernel driver in use: snd_hda_intel[/FONT]
[FONT=Times]    Kernel modules: snd_hda_intel[/FONT]
[FONT=Times]00:1f.4 SMBus [0c05]: Intel Corporation 100 Series/C230 Series Chipset Family SMBus [8086:a123] (rev 31)[/FONT]
[FONT=Times]    Subsystem: Gigabyte Technology Co., Ltd 100 Series/C230 Series Chipset Family SMBus [1458:5001][/FONT]
[FONT=Times]    Kernel driver in use: i801_smbus[/FONT]
[FONT=Times]    Kernel modules: i2c_i801[/FONT]
[FONT=Times]01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)[/FONT]
[FONT=Times]    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000][/FONT]
[FONT=Times]    Kernel driver in use: r8169[/FONT]
[FONT=Times]    Kernel modules: r8169[/FONT]
[FONT=Times]02:00.0 PCI bridge [0604]: Integrated Technology Express, Inc. IT8892E PCIe to PCI Bridge [1283:8892] (rev 41)[/FONT]
[FONT=Times]03:01.0 Ethernet controller [0200]: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300] (rev 10)[/FONT]
[FONT=Times]    Subsystem: D-Link System Inc DGE-528T PCI Gigabit Ethernet Adapter [1186:4300][/FONT]
[FONT=Times]    Kernel driver in use: r8169[/FONT]
[FONT=Times]    Kernel modules: r8169[/FONT]
[FONT=Times]anupam@anupam-ubuntu:~$ lsmod[/FONT]
[FONT=Times]Module                  Size  Used by[/FONT]
[FONT=Times]pci_stub               16384  1[/FONT]
[FONT=Times]vboxpci                24576  0[/FONT]
[FONT=Times]vboxnetadp             28672  0[/FONT]
[FONT=Times]vboxnetflt             28672  0[/FONT]
[FONT=Times]vboxdrv               483328  4 vboxpci,vboxnetadp,vboxnetflt[/FONT]
[FONT=Times]nls_iso8859_1          16384  1[/FONT]
[FONT=Times]snd_hda_codec_hdmi     53248  1[/FONT]
[FONT=Times]snd_hda_codec_realtek   114688  1[/FONT]
[FONT=Times]snd_hda_codec_generic    77824  1 snd_hda_codec_realtek[/FONT]
[FONT=Times]ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek[/FONT]
[FONT=Times]i915                 1814528  13[/FONT]
[FONT=Times]kvmgt                  28672  0[/FONT]
[FONT=Times]vfio_mdev              16384  0[/FONT]
[FONT=Times]mdev                   24576  2 kvmgt,vfio_mdev[/FONT]
[FONT=Times]vfio_iommu_type1       28672  0[/FONT]
[FONT=Times]vfio                   32768  3 kvmgt,vfio_mdev,vfio_iommu_type1[/FONT]
[FONT=Times]snd_hda_intel          40960  2[/FONT]
[FONT=Times]snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek[/FONT]
[FONT=Times]drm_kms_helper        180224  1 i915[/FONT]
[FONT=Times]snd_hda_core           86016  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek[/FONT]
[FONT=Times]drm                   475136  7 drm_kms_helper,i915[/FONT]
[FONT=Times]snd_hwdep              20480  1 snd_hda_codec[/FONT]
[FONT=Times]snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core[/FONT]
[FONT=Times]intel_rapl             24576  0[/FONT]
[FONT=Times]input_leds             16384  0[/FONT]
[FONT=Times]x86_pkg_temp_thermal    20480  0[/FONT]
[FONT=Times]intel_powerclamp       20480  0[/FONT]
[FONT=Times]i2c_algo_bit           16384  1 i915[/FONT]
[FONT=Times]snd_seq_midi           20480  0[/FONT]
[FONT=Times]snd_seq_midi_event     16384  1 snd_seq_midi[/FONT]
[FONT=Times]fb_sys_fops            16384  1 drm_kms_helper[/FONT]
[FONT=Times]snd_rawmidi            36864  1 snd_seq_midi[/FONT]
[FONT=Times]syscopyarea            16384  1 drm_kms_helper[/FONT]
[FONT=Times]sysfillrect            16384  1 drm_kms_helper[/FONT]
[FONT=Times]coretemp               20480  0[/FONT]
[FONT=Times]sysimgblt              16384  1 drm_kms_helper[/FONT]
[FONT=Times]snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event[/FONT]
[FONT=Times]kvm_intel             241664  0[/FONT]
[FONT=Times]kvm                   626688  2 kvmgt,kvm_intel[/FONT]
[FONT=Times]irqbypass              16384  1 kvm[/FONT]
[FONT=Times]snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi[/FONT]
[FONT=Times]snd_timer              36864  2 snd_seq,snd_pcm[/FONT]
[FONT=Times]crct10dif_pclmul       16384  1[/FONT]
[FONT=Times]crc32_pclmul           16384  0[/FONT]
[FONT=Times]ghash_clmulni_intel    16384  0[/FONT]
[FONT=Times]mei_me                 40960  0[/FONT]
[FONT=Times]snd                    81920  15 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi[/FONT]
[FONT=Times]aesni_intel           372736  0[/FONT]
[FONT=Times]mei                   102400  1 mei_me[/FONT]
[FONT=Times]soundcore              16384  1 snd[/FONT]
[FONT=Times]intel_pch_thermal      16384  0[/FONT]
[FONT=Times]aes_x86_64             20480  1 aesni_intel[/FONT]
[FONT=Times]crypto_simd            16384  1 aesni_intel[/FONT]
[FONT=Times]cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel[/FONT]
[FONT=Times]glue_helper            16384  1 aesni_intel[/FONT]
[FONT=Times]acpi_pad              184320  0[/FONT]
[FONT=Times]intel_cstate           20480  0[/FONT]
[FONT=Times]intel_rapl_perf        16384  0[/FONT]
[FONT=Times]intel_wmi_thunderbolt    20480  0[/FONT]
[FONT=Times]mac_hid                16384  0[/FONT]
[FONT=Times]sch_fq_codel           20480  3[/FONT]
[FONT=Times]parport_pc             40960  1[/FONT]
[FONT=Times]ppdev                  24576  0[/FONT]
[FONT=Times]lp                     20480  0[/FONT]
[FONT=Times]parport                53248  3 parport_pc,lp,ppdev[/FONT]
[FONT=Times]ip_tables              28672  0[/FONT]
[FONT=Times]x_tables               40960  1 ip_tables[/FONT]
[FONT=Times]autofs4                45056  2[/FONT]
[FONT=Times]hid_generic            16384  0[/FONT]
[FONT=Times]usbhid                 53248  0[/FONT]
[FONT=Times]hid                   126976  2 usbhid,hid_generic[/FONT]
[FONT=Times]i2c_i801               32768  0[/FONT]
[FONT=Times]ahci                   40960  5[/FONT]
[FONT=Times]r8169                  81920  0[/FONT]
[FONT=Times]libahci                32768  1 ahci[/FONT]
[FONT=Times]realtek                20480  1[/FONT]
[FONT=Times]wmi                    28672  1 intel_wmi_thunderbolt[/FONT]
[FONT=Times]video                  45056  1 i915[/FONT]
[FONT=Times]anupam@anupam-ubuntu:~$ [/FONT]

```

---

### Post by praseodym on 2019-06-22
```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
    Kernel driver in use: [COLOR="#FF0000"]r8169[/COLOR]
    Kernel modules: r8169
...
03:01.0 Ethernet controller [0200]: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300] (rev 10)
    Subsystem: D-Link System Inc DGE-528T PCI Gigabit Ethernet Adapter [1186:4300]
    Kernel driver in use: [COLOR="#FF0000"]r8169[/COLOR]
    Kernel modules: r8169
```
Ok, now you have 2 cards using the same driver. We can change the driver for both cards shown via
```

sudo apt-get install r8168-dkms dkms build-essential
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist-Realtek.conf
```
Reboot and show
```

lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by AnupamMitra on 2019-06-22
> **praseodym said:**
> ```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
    Kernel driver in use: [COLOR=#FF0000]r8169[/COLOR]
    Kernel modules: r8169
...
03:01.0 Ethernet controller [0200]: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300] (rev 10)
    Subsystem: D-Link System Inc DGE-528T PCI Gigabit Ethernet Adapter [1186:4300]
    Kernel driver in use: [COLOR=#FF0000]r8169[/COLOR]
    Kernel modules: r8169
```
Ok, now you have 2 cards using the same driver. We can change the driver for both cards shown via
```

sudo apt-get install r8168-dkms dkms build-essential
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist-Realtek.conf
```
Reboot and show
```

lspci -nnk | grep -iA2 net
lsmod
```

Thanks for your cooperation. The result is as under. 

```

anupam@anupam-ubuntu:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
    Kernel driver in use: r8169
    Kernel modules: r8168
--
03:01.0 Ethernet controller [0200]: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300] (rev 10)
    Subsystem: D-Link System Inc DGE-528T PCI Gigabit Ethernet Adapter [1186:4300]
    Kernel driver in use: r8169
    Kernel modules: r8169
anupam@anupam-ubuntu:~$ lsmod
Module                  Size  Used by
r8168                 540672  0
nls_utf8               16384  0
udf                    90112  0
crc_itu_t              16384  1 udf
uas                    24576  0
usb_storage            69632  1 uas
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               483328  3 vboxpci,vboxnetadp,vboxnetflt
nls_iso8859_1          16384  1
snd_hda_codec_hdmi     53248  1
snd_hda_codec_realtek   114688  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
i915                 1814528  10
kvmgt                  28672  0
vfio_mdev              16384  0
mdev                   24576  2 kvmgt,vfio_mdev
vfio_iommu_type1       28672  0
vfio                   32768  3 kvmgt,vfio_mdev,vfio_iommu_type1
snd_hda_intel          40960  2
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
drm_kms_helper        180224  1 i915
snd_hda_core           86016  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
drm                   475136  5 drm_kms_helper,i915
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
intel_rapl             24576  0
input_leds             16384  0
x86_pkg_temp_thermal    20480  0
intel_powerclamp       20480  0
i2c_algo_bit           16384  1 i915
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
fb_sys_fops            16384  1 drm_kms_helper
snd_rawmidi            36864  1 snd_seq_midi
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
coretemp               20480  0
sysimgblt              16384  1 drm_kms_helper
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
kvm_intel             241664  0
kvm                   626688  2 kvmgt,kvm_intel
irqbypass              16384  1 kvm
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              36864  2 snd_seq,snd_pcm
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
mei_me                 40960  0
snd                    81920  15 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
aesni_intel           372736  0
mei                   102400  1 mei_me
soundcore              16384  1 snd
intel_pch_thermal      16384  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
glue_helper            16384  1 aesni_intel
acpi_pad              184320  0
intel_cstate           20480  0
intel_rapl_perf        16384  0
intel_wmi_thunderbolt    20480  0
mac_hid                16384  0
sch_fq_codel           20480  3
parport_pc             40960  1
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
usbhid                 53248  0
hid                   126976  2 usbhid,hid_generic
i2c_i801               32768  0
ahci                   40960  4
r8169                  81920  0
libahci                32768  1 ahci
realtek                20480  1
wmi                    28672  1 intel_wmi_thunderbolt
video                  45056  1 i915
anupam@anupam-ubuntu:~$ 

```

Hope, now it stands clinched. Isn't?

---

### Post by praseodym on 2019-06-22
That looks good. Does it work?

I am wondering why it loads both drivers as bot device IDs are included in both drivers, respectively. This is why we cannot load the driver after another.

---

### Post by praseodym on 2019-06-22
Or, can we?! If its not working try

```
sudo modprobe -rfv r8168 r8169
sudo modprobe -v r8168
lspci -nnk | grep -iA2 net
sudo modprobe -v r8169
lspci -nnk | grep -iA2 net
```

---

### Post by AnupamMitra on 2019-06-22
> **praseodym said:**
> Or, can we?! If its not working try

```
sudo modprobe -rfv r8168 r8169
sudo modprobe -v r8168
lspci -nnk | grep -iA2 net
sudo modprobe -v r8169
lspci -nnk | grep -iA2 net
```

Now it is working. Even though I used the above to put it straight.

```

anupam@anupam-ubuntu:~$ sudo modprobe -rfv r8168 r8169
[sudo] password for anupam: 
rmmod r8168
rmmod r8169
rmmod realtek
anupam@anupam-ubuntu:~$ sudo modprobe -v r8168
insmod /lib/modules/5.0.0-16-generic/updates/dkms/r8168.ko 
anupam@anupam-ubuntu:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
    Kernel driver in use: r8168
    Kernel modules: r8168
--
03:01.0 Ethernet controller [0200]: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300] (rev 10)
    Subsystem: D-Link System Inc DGE-528T PCI Gigabit Ethernet Adapter [1186:4300]
    Kernel modules: r8169
anupam@anupam-ubuntu:~$ sudo modprobe -v r8169
insmod /lib/modules/5.0.0-16-generic/kernel/drivers/net/phy/realtek.ko 
insmod /lib/modules/5.0.0-16-generic/kernel/drivers/net/ethernet/realtek/r8169.ko 
anupam@anupam-ubuntu:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
    Kernel driver in use: r8168
    Kernel modules: r8168
--
03:01.0 Ethernet controller [0200]: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300] (rev 10)
    Subsystem: D-Link System Inc DGE-528T PCI Gigabit Ethernet Adapter [1186:4300]
    Kernel driver in use: r8169
    Kernel modules: r8169
anupam@anupam-ubuntu:~$ 

```

Thanks for taking pains for me!

---

### Post by AnupamMitra on 2019-06-23
> **AnupamMitra said:**
> Now it is working. Even though I used the above to put it straight.

```

anupam@anupam-ubuntu:~$ sudo modprobe -rfv r8168 r8169
[sudo] password for anupam: 
rmmod r8168
rmmod r8169
rmmod realtek
anupam@anupam-ubuntu:~$ sudo modprobe -v r8168
insmod /lib/modules/5.0.0-16-generic/updates/dkms/r8168.ko 
anupam@anupam-ubuntu:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
    Kernel driver in use: r8168
    Kernel modules: r8168
--
03:01.0 Ethernet controller [0200]: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300] (rev 10)
    Subsystem: D-Link System Inc DGE-528T PCI Gigabit Ethernet Adapter [1186:4300]
    Kernel modules: r8169
anupam@anupam-ubuntu:~$ sudo modprobe -v r8169
insmod /lib/modules/5.0.0-16-generic/kernel/drivers/net/phy/realtek.ko 
insmod /lib/modules/5.0.0-16-generic/kernel/drivers/net/ethernet/realtek/r8169.ko 
anupam@anupam-ubuntu:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
    Kernel driver in use: r8168
    Kernel modules: r8168
--
03:01.0 Ethernet controller [0200]: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300] (rev 10)
    Subsystem: D-Link System Inc DGE-528T PCI Gigabit Ethernet Adapter [1186:4300]
    Kernel driver in use: r8169
    Kernel modules: r8169
anupam@anupam-ubuntu:~$ 

```

Thanks for taking pains for me!

@ Praseodym - Though I reported you yesterday that the matter was okay and the problem could be solved, but since today the situation is worst. Yesterday I mentioned that in NETWORK of SETTINGS D-Link System Ethernet was shown "connected", but today it is not showing anything about the D-Link LAN CARD.

May I seek your advice as what to do to restore the internet connection?

---

### Post by praseodym on 2019-06-23
Please run the wireless script from the sticky thread and show the outputs. Can you activate LAN in your BIOS/UEFI?

---

