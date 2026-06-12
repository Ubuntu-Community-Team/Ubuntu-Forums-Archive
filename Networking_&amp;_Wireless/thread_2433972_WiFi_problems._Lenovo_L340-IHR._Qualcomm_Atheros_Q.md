---
title: "WiFi problems. Lenovo L340-IHR. Qualcomm Atheros QCA9377"
date: 2019-12-28
forum: Networking &amp; Wireless
---

### Post by antlord92 on 2019-12-28
Hello! I've got a laptop Lenovo L340-IHR 5-6 months ago. The laptop has a couple of problems connection to a WiFi spot. I used ubuntu 19.04, now I'm using ubuntu 19.10 with Gnome DE. The problems happend with both of the versions. Also, I tried with a couple of routers (about 5) with different settings. Some of them are 5GHz some 2.4GHz.

It losses a connection sometimes. It's not a periodical event. Once it stayed connected the whole work day. It reconnects if I try to connect to another. In details:
1. I see that connection doesn't work. I try to load a web page, ping my gateway, see that ping can't send even a package for 10-15 seconds.
2. I choose "Select Network" option in my Gnome Shell user menu, get a window where I searching of networks for 20-30 seconds
3. Choose a network I don't have access to
4. Get a dialog window asks me a password, I close it and choose my network and get connected in 99% of such event.

Laptop doesn't see wifi adapeter at all. **iw dev** shows nothing, lspci doesn't list the adapter. I see messages **ath10k_pci 0000:07:00.0: could not init core (-110)** and **ath10k_pci 0000:07:00.0: could not probe fw (-110)**. I solve it reloading kernel module of the adapter. If it doesn't help me I reboot the laptop.

Laptop see adapter but doesn't see any WiFi spot. I see message **ath10k_pci 0000:07:00.0: Could not init core: -110** in dmesg. I solve it reloading the kernel module.

Adapter model: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter
Kernel modules: ath10k_pci, ath10k_core, ath
Kernel version: 5.3.0-24-generic

lspci -knn
 ```
00:00.0 Host bridge [0600]: Intel Corporation 8th Gen Core Processor Host Bridge/DRAM Registers [8086:3ec4] (rev 07)
    Subsystem: Lenovo 8th Gen Core Processor Host Bridge/DRAM Registers [17aa:3808]
    Kernel driver in use: skl_uncore
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) [8086:1901] (rev 07)
    Kernel driver in use: pcieport
00:02.0 VGA compatible controller [0300]: Intel Corporation UHD Graphics 630 (Mobile) [8086:3e9b]
    Subsystem: Lenovo UHD Graphics 630 (Mobile) [17aa:3a2e]
    Kernel driver in use: i915
    Kernel modules: i915
00:04.0 Signal processing controller [1180]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem [8086:1903] (rev 07)
    Subsystem: Lenovo Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem [17aa:3830]
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device
00:08.0 System peripheral [0880]: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model [8086:1911]
    Subsystem: Lenovo Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model [17aa:3866]
00:12.0 Signal processing controller [1180]: Intel Corporation Cannon Lake PCH Thermal Controller [8086:a379] (rev 10)
    Subsystem: Lenovo Cannon Lake PCH Thermal Controller [17aa:3804]
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal
00:14.0 USB controller [0c03]: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller [8086:a36d] (rev 10)
    Subsystem: Lenovo Cannon Lake PCH USB 3.1 xHCI Host Controller [17aa:3807]
    Kernel driver in use: xhci_hcd
00:14.2 RAM memory [0500]: Intel Corporation Cannon Lake PCH Shared SRAM [8086:a36f] (rev 10)
    Subsystem: Lenovo Cannon Lake PCH Shared SRAM [17aa:3804]
00:15.0 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #0 [8086:a368] (rev 10)
    Subsystem: Lenovo Cannon Lake PCH Serial IO I2C Controller [17aa:3805]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:15.1 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #1 [8086:a369] (rev 10)
    Subsystem: Lenovo Cannon Lake PCH Serial IO I2C Controller [17aa:380b]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:16.0 Communication controller [0780]: Intel Corporation Cannon Lake PCH HECI Controller [8086:a360] (rev 10)
    Subsystem: Lenovo Cannon Lake PCH HECI Controller [17aa:3811]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:17.0 SATA controller [0106]: Intel Corporation Cannon Lake Mobile PCH SATA AHCI Controller [8086:a353] (rev 10)
    Subsystem: Lenovo Cannon Lake Mobile PCH SATA AHCI Controller [17aa:3801]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1d.0 PCI bridge [0604]: Intel Corporation Cannon Lake PCH PCI Express Root Port #9 [8086:a330] (rev f0)
    Kernel driver in use: pcieport
00:1d.4 PCI bridge [0604]: Intel Corporation Cannon Lake PCH PCI Express Root Port #13 [8086:a334] (rev f0)
    Kernel driver in use: pcieport
00:1d.5 PCI bridge [0604]: Intel Corporation Cannon Lake PCH PCI Express Root Port #14 [8086:a335] (rev f0)
    Kernel driver in use: pcieport
00:1e.0 Communication controller [0780]: Intel Corporation Device [8086:a328] (rev 10)
    Subsystem: Lenovo Device [17aa:3810]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:a30d] (rev 10)
00:1f.3 Audio device [0403]: Intel Corporation Cannon Lake PCH cAVS [8086:a348] (rev 10)
    Subsystem: Lenovo Cannon Lake PCH cAVS [17aa:3815]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl, sof_pci_dev
00:1f.4 SMBus [0c05]: Intel Corporation Cannon Lake PCH SMBus Controller [8086:a323] (rev 10)
    Subsystem: Lenovo Cannon Lake PCH SMBus Controller [17aa:3816]
    Kernel driver in use: i801_smbus
    Kernel modules: i2c_i801
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller [8086:a324] (rev 10)
    Subsystem: Lenovo Cannon Lake PCH SPI Controller [17aa:3803]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1f91] (rev a1)
    Subsystem: Lenovo Device [17aa:3a2e]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:10fa] (rev a1)
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
06:00.0 Non-Volatile memory controller [0108]: Sandisk Corp Device [15b7:5005] (rev 01)
    Subsystem: Sandisk Corp Device [15b7:5005]
    Kernel driver in use: nvme
    Kernel modules: nvme
07:00.0 Network controller [0280]: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter [168c:0042] (rev 31)
    Subsystem: Lenovo QCA9377 802.11ac Wireless Network Adapter [17aa:0901]
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:38cf]
    Kernel driver in use: r8169
    Kernel modules: r8169

```

Installed kernel modules
```

Module                  Size  Used by
ccm                    20480  3
ath10k_pci             45056  0
ath10k_core           471040  1 ath10k_pci
ath                    36864  1 ath10k_core
mac80211              851968  1 ath10k_core
cfg80211              712704  3 ath,mac80211,ath10k_core
libarc4                16384  1 mac80211
cmac                   16384  1
rfcomm                 81920  16
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               487424  3 vboxpci,vboxnetadp,vboxnetflt
aufs                  262144  0
overlay               114688  0
bnep                   24576  2
binfmt_misc            24576  1
btusb                  57344  0
btrtl                  20480  1 btusb
btbcm                  16384  1 btusb
btintel                24576  1 btusb
bluetooth             581632  37 btrtl,btintel,btbcm,bnep,btusb,rfcomm
uvcvideo               98304  0
ecdh_generic           16384  2 bluetooth
ecc                    28672  1 ecdh_generic
x86_pkg_temp_thermal    20480  0
intel_powerclamp       20480  0
coretemp               20480  0
nvidia_uvm            843776  0
snd_hda_codec_hdmi     61440  2
kvm_intel             278528  0
nvidia_drm             49152  8
kvm                   651264  1 kvm_intel
snd_hda_codec_realtek   118784  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
nls_iso8859_1          16384  1
nvidia_modeset       1118208  9 nvidia_drm
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
irqbypass              16384  1 kvm
nvidia              19079168  426 nvidia_uvm,nvidia_modeset
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
aesni_intel           372736  4
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
sof_pci_dev            20480  0
snd_sof_intel_hda_common    73728  1 sof_pci_dev
snd_sof_intel_hda      20480  1 snd_sof_intel_hda_common
snd_sof_intel_byt      24576  1 sof_pci_dev
snd_sof_intel_ipc      20480  1 snd_sof_intel_byt
snd_sof               102400  4 snd_sof_intel_hda_common,snd_sof_intel_byt,snd_sof_intel_ipc,sof_pci_dev
snd_sof_xtensa_dsp     16384  1 sof_pci_dev
snd_soc_skl           106496  0
snd_soc_hdac_hda       24576  2 snd_sof_intel_hda_common,snd_soc_skl
snd_hda_ext_core       32768  4 snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_soc_skl,snd_sof_intel_hda
snd_soc_skl_ipc        65536  1 snd_soc_skl
snd_soc_sst_ipc        20480  1 snd_soc_skl_ipc
snd_soc_sst_dsp        36864  1 snd_soc_skl_ipc
snd_soc_acpi_intel_match    28672  3 snd_sof_intel_hda_common,sof_pci_dev,snd_soc_skl
snd_soc_acpi           16384  3 snd_soc_acpi_intel_match,sof_pci_dev,snd_soc_skl
snd_soc_core          241664  4 snd_sof,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_soc_skl
snd_compress           24576  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hda_intel          49152  8
snd_hda_codec         131072  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek,snd_soc_hdac_hda
snd_hda_core           90112  10 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_soc_skl,snd_sof_intel_hda
snd_hwdep              20480  1 snd_hda_codec
mei_hdcp               24576  0
snd_pcm               106496  10 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_sof,snd_sof_intel_hda_common,snd_soc_core,snd_soc_skl,snd_hda_core,snd_pcm_dmaengine
intel_rapl_msr         20480  0
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
intel_cstate           20480  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
i915                 1949696  4
snd_timer              36864  2 snd_seq,snd_pcm
intel_rapl_perf        20480  0
drm_kms_helper        184320  2 nvidia_drm,i915
input_leds             16384  0
wmi_bmof               16384  0
serio_raw              20480  0
drm                   491520  12 drm_kms_helper,nvidia_drm,i915
intel_wmi_thunderbolt    20480  0
snd                    86016  29 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
ipmi_devintf           20480  0
8250_dw                20480  0
ipmi_msghandler       102400  2 ipmi_devintf,nvidia
joydev                 28672  0
processor_thermal_device    20480  0
i2c_algo_bit           16384  1 i915
fb_sys_fops            16384  1 drm_kms_helper
intel_rapl_common      24576  2 intel_rapl_msr,processor_thermal_device
mei_me                 40960  1
syscopyarea            16384  1 drm_kms_helper
idma64                 20480  0
mei                   110592  3 mei_hdcp,mei_me
sysfillrect            16384  1 drm_kms_helper
virt_dma               20480  1 idma64
intel_soc_dts_iosf     20480  1 processor_thermal_device
soundcore              16384  1 snd
sysimgblt              16384  1 drm_kms_helper
intel_pch_thermal      16384  0
mac_hid                16384  0
ideapad_laptop         20480  0
int3403_thermal        16384  0
sparse_keymap          16384  1 ideapad_laptop
int340x_thermal_zone    16384  2 int3403_thermal,processor_thermal_device
int3400_thermal        20480  0
acpi_pad              184320  0
acpi_thermal_rel       16384  1 int3400_thermal
acpi_tad               16384  0
sch_fq_codel           20480  2
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
xfs                  1273856  2
libcrc32c              16384  1 xfs
hid_rmi                24576  0
rmi_core               81920  1 hid_rmi
videobuf2_vmalloc      20480  2 rmi_core,uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
videobuf2_v4l2         24576  2 rmi_core,uvcvideo
videobuf2_common       53248  3 rmi_core,videobuf2_v4l2,uvcvideo
videodev              208896  4 rmi_core,videobuf2_v4l2,uvcvideo,videobuf2_common
mc                     53248  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
hid_generic            16384  0
nvme                   40960  3
r8169                  81920  0
ahci                   40960  0
i2c_i801               32768  0
nvme_core             102400  5 nvme
intel_lpss_pci         20480  0
realtek                20480  1
i2c_hid                28672  0
libahci                32768  1 ahci
intel_lpss             16384  1 intel_lpss_pci
hid                   131072  3 i2c_hid,hid_generic,hid_rmi
wmi                    32768  3 intel_wmi_thunderbolt,wmi_bmof,ideapad_laptop
video                  49152  2 ideapad_laptop,i915
pinctrl_cannonlake     36864  0
pinctrl_intel          28672  1 pinctrl_cannonlake

```

I found on the internet threads where similar problems were fixed by using kernel modules from Debian, by changing firmware of the wifi adapter, by updating kernel. But the topic are irrelevant. They fixed their problems by the firmware I have out of the box, by the kernel that is older than mine.

Does somebody know how to fix it? Is this problem in the kernel module or in the firmware? Might be I can just configure something.

P.S. I didn't see such problems with Windows 10 and the laptop. So I suppose it's not a hardware-related problem

P.P.S. I attach kernel logs
[http://vpaste.net/YsXE3](http://vpaste.net/YsXE3) - wifi adapter is not detected
[http://vpaste.net/aCEDE](http://vpaste.net/aCEDE) - wifi adapter detected but not connected
[http://vpaste.net/Byaai](http://vpaste.net/Byaai) - wifi adapter connected but after kernel reloading

---

### Post by antlord92 on 2020-01-08
Any idea? Is the issue a bug?

---

### Post by mörgæs on 2020-01-09
You might have better luck in the networking forum.
If you click *report* you can ask a moderator to move your thread.

---

### Post by antlord92 on 2020-01-17
I've inspected code of the driver both if the error I pointed out are raises if the driver unable to get some data from firmware. Code -110 means timeout. As far as I see the firmware is available on the internet [https://wireless.wiki.kernel.org/en/users/drivers/ath10k/firmware](https://wireless.wiki.kernel.org/en/users/drivers/ath10k/firmware). Looks like the firmware is proprietary software and I have no idea how to fix it.

---

### Post by jeremy31 on 2020-01-17
Try ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```
That will keep Network Manager from enabling wifi power management as that kernel module doesn't handle it well

---

### Post by antlord92 on 2020-01-18
I've done it already. Also, I use TLP for power management. I'm not sure if it doesn't affect WiFi. Maybe the clue in its config [http://vpaste.net/UB7a9](http://vpaste.net/UB7a9)

---

### Post by jeremy31 on 2020-01-18
You should see how to keep TLP from affecting wifi, likely something in a conf file

---

### Post by antlord92 on 2020-01-21
I removed TLP but I get the errors still. Does it make sense to send a bug report to atheros driver developers?

---

### Post by CorporateMonkey on 2020-01-21
I have the same network card and also have some problems with it.  Basically it doesn't show half of the available WiFi hot-spots around  me. But, when I boot in windows on the same laptop I can see all hot-spots  normally.

---

### Post by CorporateMonkey on 2020-01-21
I was thinking maybe our cards are more compatible with ath9k drivers instead of ath10k, but I am a big noob and I don't know how to change the drivers on linux.

---

### Post by jeremy31 on 2020-01-21
The wifi card may not be seated correctly in the motherboard if it sometimes doesn't show in lspci results

---

### Post by antlord92 on 2020-01-21
[INDENT]                     The wifi card may not be seated correctly in the motherboard if it sometimes doesn't show in lspci results                 [/INDENT]
            
                         


It was working perfect with windows for two weeks. The problems started with Ubuntu right after installation.

---

