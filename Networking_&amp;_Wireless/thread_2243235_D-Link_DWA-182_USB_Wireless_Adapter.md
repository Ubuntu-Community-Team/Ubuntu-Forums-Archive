---
title: "D-Link DWA-182 USB Wireless Adapter"
date: 2014-09-07
forum: Networking &amp; Wireless
---

### Post by rickey2 on 2014-09-07
[SIZE=3]Will Ubuntu ever include these drivers. I've tried to install them 2 or 3 different ways but still can't get them to run ![/SIZE]

---

### Post by praseodym on 2014-09-07
Please show the outputs of these commands:

```
lsusb
lsmod
```

---

### Post by rickey2 on 2014-09-08
[SIZE=2]**[SIZE=3]Tell me what you mean ?  I am a newbie when it comes to Ubuntu ! I don't know what to do with these commands ![/SIZE]**[/SIZE]

---

### Post by praseodym on 2014-09-08
Please open a terminal with CTRL+ALT+T and run the commands.

---

### Post by rickey2 on 2014-09-09
Bus 001 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 003 Device 002: ID 2001:3315 D-Link Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

---

### Post by rickey2 on 2014-09-09
Module                  Size  Used by
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391136  10 bnep,rfcomm
binfmt_misc            17468  1 
snd_hda_codec_hdmi     46368  4 
ip6t_REJECT            12939  1 
xt_hl                  12521  6 
ip6t_rt                13537  3 
nf_conntrack_ipv6      18894  8 
nf_defrag_ipv6         34768  1 nf_conntrack_ipv6
ipt_REJECT             12541  1 
nvidia              10675249  49 
xt_LOG                 17717  10 
xt_limit               12711  13 
xt_tcpudp              12884  18 
xt_addrtype            12635  4 
nf_conntrack_ipv4      15012  8 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
xt_conntrack           12760  16 
snd_hda_codec_via      27860  1 
ip6table_filter        12815  1 
ip6_tables             27025  1 ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12770  0 
nf_nat                 21841  1 nf_nat_ftp
nf_conntrack_ftp       18638  1 nf_nat_ftp
joydev                 17381  0 
nf_conntrack           96976  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12810  1 
hid_generic            12548  0 
ip_tables              27239  1 iptable_filter
x_tables               34059  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
snd_hda_intel          56451  5 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
usbhid                 52570  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
hid                   106148  3 hid_generic,usbhid
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
coretemp               13435  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69322  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
serio_raw              13462  0 
drm                   303102  2 nvidia
i2c_nforce2            13221  0 
soundcore              12680  1 snd
asus_atk0110           18657  0 
mac_hid                13205  0 
parport_pc             32701  1 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
usb_storage            62209  0 
pata_acpi              13038  0 
forcedeth              67509  0 
ahci                   25819  2 
libahci                32716  1 ahci
pata_amd               18225  0

---

### Post by praseodym on 2014-09-09
You need a new driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential git
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux
cd rtl8812AU_8821AU_linux
make
sudo make install
```

---

### Post by rickey2 on 2014-09-10
Thank You !!  Works pretty good !  Running at 867 Mb/s

---

### Post by praseodym on 2014-09-10
Glad it worked. After a kernel update you need to compile again:
```

cd rtl8812AU_8821AU_linux
make clean
make
sudo make uninstall
sudo make install
```

---

### Post by rickey2 on 2014-09-15
No such directory or file

---

### Post by praseodym on 2014-09-15
Did you remove the folder? If so, download it again:

```
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux
```

---

### Post by rickey2 on 2014-09-20
[SIZE=3]I can't stay connect to good. I found that the linux is written for USB 2.0 but the adapter is for USB 3.0 ...now does make a lot of since ?[/SIZE]

---

### Post by praseodym on 2014-09-21
Well, this is about current uptake. Any chance for an USB-hub with its own current source?

---

