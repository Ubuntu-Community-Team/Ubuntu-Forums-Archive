---
title: "No wired network after reboot"
date: 2013-11-25
forum: Networking &amp; Wireless
---

### Post by childintime on 2013-11-25
I've got a problem that Ubuntu 13.10 sometimes does not see my Ethernet cable. I have cable coming into my laptop, and static IPv4 configured correctly and working most of the time. Now after I restart computer network disappears usually, and I need to shut down and turn on computer again for it to reappear. I've also got Windows 8 and connection is always stable without any problems.

Now recently, it started to disconnect even when I am using Ubuntu, but it's only 1 time this happened. Here is ifconfig after it disconnected:

```
eth0      Link encap:Ethernet  HWaddr 74:d0:2b:d9:be:7f            UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:18948 errors:0 dropped:7 overruns:0 frame:0
          TX packets:15050 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21101335 (21.1 MB)  TX bytes:2017247 (2.0 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:67443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5127506 (5.1 MB)  TX bytes:5127506 (5.1 MB)


wlan0     Link encap:Ethernet  HWaddr 6c:71:d9:91:64:cd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
Also keep in mind, all IPv4 settings are still there and everything is good, just no connection for some reason.
I tried different commands while disconnected but nothing seems to work. Do you know any commands which can resurrect/refresh wired network without the need to shut down of computer (and keep in mind reboot usually does not help)?

Thank you :-|

---

### Post by varunendra on 2013-11-26
Please install ethtool -
```
sudo apt-get install ethtool
```

Then post back the following outputs -
```
lspci -nnk | grep -iA2 net
lsmod
sudo ethtool eth0
```

---

### Post by childintime on 2013-11-26
lspci -nnk | grep -iA2 net```
mosquito@mosquito-K56CB:~/Desktop$ lspci -nnk | grep -iA2 net03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave Device [1a3b:2c97]
    Kernel driver in use: ath9k
--
04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1587]
    Kernel driver in use: r8169

```

lsmod```
mosquito@mosquito-K56CB:~/Desktop$ lsmodModule                  Size  Used by
8021q                  24353  0 
garp                   14313  1 8021q
stp                    12976  1 garp
mrp                    18471  1 8021q
llc                    14552  2 stp,garp
ipt_MASQUERADE         12880  0 
iptable_nat            13011  0 
nf_conntrack_ipv4      15012  1 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_nat_ipv4            13263  1 iptable_nat
nf_nat                 26653  3 ipt_MASQUERADE,nf_nat_ipv4,iptable_nat
nf_conntrack           91736  5 ipt_MASQUERADE,nf_nat,nf_nat_ipv4,iptable_nat,nf_conntrack_ipv4
ip_tables              27239  1 iptable_nat
x_tables               34059  2 ip_tables,ipt_MASQUERADE
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  12 
bnep                   19564  2 
binfmt_misc            17468  1 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17377  0 
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
snd_hda_intel          48171  6 
snd_hda_codec         188738  1 snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  3 snd_pcm,snd_seq
microcode              23518  0 
snd                    69141  19 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
arc4                   12608  2 
psmouse                97626  0 
serio_raw              13413  0 
ath9k                 151173  0 
ath9k_common           13859  1 ath9k
ath9k_hw              444645  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
rtsx_pci_ms            18151  0 
memstick               16760  1 rtsx_pci_ms
ath3k                  13318  0 
mac80211              596969  1 ath9k
lpc_ich                21080  0 
btusb                  28267  0 
bluetooth             371880  23 bnep,ath3k,btusb,rfcomm
cfg80211              479757  3 ath,ath9k,mac80211
nouveau               943295  0 
soundcore              12680  1 snd
mei_me                 18421  0 
mxm_wmi                13021  1 nouveau
mei                    77692  1 mei_me
ttm                    83995  1 nouveau
i915                  655752  5 
drm_kms_helper         52651  2 i915,nouveau
drm                   296739  8 ttm,i915,drm_kms_helper,nouveau
wmi                    19070  3 mxm_wmi,nouveau,asus_wmi
video                  19318  3 i915,nouveau,asus_wmi
mac_hid                13205  0 
i2c_algo_bit           13413  2 i915,nouveau
coretemp               13435  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   105818  2 hid_generic,usbhid
rtsx_pci_sdmmc         23527  0 
r8169                  67341  0 
rtsx_pci               45546  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25819  5 
libahci                31898  1 ahci
mii                    13934  1 r8169

```

sudo ethtool eth0```
mosquito@mosquito-K56CB:~/Desktop$ sudo ethtool eth0Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes



```

---

### Post by varunendra on 2013-11-26
Everything in the outputs looks fine, and frankly, I don't have a slightest hint of what may be causing the problem.

A 'gradually increasing' problem usually indicates a physical connectivity problem. But since everything is fine in windows 8 part, that seems to be ruled out.

I haven't suggested this to anyone for a really long time (wasn't needed), but you may try the proprietary realtek driver instead.

[INDENT]1) Download it from here : [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

2) Copy the downloaded file to your desktop > right click > Extract Here

3) Open a terminal and do -
```
cd Desktop/r8168-8.037.00
sudo ./autorun.sh
```[/INDENT]

The "autorun.sh" script in the package will automatically unload the current driver, back it up, install the proprietary driver "r8168" and load it.

See if that one solves your problem. If not, and you wish to revert to the native one, we'll have to manually remove the proprietary one and restore the native one from the backup.

---

### Post by childintime on 2013-11-26
Thanks varunendra ;) I installed that driver, and will see how it goes, will update this thread after some testing, so see if problem is solved.

Btw, is this driver not any worse than my original one?

---

### Post by varunendra on 2013-11-26
Actually, when we used to suggest it frequently (in days of Lucid and Maverick), it used to work **perfectly**. But since 11.04, the native driver (r8169) improved a lot and we never needed the proprietary one after that version.

Now, for last few weeks I have been seeing similar problems again, although not exactly same as earlier (those earlier issues used to give us some clear hints). So your post is the first one after a very long time when I have suggested the proprietary driver straight away again.

Since the proprietary driver has been updated too, I hope it has become better, not worse. :)

---

### Post by childintime on 2013-11-26
great, thanks again :eek:

---

