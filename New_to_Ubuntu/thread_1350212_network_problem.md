---
title: "network problem"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by arunkmohan18 on 2009-12-09
i am new to ubuntu
i am  using ubuntu 9.1 first time when i boot ubuntu i am able to connect internet but after reboot  it is not connecting LAN automatically 
please help me

---

### Post by zeroseven0183 on 2009-12-09
Hi! you can check the option to Connect Automatically in System > Preferences > Network Connections. If you're using Wired Connection, select that tab and choose the name of your connection then click Edit. You'll see there the option Connect Automatically, check it if it's not marked.

Or may be, you have another issue which we need more information. It would be better if you will include the hardware specs of your computer.

---

### Post by arunkmohan18 on 2009-12-09
i am using realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC 
router is iball Baton
and also when i type ifconfig eth1 it shows device not found

---

### Post by ukripper on 2009-12-09
can you post output of this command:
```
lsmod
```

and
```
sudo lshw -C network
```

---

### Post by arunkmohan18 on 2009-12-09
i don't know what's going on my computer when i boot to ubuntu to check the above command this time it connected automatically

---

### Post by arunkmohan18 on 2009-12-09
arun@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
xt_TCPMSS               3868  0 
xt_tcpmss               1852  0 
xt_tcpudp               2780  0 
iptable_mangle          3452  0 
pppoe                  11076  0 
pppox                   3016  1 pppoe
binfmt_misc             8356  1 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3100  0 
ip_tables              11692  2 iptable_mangle,iptable_filter
x_tables               16544  4 xt_TCPMSS,xt_tcpmss,xt_tcpudp,ip_tables
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6688  0 
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
psmouse                56180  0 
serio_raw               5280  0 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
r8169                  32064  0 
mii                     5212  1 r8169
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

---

### Post by arunkmohan18 on 2009-12-09
arun@ubuntu:~$ sudo lshw -C network
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:7d:e4:55:29
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:9000(size=256) memory:d1010000-d1010fff(prefetchable) memory:d1000000-d100ffff(prefetchable) memory:d1020000-d102ffff(prefetchable)

---

### Post by ukripper on 2009-12-09
your card is detected fine. Have you got spare ethernet cable connecting to your computer and router? Can you try changing the cable and see if it is not dropping because of the cable.

---

