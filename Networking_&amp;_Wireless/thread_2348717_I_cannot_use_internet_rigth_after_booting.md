---
title: "I cannot use internet rigth after booting"
date: 2017-01-06
forum: Networking &amp; Wireless
---

### Post by santiagorf on 2017-01-06
When I boot Ubuntu, I'm able to connect and ping to other computers but cannot access internet. However, after waiting for about ten minutes or so, I can access to internet. This problem occurs when I connect via either wifi or cable.
This is the only device that has problem accessing internet; internet works on windows. I had the same problem when I tried Ubuntu from the usb key.

Any help would be much appreciated.
System: Ubuntu 16.4 fresh install & up to date; HP Pavilion g6 

Here is some info when I'm unable to use internet.

lspci -nnk | grep -iA2 net
```
02:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
	DeviceName: Ralink RT3290LE 802.11bgn 1x1 Wi-Fi Adapter
	Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
	DeviceName: Realtek PCIe FE Family Controller
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:1849]
	Kernel driver in use: r8169
	Kernel modules: r8169

```

lsmod
```
Module                  Size  Used by
nvram                  16384  0
msr                    16384  0
nls_iso8859_1          16384  1
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
kvm                   540672  0
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 20480  0
input_leds             16384  0
serio_raw              16384  0
k10temp                16384  0
rtsx_pci_ms            20480  0
memstick               20480  1 rtsx_pci_ms
arc4                   16384  2
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
i2c_piix4              24576  0
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
snd_hda_codec_idt      57344  1
snd_hda_codec_hdmi     53248  1
snd_hda_codec_generic    77824  1 snd_hda_codec_idt
rt2x00lib              57344  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              737280  3 rt2x00lib,rt2x00pci,rt2800lib
snd_hda_intel          40960  5
snd_hda_codec         135168  4 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
cfg80211              565248  2 mac80211,rt2x00lib
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
eeprom_93cx6           16384  1 rt2800pci
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
crc_ccitt              16384  1 rt2800lib
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  1 snd
shpchp                 36864  0
hp_wireless            16384  0
hp_accel               28672  0
lis3lv02d              20480  1 hp_accel
input_polldev          16384  1 lis3lv02d
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
rtsx_pci_sdmmc         24576  0
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  2
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon
psmouse               131072  0
r8169                  81920  0
mii                    16384  1 r8169
drm_kms_helper        155648  1 radeon
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  3
libahci                32768  1 ahci
drm                   364544  5 ttm,drm_kms_helper,radeon
wmi                    20480  1 hp_wmi
fjes                   28672  0
video                  40960  0

```

iwconfig
```
lo        no wireless extensions.

wlo1      IEEE 802.11bgn  ESSID:"verz"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:02:CF:C5:24:BE   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:34   Missed beacon:0

eno1      no wireless extensions.

```

nmcli dev show | grep DNS
```
IP4.DNS[1]:                             200.51.211.7
IP4.DNS[2]:                             200.51.212.7

```

ping 192.168.1.1
```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=254 time=1.43 ms

```

ping [www.google.com](www.google.com)
```
ping: unknown host www.google.com

```

nslookup [www.google.com](www.google.com)
```
;; connection timed out; no servers could be reached
```

---

### Post by slickymaster on 2017-01-06
*Thread moved to **Networking & Wireless**.*

---

### Post by wildmanne39 on 2017-01-06
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by santiagorf on 2017-01-06
I have run the script. Please note there are two outputs.
The first one is right after booting (when internet dosn't work), and the second output comes from the same script that was run a couple of minutes later when I had access to internet.

Without internet: [ATTACH=CONFIG]273084[/ATTACH], and after waiting a couple of minutes (and with internet working): [ATTACH=CONFIG]273083[/ATTACH].

I have noticed that once internet starts working, and, after a while, it stops working again, so it seems that internet goes on and off intermittently.

---

### Post by wildmanne39 on 2017-01-06
First let's turn off power management with a command I picked up from jeremy31:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Then check to make sure power management is off by running:
```
iwconfig
```
Change the settings in the router. WPA2-AES is best; do not use WPA and WPA2 mixed mode unless you absolutely have too and do not use TKIP. Second, if your router is capable of N speeds, You may have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. Set a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Add the google nameservers 8.8.8.8 and 8.8.4.4) in "IPv4-settings" in the network-manager applet.

Right-click->Edit connections->choose your network name->Edit->IPv4-setings

Change to "Automatic (DHCP), addresses only" and add the nameservers like this 8.8.8.8,8.8.4.4 in the field "DNS-servers".

Then go into the IPV6 setting and set it to ignore then save settings, while in network manager remove the second wifi connection.

Restart the network after that by doing:
```
sudo systemctl restart NetworkManager.service
```
Set your country code:
```
sudo iw reg set AR
sudo sed -i 's/^REG.*=$/&AR/' /etc/default/crda
```
Do:
```
echo "options rt2800pci nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```

All of these things will make your connection much better but if you still have an issue connecting when you boot it could be the network manager but that has been solved through an update but is still causing a few people trouble, if you have an issue try:
```
sudo systemctl restart NetworkManager.service
```
Thanks

---

### Post by santiagorf on 2017-01-07
Thanks for the solution, it worked like a charm! I rebooted twice and internet works right away.

I just didn't do these steps:

> Change the settings in the router. WPA2-AES is best; do not use WPA and WPA2 mixed mode unless you absolutely have too and do not use TKIP. Second, if your router is capable of N speeds, You may have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. Set a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router. I didn't change the router's setting as this is not my router. I'll see if I can change these setting later.
>  ... while in network manager remove the second wifi connection. as I wasn't sure what to do here.

```
sudo systemctl restart NetworkManager.service
``` since internet was already working after applying the previous steps.

---

### Post by wildmanne39 on 2017-01-07
Your welcome!
Enjoy!

---

