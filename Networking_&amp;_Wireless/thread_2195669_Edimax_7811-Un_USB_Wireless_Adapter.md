---
title: "Edimax 7811-Un USB Wireless Adapter"
date: 2013-12-25
forum: Networking &amp; Wireless
---

### Post by jeffroaltiere1 on 2013-12-25
Hey. So recently, I got a new wireless adaptor for my PC. It's an old Dell E310, and I tried using it on such, but it didn't work. I couldn't find much on the manufacturer's website that would help. Could anyone help me out here?

Oh, also, the adaptor did come with a disk.

---

### Post by mörgæs on 2013-12-26
Which version of Buntu are you using?

---

### Post by jeffroaltiere1 on 2014-01-17
I'm using 13.10.

---

### Post by mörgæs on 2014-01-18
- and the full name of the Edimax adapter? 

In general you should post much more information. Noone can help you based upon what has been posted so far.

---

### Post by praseodym on 2014-01-18
Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lsusb #with the stick plugged in!
lsmod
iwconfig
cat /etc/resolv.conf
```
Does LAN work?

---

### Post by jeffroaltiere1 on 2014-01-18
I'm using an Edimax 7811-Un. 

As for the commands ran:

lsub
```
Bus 001 Device 011: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 001 Device 004: ID 046d:0991 Logitech, Inc. QuickCam Pro for Notebooks
Bus 001 Device 010: ID 0930:6533 Toshiba Corp. 512M Stick
Bus 001 Device 008: ID 1bcf:053a Sunplus Innovation Technology Inc. Targa Silvercrest OMC807-C optische Funkmaus
Bus 001 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 059b:0032 Iomega Corp. Zip 250 (Ver 2)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

lsmod:

```
Module                  Size  Used by
nls_iso8859_1          12617  1 
parport_pc             31981  0 
ppdev                  17391  0 
joydev                 17097  0 
rfcomm                 53664  0 
bnep                   18959  2 
bluetooth             323656  10 bnep,rfcomm
arc4                   12536  2 
hid_generic            12492  0 
gpio_ich               13229  0 
rtl8192cu              66675  0 
dcdbas                 14383  0 
rtl_usb                18072  1 rtl8192cu
rtlwifi                52621  2 rtl_usb,rtl8192cu
rtl8192c_common        47173  1 rtl8192cu
ip6t_REJECT            12826  1 
xt_hl                  12465  6 
ip6t_rt                13259  3 
mac80211              517444  3 rtl_usb,rtlwifi,rtl8192cu
nf_conntrack_ipv6      18450  7 
binfmt_misc            13140  1 
nf_defrag_ipv6         26064  1 nf_conntrack_ipv6
ipt_REJECT             12485  1 
xt_LOG                 17446  10 
xt_limit               12541  13 
xt_tcpudp              12756  18 
xt_addrtype            12563  4 
nf_conntrack_ipv4      14492  7 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_conntrack           12664  14 
prism2_usb            185205  0 
r8712u                158680  0 
cfg80211              401762  3 mac80211,rtlwifi,prism2_usb
usb_storage            48294  1 
uvcvideo               71309  0 
usbhid                 47361  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
hid                    87370  2 hid_generic,usbhid
videodev              107508  2 uvcvideo,videobuf2_core
snd_usb_audio         119227  1 
snd_usbmidi_lib        24326  1 snd_usb_audio
ip6table_filter        12711  1 
ip6_tables             17819  1 ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12645  0 
nf_nat                 25588  1 nf_nat_ftp
nf_conntrack_ftp       14056  1 nf_nat_ftp
nf_conntrack           82913  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12706  1 
ip_tables              17987  1 iptable_filter
x_tables               22067  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
snd_hda_codec_idt      44605  1 
microcode              18830  0 
snd_hda_intel          42658  3 
snd_hda_codec         164003  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  2 snd_usb_audio,snd_hda_codec
snd_pcm                89488  3 snd_usb_audio,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  2 snd_usbmidi_lib,snd_seq_midi
psmouse                90642  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
serio_raw              13189  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
snd                    60790  20 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i915                  594380  3 
video                  18777  1 i915
drm_kms_helper         46867  1 i915
soundcore              12600  1 snd
lpc_ich                16864  0 
mac_hid                13037  0 
drm                   242400  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
e100                   35945  0 
mii                    13654  1 e100

```

iwconfig:

```
wlan2     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

```

cat /etc/resolv.conf:
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

```

I cannot find whether LAN works or not. My router is too far away and I don't have a long enough cord to run to it.

---

### Post by chili555 on 2014-01-18
@praseodym--

I think he needs to remove from /etc/modules or blacklist rtl8192cu as it doesn't drive his device.> 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]This driver does, but you and I would structure the procedure a bit differently: [http://askubuntu.com/questions/364972/realtek-8188cus-doesnt-work](http://askubuntu.com/questions/364972/realtek-8188cus-doesnt-work)

Here is my test:```
$ modinfo rtl8192cu-fixes/8192cu.ko | grep 7811
alias:          usb:v[COLOR="#FF0000"]7392[/COLOR]p[COLOR="#FF0000"]7811[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*

```We now return you to your regularly scheduled guru!

---

### Post by praseodym on 2014-01-19
Download these files and save them in "Downloads" and extraxt the tarball there:

[https://dl.dropboxusercontent.com/u/2902662/rtl8192cu-fixes.tar.gz](https://dl.dropboxusercontent.com/u/2902662/rtl8192cu-fixes.tar.gz)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu4_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu4_all.deb)

Installation:
```

cd ~/Downloads/
sudo dpkg -i *.deb
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.8
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot

Edit: New Link!

---

### Post by jeffroaltiere1 on 2014-01-20
Okay. It took a while, but after a few long minutes, it all worked. I rebooted, and now I'm connected. Thank you all so much for your help!:D

---

### Post by praseodym on 2014-01-20
Check if all necessary stuff is installed:
```

sudo apt-get install linux-headers-generic linux-headers-$(uname -r) build-essential
```
Edit: With this the driver will be compiled automatically after a kernel upgrade

---

