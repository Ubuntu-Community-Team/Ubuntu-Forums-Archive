---
title: "Yoga 2 pro Ethernet/wifi keeps on disconnecting"
date: 2015-05-10
forum: Networking &amp; Wireless
---

### Post by shai4 on 2015-05-10
Both wifi and ethernet keeps on disconnecting every few minutes.
Somehow the etherent is connecting over "Auto Ethernet" instead of eth0.
ubuntu 14.04

Here are some outputs:
```
 
 > lspci -nnk | grep -iA2 net01:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c170]
    Kernel driver in use: iwlwifi

```

```
 
>lsmod
Module                  Size  Used by
xt_addrtype            12635  2 
xt_conntrack           12760  1 
ipt_MASQUERADE         12880  1 
iptable_nat            13011  1 
nf_conntrack_ipv4      15012  2 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
nf_nat_ipv4            13263  1 iptable_nat
iptable_filter         12810  1 
ip_tables              27239  2 iptable_filter,iptable_nat
x_tables               34059  5 ip_tables,ipt_MASQUERADE,xt_conntrack,iptable_filter,xt_addrtype
nf_nat                 21841  3 ipt_MASQUERADE,nf_nat_ipv4,iptable_nat
nf_conntrack           96976  6 ipt_MASQUERADE,nf_nat,nf_nat_ipv4,xt_conntrack,iptable_nat,nf_conntrack_ipv4
bridge                110833  0 
stp                    12976  1 bridge
llc                    14552  2 stp,bridge
aufs                  202783  0 
sr9700                 13818  0 
dm9601                 13887  0 
usbnet                 43913  2 dm9601,sr9700
mii                    13934  3 dm9601,sr9700,usbnet
hid_generic            12548  0 
ipheth                 13448  0 
hid_sensor_magn_3d     13209  0 
hid_sensor_gyro_3d     13209  0 
hid_sensor_als         13123  0 
hid_sensor_accel_3d    13221  0 
hid_sensor_trigger     12916  8 hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_als,hid_sensor_magn_3d
industrialio_triggered_buffer    12882  4 hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_als,hid_sensor_magn_3d
kfifo_buf              13379  1 industrialio_triggered_buffer
industrialio           54069  7 hid_sensor_trigger,hid_sensor_gyro_3d,industrialio_triggered_buffer,hid_sensor_accel_3d,hid_sensor_als,kfifo_buf,hid_sensor_magn_3d
hid_sensor_iio_common    13755  4 hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_als,hid_sensor_magn_3d
hid_multitouch         17407  0 
hid_sensor_hub         19536  6 hid_sensor_trigger,hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_als,hid_sensor_magn_3d,hid_sensor_iio_common
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
usbhid                 52659  0 
videobuf2_core         40664  1 uvcvideo
hid                   106148  4 hid_multitouch,hid_generic,hid_sensor_hub,usbhid
videodev              134688  2 uvcvideo,videobuf2_core
btusb                  32412  0 
ctr                    13049  3 
ccm                    17773  3 
rfcomm                 69160  8 
bnep                   19624  2 
bluetooth             391136  22 bnep,btusb,rfcomm
snd_hda_codec_realtek    65580  1 
snd_hda_codec_hdmi     46368  1 
arc4                   12608  2 
joydev                 17381  0 
nls_iso8859_1          12713  1 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   455835  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
iwlmvm                189852  0 
aesni_intel            55624  6 
mac80211              630669  1 iwlmvm
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          56531  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
serio_raw              13462  0 
snd_hwdep              13602  1 snd_hda_codec
iwlwifi               169932  1 iwlmvm
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
i915                  784123  7 
snd_rawmidi            30144  1 snd_seq_midi
video                  19476  1 i915
drm_kms_helper         55071  1 i915
intel_smartconnect     12619  0 
drm                   303102  6 i915,drm_kms_helper
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
parport_pc             32701  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
ppdev                  17671  0 
snd_timer              29482  2 snd_pcm,snd_seq
lpc_ich                21080  0 
shpchp                 37032  0 
mei_me                 18627  0 
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei                    82276  1 mei_me
lp                     17759  0 
soundcore              12680  1 snd
parport                42348  3 lp,ppdev,parport_pc
i2c_algo_bit           13413  1 i915
mac_hid                13205  0 
psmouse               106714  0 
ahci                   29915  3 
libahci                32716  1 ahci

```

ifconfig : (I'm sure that 'eth0' use to be there)

```
 
>ifconfig
docker0   Link encap:Ethernet  HWaddr 56:84:7a:fe:97:99  
          inet addr:172.17.42.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:206162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:206162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:199170732 (199.1 MB)  TX bytes:199170732 (199.1 MB)


rename4   Link encap:Ethernet  HWaddr 00:e0:4c:53:44:58  
          inet addr:192.168.12.237  Bcast:192.168.12.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe53:4458/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68368 errors:1997 dropped:432 overruns:397 frame:2416
          TX packets:64503 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45157491 (45.1 MB)  TX bytes:30929130 (30.9 MB)


wlan0     Link encap:Ethernet  HWaddr e8:2a:ea:96:ac:9e  
          inet addr:192.168.12.154  Bcast:192.168.12.255  Mask:255.255.255.0
          inet6 addr: fe80::ea2a:eaff:fe96:ac9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28750 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14787228 (14.7 MB)  TX bytes:1599888 (1.5 MB)



```

```

 sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 6b
       serial: e8:2a:ea:96:ac:9e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-51-generic firmware=22.24.8.0 ip=192.168.12.154 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:59 memory:b0400000-b0401fff
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: rename4
       serial: 00:e0:4c:53:44:58
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=dm9601 driverversion=22-Aug-2005 duplex=full firmware=Davicom DM96xx USB 10/100 Ether ip=192.168.12.237 link=yes multicast=yes port=MII speed=100Mbit/s

```

---

