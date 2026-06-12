---
title: "WiFi is disabled by hardware switch on HP 15, how to turn it on"
date: 2019-01-08
forum: Networking &amp; Wireless
---

### Post by erabxes on 2019-01-08
[COLOR=#000000]Hi,[/COLOR]
[COLOR=#000000]I recently installed ubuntu 18.04 on my HP 15 laptop PC (on a partioned hard disk) on which I already had installed Win 10 (as Multi-Boot System). [/COLOR]
[COLOR=#000000]Now, in ubuntu 18.04 my WiFi does not work, it is switched off. In the settings-menu  for the WiFi tab, I get "No WiFi Adapter Found", and I get "Airplane Mode On", and where I get the WiFi icon, I have WiFi Off.[/COLOR]
[COLOR=#000000]but the WiFi works just fine under Win 10.  

Please can anyone help me on how to switch on the WiFi wireless

I have [/COLOR][COLOR=#000000] created a detailed report for troubleshooting wireless problems using the wireless info script created by @varunendra and co, and the link to it on pastebin is [/COLOR][https://pastebin.ubuntu.com/p/MJpxSRwqh9/](https://pastebin.ubuntu.com/p/MJpxSRwqh9/)

Thanks in advance for the help

---

### Post by praseodym on 2019-01-08
Any button, switch, key or key combo? Lets try
```

sudo rfkill unblock all
rfkill list
iwconfig
```

---

### Post by erabxes on 2019-01-09
When I ran the commands below:

```
sudo rfkill unblock all
```
```
rfkill list
```

I got this  below:

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

And when I ran the command :  ```
iwconfig

```

I got this below: 

```

wlp2s0f0  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


enp4s0    no wireless extensions.


```

---

### Post by praseodym on 2019-01-09
Ok, lets try
```

sudo modprobe -rfv rt2800pci
sudo rfkill unblock all
sudo modprobe -v rt2800pci
rfkill list
```
If it is stil blocked, try
```

echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp.conf
```
and reboot

---

### Post by erabxes on 2019-01-10
@praseodym, I executed the commands that you requested of me, see below my outputs for the various commands

For these sets of commands:

sudo modprobe -rfv rt2800pci
sudo rfkill unblock all
sudo modprobe -v rt2800pci
rfkill list
I got this:

```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

But my observation was that while I was executing 

```
sudo modprobe -rfv rt2800pci
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]

```

I observed that the airplane mode icon disappeared, but later came on when I executed

```
sudo rfkill unblock all
```

And finally when I did 

```
echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp.conf
```

and rebooted, the WiFi is still disabled.
Thanks in anticipation for your next directive sir.

---

### Post by praseodym on 2019-01-10
Is it a BIOS or an /U(EFI? If BIOS: Reset it to default settings

---

### Post by erabxes on 2019-01-15
So sorry, it took me a while to reply you. I think my system should be a BIOS categorised system and It doesn't possess the option to restore BIOS to default setting.

---

### Post by praseodym on 2019-01-15
Here, resetting is pressing F9, save&exit with F10.

Please show
```

lsmod
```

completely

---

### Post by erabxes on 2019-01-16
I did as you requested. I went to the BIOS settings and reset pressing F9, saved and exit with F10. 


Here below is the result for :
```
lsmod
```

is below:
```

Module                  Size  Used by
bnep                   20480  2
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
rtsx_pci_ms            20480  0
memstick               16384  1 rtsx_pci_ms
intel_rapl             20480  0
intel_soc_dts_thermal    16384  0
intel_soc_dts_iosf     16384  1 intel_soc_dts_thermal
intel_powerclamp       16384  0
coretemp               16384  0
kvm                   598016  0
irqbypass              16384  1 kvm
punit_atom_debug       16384  0
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
cryptd                 24576  1 ghash_clmulni_intel
intel_cstate           20480  0
arc4                   16384  2
rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib             114688  2 rt2800mmio,rt2800pci
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
input_leds             16384  0
rt2x00pci              16384  1 rt2800pci
joydev                 24576  0
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
wmi_bmof               16384  0
rt2x00lib              53248  5 rt2x00mmio,rt2x00pci,rt2800mmio,rt2800pci,rt2800lib
serio_raw              16384  0
mac80211              778240  3 rt2x00pci,rt2x00lib,rt2800lib
lpc_ich                24576  0
snd_hda_intel          40960  6
cfg80211              622592  2 rt2x00lib,mac80211
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
eeprom_93cx6           16384  1 rt2800pci
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
dw_dmac                16384  0
dw_dmac_core           24576  1 dw_dmac
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
hci_uart              106496  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
btbcm                  16384  1 hci_uart
snd_timer              32768  2 snd_seq,snd_pcm
btqca                  16384  1 hci_uart
hp_wireless            16384  0
btintel                16384  1 hci_uart
bluetooth             548864  11 btqca,btintel,hci_uart,btbcm,bnep
rfkill_gpio            16384  0
ecdh_generic           24576  1 bluetooth
mei_txe                20480  0
pwm_lpss_platform      16384  0
pwm_lpss               16384  1 pwm_lpss_platform
mei                    90112  1 mei_txe
mac_hid                16384  0
snd                    81920  23 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
soundcore              16384  1 snd
shpchp                 36864  0
sch_fq_codel           20480  2
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
rtsx_pci_sdmmc         24576  0
i915                 1617920  20
i2c_algo_bit           16384  1 i915
drm_kms_helper        172032  1 i915
syscopyarea            16384  1 drm_kms_helper
psmouse               147456  0
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
r8169                  86016  0
drm                   401408  15 drm_kms_helper,i915
ahci                   36864  1
rtsx_pci               65536  2 rtsx_pci_sdmmc,rtsx_pci_ms
mii                    16384  1 r8169
i2c_i801               28672  0
libahci                32768  1 ahci
wmi                    24576  2 hp_wmi,wmi_bmof
i2c_hid                20480  0
hid                   118784  1 i2c_hid
video                  45056  1 i915

```

Thanks in anticipation for your next directive.

---

### Post by praseodym on 2019-01-16
Check first
```

rfkill list
sudo modprobe -rfv rt2800pci
sudo rfkill unblock all
sudo modprobe -v rt2800pci
rfkill list
iwconfig
```
Any change? If not, try
```

echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp_wmi.conf
```
Reboot and show again
```

rfkill list
iwconfig
```

---

### Post by erabxes on 2019-01-17
I executed all the codes above  and the  result of  

```
rfkill list
```

is below:

```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes



```


while when I ran the command:

```
iwconfig
```

I got this below:

```

wlp2s0f0  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


enp4s0    no wireless extensions.



```

Thanks in anticipation of your next assistance.

---

