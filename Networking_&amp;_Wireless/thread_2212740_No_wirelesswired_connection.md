---
title: "No wireless/wired connection"
date: 2014-03-22
forum: Networking &amp; Wireless
---

### Post by sama2 on 2014-03-22
I am posting this from another laptop as there are no wired neither wireless connections. I ruined the connection many times but this time I could not fix it.
I lost the Ethernet connection a while ago and now I lost the wireless connection  :(


I use ubuntu 12.04 LTS
**lsb_release -a **
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise
```

The iwconfic does not show wlan1 which I used to have  before 
**iwconfig**
```
br0       no wireless extensions.
eth1      no wireless extensions.
lo        no wireless extensions.
```




**sudo lshw -C network**
```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 07
       serial: 74:86:7a:3e:50:69
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 ip=192.168.1.9 latency=0 multicast=yes
       resources: irq:60 ioport:4000(size=256) memory:c0700000-c0700fff memory:c0400000-c0403fff


  *-network UNCLAIMED
       description: Network controller
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c0600000-c067ffff memory:9fb00000-9fb0ffff
```






**lspci -nnk | grep -iA2 net**
```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:05ea]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]
03:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT [Radeon HD 8670A] [1002:6660]
```

**uname -a**
```
Linux user-Inspiron-5537 3.5.0-47-generic #71~precise1-Ubuntu SMP Wed Feb 19 22:02:52 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Iowan on 2014-03-22
Looks like eth1 gets an IP address. Can you **ping** the router (probably at 192.168.1.1)?

br0  is a bridge - I'm not sure what it's doing.
Does this machine get a DHCP address (or is it a static address)? 
Are you using Network Manager, or are interfaces configured via */etc/network/interfaces*?

---

### Post by sama2 on 2014-03-23
[FONT=Times][SIZE=3]Thank you very much for your reply 
[B]

ping 192.168.1.1[/B]

[/SIZE][/FONT][SIZE=3]```

[FONT=Times]PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.[/FONT]
[FONT=Times]From 192.168.1.9 icmp_seq=1 Destination Host Unreachable[/FONT]
[FONT=Times]From 192.168.1.9 icmp_seq=2 Destination Host Unreachable[/FONT]
[FONT=Times]From 192.168.1.9 icmp_seq=3 Destination Host Unreachable[/FONT]
[FONT=Times]From 192.168.1.9 icmp_seq=4 Destination Host Unreachable[/FONT]
[FONT=Times]From 192.168.1.9 icmp_seq=5 Destination Host Unreachable[/FONT]
[FONT=Times]From 192.168.1.9 icmp_seq=6 Destination Host Unreachable[/FONT]
[FONT=Times]From 192.168.1.9 icmp_seq=7 Destination Host Unreachable[/FONT]
[FONT=Times]From 192.168.1.9 icmp_seq=8 Destination Host Unreachable[/FONT]
[FONT=Times]From 192.168.1.9 icmp_seq=9 Destination Host Unreachable[/FONT]
[FONT=Times]…[/FONT]
[FONT=Times]….[/FONT]
[FONT=Times]…....[/FONT]

```
[FONT=Times]
[/FONT]
[FONT=Times]I set up bridge once, then I deleted it. I don't know why br0 is still exist!![/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]this is what does** /etc/network/interface ** look like :[/FONT]
[FONT=Times]
[/FONT]```


[FONT=Times]# The loopback network interface[/FONT]
[FONT=Times]auto lo[/FONT]
[FONT=Times]iface lo inet loopback[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]# The primary network interface[/FONT]
[FONT=Times]auto eth1[/FONT]
[FONT=Times]iface eth1 inet manual[/FONT]

```[FONT=Times]
[/FONT]
[/SIZE][FONT=Times]
[/FONT]

---

### Post by sama2 on 2014-03-23
I am wonder why wireless device is UNCLAIMED does it need to reinstall the driver ? 

and regard the ethernet, in the network manager  it becomes grey before I lost the wifi connection but I did't  fix it.

---

### Post by sama2 on 2014-03-23
I found this solution and its fixed my wireless HURRaaay  :)


[COLOR=#000000]Downloaded the driver package from [/COLOR][http://drvbp1.linux-foundation.org/~...tml/backports/]("http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/")[COLOR=#000000] , extracted it to Desktop and then went back to the Terminal:
[/COLOR]
```

cd Desktop/backports-3.13.2-1
make defconfig-ath9k
make
sudo make install

```

Source :
[http://ubuntuforums.org/showthread.php?t=2206487&page=2&p=12936742#post12936742](http://ubuntuforums.org/showthread.php?t=2206487&page=2&p=12936742#post12936742)

But I still want to fix the **ethernet**. I have no clue why is this happen. Any solution will be highly appreciated ???

---

### Post by praseodym on 2014-03-23
Is the driver loaded?
```

lsmod
```

---

### Post by sama2 on 2014-03-23
this is what I got from lsmod

```


lsmod
Module                  Size  Used by
vhost_net              32360  1 
macvtap                18529  1 vhost_net
macvlan                19003  1 macvtap
ipt_MASQUERADE         12760  3 
iptable_nat            13230  1 
nf_nat                 25646  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      14531  4 iptable_nat,nf_nat
nf_defrag_ipv4         12730  1 nf_conntrack_ipv4
xt_state               12579  1 
nf_conntrack           83300  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT             12577  2 
xt_CHECKSUM            12550  1 
iptable_mangle         12735  1 
xt_tcpudp              12604  5 
ipheth                 13534  0 
brcompat               13513  0 
openvswitch            84161  3 brcompat
nls_iso8859_1          12714  1 
ip6table_filter        12816  0 
ip6_tables             27686  1 ip6table_filter
iptable_filter         12811  1 
ip_tables              27474  3 iptable_nat,iptable_mangle,iptable_filter
ebtable_nat            12808  0 
ebtables               31024  1 ebtable_nat
x_tables               29892  12 ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_CHECKSUM,iptable_mangle,xt_tcpudp,ip6table_filter,ip6_tables,iptable_filter,ip_tables,ebtables
parport_pc             32867  0 
ppdev                  17114  0 
bnep                   18240  2 
rfcomm                 47562  0 
joydev                 17694  0 
arc4                   12530  2 
ath9k                  96879  0 
mac80211              558021  1 ath9k
ath9k_common           13859  1 ath9k
ath9k_hw              405891  2 ath9k,ath9k_common
btusb                  22432  0 
ath                    23828  3 ath9k,ath9k_common,ath9k_hw
coretemp               13642  0 
kvm_intel             137888  3 
kvm                   422160  1 kvm_intel
ghash_clmulni_intel    13221  0 
aesni_intel            51134  1 
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
cfg80211              546086  3 ath9k,mac80211,ath
snd_hda_codec_realtek    46366  1 
snd_hda_codec_hdmi     36726  1 
dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop
microcode              23030  0 
fglrx                6728782  120 
rts5139               350620  0 
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
amd_iommu_v2           19228  1 fglrx
compat                 22191  5 ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211
snd_hda_intel          43682  5 
snd_hda_codec         188269  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
psmouse               102541  0 
serio_raw              13216  0 
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath3k                  12918  0 
bluetooth             212001  15 bnep,rfcomm,btusb,ath3k
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19257  1 dell_wmi
soundcore              15092  1 snd
i915                  600141  4 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
drm_kms_helper         49259  1 i915
drm                   290595  5 i915,drm_kms_helper
i2c_algo_bit           13565  1 i915
video                  19653  1 i915
mac_hid                13254  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
usb_storage            49288  1 
ahci                   25869  2 
libahci                31434  1 ahci
r8169                  62741  0



```

---

### Post by praseodym on 2014-03-23
Did you setup the firewall on your own? Uninstall it via
```

sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```
If you activate the FW in your router it is enough.

---

