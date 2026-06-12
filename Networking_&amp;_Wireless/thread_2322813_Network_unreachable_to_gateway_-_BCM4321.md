---
title: "Network unreachable to gateway - BCM4321"
date: 2016-04-30
forum: Networking &amp; Wireless
---

### Post by 98cwitr on 2016-04-30
Just upgraded to 16.04 LTS in hopes of a fix ans so I really had hoped after two years broadcom would have fixed this, but unfortunately I cannot get my wifi to work. Pinging the gateway after pulling an IP from the router results in network unreachable. 

```

<removed>~$ lshw -C network
  *-network
       description: Wireless interface
       product: BCM4321 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlp5s0
       version: 01
       serial: <removed>
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=<removed>latency=32 multicast=yes wireless=IEEE 802.11abg
       resources: irq:20 memory:fb000000-fb003fff

```

```

<removed>:~$ ifconfig wlp5s0
wlp5s0    Link encap:Ethernet  HWaddr <removed> 
          inet addr:<removed> Bcast:<removed>  Mask:<removed>
          inet6 addr: <removed> Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2516 errors:0 dropped:0 overruns:0 frame:4069230
          TX packets:239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:336929 (336.9 KB)  TX bytes:30806 (30.8 KB)
          Interrupt:20 

```

My old thread on the topic is here: [http://ubuntuforums.org/showthread.php?t=2217589](http://ubuntuforums.org/showthread.php?t=2217589)

---

### Post by 98cwitr on 2016-12-19
Plot thickness a bit. Connected the wifi to my mobile hotspot, works just fine. Connect it back to my Netgear WNDR3700 router...no joy. arp table is incomplete, but when I manually populate it there's no change.

If I set the router to use no encryption it works.

---

### Post by 98cwitr on 2017-01-10
Finding this in kern.log over and over again:

> 
Jan 10 02:15:59 kernel: [22896.296094] WARNING: CPU: 0 PID: 645 at /build/linux-7x12eW/linux-4.4.0/net/wireless/sme.c:850 cfg80211_roamed+0x86/0xa0 [cfg80211]()

Jan 10 02:15:59 kernel: [22896.296095] Modules linked in: pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) gpio_ich coretemp kvm_intel kvm irqbypass uvcvideo videobuf2_vmalloc wl(POE) videobuf2_memops input_leds videobuf2_v4l2 videobuf2_core v4l2_common snd_hda_codec_realtek snd_hda_codec_generic serio_raw videodev snd_hda_intel media snd_hda_codec snd_usb_audio snd_hda_core snd_usbmidi_lib snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi lpc_ich cfg80211 snd_seq snd_seq_device snd_timer 8250_fintek snd soundcore shpchp mac_hid parport_pc ppdev lp parport autofs4 hid_generic usbhid hid nouveau psmouse pata_acpi mxm_wmi wmi video r8169 i2c_algo_bit mii ttm pata_jmicron drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm fjes

---

