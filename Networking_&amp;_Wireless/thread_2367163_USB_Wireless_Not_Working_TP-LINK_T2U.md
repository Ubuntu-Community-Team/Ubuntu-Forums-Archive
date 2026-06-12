---
title: "USB Wireless Not Working TP-LINK T2U"
date: 2017-07-26
forum: Networking &amp; Wireless
---

### Post by khan3 on 2017-07-26
Hi,

I am trying to get my device to work with Ubuntu 16.04. I would like to switch my on-board wireless in favour for my USB wireless adapter to test if it works. 

```
sudo lshw -C network
```

```
 *-network               
       description: Wireless interface
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 3a
       serial: a4:34:d9:80:7e:ec
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-83-generic firmware=16.242414.0 ip=10.186.194.209 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:132 memory:df100000-df101fff
  *-network (THIS ONE IS MY USB)
       description: Wireless interface
       physical id: 2
       logical name: ra0
       serial: c4:e9:84:dd:27:04
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN multicast=yes wireless=Ralink STA
```

```
ifconfig
```

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:61402 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:7058416 (7.0 MB)  TX bytes:7058416 (7.0 MB)

ra0       Link encap:Ethernet  HWaddr c4:e9:84:dd:27:04  
          inet6 addr: fe80::c6e9:84ff:fedd:2704/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp1s0    Link encap:Ethernet  HWaddr a4:34:d9:80:7e:ec  
          inet6 addr: fe80::770e:513a:1187:ce17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:876709 errors:0 dropped:0 overruns:0 frame:0
          TX packets:414460 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:910750958 (910.7 MB)  TX bytes:82226757 (82.2 MB)
```

```
rfkill list
```

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

iwconfig

```
lo        no wireless extensions.

wlp1s0    IEEE 802.11abgn  ESSID:"eduroam"  
          Mode:Managed  Frequency:5.24 GHz  Access Point: 6C:F3:7F:A6:EF:90   
          Bit Rate=117 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:4   Missed beacon:0

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"MT7610U_STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

And everytime i take the usb out i have to run: ```
ifconfig ra0 up
```

---

### Post by praseodym on 2017-07-26
Please show
```

lsusb
lsmod
```

---

### Post by khan3 on 2017-07-27
[URL="https://ubuntuforums.org/member.php?u=1411497"][B][COLOR=#000000]@praseodym
[/COLOR][/B][/URL]
lsusb

```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 112: ID 148f:761a Ralink Technology, Corp. 
Bus 001 Device 003: ID 058f:3822 Alcor Micro Corp. 
Bus 001 Device 002: ID 062a:4101 Creative Labs Wireless Keyboard/Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


lsmod
```

Module                  Size  Used by
mt7650u_sta           913408  1
mt7601u               102400  0
btrfs                 987136  0
xor                    24576  1 btrfs
raid6_pq              102400  1 btrfs
ufs                    73728  0
qnx4                   16384  0
hfsplus               106496  0
hfs                    57344  0
minix                  36864  0
ntfs                   98304  0
msdos                  20480  0
jfs                   180224  0
xfs                   970752  0
libcrc32c              16384  1 xfs
cpuid                  16384  0
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  2
ccm                    20480  2
bnep                   20480  2
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               454656  3 vboxnetadp,vboxnetflt,vboxpci
snd_hda_codec_hdmi     53248  1
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
binfmt_misc            20480  1
arc4                   16384  2
snd_soc_skl            49152  0
snd_soc_skl_ipc        32768  1 snd_soc_skl
snd_hda_ext_core       28672  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        53248  1 snd_soc_skl_ipc
snd_soc_core          212992  1 snd_soc_skl
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
dw_dmac_core           24576  1 snd_soc_sst_dsp
snd_hda_intel          40960  6
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  7 snd_hda_codec_realtek,snd_hda_ext_core,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_soc_skl
snd_hwdep              16384  1 snd_hda_codec
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
snd_pcm               106496  8 snd_hda_ext_core,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_skl,snd_pcm_dmaengine,snd_hda_core
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
media                  24576  2 uvcvideo,videodev
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             172032  0
snd_seq_midi           16384  0
kvm                   544768  1 kvm_intel
snd_seq_midi_event     16384  1 snd_seq_midi
joydev                 20480  0
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
iwlmvm                311296  0
aesni_intel           167936  4
snd_rawmidi            32768  1 snd_seq_midi
mac80211              737280  2 mt7601u,iwlmvm
aes_x86_64             20480  1 aesni_intel
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_timer              32768  2 snd_pcm,snd_seq
iwlwifi               200704  1 iwlmvm
input_leds             16384  0
serio_raw              16384  0
cfg80211              565248  4 iwlwifi,mac80211,mt7601u,iwlmvm
snd                    81920  25 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
soundcore              16384  1 snd
shpchp                 36864  0
mei_me                 36864  0
mei                    98304  1 mei_me
hci_uart               77824  0
btbcm                  16384  1 hci_uart
btqca                  16384  1 hci_uart
btintel                16384  1 hci_uart
bluetooth             520192  9 bnep,btbcm,btqca,hci_uart,btintel
intel_lpss_acpi        16384  0
intel_lpss             16384  1 intel_lpss_acpi
tpm_crb                16384  0
acpi_pad               24576  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
i915_bpo             1306624  10
intel_ips              20480  1 i915_bpo
i2c_algo_bit           16384  1 i915_bpo
drm_kms_helper        155648  1 i915_bpo
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
psmouse               131072  0
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  11 i915_bpo,drm_kms_helper
nvme                   65536  4
ahci                   36864  0
libahci                32768  1 ahci
pinctrl_sunrisepoint    28672  0
video                  40960  1 i915_bpo
pinctrl_intel          20480  1 pinctrl_sunrisepoint
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_generic,usbhid
fjes                   28672  0

```

---

### Post by praseodym on 2017-07-27
Where did you get the driver from? If self-compiled you may need to do it again, first manipulating the file config.mk according to
```

# Support Wpa_Supplicant
# i.e. wpa_supplicant -Dralink
HAS_WPA_SUPPLICANT=y


# Support Native WpaSupplicant for Network Maganger
# i.e. wpa_supplicant -Dwext
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```
Where does mt7601u come from?!

```
modprobe -c | grep -i "148f.*761a"
dmesg | grep mt7
```

---

### Post by khan3 on 2017-07-27
I got the driver from here

[https://github.com/chenhaiq/mt7610u_wifi_sta_v3002_dpo_20130916](https://github.com/chenhaiq/mt7610u_wifi_sta_v3002_dpo_20130916)

I did self compile this with no errors, but a few warnings. ( Just been trying anything )

but i failed trying to do - 
**sudo modprobe mt7610u_sta**


```
modprobe: FATAL: Module mt7610u_sta not found in directory /lib/modules/4.4.0-83-generic
```

Where is the conf.mk file?

modprobe -c | grep -i "148f.*761a"

```
alias usb:v148Fp761Ad*dc*dsc*dp*ic*isc*ip*in* mt7650u_sta
```

dmesg | grep mt7

```
[ 1100.900286] usbcore: registered new interface driver mt7601u
[38694.256909] /home/kay/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../chips/mt76x0.c:2114 assert (pAd->TxPower[choffset].Channel == 36)failed
[38694.263457] mt76x0_read_tx_alc_info_from_eeprom: EEPROM_MT76x0_TEMPERATURE_OFFSET (0xD1) = 0xf8
[38694.263459] mt76x0_read_tx_alc_info_from_eeprom: TemperatureOffset = 0xfffffff8
[39445.302394] /home/kay/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../chips/mt76x0.c:2114 assert (pAd->TxPower[choffset].Channel == 36)failed
[39445.307934] mt76x0_read_tx_alc_info_from_eeprom: EEPROM_MT76x0_TEMPERATURE_OFFSET (0xD1) = 0xf8
[39445.307935] mt76x0_read_tx_alc_info_from_eeprom: TemperatureOffset = 0xfffffff8
[42809.840867] /home/kay/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../chips/mt76x0.c:2114 assert (pAd->TxPower[choffset].Channel == 36)failed
[42809.846404] mt76x0_read_tx_alc_info_from_eeprom: EEPROM_MT76x0_TEMPERATURE_OFFSET (0xD1) = 0xf8
[42809.846406] mt76x0_read_tx_alc_info_from_eeprom: TemperatureOffset = 0xfffffff8

```

---

### Post by praseodym on 2017-07-27
As you see the driver is mt7650u_sta!
```

sudo modprobe -rfv mt7650u_sta mt7601u
sudo modprobe -v mt7650u_sta
dmesg | grep mt7
iwconfig
```

---

### Post by khan3 on 2017-07-27
iwconfig

```

lo        no wireless extensions.

wlp1s0    IEEE 802.11abgn  ESSID:"eduroam"  
          Mode:Managed  Frequency:5.24 GHz  Access Point: 00:1A:1E:5E:46:F1   
          Bit Rate=117 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:1   Missed beacon:0

ra0       Ralink STA  

```

So did i install the wrong driver?
how do i switch to using the usb wireless instead of onboard and visa versa

---

### Post by praseodym on 2017-07-27
Lets see:
```

sudo modprobe -rfv iwlwifi mt7650u_sta
sudo modprobe -v mt7650u_sta
iwconfig
```

---

### Post by khan3 on 2017-07-27
sudo modprobe -rfv iwlwifi mt7650u_sta

```

remove (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) && /sbin/modprobe -r mac80211
rmmod mac80211
rmmod cfg80211
modprobe: FATAL: Module mt7650u_sta not found.

```
udo modprobe -v mt7650u_sta
```

modprobe: FATAL: Module mt7650u_sta not found in directory /lib/modules/4.4.0-87-generic

```
wconfig
```

lo        no wireless extensions.

```

Had to restart my computer to get internet working again. I assume i did install the wrong drivers then? How can i set this up properly and be able to switch between my wireless usb and onboard.

---

### Post by praseodym on 2017-07-27
Please uninstall the driver and try this one instead:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
git clone https://sanrath@bitbucket.org/sanrath/mediatek_mt7610u_sta_driver_linux-64bit
cd mediatek_mt7610u_sta_driver_linux-64bit
```
Open the file **common/vim rtusb_dev_id.c** and add these lines where the other IDs are located

```
{USB_DEVICE(0x148f,0x761a)}, /* TP-Link T2UH */
```
After that open the file /etc/Wireless/RT2870STA/RT2870STA.dat and change the settings to

```
CountryRegion=1
CountryRegionABand=1
CountryCode=[COLOR="#FF0000"]de[/COLOR]
```
Change the country code to yours.

After that
```

make
sudo make install
sudo modprobe mt7610u_sta
```

---

### Post by khan3 on 2017-07-28
@[**[COLOR=#000000]praseodym[/COLOR]**]("https://ubuntuforums.org/member.php?u=1411497")

Hey, im not sure how to uninstall the previous one, there is no instructions on the original github.

and this is the device i have. TPT2U, just want to clarify this new driver is for this device. [https://www.amazon.co.uk/TP-LINK-Archer-T2U-Wireless-Adapter/dp/B00K11UIV4/ref=sr_1_1?ie=UTF8&qid=1501231445&sr=8-1&keywords=TP+T2U](https://www.amazon.co.uk/TP-LINK-Archer-T2U-Wireless-Adapter/dp/B00K11UIV4/ref=sr_1_1?ie=UTF8&qid=1501231445&sr=8-1&keywords=TP+T2U).

And if we determined the driver was "As you see the driver is mt7650u_sta!" why am i installing this new one? (mt7610u_sta)

---

### Post by praseodym on 2017-07-28
Try inside the cloned driver folder of the old one
```

make clean
make
sudo make uninstall
```
The "new" one worked after adding the device ID as described. Maybe it is also unstable, too?!

---

### Post by khan3 on 2017-07-28
Im confused now, so the one the one that showed up in iwconfig didint work? 
ra0       Ralink STA

maybe its unstable ? how do you know. Can you please tell me how to switch between my onboard and usb one.... so i can actually test it and report back.

Ive uninstalled my previous one, following ur steps.

but now ur telling me to add this line "
{USB_DEVICE(0x148f,0x761a)}, /* TP-Link T2UH */"

I have T2U , not T2UH.. Where are you getting this USB device code from, please provide a little more information so im not blindly following your commands that i don't know . thank you

UPDATE:

i installed your one with no errors even after doing modprobe there was no error message.

---

### Post by praseodym on 2017-07-28
These drivers are pretty new and are currently not in the stable branch of the kernel, so devices with these drivers are not recommended.

Please show now
```

iwconfig
iwlist chan
lsmod
sudo iwlist scan
route -n
dmesg | grep mt7
cat /etc/resolv.conf
```

---

### Post by chili555 on 2017-07-28
> so devices with these drivers are not recommended.+1000> I would like to switch my on-board wireless in favour for my USB wireless adapter to test if it works. 
It doesn't. I have worked on quite a few cases involving the mt7610u chipset, some with the help of my colleague praseodym. None *EVER* worked. 

I can think of nothing that this device can do that your built-in Intel can't do much, much better.

---

### Post by BenginM on 2017-07-28
Well, praseodym , chili .. you guys missin' the point of his dilemma , he want to pen-test with HIS TP-link :

[https://ubuntuforums.org/showthread.php?t=2367071](https://ubuntuforums.org/showthread.php?t=2367071)

if they're lookin' for air sniffing , that's achievable with the Intel one.

So this is the device in question ..!

[https://wikidevi.com/wiki/TP-LINK_Archer_T2U](https://wikidevi.com/wiki/TP-LINK_Archer_T2U)

---

### Post by khan3 on 2017-07-29
[URL="https://ubuntuforums.org/member.php?u=1100835"][B][COLOR=#000000]@BenginM
[/COLOR][/B][/URL]
Yes, ye that is my device.

@praseodym Here you go.

iwconfig

```

tun0      no wireless extensions.

lo        no wireless extensions.

wlp1s0    IEEE 802.11abgn  ESSID:"eduroam"  
          Mode:Managed  Frequency:5.52 GHz  Access Point: 6C:F3:7F:A6:EB:70   
          Bit Rate=650 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:1   Missed beacon:0

ra0       Ralink STA  ESSID:""  Nickname:"MT7610U_STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

iwlist chan

```

tun0      no frequency information.

lo        no frequency information.

wlp1s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:5.52 GHz (Channel 104)

ra0       11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)


```

lsmod

```

Module                  Size  Used by
mt7610u_sta           835584  1
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  2
ccm                    20480  2
bnep                   20480  2
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               454656  3 vboxnetadp,vboxnetflt,vboxpci
snd_hda_codec_hdmi     53248  1
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
binfmt_misc            20480  1
arc4                   16384  2
snd_soc_skl            49152  0
snd_soc_skl_ipc        32768  1 snd_soc_skl
snd_hda_ext_core       28672  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        53248  1 snd_soc_skl_ipc
snd_soc_core          212992  1 snd_soc_skl
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
coretemp               16384  0
snd_pcm_dmaengine      16384  1 snd_soc_core
dw_dmac_core           24576  1 snd_soc_sst_dsp
kvm_intel             172032  0
snd_hda_intel          40960  3
kvm                   544768  1 kvm_intel
irqbypass              16384  1 kvm
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_hda_core           73728  7 snd_hda_codec_realtek,snd_hda_ext_core,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_soc_skl
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  8 snd_hda_ext_core,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_skl,snd_pcm_dmaengine,snd_hda_core
aesni_intel           167936  4
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
uvcvideo               90112  0
glue_helper            16384  1 aesni_intel
snd_seq_midi           16384  0
ablk_helper            16384  1 aesni_intel
snd_seq_midi_event     16384  1 snd_seq_midi
videobuf2_vmalloc      16384  1 uvcvideo
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_rawmidi            32768  1 snd_seq_midi
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
iwlmvm                311296  0
joydev                 20480  0
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
mac80211              737280  1 iwlmvm
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
input_leds             16384  0
iwlwifi               200704  1 iwlmvm
serio_raw              16384  0
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
snd                    81920  19 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
soundcore              16384  1 snd
shpchp                 36864  0
mei_me                 36864  0
mei                    98304  1 mei_me
hci_uart               77824  0
btbcm                  16384  1 hci_uart
btqca                  16384  1 hci_uart
btintel                16384  1 hci_uart
bluetooth             520192  9 bnep,btbcm,btqca,hci_uart,btintel
intel_lpss_acpi        16384  0
intel_lpss             16384  1 intel_lpss_acpi
tpm_crb                16384  0
acpi_pad               24576  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
i915_bpo             1306624  6
intel_ips              20480  1 i915_bpo
i2c_algo_bit           16384  1 i915_bpo
drm_kms_helper        155648  1 i915_bpo
psmouse               131072  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
nvme                   65536  4
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  7 i915_bpo,drm_kms_helper
ahci                   36864  0
libahci                32768  1 ahci
video                  40960  1 i915_bpo
pinctrl_sunrisepoint    28672  0
pinctrl_intel          20480  1 pinctrl_sunrisepoint
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_generic,usbhid
fjes                   28672  0


```

sudo iwlist scan

[https://pastebin.com/PhCUeTPf](https://pastebin.com/PhCUeTPf)

route -n

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.186.255.250  0.0.0.0         UG    600    0        0 wlp1s0
10.186.0.0      0.0.0.0         255.255.0.0     U     600    0        0 wlp1s0
10.192.0.0      172.16.192.1    255.192.0.0     UG    0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp1s0
172.16.192.0    0.0.0.0         255.255.192.0   U     0      0        0 tun0


```

dmesg | grep mt7

```

[ 1097.079562] /home/kay/mediatek_mt7610u_sta_driver_linux-64bit/os/linux/../../chips/mt76x0.c:2114 assert (pAd->TxPower[choffset].Channel == 36)failed
[ 1097.085224] mt76x0_read_tx_alc_info_from_eeprom: EEPROM_MT76x0_TEMPERATURE_OFFSET (0xD1) = 0xf8
[ 1097.085226] mt76x0_read_tx_alc_info_from_eeprom: TemperatureOffset = 0xfffffff8

```

cat /etc/resolv.conf

```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 10.192.0.9
nameserver 8.8.8.8
nameserver 127.0.1.1
search manchester.ac.uk


```

---

### Post by chili555 on 2017-07-29
> Well, praseodym , chili .. you guys missin' the point of his dilemma , he want to pen-test with HIS TP-link :I'm not missing the point at all. The most salient point, in my opinion, is that praseodym, Jeremy, Hadaka, Pilot6, wildmanne and I have all worked on these mt7610u chipsets for years. With the available drivers and a newer kernel version; that is, not yet end-of-life, I have not seen ANY case where it actually connects and pulls web pages. If you can get it to connect, which I doubt, then we wonder if the SoftAP function works, again, with the available drivers and later kernels.

It is the classic dilemna:

Original Poster: Help me make this work.
Driver guru: It can't work.
Original Poster: But, but, isn't there another solution?
Driver guru: Sure. Put this under the wheel of your car as you drive down to the store to get a different device.

There is little to nothing we can do when MediaTek and TP-Link don't supply a driver for newer kernels; i.e. 4.8 and newer. You can certainly email them and ask for a newer driver. I am quite confident that they have no interest in pen testing. 

You could study the code and write one yourself. You could try installing an older Ubuntu version that uses, for example, a 3.6 kernel and try the drivers again. However, don't expect support from most of the driver gurus here. We don't have any 3.6 installations on hand with which to try to guide you.

---

### Post by praseodym on 2017-07-29
One remark:

```
iwlist chan
```

shows 13 channels for the internal card and 11 channels for the stick, repectively. As the network is "eduroam" it is a university network or similar? Maybe the APs are roaming along the 2,4 GHz band and also use channels 12 and 13 (and also maybe the 5GHz band, too?!). Which country do you live? Change the country code settings according to

```
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=[COLOR="#FF0000"]DE[/COLOR]/g" /etc/default/crda 
```
Change DE with your country code

[https://en.wikipedia.org/wiki/ISO_3166-1](https://en.wikipedia.org/wiki/ISO_3166-1)

Reboot and run
```

iwlist chan
sudo iwlist scan
dmesg | grep country
```

---

### Post by khan3 on 2017-07-29
I live in the UK.

You are right i am currently not at home, im at university on the university network.



iwlist chan

```

tun0      no frequency information.

lo        no frequency information.

wlp1s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:5.24 GHz (Channel 48)

ra0       11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)


```

sudo iwlist scan

[https://pastebin.com/YQXE6k8t](https://pastebin.com/YQXE6k8t)

dmesg | grep country

it returned nothing

---

### Post by praseodym on 2017-07-29
Ok, so "eduroam" is shown on channels 1, 6, 6 again, 44, 48, 48 again, and soon. 13 channels may even not be allowed in the UK, please check
```

sudo apt-get install iw
iw reg get
sudo iw reg set UK
iw reg get
iwlist chan
```
You can chose the strongest signal and add the MAC address of that AP to the field BSSID in the network-manager applet, always connecting to that AP. Of course, channels 1-11 are recommended for the stick

---

### Post by khan3 on 2017-07-29
Yes Eduroam is the university network i was on at the time of posting the commands.

---

### Post by khan3 on 2017-07-29
iw reg get

```

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

```

iwlist chan

```

tun0      no frequency information.

lo        no frequency information.

wlp1s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.412 GHz (Channel 1)

ra0       11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)

```

---

### Post by praseodym on 2017-07-29
Are you connected with both devices? Disable the connection from the internal card

---

### Post by khan3 on 2017-07-29
Yes i can't seem to connect it always reverts back to my onboard one even though i set ifconfig wlps10 down.

And i can't seem to change the BSSID and device field in network settings to the new hw adress. says invalid wpa-psk invalid key length 0

---

### Post by cap69 on 2018-03-27
still not allowing my device to be seen..

---

