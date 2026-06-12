---
title: "Realtek 8822be Kubuntu 19.04 WIFI works with &quot;Try Kubuntu&quot; but doesn't once the OS in"
date: 2019-08-24
forum: Networking &amp; Wireless
---

### Post by sashatheduckling on 2019-08-24
Hi  guys!

Firstly, let me inroduce the main characters (at least I think so):
PC: Asus Vivobook F510QA
OS: Kubuntu 19.04 (latest one, fully updated and upragded).
WIFI/Bluetooth module: Realtek 8822be

The problem itself: I wanted to install the latest version of Kubuntu on  my new laptop. Before doing this, I decided to run a demo  version of  this OS from the bootable USB drive using the "Try Kubuntu" feature and  everything worked fine for me so I decided to move on. However, after  installing the Kubuntu, I found out that my WIFI wasn't working (while  Bluetooth running the same module was totally OK). I've checked the  module and everything seems to be fine: the module isn't bloked by  neither the hard- nor the software, it has the power supply, the driver  and so on. Seems like the module is working but doesn't scan for any  networks (connection via the command line doesn't work as well).

I started digging the issue through the web but wans't able to find any  matching case with the solution.The only difference between the "Try  Kubuntu" and the installed OS I managed to find if that the installed  one is missing this part when I check the dmesg:

```

[  133.558397] wlp1s0: authenticate with 06:18:d6:cd:fa:fb
[  134.086760] wlp1s0: send auth to 06:18:d6:cd:fa:fb (try 1/3)
[  134.094195] wlp1s0: authenticated
[  134.094790] wlp1s0: associating with AP with corrupt beacon
[  134.098331] wlp1s0: associate with 06:18:d6:cd:fa:fb (try 1/3)
[  134.105964] wlp1s0: RX AssocResp from 06:18:d6:cd:fa:fb (capab=0x31 status=0 aid=8)
[  134.106479] wlp1s0: associated
[  138.117900] wlp1s0: deauthenticated from 06:18:d6:cd:fa:fb (Reason: 2=PREV_AUTH_NOT_VALID)
[  173.512044] wlp1s0: authenticate with 06:18:d6:cd:fa:fb
[  173.512363] wlp1s0: send auth to 06:18:d6:cd:fa:fb (try 1/3)
[  173.520196] wlp1s0: authenticated
[  173.520464] wlp1s0: associating with AP with corrupt beacon
[  173.522184] wlp1s0: associate with 06:18:d6:cd:fa:fb (try 1/3)
[  173.530060] wlp1s0: RX AssocResp from 06:18:d6:cd:fa:fb (capab=0x31 status=0 aid=9)
[  173.530316] wlp1s0: associated
[  173.570946] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready

```

The output of wildmanne39's "Wireless Script" is attached.

Any help will be appreciated.

---

### Post by dbergst on 2019-08-24
[**[COLOR=#000000]sashatheduckling[/COLOR]**]("https://ubuntuforums.org/member.php?u=2130846"), I had some recent experience with this driver (pre-release version).  It appears from your wireless-info.tar.gz post that the rtw88 module may not be loaded.  Can you try running modprobe rtw88 and post back the results?

---

### Post by sashatheduckling on 2019-08-25
Hi @dbergst,

Sure. I tried running "modprobe rtw88" and "modprobe r8822be" but had no output for none: [[IMG]http://pix.toile-libre.org/upload/img/1566710191.png[/IMG]]("http://pix.toile-libre.org/?img=1566710191.png")

---

### Post by dbergst on 2019-08-26
> **sashatheduckling said:**
> Hi @dbergst,

Sure. I tried running "modprobe rtw88" and "modprobe r8822be" but had no output for none: [[IMG]http://pix.toile-libre.org/upload/img/1566710191.png[/IMG]]("http://pix.toile-libre.org/?img=1566710191.png")

Hi sashatheduckling.  r9922be is the old driver for the card, so you probably don't want it loaded at the same time as rtw88.  I believe the rtwpci driver may also need to be loaded first, so you may want to try:

modprobe rtwpci
modprobe rtw88

---

### Post by sashatheduckling on 2019-08-26
Hi, thanks for getting back to me.

I tried running the suggested commands [[img]http://pix.toile-libre.org/upload/img/1566839082.png[/img]](http://pix.toile-libre.org/?img=1566839082.png) and restarted the network manager -- unfortunately, it didn't help.

---

### Post by dbergst on 2019-08-27
On second thought you should need to run those commands as root, i.e.,
sudo modprobe rtwpci
sudo modprobe rtw88

Aside from that have you checked to see if your wireless interface is enabled in your UEFI / BIOS?

---

### Post by sashatheduckling on 2019-08-28
Sure, I tried running the commands as root. 
As for the BIOS settings, the only thing related to the network looks like this: 

[[img]http://pix.toile-libre.org/upload/img/1566990612.png"]http://pix.toile-libre.org/?img=1566990612.png][img]http://pix.toile-libre.org/upload/img/1566990612.png[/img]]([URL="http://pix.toile-libre.org/?img=1566990612.png)
[/URL] 

[[img]http://pix.toile-libre.org/upload/img/1566990632.png[/img][/url"]http://pix.toile-libre.org/?img=1566990632.png][img]http://pix.toile-libre.org/upload/img/1566990632.png]([URL="http://pix.toile-libre.org/?img=1566990632.png)[/img][/url]

---

### Post by dbergst on 2019-08-28
As I remember I had to blacklist the old r8822be driver in order for the new rtw88 driver to work.  Also, if you could post the output of the rfkill command we can see if your wifi interface is beling blocked.

---

### Post by sashatheduckling on 2019-08-28
Thanks for not leaving me alone :) 

I’ve blacklisted the module you mentioned. To install the new module , I tried “sudo modprobe ***” (as shown in my previous replies). Was it a correct way to install the new modules?

According to the output of rfkill,  my “WiFi” isn’t being blocked by neither the software nor the hardware. 

Actually, this issue could have been resolved by getting a USB adapter for the wireless network, but it’s pretty strange so I decided to figure it out. The WiFi works perfectly on windows 7/10 and with “try Kubuntu (Ubuntu)” option, but fails to work once I install one of these OS. This odd behavior got me curious, confused and a bit angry at the same time :)

---

### Post by dbergst on 2019-08-29
It sounds like you are close to getting the wifi working.  I'm a bit perplexed that we have not solved the issue though.  Looking back at my notes it appears that I gave you some inaccurate instructions.  Please use the lsmod command to confirm that the r8822be (blacklisted) is not loaded.  You can then load/unload the rtw88 module using the rtwpci module.

Sorry for any confusion on my part.

---

### Post by sashatheduckling on 2019-08-29
Here is the output of the lsmod command:

```

Module                  Size  Used by
rfcomm                 77824  16
ipheth                 16384  0
bnep                   24576  2
nls_iso8859_1          16384  1
edac_mce_amd           28672  0
kvm_amd                94208  0
ccp                    86016  1 kvm_amd
snd_hda_codec_generic    77824  1
kvm                   626688  1 kvm_amd
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_hda_codec_hdmi     53248  1
irqbypass              16384  1 kvm
snd_hda_intel          40960  6
snd_hda_codec         131072  3 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel
snd_hda_core           86016  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               102400  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
crct10dif_pclmul       16384  1
arc4                   16384  2
crc32_pclmul           16384  0
snd_seq_midi           20480  0
ghash_clmulni_intel    16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
joydev                 24576  0
snd_rawmidi            36864  1 snd_seq_midi
rtwpci                 24576  0
rtw88                 413696  1 rtwpci
btusb                  49152  0
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
btrtl                  20480  1 btusb
btbcm                  16384  1 btusb
btintel                24576  1 btusb
aesni_intel           372736  0
mac80211              806912  2 rtwpci,rtw88
bluetooth             557056  41 btrtl,btintel,btbcm,bnep,btusb,rfcomm
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
asus_nb_wmi            28672  0
aes_x86_64             20480  1 aesni_intel
snd_timer              36864  2 snd_seq,snd_pcm
asus_wmi               28672  1 asus_nb_wmi
crypto_simd            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
input_leds             16384  0
sparse_keymap          16384  1 asus_wmi
glue_helper            16384  1 aesni_intel
hid_multitouch         24576  0
ecdh_generic           28672  1 bluetooth
snd                    81920  21 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_pcm,snd_rawmidi
serio_raw              20480  0
wmi_bmof               16384  0
cfg80211              671744  2 mac80211,rtw88
k10temp                16384  0
fam15h_power           16384  0
soundcore              16384  1 snd
uvcvideo               98304  0
videobuf2_vmalloc      20480  1 uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_common       49152  2 videobuf2_v4l2,uvcvideo
8250_dw                20480  0
videodev              200704  3 videobuf2_v4l2,uvcvideo,videobuf2_common
asus_wireless          20480  0
mac_hid                16384  0
media                  53248  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
sch_fq_codel           20480  6
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                45056  2
amdgpu               3518464  31
hid_generic            16384  0
chash                  16384  1 amdgpu
amd_iommu_v2           20480  1 amdgpu
gpu_sched              32768  1 amdgpu
i2c_algo_bit           16384  1 amdgpu
ttm                   102400  1 amdgpu
drm_kms_helper        180224  1 amdgpu
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
ahci                   40960  4
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
libahci                32768  1 ahci
drm                   475136  13 gpu_sched,drm_kms_helper,amdgpu,ttm
i2c_piix4              28672  0
wmi                    28672  2 asus_wmi,wmi_bmof
i2c_hid                28672  0
video                  45056  1 asus_wmi
hid                   126976  3 i2c_hid,hid_multitouch,hid_generic

```

---

### Post by sashatheduckling on 2019-08-29
I'm a bit concerned about the nmcli result:

```

enp0s16u3c4i2: connected to Wired connection 1
        "Apple iPhone5/5C/5S/6"
        ethernet (ipheth), 3E:AB:8E:A5:CC:CE, hw, mtu 1500
        ip4 default
        inet4 172.20.10.12/28
        route4 0.0.0.0/0
        route4 172.20.10.0/28
        route4 169.254.0.0/16
        inet6 fe80::d71c:7d5b:94d1:e077/64
        route6 fe80::/64
        route6 ff00::/8

wlp1s0: disconnected
        "Realtek RTL8822BE 802.11a/b/g/n/ac"
        wifi (rtw_pci), DC:F5:05:77:32:CB, hw, mtu 1500

lo: unmanaged
        "lo"
        loopback (unknown), 00:00:00:00:00:00, sw, mtu 65536

DNS configuration:
        servers: 172.20.10.1
        interface: enp0s16u3c4i2

Use "nmcli device show" to get complete information about known devices and
"nmcli connection show" to get an overview on active connection profiles.

Consult nmcli(1) and nmcli-examples(5) manual pages for complete usage details.

```

```

simon@simon:~$ nmcli radio
WIFI-HW  WIFI     WWAN-HW  WWAN    
enabled  enabled  enabled  enabled 
simon@simon:~$ iwlist wlp1s0 scanning
wlp1s0    No scan results

```

---

### Post by dbergst on 2019-08-30
nmcli shows your device is disconnected and your wired connection is active.  What happens when the wired interface is disconnected?

---

### Post by sashatheduckling on 2019-08-30
Hi dbergst, 

Nmcli works correctly with the wired connection: registers and displays each change of its state and so on, but fails with the wireless connection. 

I had to accept this fact and let the default WiFi go... :)
I’ve been playing around this issue for almost a week and it seems a bit to much for my busy work schedule. So I’m back to using the USB adapter (it comes with a special big and shiny “L” sign). Nevertheless, this tricky situation has taught me a lot about the Linux systems and I’m glad with this, especially, taking into account it was my first experience with this OS. 

And the last, but not the least important thing: I’d like to thank you for the helpful advices and the time you’ve spent in this thread, I appreciate it indeed.

---

