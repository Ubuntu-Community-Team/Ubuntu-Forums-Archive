---
title: "Lubuntu 12.04 LTS - Bluetooth and Dell D600"
date: 2014-07-08
forum: Networking &amp; Wireless
---

### Post by bartek6 on 2014-07-08
Hello,

I'm new Lubuntu user and I'm using Dell D600 notebook. I want to connect my computer with Bluetooth device, but I can't do it. In Bluetooth Manager I can't turn it on. Can anybody help me to solve this problem?

---

### Post by jeremy31 on 2014-07-08
Open terminal (CTRL+ALT+t) and enter these commands
```
rfkill list
``````
lsusb
``````
lsmod
```
That should be a good start to figuring it out

---

### Post by bartek6 on 2014-07-08
**1) rfkill list**

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


[B]
2) lsusb[/B]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 09da:001a A4 Tech Co., Ltd Wireless Mouse & RXM-15 Receiver



**3) lsmod**
Module                  Size  Used by
bnep                   17830  2 
rfcomm                 38139  4 
bluetooth             158447  10 bnep,rfcomm
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13175  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  12 
xt_tcpudp              12531  18 
xt_addrtype            12596  4 
xt_state               12514  14 
snd_intel8x0           33455  2 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
ip6table_filter        12711  1 
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
radeon                738089  2 
snd_seq_midi           13132  0 
joydev                 17393  0 
ttm                    65344  1 radeon
nf_nat_ftp             12595  0 
nf_nat                 24959  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
snd_rawmidi            25424  1 snd_seq_midi
drm_kms_helper         45466  1 radeon
nf_conntrack_ftp       13183  1 nf_nat_ftp
arc4                   12473  2 
b43legacy             127222  0 
dcdbas                 14098  0 
pcmcia                 39826  0 
snd_seq_midi_event     14475  1 snd_seq_midi
drm                   197641  4 radeon,ttm,drm_kms_helper
nf_conntrack           73847  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
ip_tables              18106  1 iptable_filter
snd_timer              28931  2 snd_pcm,snd_seq
x_tables               22011  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
psmouse                97180  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 radeon
soundcore              14635  1 snd
serio_raw              13027  0 
mac80211              436493  1 b43legacy
cfg80211              178877  2 b43legacy,mac80211
ppdev                  12849  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
video                  19115  0 
mac_hid                13077  0 
parport_pc             32114  1 
shpchp                 32265  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
hid_a4tech             12590  0 
tg3                   141465  0 
ssb                    50691  1 b43legacy
usbhid                 41937  0 
hid                    81731  2 hid_a4tech,usbhid

---

### Post by mörgæs on 2014-07-08
Lubuntu 12.04 is not LTS, in fact it's out of support. Better to begin with a fresh install of 14.04, which is LTS.

---

### Post by bartek6 on 2015-06-10
> **mörgæs said:**
> Lubuntu 12.04 is not LTS, in fact it's out of support. Better to begin with a fresh install of 14.04, which is LTS.

I've forgot about my problem with bluetooth. I've now Lubuntu 14.04.2 LTS. Herewith outputs of commands:
**1) lsusb**
```

Bus 001 Device 003: ID 04f3:0216 Elan Microelectronics Corp. 
Bus 001 Device 002: ID 413c:0058 Dell Computer Corp. Port Replicator
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

**2) lsusb**

```
Module                  Size  Used by
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342208  10 bnep,rfcomm
binfmt_misc            13140  1 
snd_intel8x0           33110  1 
snd_ac97_codec        105709  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
arc4                   12536  2 
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
gpio_ich               13229  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
dell_laptop            17808  0 
b43                   356470  0 
radeon               1420720  2 
dcdbas                 14448  1 dell_laptop
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
bcma                   42043  1 b43
ttm                    80983  1 radeon
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
pcmcia                 51828  0 
snd_timer              28584  2 snd_pcm,snd_seq
drm_kms_helper         48868  1 radeon
mac80211              546118  1 b43
snd                    60939  10 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
drm                   244037  4 ttm,drm_kms_helper,radeon
cfg80211              409394  2 b43,mac80211
joydev                 17101  0 
yenta_socket           40201  0 
serio_raw              13230  0 
soundcore              12600  1 snd
pcmcia_rsrc            18319  1 yenta_socket
i2c_algo_bit           13197  1 radeon
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
lpc_ich                16864  0 
shpchp                 32128  0 
video                  18903  0 
mac_hid                13037  0 
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47070  0 
hid                    87604  2 hid_generic,usbhid
tg3                   152160  0 
psmouse                95353  0 
ptp                    18445  1 tg3
ssb                    51854  1 b43
pata_acpi              12886  0 
pps_core               18799  1 ptp
```


**3) rfkill list**
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

### Post by jeremy31 on 2015-06-10
I see no signs of a bluetooth adapter being present, did it ever work?

---

### Post by bartek6 on 2015-06-11
> **jeremy31 said:**
> I see no signs of a bluetooth adapter being present, did it ever work?

Direct hit jeremy31! There was no Bluetooth module inserted in slot. It was answer, why I can't use Blutooth on my notebook. Fortunately I had second broken Dell D600 where I've found Bluetooth module. Now it works perfectly. :p

---

