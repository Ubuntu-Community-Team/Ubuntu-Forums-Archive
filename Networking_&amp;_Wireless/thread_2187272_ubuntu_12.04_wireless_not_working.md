---
title: "ubuntu 12.04 wireless not working"
date: 2013-11-11
forum: Networking &amp; Wireless
---

### Post by elayoubii on 2013-11-11
Hi,

My wifi used to drop every minute, but after I tried to fix it, now it never connects... 

I tried to install the backports package for my level of ubuntu, and I think I completely fried my wireless configuration.

Here are the commands I ran to collect diagnostics:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a
sudo iwlist scan
cat /etc/resolv.conf

```

Here's the output captured by the script utility.

```
Script started on Mon 11 Nov 2013 12:45:04 PM EST
$ 
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c660]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Samsung Electronics Co Ltd Device [144d:4112]
    Kernel driver in use: ath9k
$ 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 2232:1035  
Bus 005 Device 005: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II]
Bus 004 Device 005: ID 0cf3:3004 Atheros Communications, Inc. 
$ 
Module                  Size  Used by
cdc_acm                26821  0 
nls_utf8               12557  1 
isofs                  40257  1 
ipt_LOG                12919  2 
ipt_REJECT             12576  1 
iptable_nat            13229  0 
nf_nat                 25891  1 iptable_nat
nf_conntrack_ipv4      19716  7 iptable_nat,nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_filter         12810  1 
ip_tables              27473  2 iptable_nat,iptable_filter
ip6t_LOG               16974  2 
xt_limit               12711  4 
ip6t_REJECT            12609  1 
xt_tcpudp              12603  95 
ip6t_ah                12529  1 
nf_conntrack_ipv6      13906  3 
nf_defrag_ipv6         13412  1 nf_conntrack_ipv6
xt_state               12578  7 
ip6table_filter        12815  1 
ip6_tables             27864  3 ip6t_LOG,ip6t_ah,ip6table_filter
x_tables               29891  13 ipt_LOG,ipt_REJECT,iptable_nat,iptable_filter,ip_tables,ip6t_LOG,xt_limit,ip6t_REJECT,xt_tcpudp,ip6t_ah,xt_state,ip6table_filter,ip6_tables
symap_custom_3.2.0_56_generic_x86_64    41434  24 
symev_custom_3.2.0_56_generic_x86_64    80183  2 symap_custom_3.2.0_56_generic_x86_64
rfcomm                 47604  12 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_codec_realtek   224173  1 
snd_hda_codec_hdmi     32474  0 
joydev                 17693  0 
arc4                   12529  2 
dm_multipath           23275  0 
ath9k                 132428  0 
psmouse                97519  0 
mac80211              506862  1 ath9k
snd_seq_midi           13324  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_intel          33719  3 
ath9k_common           14053  1 ath9k
snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
ath9k_hw              411239  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
snd_rawmidi            30748  1 snd_seq_midi
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
cfg80211              205774  3 ath9k,mac80211,ath
fglrx                5291666  292 
serio_raw              13211  0 
k10temp                13166  0 
snd_seq_midi_event     14899  1 snd_seq_midi
i2c_piix4              13301  0 
ath3k                  12961  0 
btusb                  18332  1 
bluetooth             180113  24 rfcomm,bnep,ath3k,btusb
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  16 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
nf_conntrack_ftp       13452  0 
nf_conntrack           81926  6 iptable_nat,nf_nat,nf_conntrack_ipv4,nf_conntrack_ipv6,xt_state,nf_conntrack_ftp
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_crypt               23125  5 
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20961  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
usb_storage            49198  0 
r8169                  62190  0 
video                  19651  0 
wmi                    19256  0 
$ 
lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


cscotun0  no wireless extensions.


$ 
cscotun0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:9.26.41.68  P-t-P:9.26.41.68  Mask:255.255.252.0
          inet6 addr: fe80::2334:d949:2625:5d81/128 Scope:Link
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1399  Metric:1
          RX packets:32204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31599 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:28508947 (28.5 MB)  TX bytes:11638708 (11.6 MB)


eth0      Link encap:Ethernet  HWaddr e8:03:9a:ef:71:77  
          inet addr:192.168.2.21  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::ea03:9aff:feef:7177/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:199622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95325509 (95.3 MB)  TX bytes:25733603 (25.7 MB)
          Interrupt:46 Base address:0x8000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11867819 (11.8 MB)  TX bytes:11867819 (11.8 MB)


wlan0     Link encap:Ethernet  HWaddr 50:b7:c3:24:b0:f7  
          inet6 addr: fe80::52b7:c3ff:fe24:b0f7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:100095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:93204811 (93.2 MB)  TX bytes:10939079 (10.9 MB)


$ 
[sudo] password for elayoubi: 
Sorry, try again.
[sudo] password for elayoubi: 
lo        Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Device or resource busy


eth0      Interface doesn't support scanning.


cscotun0  Interface doesn't support scanning.


$ cat /etc/conf/     reo solv.conf
domain canlab.ibm.com
nameserver 9.26.4.6
nameserver 9.26.4.5
nameserver 127.0.0.1
$ exit


Script done on Mon 11 Nov 2013 12:45:49 PM EST

```

---

