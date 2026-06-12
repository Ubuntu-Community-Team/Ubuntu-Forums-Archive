---
title: "Wi-fi stopped working"
date: 2019-08-17
forum: Networking &amp; Wireless
---

### Post by bilkay on 2019-08-17
Ubuntu 16,04 on an HP Laptop with a RealTek wi-fi adapter. When ubuntu 16.04 first installed, had to follow the procedure in thread [https://ubuntuforums.org/showthread.php?t=2419146](https://ubuntuforums.org/showthread.php?t=2419146) to get the adapter to work. Everything was working fine until I tried to run Boot Repair from CDROM (unrelated problem). I couldn't get the laptop to boot the CD. I tried switching legacy mode off in the bios, and it still wouldn't boot. I then re-enabled legacy mode and booted back into ununtu. That's when I saw that I had no wi-fi with networking enabled. Booted into windoze to see if the adapter was working - it was. Booted back into ubuntu. This is what I got from ifconfig:

```
$ ifconfig

enp2s0    Link encap:Ethernet  HWaddr c4:65:16:92:40:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2119376 (2.1 MB)  TX bytes:522208 (522.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109995 (109.9 KB)  TX bytes:109995 (109.9 KB)
```

Then tried ifup (as root):

```
$ ifup wlo1

Unknown interface wlo1
```

Next, tried lshw:

```
$ lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 15
       serial: c4:65:16:92:40:53
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:32 ioport:3000(size=256) memory:f0b04000-f0b04fff memory:f0b00000-f0b03fff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0a00000-f0a0ffff
```

Grasping at straws, I tried:

```
$ modprobe rtl8723de
modprobe: ERROR: could not insert 'rtl8723de': Required key not available
```

Here is what I think is relevant output in syslog following boot:

```
Aug 17 12:29:50 Laptop kernel: [   21.711577] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723d_config.bin
Aug 17 12:29:50 Laptop kernel: [   21.770180] media: Linux media interface: v0.10
Aug 17 12:29:50 Laptop kernel: [   21.778484] Linux video capture interface: v2.00
Aug 17 12:29:50 Laptop kernel: [   21.781908] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723d_config.bin failed with error -2
Aug 17 12:29:50 Laptop kernel: [   21.781915] Bluetooth: Necessary config file rtl_bt/rtl8723d_config.bin not found
Aug 17 12:29:50 Laptop kernel: [   21.781915] 
Aug 17 12:29:50 Laptop kernel: [   21.781920] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723d_fw.bin
Aug 17 12:29:50 Laptop kernel: [   21.781940] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723d_fw.bin failed with error -2
Aug 17 12:29:50 Laptop kernel: [   21.781942] Bluetooth: hci0: Failed to load rtl_bt/rtl8723d_fw.bin
Aug 17 12:29:50 Laptop kernel: [   21.806216] uvcvideo: Found UVC 1.00 device HP Webcam (04ca:707d)
Aug 17 12:29:50 Laptop kernel: [   21.812168] snd_hda_intel 0000:00:01.1: Force to non-snoop mode
Aug 17 12:29:50 Laptop kernel: [   21.815685] uvcvideo 2-1:1.0: Entity type for entity Extension 7 was not initialized!
Aug 17 12:29:50 Laptop kernel: [   21.815689] uvcvideo 2-1:1.0: Entity type for entity Processing 2 was not initialized!
Aug 17 12:29:50 Laptop kernel: [   21.815691] uvcvideo 2-1:1.0: Entity type for entity Camera 1 was not initialized!
Aug 17 12:29:50 Laptop kernel: [   21.815692] uvcvideo 2-1:1.0: Entity type for entity Extension 4 was not initialized!
Aug 17 12:29:50 Laptop kernel: [   21.815930] input: HP Webcam: HP Webcam as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input11
Aug 17 12:29:50 Laptop kernel: [   21.816605] [drm] {1366x768, 1592x800@76420Khz}
Aug 17 12:29:50 Laptop kernel: [   21.816716] usbcore: registered new interface driver uvcvideo
Aug 17 12:29:50 Laptop kernel: [   21.816717] USB Video Class driver (1.1.1)
Aug 17 12:29:50 Laptop kernel: [   21.823602] [drm] HBRx1 pass VS=0, PE=0
Aug 17 12:29:50 Laptop kernel: [   21.829124] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input12
Aug 17 12:29:50 Laptop kernel: [   21.840046] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC236: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
Aug 17 12:29:50 Laptop kernel: [   21.840050] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Aug 17 12:29:50 Laptop kernel: [   21.840051] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
Aug 17 12:29:50 Laptop kernel: [   21.840054] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
Aug 17 12:29:50 Laptop kernel: [   21.840055] snd_hda_codec_realtek hdaudioC1D0:    inputs:
Aug 17 12:29:50 Laptop kernel: [   21.840500] snd_hda_codec_realtek hdaudioC1D0:      Mic=0x19
Aug 17 12:29:50 Laptop kernel: [   21.840502] snd_hda_codec_realtek hdaudioC1D0:      Internal Mic=0x12
Aug 17 12:29:50 Laptop kernel: [   21.886874] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:09.2/sound/card1/input13
Aug 17 12:29:50 Laptop kernel: [   21.886941] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:09.2/sound/card1/input14
Aug 17 12:29:50 Laptop kernel: [   21.933991] AVX2 version of gcm_enc/dec engaged.
Aug 17 12:29:50 Laptop kernel: [   21.933994] AES CTR mode by8 optimization enabled
Aug 17 12:29:50 Laptop kernel: [   22.010698] kvm: disabled by bios
Aug 17 12:29:50 Laptop kernel: [   22.014207] MCE: In-kernel MCE decoding enabled.
Aug 17 12:29:50 Laptop kernel: [   22.094548] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
Aug 17 12:29:50 Laptop kernel: [   22.094552] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723d_config.bin
Aug 17 12:29:50 Laptop kernel: [   22.094569] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723d_config.bin failed with error -2
Aug 17 12:29:50 Laptop kernel: [   22.094572] Bluetooth: Necessary config file rtl_bt/rtl8723d_config.bin not found
Aug 17 12:29:50 Laptop kernel: [   22.094572] 
Aug 17 12:29:50 Laptop kernel: [   22.094577] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723d_fw.bin
Aug 17 12:29:50 Laptop kernel: [   22.094585] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723d_fw.bin failed with error -2
Aug 17 12:29:50 Laptop kernel: [   22.094586] Bluetooth: hci0: Failed to load rtl_bt/rtl8723d_fw.bin

```


Coincidentally (?), I bought this Laptop because the adapter on my old HP laptop stopped working similarly (it was time and I was looking for an excuse). After a while (many days) it started working again.

---

### Post by jeremy31 on 2019-08-17
Go into BIOS and disable Secure Boot, leave the Secure Boot keys alone

---

### Post by bilkay on 2019-08-17
That's the ticket! Secure Boot must have re-enabled itself when I switched modes. Muchas Gracias!

---

