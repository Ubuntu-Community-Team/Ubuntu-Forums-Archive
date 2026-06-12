---
title: "wireless internet connection stopped working in Xubuntu 14.10"
date: 2015-01-29
forum: Networking &amp; Wireless
---

### Post by arturo11 on 2015-01-29
Yesterday the wifi worked and today it stopped working. The computer is an HP ProBook 4310s laptop. Here are some details:

usuario@linux:/etc/modprobe.d$ lspci
    00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
    00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
    00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
    00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
    00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
    00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
    00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
    02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
    85:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8072 PCI-E Gigabit Ethernet Controller (rev 10)


usuario@linux:/etc/modprobe.d$ lsusb
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 001 Device 003: ID 04f2:b159 Chicony Electronics Co., Ltd 
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. AES2810
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


usuario@linux:/etc/modprobe.d$ ifconfig
eth2      Link encap:Ethernet  direcciónHW 00:26:55:c0:9c:60  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:17 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:65536  Métrica:1
          Paquetes RX:157 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:157 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:11156 (11.1 KB)  TX bytes:11156 (11.1 KB)


usuario@linux:/etc/modprobe.d$ iwconfig
    lo        no wireless extensions.

    eth2      no wireless extensions.


    usuario@linux:/etc/modprobe.d$ lsmod
    Module                  Size  Used by
    dm_crypt               22584  0 
    bnep                   18829  2 
    rfcomm                 58045  4 
    bluetooth             390981  10 bnep,rfcomm
    6lowpan_iphc           18262  1 bluetooth
    snd_hda_codec_hdmi     46395  1 
    snd_hda_codec_analog    14537  1 
    snd_hda_codec_generic    62849  1 snd_hda_codec_analog
    uvcvideo               71457  0 
    videobuf2_vmalloc      13048  1 uvcvideo
    videobuf2_memops       13170  1 videobuf2_vmalloc
    videobuf2_core         48344  1 uvcvideo
    v4l2_common            15132  1 videobuf2_core
    videodev              131257  3 uvcvideo,v4l2_common,videobuf2_core
    media                  20951  2 uvcvideo,videodev
    hp_wmi                 13741  0 
    sparse_keymap          13708  1 hp_wmi
    snd_hda_intel          29211  3 
    snd_hda_controller     29944  1 snd_hda_intel
    b43                   377514  0 
    snd_hda_codec         120356  5 snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller,snd_hda_codec_analog
    snd_hwdep              13272  1 snd_hda_codec
    snd_pcm                91280  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
    coretemp               13201  0 
    snd_seq_midi           13324  0 
    snd_seq_midi_event     14475  1 snd_seq_midi
    snd_rawmidi            25722  1 snd_seq_midi
    snd_seq                56638  2 snd_seq_midi_event,snd_seq_midi
    bcma                   46430  1 b43
    joydev                 17072  0 
    snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
    snd_timer              28579  2 snd_pcm,snd_seq
    serio_raw              13210  0 
    mac80211              567098  1 b43
    snd                    66629  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog
    lpc_ich                16877  0 
    cfg80211              430618  2 b43,mac80211
    shpchp                 32136  0 
    soundcore              14604  2 snd,snd_hda_codec
    hp_accel               25778  0 
    lis3lv02d              19500  1 hp_accel
    input_polldev          14247  1 lis3lv02d
    mac_hid                13059  0 
    parport_pc             32021  0 
    ppdev                  17391  0 
    lp                     17395  0 
    parport                40795  3 lp,ppdev,parport_pc
    psmouse                95318  0 
    ahci                   25622  1 
    libahci                31066  1 ahci
    sky2                   52917  0 
    i915                  824137  3 
    ssb                    51849  1 b43
    i2c_algo_bit           13190  1 i915
    drm_kms_helper         55051  1 i915
    video                  19528  1 i915
    drm                   255383  5 i915,drm_kms_helper
    wmi                    18689  1 hp_wmi


usuario@linux:/etc/modprobe.d$ dmesg | grep "wlan"


usuario@linux:/etc/modprobe.d$ sudo lshw -C network
  *-network               
       descripción: Network controller
       producto: BCM4312 802.11b/g LP-PHY
       fabricante: Broadcom Corporation
       id físico: 0
       información del bus: pci@0000:02:00.0
       versión: 01
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list
       configuración: driver=b43-pci-bridge latency=0
       recursos: irq:17 memoria:d8700000-d8703fff
  *-network
       descripción: Ethernet interface
       producto: 88E8072 PCI-E Gigabit Ethernet Controller
       fabricante: Marvell Technology Group Ltd.
       id físico: 0
       información del bus: pci@0000:85:00.0
       nombre lógico: eth2
       versión: 10
       serie: 00:26:55:c0:9c:60
       capacidad: 1Gbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       recursos: irq:45 memoria:d0600000-d0603fff ioport:2000(size=256) memoria:d0620000-d063ffff


usuario@linux:/etc/modprobe.d$ iwlist scan
    lo        Interface doesn't support scanning.

    eth2      Interface doesn't support scanning.


usuario@linux:/etc/modprobe.d$ sudo /etc/init.d/networking restart
    stop: Job failed while stopping
    start: Job is already running: networking

---

