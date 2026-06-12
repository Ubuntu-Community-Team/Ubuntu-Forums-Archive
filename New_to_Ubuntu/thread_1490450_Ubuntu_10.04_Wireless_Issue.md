---
title: "Ubuntu 10.04 Wireless Issue"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by AnneM on 2010-05-22
Hi

I just switched over to a new wireless modem from my ISP and now I am having trouble connecting via wireless. It was an issue before but I was using a wired connection for my desktop. However, I switched to a wireless modem to get rid of cables.

Anyway, after a lot of fiddling I managed to get it connected yesterday. I have no idea what did it because I tried the same things today to no avail. 

The wireless network is there and the signal is strong enough for the PC to see it but it keeps trying to connect, asking for the password and then just gives up trying after being unsuccessful. My laptop, which is running Win 7 connects just fine.

Anyway, I went through a few posts here and saw what info I should post so I am really sorry if this is TMI but I thought more is better.

Thanks a million for your help.

                                 ```
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
 08:00.0 Network controller: RaLink RT2760 Wireless 802.11n 1T/2R Cardbus
 08:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10) 
```  
 ```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 002 Device 006: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
 Bus 002 Device 005: ID 0409:005a NEC Corp. HighSpeed Hub
 Bus 002 Device 004: ID 045e:00dd Microsoft Corp.  
 Bus 002 Device 003: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
 Bus 002 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``` ```
*-network               
        description: Ethernet interface
        product: 88E8056 PCI-E Gigabit Ethernet Controller
        vendor: Marvell Technology Group Ltd.
        physical id: 0
        bus info: pci@0000:05:00.0
        logical name: eth1
        version: 12
        serial: 00:1d:60:95:bd:75
        width: 64 bits
        clock: 33MHz
        capabilities: bus_master cap_list rom ethernet physical
        configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
        resources: irq:31 memory:f7efc000-f7efffff ioport:c800(size=256) memory:f7ec0000-f7edffff(prefetchable)
   *-network:0
        description: Wireless interface
        product: RT2760 Wireless 802.11n 1T/2R Cardbus
        vendor: RaLink
        physical id: 0
        bus info: pci@0000:08:00.0
        logical name: wlan0
        version: 00
        serial: 00:1f:1f:17:ef:bd
        width: 32 bits
        clock: 33MHz
        capabilities: bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=rt2860 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless
        resources: irq:16 memory:febf0000-febfffff
   *-network:1
        description: Ethernet interface
        product: RTL-8110SC/8169SC Gigabit Ethernet
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 4
        bus info: pci@0000:08:04.0
        logical name: eth0
        version: 10
        serial: 00:1d:60:95:c3:0d
        width: 32 bits
        clock: 66MHz
        capabilities: bus_master cap_list rom ethernet physical
        configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.2.100 latency=64 maxlatency=64 mingnt=32 multicast=yes
        resources: irq:16 ioport:e800(size=256) memory:febeec00-febeecff memory:f0800000-f081ffff(prefetchable)
 
``` ```
Module                  Size  Used by
 binfmt_misc             6587  1  
 ppdev                   5259  0  
 snd_hda_codec_atihdmi     2367  1  
 nls_iso8859_1           3249  1  
 nls_cp437               4919  1  
 vfat                    8901  1  
 fat                    47767  1 vfat
 snd_hda_codec_analog    58566  1  
 snd_ctxfi              82726  2  
 snd_pcm_oss            35308  0  
 snd_hda_intel          21877  2  
 snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_analog,snd_hda_intel
 snd_mixer_oss          13746  1 snd_pcm_oss
 snd_hwdep               5412  1 snd_hda_codec
 snd_pcm                70662  4 snd_ctxfi,snd_pcm_oss,snd_hda_intel,snd_hda_codec
 snd_seq_dummy           1338  0  
 snd_seq_oss            26726  0  
 snd_seq_midi            4557  0  
 snd_rawmidi            19056  1 snd_seq_midi
 snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
 snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
 joydev                  8708  0  
 snd_timer              19098  2 snd_pcm,snd_seq
 r8169                  33884  0  
 snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
 fbcon                  35102  73  
 tileblit                2031  1 fbcon
 font                    7557  1 fbcon
 bitblit                 4707  1 fbcon
 asus_atk0110            9017  0  
 softcursor              1189  1 bitblit
 snd                    54148  21 snd_hda_codec_analog,snd_ctxfi,snd_pcm_oss,snd_hda_intel,snd_hda_codec,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
 ohci1394               26950  0  
 rt2860sta             481561  1  
 fglrx                2092908  35  
 agpgart                31724  1 fglrx
 vga16fb                11385  1  
 vgastate                8961  1 vga16fb
 serio_raw               3978  0  
 x38_edac                2923  0  
 lp                      7028  0  
 soundcore               6620  1 snd
 snd_page_alloc          7076  3 snd_ctxfi,snd_hda_intel,snd_pcm
 edac_core              37331  2 x38_edac
 parport                32635  2 ppdev,lp
 usbhid                 36110  0  
 hid                    67032  1 usbhid
 floppy                 53016  0  
 usb_storage            39425  0  
 sky2                   40775  0  
 mii                     4381  1 r8169
 ieee1394               81181  1 ohci1394
 ahci                   32008  0  
 pata_jmicron            1843  0
``` ```
This file lists those modules which we don't want to be loaded by
 # alias expansion, usually so some other driver will be loaded for the
 # device instead.
  
 # evbug is a debug tool that should be loaded explicitly
 blacklist evbug
  
 # these drivers are very simple, the HID drivers are usually preferred
 blacklist usbmouse
 blacklist usbkbd
  
 # replaced by e100
 blacklist eepro100
  
 # replaced by tulip
 blacklist de4x5
  
 # causes no end of confusion by creating unexpected network interfaces
 blacklist eth1394
  
 # snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
 # hardware on its own (Ubuntu bug #2011, #6810)
 blacklist snd_intel8x0m
  
 # Conflicts with dvb driver (which is better for handling this device)
 blacklist snd_aw2
  
 # causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
 blacklist i2c_i801
  
 # replaced by p54pci
 blacklist prism54
  
 # replaced by b43 and ssb.
 blacklist bcm43xx
  
 # most apps now use garmin usb driver directly (Ubuntu: #114565)
 blacklist garmin_gps
  
 # replaced by asus-laptop (Ubuntu: #184721)
 blacklist asus_acpi
  
 # low-quality, just noise when being used for sound playback, causes
 # hangs at desktop session start (Ubuntu: #246969)
 blacklist snd_pcsp
  
 # ugly and loud noise, getting on everyone's nerves; this should be done by a
 # nice pulseaudio bing (Ubuntu: #77010)
 blacklist pcspkr
  
 # EDAC driver for amd76x clashes with the agp driver preventing the aperture
 # from being initialised (Ubuntu: #297750). Blacklist so that the driver
 # continues to build and is installable for the few cases where its
 # really needed.
 blacklist amd76x_edac
``` ```
lo        no wireless extensions.
  
 eth1      no wireless extensions.
  
 wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
           Mode:Auto  Frequency=2.462 GHz  Bit Rate=1 Mb/s    
           RTS thr:off   Fragment thr:off
           Link Quality=91/100  Signal level:0 dBm  Noise level:-97 dBm
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
  
 eth0      no wireless extensions. 
```

---

### Post by izark47 on 2010-05-22
I had the same issue when i installed 10.04,  Searching around in here i found a thread that said to set to WPA-psk, and set to only aes.  After doing that it connected almost immediately.  You do this by logging into the modem and the settings are under wireless security.  You might need to call the ISP to get the login info for he modem.  Also this can be done in windows if you cannot login in 10.04.

---

### Post by izark47 on 2010-05-22
Sorry i for got this.  This seems to be an issue with Ralink chipsets.

---

### Post by AnneM on 2010-05-22
Thank you, thank you, a million times thank you ... It worked :D... I was close to crying I was getting so annoyed with it not working. You are an absolute angel.

---

### Post by izark47 on 2010-05-22
You are most welcome.  Be sure to mark this as solved

---

