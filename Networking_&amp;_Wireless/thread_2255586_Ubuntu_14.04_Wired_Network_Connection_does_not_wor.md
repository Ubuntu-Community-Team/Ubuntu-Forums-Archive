---
title: "Ubuntu 14.04 Wired Network Connection does not work"
date: 2014-12-06
forum: Networking &amp; Wireless
---

### Post by db579 on 2014-12-06
Running Ubuntu 14.04 on my laptop I can connect to the internet wirelessly no problem but when I try to connect to the router via a lan cable I am unable to get a connection. It seems I am unable to get the DHCP to assign an ipv4 address (Warning from tcpdump). My Windows 8 machine is able to connect no problem so I think the router/cables are not the problem here.

ifconfig eth0 gives the following output:

```
 eth0      Link encap:Ethernet  HWaddr 08:9e:01:e0:2d:71            inet6 addr: fe80::a9e:1ff:fee0:2d71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:80150 (80.1 KB)

```

and lshw -C network gives the following output:

```

  *-network               
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 73
       serial: 0c:8b:fd:4a:25:7c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-40-generic firmware=22.24.8.0 ip=192.168.0.187 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:66 memory:b3500000-b3501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:05:00.1
       logical name: eth0
       version: 14
       serial: 08:9e:01:e0:2d:71
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities

```

---

### Post by praseodym on 2014-12-06
Hi,

change the driver for this device:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.039.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.039.00
sudo dkms build -m r8168-dkms -v 8.039.00
sudo dkms install -m r8168-dkms -v 8.039.00
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo depmod -a
sudo update-initramfs -u 

```Reboot

---

### Post by db579 on 2014-12-06
Hi praseodym, thanks for the suggestion. Unfortunately doesn't help though I get the same problem. Also on booting the laptop I get the error message 'No DHCP or ProxyOffers were received'.

---

### Post by praseodym on 2014-12-06
Ok, lets check
```
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by db579 on 2014-12-06
lsmod:

```

Module                  Size  Used by
bbswitch               13943  0 
rfcomm                 69160  8 
bnep                   19624  2 
binfmt_misc            17468  1 
hid_multitouch         17407  0 
hid_logitech_dj        18581  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
btusb                  32412  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
usbhid                 52659  0 
videobuf2_core         40664  1 uvcvideo
hid                   106148  3 hid_multitouch,usbhid,hid_logitech_dj
videodev              134688  2 uvcvideo,videobuf2_core
bluetooth             391136  22 bnep,btusb,rfcomm
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
arc4                   12608  2 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143148  0 
kvm                   455785  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
iwlmvm                189813  0 
joydev                 17381  0 
serio_raw              13462  0 
mac80211              626557  1 iwlmvm
snd_hda_intel          56451  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
lpc_ich                21080  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
rtsx_pci_ms            18151  0 
memstick               16966  1 rtsx_pci_ms
iwlwifi               169932  1 iwlmvm
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
i915                  784207  4 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                 18627  0 
mei                    82276  1 mei_me
soundcore              12680  1 snd
drm_kms_helper         55071  1 i915
drm                   303102  3 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
parport_pc             32701  0 
ppdev                  17671  0 
wmi                    19177  1 acer_wmi
video                  19476  2 i915,acer_wmi
intel_smartconnect     12619  0 
lp                     17759  0 
mac_hid                13205  0 
parport                42348  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         23274  0 
psmouse               106714  0 
ahci                   25819  2 
libahci                32716  1 ahci
rtsx_pci               46202  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8168                 434402  0 

```

ifconfig -a:

```

eth0      Link encap:Ethernet  HWaddr 08:9e:01:e0:2d:71  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:52 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4382 (4.3 KB)
          Interrupt:61 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:504894 (504.8 KB)  TX bytes:504894 (504.8 KB)


wlan0     Link encap:Ethernet  HWaddr 0c:8b:fd:4a:25:7c  
          inet addr:192.168.0.187  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e8b:fdff:fe4a:257c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13225 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7551495 (7.5 MB)  TX bytes:3404954 (3.4 MB)

```


cat [COLOR=#000000][FONT=Ubuntu Mono]/etc/network/interfaces:

[/FONT][/COLOR]```
# interfaces(5) file used by ifup(8) and ifdown(8)
 auto lo
 iface lo inet loopback[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]


[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]cat /etc/resolv.conf

[/FONT][/COLOR]```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

```[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by praseodym on 2014-12-07
Ok, remove any connection in "Cable" and "DSL" of the network-manager profiles and reboot:
```

ifconfig -a
cat /etc/resolv.conf
route -n
arp -av
```

---

### Post by db579 on 2014-12-07
Thanks for sticking with this. Tried that but made no difference, still got the same problem.

---

### Post by praseodym on 2014-12-07
Obviously, you don't get an IPv4 address. Try:
```

sudo dhclient eth0
ifconfig -a
```

---

### Post by db579 on 2014-12-07
Tried that - sudo dhclient eth0 didn't seem to do anything though. I waited for 5+ minutes but didn't complete.

ifconfig -a gave:

```

eth0      Link encap:Ethernet  HWaddr 08:9e:01:e0:2d:71  
          inet6 addr: fe80::a9e:1ff:fee0:2d71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101411 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1433 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6093838 (6.0 MB)  TX bytes:278936 (278.9 KB)
          Interrupt:61 Base address:0xc000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:22496 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6374096 (6.3 MB)  TX bytes:6374096 (6.3 MB)


wlan0     Link encap:Ethernet  HWaddr 0c:8b:fd:4a:25:7c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:204559 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46372906 (46.3 MB)  TX bytes:75596762 (75.5 MB)

```

---

### Post by praseodym on 2014-12-07
Ok, try uninstalling the package "resolvconf":
```

sudo apt-get remove --purge resolvconf
```
Reboot.

---

### Post by db579 on 2014-12-08
Hi praeodym. Thanks, I tried that and rebooted. Still the same problem though.

---

