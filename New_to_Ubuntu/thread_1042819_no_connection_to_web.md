---
title: "no connection to web"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by trucker33377 on 2009-01-17
this is a HP pavillion ez4900. Ive installed ubuntu Studio 8.04 NICE too by the way.
Thing is theres no way I can get on internet. the Lan has its light on but theres nothing happening. the wlan shows in term. same thing nothing in or out. Ive tried  ndiswrapper with windows driver says its installed. Ive put in bcm43xx. still wont work. installed bcm43xx-firmware_1.4-0cafusgo1_all.deb that didn't help. there was a message about driver being installed but firmware was a problem that was b4 i put in the deb.
I do have it working with a usb nic. plus puppy 4.0 has wireless with this laptop. 
one last thing HP gave me the driver for windows xp. xp wireless works but not the Lan plug. light is on but nothing in the device manager shows up for lan hardware.
Anyone have Any ideas? I just don't know where to go on this.
Pull out the big guns here guys :) this is a sweet Disto

---

### Post by handydan918 on 2009-01-17
Need some hardware info. ```
lspci |grep -i net
```

and ```
lsmod
```

---

### Post by trucker33377 on 2009-01-18
shawn@ubuntu:~$ sudo lspci |grep -i net
[sudo] password for shawn: 
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
shawn@ubuntu:~$ lsmod
Module                  Size  Used by
snd_rtctimer            4640  1 
i915                   32512  2 
drm                    82964  3 i915
rfcomm                 43280  2 
l2cap                  26112  13 rfcomm
bluetooth              62500  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_ondemand        9740  0 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8840  0 
cpufreq_stats           7360  0 
ipv6                  275428  8 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
sbs                    15368  0 
sbshc                   7808  1 sbs
dock                   11564  0 
iptable_filter          3968  0 
ip_tables              14820  1 iptable_filter
x_tables               16644  1 ip_tables
parport_pc             36516  0 
lp                     13252  0 
parport                38600  3 ppdev,parport_pc,lp
loop                   19460  0 
af_packet              24196  2 
pcmcia                 41260  0 
joydev                 13248  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8580  1 ecb
b43                   145188  0 
rfkill                  8852  1 b43
mac80211              168212  1 b43
cfg80211               15368  1 mac80211
led_class               6148  1 b43
input_polldev           5896  1 b43
snd_intel8x0           35228  2 
snd_ac97_codec        101284  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
rtl8150                14208  0 
snd_pcm_oss            42400  0 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_pcm                78852  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
yenta_socket           27404  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            41264  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_dummy           4868  0 
snd_seq_oss            35968  0 
snd_seq_midi            9376  0 
container               5760  0 
snd_rawmidi            25632  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
video                  19984  0 
output                  4736  1 video
serio_raw               7940  0 
snd_seq                54992  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
battery                14596  0 
snd_timer              24836  3 snd_rtctimer,snd_pcm,snd_seq
psmouse                41104  0 
wmi_acer                9772  0 
ac                      7044  0 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               13524  0 
button                  9232  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25492  1 
snd                    57636  17 snd_rtctimer,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 34708  0 
pci_hotplug            31776  1 shpchp
pcspkr                  4224  0 
agpgart                34900  3 drm,intel_agp
evdev                  13312  6 
soundcore               9312  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
ext3                  137480  1 
jbd                    49044  1 ext3
mbcache                 9856  1 ext3
sg                     36696  0 
sr_mod                 18084  1 
cdrom                  37152  1 sr_mod
sd_mod                 31152  3 
pata_acpi               8320  0 
ata_generic             8452  0 
ata_piix               19716  3 
libata                160240  3 pata_acpi,ata_generic,ata_piix
ssb                    34692  1 b43
scsi_mod              153196  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37644  0 
uhci_hcd               26896  0 
usbcore               147372  4 rtl8150,ehci_hcd,uhci_hcd
thermal                16924  0 
processor              37256  2 thermal
fan                     5636  0 
fuse                   51604  1 
shawn@ubuntu:~$

---

### Post by superprash2003 on 2009-01-18
post output of the following
1)ifconfig
2)iwconfig
3)lshw -C network
4)iwlist scanning

---

### Post by trucker33377 on 2009-01-18
shawn@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:03:4f:4e  
          inet addr:192.168.15.102  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe03:4f4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1540  Metric:1
          RX packets:2915 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3009 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3191594 (3.0 MB)  TX bytes:368462 (359.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:146300 (142.8 KB)  TX bytes:146300 (142.8 KB)

shawn@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

shawn@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:e0:4c:03:4f:4e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rtl8150 driverversion=v0.6.2 (2004/08/27) ip=192.168.15.102 multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:b6:45:57
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
shawn@ubuntu:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

shawn@ubuntu:~$

---

