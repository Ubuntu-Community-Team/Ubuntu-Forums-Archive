---
title: "Wired network problem"
date: 2014-03-30
forum: Networking &amp; Wireless
---

### Post by nautiman on 2014-03-30
Hi,  Ubuntu 13.04.  After using wireless, my wired connection refuses to connect.  It shows as connected (with the arrows, and sending and receiving data packets)  but gives message that DNS fails.   There is no DNS failure with wireless connection.  Any suggestions ?

---

### Post by praseodym on 2014-03-30
Hi,

does it work alone after rebooting? Please show these terminal outputs:
```

uname -a
lspci -nnk | grep -iA2 net
ifconfig -a
lsmod
cat /etc/resolv.conf
```
13.04 was running out of support in January, so I recommend upgrading to 13.10.

---

### Post by nautiman on 2014-04-07
Sorry - I am on 13.10 !!   Here's the output from those commands (taken when on a wireless connection...?) :
Uname -a
paul@paul-Lenovo-B560:~$ uname -a
Linux paul-Lenovo-B5603.11.0-19-generic #33-Ubuntu SMP Tue Mar 11 18:48:32 UTC 2014 i686i686 i686 GNU/Linux
paul@paul-Lenovo-B560:~$ lspci -nnk |grep -iA2 net
03:00.0 Ethernet controller [0200]:Qualcomm Atheros AR8131 Gigabit Ethernet [1969:1063] (rev c0)
	Subsystem: Lenovo Device [17aa:3956]
	Kernel driver in use: atl1c
04:00.0 Network controller [0280]:Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter[14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device[14e4:0510]
	Kernel driver in use: wl
paul@paul-Lenovo-B560:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddrf0:de:f1:2b:e4:b9  
          UP BROADCAST MULTICAST MTU:1500  Metric:1
          RX packets:0 errors:0dropped:0 overruns:0 frame:0
          TX packets:0 errors:0dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TXbytes:0 (0.0 B)
eth1      Link encap:Ethernet  HWaddrac:81:12:16:9e:27  
          inet addr:192.168.1.229 Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr:fe80::ae81:12ff:fe16:9e27/64 Scope:Link
          UP BROADCAST RUNNINGMULTICAST  MTU:1500  Metric:1
          RX packets:72298 errors:0dropped:0 overruns:0 frame:1230427
          TX packets:67023 errors:0dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:61441118 (61.4 MB) TX bytes:15435195 (15.4 MB)
          Interrupt:17 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128Scope:Host
          UP LOOPBACK RUNNING MTU:65536  Metric:1
          RX packets:3159 errors:0dropped:0 overruns:0 frame:0
          TX packets:3159 errors:0dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:328943 (328.9 KB) TX bytes:328943 (328.9 KB)
paul@paul-Lenovo-B560:~$ lsmod
Module                  Size  Used by
cuse                   13074  3 
dm_crypt               22316  0 
joydev                 17097  0 
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18959  2 
intel_powerclamp       14239  0 
coretemp               13195  0 
kvm                   368975  0 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1uvcvideo
videobuf2_memops       13170  1videobuf2_vmalloc
videobuf2_core         39125  1uvcvideo
videodev              107508  2uvcvideo,videobuf2_core
rfcomm                 53664  12 
dm_multipath           22402  0 
scsi_dh                14458  1dm_multipath
snd_hda_codec_realtek    50315  1 
snd_hda_intel          42658  3 
lib80211_crypt_tkip    17456  0 
snd_hda_codec         164003  2snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1snd_hda_codec
snd_pcm                89488  2snd_hda_codec,snd_hda_intel
microcode              18894  0 
psmouse                90642  0 
snd_page_alloc         14230  2snd_pcm,snd_hda_intel
serio_raw              13189  0 
wl                   3999620  0 
intel_ips              18055  0 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1snd_seq_midi
btusb                  23443  0 
bluetooth             323656  22bnep,btusb,rfcomm
lib80211               14040  2wl,lib80211_crypt_tkip
cfg80211              401762  1 wl
snd_rawmidi            25094  1snd_seq_midi
lpc_ich                16864  0 
snd_seq                55383  2snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3snd_seq,snd_rawmidi,snd_seq_midi
ideapad_laptop         17974  0 
sparse_keymap          13708  1ideapad_laptop
snd_timer              24447  2snd_pcm,snd_seq
snd                    60790  16snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                 13933  0 
mei                    66411  1 mei_me
soundcore              12600  1 snd
mac_hid                13037  0 
lp                     13299  0 
binfmt_misc            13140  1 
parport                40795  3lp,ppdev,parport_pc
btrfs                 808940  0 
zlib_deflate           26445  1 btrfs
raid6_pq               97455  1 btrfs
libcrc32c              12543  1 btrfs
dm_raid45              75297  0 
xor                    26221  2btrfs,dm_raid45
dm_mirror              21715  0 
dm_region_hash         15984  1dm_mirror
dm_log                 18072  3dm_region_hash,dm_mirror,dm_raid45
ums_realtek            17733  0 
usb_storage            48294  1ums_realtek
i915                  594442  7 
i2c_algo_bit           13197  1 i915
drm_kms_helper         46867  1 i915
drm                   242400  3i915,drm_kms_helper
ahci                   25579  2 
atl1c                  40949  0 
libahci                26619  1 ahci
wmi                    18590  0 
video                  18777  1 i915
paul@paul-Lenovo-B560:~$ cat/etc/resolv.conf
# Dynamic resolv.conf(5) file for glibcresolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND --YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1 

Cheers.

---

### Post by praseodym on 2014-04-08
The driver is loaded, lets check
```

sudo apt-get install ethtool
sudo ethtool eth0
```

---

### Post by nautiman on 2014-04-13
Here's what I got :

paul@paul-Lenovo-B560:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: Unknown!
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x0000003f (63)
			       drv probe link timer ifdown ifup
	Link detected: no

....................does this help ?

---

### Post by praseodym on 2014-04-13
> ```
 Speed: Unknown!
...
 Link detected: no
```
Try:
```

sudo ethtool -s eth0 speed 100 duplex full
sudo ethtool eth0
```
Link detected "no" means, that the cable may be checked.

---

### Post by nautiman on 2014-04-16
First I ran the command '[COLOR=#000000][FONT=Ubuntu Mono]sudo ethtool -s eth0 speed 100 duplex full' and had to input my password.  And then :[/FONT][/COLOR] 

paul@paul-Lenovo-B560:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: Unknown!
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x0000003f (63)
			       drv probe link timer ifdown ifup
	Link detected: no

This was all done while on a wifi link.   Cheers.

---

### Post by praseodym on 2014-04-16
So, lets start with
```

sudo ethtool -s etho autoneg off
sudo ethtool -s eth0 speed 10 duplex full
sudo ethtool -s eth0 speed 10 duplex half

```Please check after each command:
```

sudo ethtool eth0
```

---

### Post by baphomet2 on 2014-04-16
I'm kind of confused.  The output from your ifconfig -a doesn't show a wireless connection.  I see eth0 that is up but has no address or any traffic, and then eth1 that does have an address and a ton of traffic.  Can you do a sudo ethtool eth1 and paste the output?

---

### Post by praseodym on 2014-04-16
eth1 is the wireless interface of the STA driver

---

### Post by baphomet2 on 2014-04-16
Thanks praseodym.  I've never seen that before.  So eth0 isn't pulling an address and doesn't see a cable/link.  Is there a link light?

---

