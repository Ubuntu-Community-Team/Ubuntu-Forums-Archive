---
title: "Network drops out with too many requests (Driver?)"
date: 2013-10-12
forum: Networking &amp; Wireless
---

### Post by bsf on 2013-10-12
Hello everyone.

My network driver seems to dropout whenever I try to download things or SCP files onto the computer. I'm using Mythbuntu 12.04 (which works fine) and the wireless dongle is a **TP-LINK TL-WN821N**. If I just browse the internet or SSH into the box it works fine, but I would like to be able to download things as well.

I was trying to get the latest driver to install but it keeps defaulting to the **RTL8192CU** driver even after I blacklist it!

Not really sure what I need to post so here are a few things:

uname -a
```
Linux media 3.8.0-30-generic #44~precise1-Ubuntu SMP Fri Aug 23 17:33:45 UTC 2013 i686 i686 i386 GNU/Linux
```

sudo lshw -C network
```
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: bc:5f:f4:56:e7:d5
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:d000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@3:3
       logical name: wlan0
       serial: a0:f3:c1:29:59:91
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu ip=192.168.1.110 multicast=yes wireless=IEEE 802.11bgn

```

**lsmod**
```
Module                  Size  Used by
rfcomm                 38400  0 
bluetooth             211435  3 rfcomm
rc_dib0700_rc5         12460  0 
snd_hda_codec_hdmi     36564  1 
dvb_usb_dib0700       102288  1 
snd_hda_codec_realtek    65004  1 
dib0090                38123  1 dvb_usb_dib0700
dib7000p               34022  3 dvb_usb_dib0700
dib7000m               22994  1 dvb_usb_dib0700
dib0070                18143  3 dvb_usb_dib0700
dvb_usb                23898  1 dvb_usb_dib0700
dib8000                47910  1 dvb_usb_dib0700
dvb_core               91024  3 dib7000p,dvb_usb,dib8000
dib3000mc              22906  1 dvb_usb_dib0700
rc_core                21294  4 rc_dib0700_rc5,dvb_usb_dib0700,dvb_usb
snd_hda_intel          38819  3 
snd_hda_codec         118650  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
dibx000_common         18456  5 dvb_usb_dib0700,dib7000p,dib7000m,dib8000,dib3000mc
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  550344  4 
joydev                 17329  0 
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
coretemp               13324  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         47749  1 i915
kvm_intel             127786  0 
drm                   233935  5 i915,drm_kms_helper
snd                    57014  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
kvm                   384557  1 kvm_intel
psmouse                82769  0 
soundcore              12600  1 snd
microcode              18433  0 
ppdev                  12849  0 
i2c_algo_bit           13316  1 i915
serio_raw              13031  0 
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
parport_pc             27612  1 
mac_hid                13077  0 
lpc_ich                17048  0 
video                  19116  1 i915
mei                    36756  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
hid_logitech_dj        18311  0 
usbhid                 46125  1 hid_logitech_dj
hid                    83037  2 hid_logitech_dj,usbhid
r8169                  62532  0 
ahci                   25631  4 
libahci                26336  1 ahci
8192cu                502693  0 

```

blacklist.conf
```

# This file lists those modules which we don't want to be loaded by
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


# Blacklist old wifi
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

```

---

### Post by praseodym on 2013-10-12
Hi,

replace the driver according to this:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb
sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by bsf on 2013-10-20
Sorry for the late reply, that worked a charm. Thanks a lot! I'll see if I can mark this as solved.

---

