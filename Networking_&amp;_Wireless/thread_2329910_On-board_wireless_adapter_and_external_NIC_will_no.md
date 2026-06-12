---
title: "On-board wireless adapter and external NIC will not work in Linux"
date: 2016-07-06
forum: Networking &amp; Wireless
---

### Post by mmojunior on 2016-07-06
Never had this issue on other laptops. Just bought this Lenovo Thinkpad T61 and was getting it up and running. Won't let me connect to wifi with the PCI card or the USB AWUS036H external card i have. This is troubling. I will copy/paste any data i can to assist.

Output of iwconfig:
```
iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:on
          
eth0      no wireless extensions.


```

Output of rfkill:
```
 rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: yes
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```

Output from lsusb:
```
  lsusb
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

and finally the output from lsmod:
```
 lsmod
Module                  Size  Used by
fuse                   98304  3
rfcomm                 69632  0
bnep                   20480  0
nfnetlink_queue        20480  0
nfnetlink_log          20480  0
nfnetlink              16384  2 nfnetlink_log,nfnetlink_queue
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             516096  9 bnep,btbcm,btrtl,btusb,rfcomm,btintel
binfmt_misc            20480  1
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             188416  0
iTCO_wdt               16384  0
iTCO_vendor_support    16384  1 iTCO_wdt
arc4                   16384  4
rtl8192se              61440  0
rtl8187                61440  0
rtl_pci                28672  1 rtl8192se
eeprom_93cx6           16384  1 rtl8187
rtlwifi                77824  2 rtl_pci,rtl8192se
mac80211              638976  4 rtl8187,rtl_pci,rtlwifi,rtl8192se
cfg80211              573440  3 mac80211,rtl8187,rtlwifi
kvm                   561152  1 kvm_intel
joydev                 20480  0
intel_ips              20480  0
snd_hda_codec_hdmi     45056  1
thinkpad_acpi          86016  0
irqbypass              16384  1 kvm
snd_hda_codec_realtek    81920  1
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
jmb38x_ms              20480  0
nvram                  16384  1 thinkpad_acpi
memstick               20480  1 jmb38x_ms
rfkill                 24576  5 cfg80211,thinkpad_acpi,bluetooth
pcspkr                 16384  0
evdev                  24576  15
i2c_i801               20480  0
serio_raw              16384  0
wmi                    20480  0
sg                     32768  0
snd_hda_intel          36864  6
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
acpi_cpufreq           20480  1
snd_hda_core           81920  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_timer              32768  1 snd_pcm
battery                16384  0
tpm_tis                20480  0
i915                 1245184  13
video                  40960  2 i915,thinkpad_acpi
button                 16384  1 i915
drm_kms_helper        147456  1 i915
drm                   356352  10 i915,drm_kms_helper
tpm                    45056  1 tpm_tis
mei_me                 32768  0
mei                    94208  1 mei_me
lpc_ich                24576  0
mfd_core               16384  1 lpc_ich
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,thinkpad_acpi
soundcore              16384  1 snd
ac                     16384  0
i2c_algo_bit           16384  1 i915
shpchp                 36864  0
processor              36864  1 acpi_cpufreq
autofs4                40960  2
ext4                  593920  5
ecb                    16384  0
crc16                  16384  2 ext4,bluetooth
jbd2                  106496  1 ext4
crc32c_generic         16384  0
mbcache                16384  6 ext4
algif_skcipher         20480  0
af_alg                 16384  1 algif_skcipher
dm_crypt               24576  1
dm_mod                106496  18 dm_crypt
sr_mod                 24576  0
cdrom                  57344  1 sr_mod
sd_mod                 45056  3
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
crc32c_intel           24576  0
ghash_clmulni_intel    16384  0
jitterentropy_rng      16384  0
hmac                   16384  1
drbg                   24576  1
ansi_cprng             16384  0
aesni_intel           167936  3
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  4 ghash_clmulni_intel,aesni_intel,ablk_helper
ahci                   36864  2
libahci                32768  1 ahci
psmouse               126976  0
libata                233472  2 ahci,libahci
scsi_mod              229376  4 sg,libata,sd_mod,sr_mod
r8169                  81920  0
ehci_pci               16384  0
mii                    16384  1 r8169
sdhci_pci              28672  0
ehci_hcd               77824  1 ehci_pci
sdhci                  40960  1 sdhci_pci
mmc_core              126976  2 sdhci,sdhci_pci
usbcore               241664  4 btusb,rtl8187,ehci_hcd,ehci_pci
usb_common             16384  1 usbcore
thermal                20480  0
fjes                   28672  0

```

Thank you for all the help in advance. I can't unblock anything with rfkill and i'm really stumped on why this doesn't work.

---

### Post by mmojunior on 2016-07-06
Ok guys. Don't be like me and go all need mode trying to find out the darn solution when I noticed the switch on the side of my Lenovo for wifi was in the "off" position. FML. Sorry guys.

---

