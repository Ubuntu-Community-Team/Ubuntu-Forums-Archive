---
title: "Xubuntu 18.04 weak wifi signal"
date: 2019-05-01
forum: Networking &amp; Wireless
---

### Post by easy3232 on 2019-05-01
Hello, I bought a notebook, but for some reason it has a very weak wifi signal.

I understand that the WIFI module is connected via USB. In a tray in network manager it is written that rtl8723be driver is used.

I tried to specify the number of antennas for the adapter, but the network state did not react at all. It didn't even reboot.

Tried the instructions to compile driver from here [https://github.com/lwfinger/rtlwifi_new/](https://github.com/lwfinger/rtlwifi_new/)

Other notebook, phone and tablet work fine.

Please help!

ps xubuntu 18.04

```
easy@easy-notebook-d:~$ sudo modprobe -rv rtl8723bermmod rtl8723be
rmmod rtl_pci
rmmod rtl8723_common
rmmod btcoexist
rmmod rtlwifi
rmmod mac80211
easy@easy-notebook-d:~$ sudo modprobe -v rtl8723be ant_sel=1
insmod /lib/modules/4.18.0-18-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.18.0-18-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko 
insmod /lib/modules/4.18.0-18-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko 
insmod /lib/modules/4.18.0-18-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723com/rtl8723-common.ko 
insmod /lib/modules/4.18.0-18-generic/kernel/drivers/net/wireless/realtek/rtlwifi/btcoexist/btcoexist.ko 
insmod /lib/modules/4.18.0-18-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko ant_sel=1
```

```
easy@easy-notebook-d:~$ lspci
00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 36)
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers (rev 36)
00:03.0 Multimedia controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit (rev 36)
00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 36)
00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 36)
00:1a.0 Encryption controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine (rev 36)
00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 36)
```

```
easy@easy-notebook-d:~$ lsusbBus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 058f:5608 Alcor Micro Corp. 
Bus 001 Device 006: ID 05e3:0718 Genesys Logic, Inc. IDE/SATA Adapter
Bus 001 Device 007: ID 0bda:8152 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 002: ID 6080:8060  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
easy@easy-notebook-d:~$ iwconfig
enxfcaa1430f0b5  no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Easy"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 40:31:3C:D0:DC:49   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=30/100  Signal level=29/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
easy@easy-notebook-d:~$ lsmod
Module                 Size  Used by
nls_iso8859_1          16384  1
snd_soc_sst_bytcr_rt5651    24576  2
axp288_adc             16384  0
axp288_charger         20480  0
axp288_fuel_gauge      24576  0
axp20x_pek             16384  0
industrialio           69632  2 axp288_adc,axp288_fuel_gauge
extcon_axp288          16384  0
intel_rapl             20480  0
intel_powerclamp       16384  0
coretemp               16384  0
gpio_keys              20480  0
kvm_intel             208896  0
kvm                   626688  1 kvm_intel
irqbypass              16384  1 kvm
punit_atom_debug       16384  0
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
aesni_intel           200704  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
glue_helper            16384  1 aesni_intel
input_leds             16384  0
intel_cstate           20480  0
uvcvideo               94208  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
cdc_ether              16384  0
videobuf2_v4l2         24576  1 uvcvideo
usbnet                 45056  1 cdc_ether
videobuf2_common       40960  2 videobuf2_v4l2,uvcvideo
videodev              188416  3 videobuf2_v4l2,uvcvideo,videobuf2_common
r8152                  61440  0
mii                    16384  2 usbnet,r8152
media                  40960  2 videodev,uvcvideo
i915                 1740800  4
snd_intel_sst_acpi     16384  1
snd_intel_sst_core     53248  1 snd_intel_sst_acpi
snd_soc_sst_atom_hifi2_platform   102400  2 snd_intel_sst_core
snd_soc_acpi           16384  2 snd_soc_sst_bytcr_rt5651,snd_intel_sst_acpi
snd_soc_rt5651         90112  1
snd_soc_acpi_intel_match    20480  1 snd_intel_sst_acpi
snd_soc_rl6231         16384  1 snd_soc_rt5651
snd_soc_core          229376  3 snd_soc_rt5651,snd_soc_sst_bytcr_rt5651,snd_soc_sst_atom_hifi2_platform
mei_txe                20480  0
drm_kms_helper        172032  1 i915
intel_xhci_usb_role_switch    16384  1
snd_compress           20480  1 snd_soc_core
roles                  16384  2 extcon_axp288,intel_xhci_usb_role_switch
mei                    98304  1 mei_txe
lpc_ich                24576  0
ac97_bus               16384  1 snd_soc_core
snd_seq_midi           16384  0
snd_pcm_dmaengine      16384  1 snd_soc_core
drm                   458752  6 drm_kms_helper,i915
snd_seq_midi_event     16384  1 snd_seq_midi
snd_pcm                98304  5 snd_soc_rt5651,snd_soc_sst_bytcr_rt5651,snd_soc_sst_atom_hifi2_platform,snd_soc_core,snd_pcm_dmaengine
snd_rawmidi            32768  1 snd_seq_midi
r8723bs               606208  0
intel_hid              16384  0
dw_dmac                16384  0
sparse_keymap          16384  1 intel_hid
dw_dmac_core           24576  1 dw_dmac
intel_cht_int33fe      16384  0
axp20x_i2c             16384  0
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
axp20x                 28672  1 axp20x_i2c
i2c_algo_bit           16384  1 i915
fb_sys_fops            16384  1 drm_kms_helper
cfg80211              667648  1 r8723bs
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
syscopyarea            16384  1 drm_kms_helper
snd_timer              32768  2 snd_seq,snd_pcm
sysfillrect            16384  1 drm_kms_helper
snd                    81920  12 snd_seq,snd_seq_device,snd_timer,snd_compress,snd_soc_sst_atom_hifi2_platform,snd_soc_core,snd_pcm,snd_rawmidi
sysimgblt              16384  1 drm_kms_helper
soundcore              16384  1 snd
8250_dw                16384  0
int3406_thermal        16384  0
spi_pxa2xx_platform    24576  0
mac_hid                16384  0
video                  45056  2 int3406_thermal,i915
acpi_pad              180224  0
int3400_thermal        16384  0
int3403_thermal        16384  0
processor_thermal_device    16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
int340x_thermal_zone    16384  2 int3403_thermal,processor_thermal_device
intel_int0002_vgpio    16384  1
acpi_thermal_rel       16384  1 int3400_thermal
soc_button_array       16384  0
sch_fq_codel           20480  6
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
uas                    24576  0
usb_storage            69632  2 uas
mmc_block              45056  4
sdhci_acpi             16384  0
sdhci                  49152  1 sdhci_acpi
hid_generic            16384  0
usbhid                 49152  0
hid                   122880  2 usbhid,hid_generic
```

---

### Post by jeremy31 on 2019-05-01
Moved to networking & wireless.  Have you tried the ant_sel=2 parameter?

---

### Post by easy3232 on 2019-05-01
Nothing changes.

After "modprobe -rv" the WI-FI module should be disabled? It continues to work for me.

If I do "sudo service network-manager restart", then the signal strength does not change either.

```
easy@easy-notebook-d:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"Easy"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 40:31:3C:D0:DC:49   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=22/100  Signal level=20/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
easy@easy-notebook-d:~$ sudo modprobe -rv rtl8723be
rmmod rtl8723be
rmmod rtl_pci
rmmod rtl8723_common
rmmod btcoexist
rmmod rtlwifi
rmmod mac80211
easy@easy-notebook-d:~$ sudo modprobe -v rtl8723be ant_sel=2
insmod /lib/modules/4.18.0-18-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.18.0-18-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko 
insmod /lib/modules/4.18.0-18-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko 
insmod /lib/modules/4.18.0-18-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723com/rtl8723-common.ko 
insmod /lib/modules/4.18.0-18-generic/kernel/drivers/net/wireless/realtek/rtlwifi/btcoexist/btcoexist.ko 
insmod /lib/modules/4.18.0-18-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko ant_sel=2
easy@easy-notebook-d:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"Easy"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 40:31:3C:D0:DC:49   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=25/100  Signal level=27/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by jeremy31 on 2019-05-01
That fix will not work for you as you have a different wifi chipset, you have the Rtl8723BS 
you could try ```
sudo modprobe -r r8723bs
sudo modprobe r8723bs rtw_ant_num=1
```

See if there is any difference and then try rtw_ant_num=2

---

### Post by easy3232 on 2019-05-01
Wi-fi really turns off and turns on after run commands. At the beginning the signal is strong, but after a couple of seconds it also drops to ~25 out of 100.

---

### Post by jeremy31 on 2019-05-01
That is a different issue then, lets try
```
echo "options r8723bs rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/r8723bs
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot

---

### Post by easy3232 on 2019-05-01
I did, but nothing's changed. If it can enable power-saving mode for USB?

---

### Post by easy3232 on 2019-05-01
It is still very strange that the speed only 72 mb\s is shown in iwconfig

---

### Post by jeremy31 on 2019-05-01
Who made this computer?  If it isn't HP, you shouldn't need to set antenna

---

### Post by easy3232 on 2019-05-01
This is not HP.
Something I can do or is it better to buy a USB wi-fi adapter?

---

### Post by him610 on 2019-05-01
Signal level is an indication of received signal strength.
```
man iwconfig
....
       Link quality
              Overall  quality  of the link. May be based on the level of contention or interfer&#8208;
              ence, the bit or frame error rate, how good the received  signal  is,  some  timing
              synchronisation,  or other hardware metric. This is an aggregate value, and depends
              totally on the driver and hardware.

       Signal level
              Received signal strength (RSSI - how strong the received signal is). May  be  arbi&#8208;
              trary  units  or  dBm,  iwconfig  uses driver meta information to interpret the raw
              value given by /proc/net/wireless and display the  proper  unit  or  maximum  value
              (using  8 bit arithmetic). In Ad-Hoc mode, this may be undefined and you should use
              iwspy.

```
Try moving closer to the wireless router/AP to see if that increases signal level.

---

### Post by easy3232 on 2019-05-02
Even close to my router, both parameters never exceed 50

---

### Post by him610 on 2019-05-02
This is the partial outout of your *iwconfig*
```
Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
```
This is what mine looks like (same lines)
```
Bit Rate=86.7 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```
Note the differences. Yours does not show [COLOR="#FF0000"]TX-Power[/COLOR]. It shows [COLOR="#FF0000"]Retry: off[/COLOR] and [COLOR="#FF0000"]Power Management: off[/COLOR]
I have little expertise in wireless drivers, but I think if you get the transmitter powered up it may solve your problem. Maybe Jeremy31 or Chilli555 will provide some recommended corrective actions.

---

