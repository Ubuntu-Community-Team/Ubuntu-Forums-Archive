---
title: "Lenovo (Dual Booting) Ubuntu 16.04 LTS barely able to connect to the internet"
date: 2016-08-11
forum: Networking &amp; Wireless
---

### Post by xaotic2 on 2016-08-11
Hello everybody!
Ive installed Ubuntu on my Lenovo Laptop just yesterday and internet access seems to work pretty much never.
This laptop is also running Win10 which has no issues connecting at all.

Basically the main issue is, that it is able to connect to the router but still allows no external connections.
For exampe, pinging google.com just says something as unknown host or could not reach host.
I also cant ping my local gateway (192.168.2.1). Ive disabled ipv6 in every way possible, ipv4 is set on DHCP.
Now to the weird part; It might work just a couple minutes after a router restart sometimes but if i restart the pc in this period of time it stops working once again.
Router says that the PC is connected to the router.

My RPI works just fine on this.

I have to manually type this out.
rfkill
```

0: ideapad_wlan: Wireless LAN
  Soft Blocked: no
  Hard blocked: no
1: ideapad_bluetooth -- skipping this one
2: hci0: Bluetooth -- skipping this one too
3: phy0: Wireless Lan
  Soft blocked: no
  Hard blocked: no

```

ifconfig
(too risky to type out)
Image of output:
[http://i.imgur.com/g9vr91G.jpg](http://i.imgur.com/g9vr91G.jpg)

I havent found a solution on this on the internet, nor identical problems.
Thank you all for trying to help me out!

---

### Post by xaotic2 on 2016-08-15
bump, still having this issue

---

### Post by wildmanne39 on 2016-08-15
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.

Copy the output to a flash drive then use the computer with internet access to post it here.

Is the issue with your wifi?
Thank you

---

### Post by xaotic2 on 2016-08-16
Thanks alot for your reply!
Got the following output:
```

xaotic@memecat:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
Linux memecat 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
xaotic@memecat:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
	Subsystem: Lenovo RTL8821AE 802.11ac PCIe Wireless Network Adapter [17aa:a814]
	Kernel driver in use: rtl8821ae
	Kernel modules: rtl8821ae
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Lenovo RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [17aa:381e]
	Kernel driver in use: r8169
	Kernel modules: r8169
xaotic@memecat:~$ lsusb
Bus 002 Device 004: ID 5986:06b3 Acer, Inc 
Bus 002 Device 003: ID 0bda:0821 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 24db:3257  
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
xaotic@memecat:~$ iwconfig
enp2s0    no wireless extensions.


lo        no wireless extensions.


wlp1s0    IEEE 802.11abgn  ESSID:"WLAN-126827"  
          Mode:Managed  Frequency:5.5 GHz  Access Point: 84:9C:A6:D7:63:2D   
          Bit Rate=6 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


xaotic@memecat:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
xaotic@memecat:~$ lsmod
Module                  Size  Used by
uas                    24576  0
usb_storage            69632  2 uas
rfcomm                 69632  0
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  2
ccm                    20480  2
bnep                   20480  2
nls_iso8859_1          16384  2
rtsx_usb_ms            20480  0
memstick               20480  1 rtsx_usb_ms
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
kvm                   536576  0
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
irqbypass              16384  1 kvm
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hda_codec_realtek    86016  1
arc4                   16384  2
media                  24576  2 uvcvideo,videodev
aesni_intel           167936  4
aes_x86_64             20480  1 aesni_intel
rtl8821ae             225280  0
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     53248  1
btcoexist              53248  1 rtl8821ae
glue_helper            16384  1 aesni_intel
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
rtl_pci                28672  1 rtl8821ae
rtlwifi                77824  2 rtl_pci,rtl8821ae
btusb                  45056  0
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
ablk_helper            16384  1 aesni_intel
mac80211              737280  3 rtl_pci,rtlwifi,rtl8821ae
snd_hwdep              16384  1 snd_hda_codec
cryptd                 20480  2 aesni_intel,ablk_helper
btrtl                  16384  1 btusb
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
cfg80211              565248  2 mac80211,rtlwifi
ideapad_laptop         24576  0
btbcm                  16384  1 btusb
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
btintel                16384  1 btusb
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
bluetooth             520192  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
input_leds             16384  0
joydev                 20480  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
edac_mce_amd           24576  0
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  1 snd
serio_raw              16384  0
fam15h_power           16384  0
shpchp                 36864  0
edac_core              53248  0
k10temp                16384  0
acpi_als               16384  0
i2c_piix4              24576  0
ccp                    36864  0
kfifo_buf              16384  1 acpi_als
industrialio           57344  2 acpi_als,kfifo_buf
mac_hid                16384  0
tpm_crb                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
rtsx_usb_sdmmc         28672  0
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  3
psmouse               126976  0
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon
drm_kms_helper        147456  1 radeon
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   360448  51 ttm,drm_kms_helper,radeon
r8169                  81920  0
ahci                   36864  3
mii                    16384  1 r8169
libahci                32768  1 ahci
video                  40960  1 ideapad_laptop
fjes                   28672  0

```

Its very unlikely that its my wifi, i couldnt test it with any other but my other linux device (rpi) works just fine with it and i am not having any issues with any other devices connected to the internet. also ive given it a new local ip and all that which didnt really work.

---

### Post by xaotic2 on 2016-08-17
bump

---

### Post by wildmanne39 on 2016-08-18
Log into your router and change 802.11n to 802.11g and see if that makes it stable it should.
Thanks

---

### Post by xaotic2 on 2016-08-18
Thanks again for the reply, altough can you be a bit more specific? I am not too sure what you mean by that.
Thank you!

Edit:
Nevermind, I did that altough both 802.11n and 802.11g were activated as a feature of the router..
But after all this has not changed anything regarding my problem.

---

### Post by wildmanne39 on 2016-08-18
Are they both still active? or did you change it to just 802.11g only to see if that works?
Thanks

---

### Post by xaotic2 on 2016-08-18
> **Wild Man said:**
> Are they both still active? or did you change it to just 802.11g only to see if that works?
Thanks
ive tried either and both at the same time

---

### Post by xaotic2 on 2016-08-21
bump

---

### Post by xaotic2 on 2016-08-22
bump once again, i do not have an eth0 nor wlan0 interface, is that bad?
It worked yesterday evening for some time once again but now it doesnt anymore.

---

