---
title: "Wireless driver ndiswrapper issues"
date: 2019-02-23
forum: Networking &amp; Wireless
---

### Post by 99schwenk on 2019-02-23
I installed ubuntu 18.04 as a dual boot with windows 10. I keep getting booted off of the wifi network. I experienced the same problem with windows 10, but a simple driver update fixed the issue. Would using ndiswrapper to update my drivers in ubuntu fix the problem again? If so, I can't find any relevant information about installing windows drivers for 18.04 with ndiswrapper. If not, what should I do? I have already tried installing my current windows wireless drivers using ndiswrapper to copy my inf files. It doesnt seem to have worked, but I did not get a confirmation or an error message.

---

### Post by chili555 on 2019-02-23
ndiswrapper is old and not well supported. I haven't seen it work at all in many years. Moreover, it requires Windows XP inf and sys files which are generally not available. From *man ndiswrapper:*> ndiswrapper is two parts: user space tool that is used to install Windows XP drivers and kernel module to load the Windows XP drivers. Both are called ndiswrapper. > I keep getting booted off of the wifi network. I experienced the same problem with windows 10, Doesn't that suggest that the problem might actually be with your network? What does this tell us about your network?```
sudo iwlist scan
```Please redact the MAC address like this:```

wlp3s0    Scan completed :
          Cell 01 - Address: [COLOR="#FF0000"]xxxxxx[/COLOR]
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"GBR5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000245e05ff595
                    Extra: Last beacon: 468ms ago
                    IE: Unknown: <snip>
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


```

---

### Post by 99schwenk on 2019-02-24
I have another laptop which has never had issues with the network. I believe it was either the card or the drivers with the issue. Here is the report:

wlp2s0    Scan completed :
          Cell 01 - Address: xxxxxxxx
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002450e39e64
                    Extra: Last beacon: 756ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0706555349010B24
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A2D0803FEFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 7F080410000200000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported

---

### Post by praseodym on 2019-02-24
Without knowledge on the hardware, its difficult...Lets see the outputs of
```

lspci -nnk
lsusb
lsmod
iwconfig
```

---

### Post by chili555 on 2019-02-24
Eduroam? Eduroam, you say? Please check here: [https://askubuntu.com/questions/841620/my-ubuntu-16-04-keeps-disconnecting-from-the-wi-fi-eduroam-why/841624#841624](https://askubuntu.com/questions/841620/my-ubuntu-16-04-keeps-disconnecting-from-the-wi-fi-eduroam-why/841624#841624)

---

### Post by 99schwenk on 2019-02-25
chili555: when I follow those instructions I get a message "activation of network connection failed"

---

### Post by 99schwenk on 2019-02-25
```
caleb@caleb-Aspier-XXXX:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers [8086:1904] (rev 08)
	Subsystem: Acer Incorporated [ALI] Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers [1025:0975]
	Kernel driver in use: skl_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation Skylake GT2 [HD Graphics 520] [8086:1916] (rev 07)
	Subsystem: Acer Incorporated [ALI] Skylake GT2 [HD Graphics 520] [1025:0975]
	Kernel driver in use: i915
	Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller [8086:9d2f] (rev 21)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-LP USB 3.0 xHCI Controller [1025:0975]
	Kernel driver in use: xhci_hcd
00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Thermal subsystem [8086:9d31] (rev 21)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-LP Thermal subsystem [1025:0975]
	Kernel driver in use: intel_pch_thermal
	Kernel modules: intel_pch_thermal
00:15.0 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 [8086:9d60] (rev 21)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-LP Serial IO I2C Controller [1025:0975]
	Kernel driver in use: intel-lpss
	Kernel modules: intel_lpss_pci
00:15.1 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 [8086:9d61] (rev 21)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-LP Serial IO I2C Controller [1025:0975]
	Kernel driver in use: intel-lpss
	Kernel modules: intel_lpss_pci
00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-LP CSME HECI #1 [8086:9d3a] (rev 21)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-LP CSME HECI [1025:0975]
	Kernel driver in use: mei_me
	Kernel modules: mei_me
00:17.0 SATA controller [0106]: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] [8086:9d03] (rev 21)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-LP SATA Controller [AHCI mode] [1025:0975]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1c.0 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 [8086:9d14] (rev f1)
	Kernel driver in use: pcieport
00:1c.5 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 [8086:9d15] (rev f1)
	Kernel driver in use: pcieport
00:1f.0 ISA bridge [0601]: Intel Corporation Sunrise Point-LP LPC Controller [8086:9d48] (rev 21)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-LP LPC Controller [1025:0975]
00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-LP PMC [8086:9d21] (rev 21)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-LP PMC [1025:0975]
00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-LP HD Audio [8086:9d70] (rev 21)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-LP HD Audio [1025:0975]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel, snd_soc_skl
00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-LP SMBus [8086:9d23] (rev 21)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-LP SMBus [1025:0975]
	Kernel modules: i2c_i801
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader [10ec:5287] (rev 01)
	Subsystem: Acer Incorporated [ALI] RTL8411B PCI Express Card Reader [1025:0975]
	Kernel driver in use: rtsx_pci
	Kernel modules: rtsx_pci
01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
	Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:0975]
	Kernel driver in use: r8169
	Kernel modules: r8169
02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5010]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi
caleb@caleb-Aspier-XXXX:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:57cc Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0a2a Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
caleb@caleb-Aspier-XXXX:~$ lsmod
Module                  Size  Used by
rfcomm                 77824  4
cmac                   16384  1
bnep                   20480  2
nls_iso8859_1          16384  1
joydev                 24576  0
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek   106496  1
snd_soc_skl           102400  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_soc_skl_ipc        61440  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        32768  1 snd_soc_skl_ipc
snd_hda_ext_core       24576  1 snd_soc_skl
snd_soc_acpi           16384  1 snd_soc_skl
hid_multitouch         20480  0
snd_soc_core          229376  1 snd_soc_skl
hid_generic            16384  0
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hda_intel          40960  6
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           81920  7 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_soc_skl
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  8 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_soc_core,snd_soc_skl,snd_hda_core,snd_pcm_dmaengine
arc4                   16384  2
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
snd_seq_midi           16384  0
coretemp               16384  0
kvm_intel             208896  0
snd_seq_midi_event     16384  1 snd_seq_midi
kvm                   626688  1 kvm_intel
snd_rawmidi            32768  1 snd_seq_midi
iwlmvm                376832  0
irqbypass              16384  1 kvm
mac80211              802816  1 iwlmvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
aesni_intel           200704  2
aes_x86_64             20480  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
crypto_simd            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
iwlwifi               299008  1 iwlmvm
glue_helper            16384  1 aesni_intel
snd_timer              32768  2 snd_seq,snd_pcm
intel_cstate           20480  0
intel_wmi_thunderbolt    16384  0
intel_rapl_perf        16384  0
uvcvideo               94208  0
videobuf2_vmalloc      16384  1 uvcvideo
input_leds             16384  0
videobuf2_memops       16384  1 videobuf2_vmalloc
serio_raw              16384  0
videobuf2_v4l2         24576  1 uvcvideo
snd                    81920  25 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
videobuf2_common       40960  2 videobuf2_v4l2,uvcvideo
btusb                  45056  0
wmi_bmof               16384  0
acer_wmi               20480  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
videodev              188416  3 videobuf2_v4l2,uvcvideo,videobuf2_common
btintel                20480  1 btusb
rtsx_pci_ms            20480  0
bluetooth             552960  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm
media                  40960  2 videodev,uvcvideo
soundcore              16384  1 snd
cfg80211              667648  3 iwlmvm,iwlwifi,mac80211
idma64                 20480  0
virt_dma               16384  1 idma64
memstick               16384  1 rtsx_pci_ms
mei_me                 40960  0
ecdh_generic           24576  2 bluetooth
mei                    98304  1 mei_me
intel_pch_thermal      16384  0
intel_lpss_pci         20480  0
intel_lpss             16384  1 intel_lpss_pci
intel_vbtn             16384  0
sparse_keymap          16384  2 acer_wmi,intel_vbtn
acpi_pad              180224  0
mac_hid                16384  0
sch_fq_codel           20480  6
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
i915                 1740800  21
i2c_algo_bit           16384  1 i915
drm_kms_helper        172032  1 i915
syscopyarea            16384  1 drm_kms_helper
rtsx_pci_sdmmc         24576  0
sysfillrect            16384  1 drm_kms_helper
r8169                  86016  0
sysimgblt              16384  1 drm_kms_helper
rtsx_pci               65536  2 rtsx_pci_sdmmc,rtsx_pci_ms
mii                    16384  1 r8169
fb_sys_fops            16384  1 drm_kms_helper
drm                   458752  15 drm_kms_helper,i915
ahci                   40960  2
libahci                32768  1 ahci
i2c_hid                20480  0
hid                   122880  3 i2c_hid,hid_multitouch,hid_generic
wmi                    24576  3 intel_wmi_thunderbolt,acer_wmi,wmi_bmof
video                  45056  2 acer_wmi,i915
pinctrl_sunrisepoint    28672  0
pinctrl_intel          20480  1 pinctrl_sunrisepoint
caleb@caleb-Aspier-XXXX:~$ iwconfig
lo        no wireless extensions.


enp1s0f1  no wireless extensions.


wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
caleb@caleb-Aspier-XXXX:~$
```

---

### Post by wildmanne39 on 2019-02-25
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by chili555 on 2019-02-26
Are you sure that you bound the wifi to the nearest, strongest instance of eduroam? What format did you use in Network Manager? It should be in the form of A8:D7:19:41:54:ED, not a8:d7:19:41:54:ed and not a8d7194154ed. Please proofread and double-check.

---

