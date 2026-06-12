---
title: "slow internet myBro Wimax Greenpacket 1Mbps"
date: 2013-10-01
forum: Networking &amp; Wireless
---

### Post by JuanLuna on 2013-10-01
Hi, is it normal in linux to have slow internet? coz when im using my other OS, my internet connection speed is x 50 i guess (i can stream within second, download hundreds of mb in less than 3mins-up, but when im using linux its kinda slow as in super slow). i tried downloading & install vlc last night and it took almost 5hours to complete . btw now im installing wine and it say there that i should run this command first "sudo apt-get update" and its been almost 3hours since i started.   
[ATTACH=CONFIG]246676[/ATTACH]


is there any tweak or set-up to maximize the speed of my internet. thanks in advance

---

### Post by varunendra on 2013-10-02
Is it a USB wireless adapter? If so, please post the output of-
```
lsusb
uname -mr
nm-tool
iwconfig
lsmod
```

If it is an internal card, then replace the first (lsusb) command with -
```
lspci -nnk | grep -iA2 net
```

While posting back the outputs, please use code tags (please follow the "Using Code Tags" link in my signature to see how).

---

### Post by JuanLuna on 2013-10-02
Sorry for the late reply, kinda mess my ubuntu last night and it didnt boot through GUI & just finish reinstalling it. Btw thanks in advance 

lspci -nnk | grep -iA2 net
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7641]
    Kernel driver in use: r8169
```

uname -mr
```
3.8.0-29-generic x86_64
```

nm-tool
```
NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        8C:89:A5:68:8F:34

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.15.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.15.1

    DNS:             121.1.3.88
    DNS:             121.1.3.20
    DNS:             121.1.3.250


```

iwconfig
```
eth0      no wireless extensions.

lo        no wireless extensions.
```

lsmod
```
Module                  Size  Used by
nls_utf8               12557  1 
udf                    94509  1 
crc_itu_t              12707  1 udf
nls_iso8859_1          12713  0 
bnep                   18258  2 
rfcomm                 47864  0 
bluetooth             247024  10 bnep,rfcomm
parport_pc             28284  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     37434  1 
gspca_ov519            49636  0 
gspca_main             28738  1 gspca_ov519
videodev              130053  2 gspca_ov519,gspca_main
radeon                960918  3 
snd_hda_codec_realtek    79916  1 
snd_hda_intel          44339  5 
snd_hda_codec         141716  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
kvm_amd                60205  0 
kvm                   455932  1 kvm_amd
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ghash_clmulni_intel    13259  0 
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
aesni_intel            55495  0 
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    84051  1 radeon
drm_kms_helper         49597  1 radeon
ablk_helper            13597  1 aesni_intel
sp5100_tco             13870  0 
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
drm                   287564  5 radeon,ttm,drm_kms_helper
lrw                    13294  1 aesni_intel
aes_x86_64             17255  1 aesni_intel
xts                    12922  1 aesni_intel
gf128mul               14951  2 lrw,xts
i2c_piix4              13459  0 
i2c_algo_bit           13564  1 radeon
snd                    69533  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17613  0 
mac_hid                13253  0 
serio_raw              13215  0 
soundcore              12680  1 snd
k10temp                13173  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
edac_core              62724  0 
edac_mce_amd           23343  0 
fam15h_power           13166  0 
microcode              23017  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_generic            12540  0 
usbhid                 47346  0 
hid                   105549  2 hid_generic,usbhid
pata_acpi              13038  0 
usb_storage            61749  0 
r8169                  68716  0 
pata_atiixp            13242  0 
ahci                   25879  4 
libahci                31606  1 ahc
```

---

### Post by varunendra on 2013-10-02
I thought it is some sort of USB wireless adapter.

Is it the kind of modem that itself receives signal wirelessly and transmits it to the computer via a cable connection (Ethernet)? If so, please post the outputs of -
```
ifconfig
sudo ethtool eth0
```
..and maybe a description of the setup would be helpful to my understanding.

---

### Post by JuanLuna on 2013-10-03
Hi, :) sorry again for the late reply, just got home.. btw the next code says error.

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 8c:89:a5:68:8f:34  
          inet addr:192.168.15.2  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::8e89:a5ff:fe68:8f34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15786437 (15.7 MB)  TX bytes:967597 (967.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44814 (44.8 KB)  TX bytes:44814 (44.8 KB)


```

sudo ethtool eth0
```
sudo: ethtool: command not found
```

---

### Post by varunendra on 2013-10-03
> **JuanLuna said:**
> sudo ethtool eth0
```
sudo: ethtool: command not found
```
It must have prompted you to install it, do so and try again -
[code]sudo apt-get install ethtool
sudo ethtool eth0[code]

For now, please try disabling IPv6 following this [post=12640479]post[/post]. If this alone does not help, also try setting MTU in your connection settings in Network Manager to 1492 (currently it would be set to "automatic"). If these didn't help, we need to look at the output of ethtool, as well as ifconfig again.

---

