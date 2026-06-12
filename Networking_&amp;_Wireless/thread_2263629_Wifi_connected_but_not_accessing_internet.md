---
title: "Wifi connected but not accessing internet"
date: 2015-02-02
forum: Networking &amp; Wireless
---

### Post by toran2 on 2015-02-02
Hello I am new to linux so have no clue here yet.

Here is the issue I have ubuntu 14 the wifi shows it is connected but the internet is not working.  I have updated the machine, the machine is brand new. Some help getting the wifi working would be great!

Thanks

---

### Post by toran2 on 2015-02-02
Not sure if this will help any

*-network               
       description: Wireless interface
       product: RTL8192CE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 04:8d:38:53:b1:9d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.13.0-45-generic firmware=N/A ip=192.168.1.89 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:ee00(size=256) memory:fdefc000-fdefffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: fc:aa:14:53:d5:61
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.90 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:de00(size=256) memory:fdbff000-fdbfffff memory:fdbf8000-fdbfbfff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
pc@pc-GA-78LMT-USB3:~$ lsmod
Module                  Size  Used by
8192eu                688233  0 
ctr                    12905  1 
ccm                    17496  1 
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm
snd_hda_codec_hdmi     45440  1 
arc4                   12536  2 
snd_hda_codec_via      23156  1 
kvm                   388310  0 
snd_hda_intel          42794  5 
snd_hda_codec         164067  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_rawmidi            25135  1 snd_seq_midi
radeon               1420704  3 
crc32_pclmul           12967  0 
aesni_intel            18156  2 
aes_i586               16995  1 aesni_intel
rtl8192ce              52806  0 
xts                    12749  1 aesni_intel
rtl_pci                26314  1 rtl8192ce
lrw                    13057  1 aesni_intel
rtlwifi                52835  2 rtl_pci,rtl8192ce
gf128mul               14503  2 lrw,xts
rtl8192c_common        47340  1 rtl8192ce
ablk_helper            13357  1 aesni_intel
cryptd                 15578  1 ablk_helper
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
mac80211              546067  3 rtl_pci,rtlwifi,rtl8192ce
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
ttm                    72725  1 radeon
serio_raw              13230  0 
fam15h_power           12959  0 
k10temp                12958  0 
sp5100_tco             13643  0 
drm_kms_helper         48868  1 radeon
i2c_piix4              17723  0 
snd                    60939  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cfg80211              409394  2 mac80211,rtlwifi
drm                   244037  5 ttm,drm_kms_helper,radeon
soundcore              12600  1 snd
i2c_algo_bit           13197  1 radeon
shpchp                 32128  0 
mac_hid                13037  0 
wmi                    18673  0 
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47070  0 
hid                    87604  2 hid_generic,usbhid
pata_acpi              12886  0 
usb_storage            48417  2 
ahci                   25579  2 
r8169                  61562  0 
pata_atiixp            13058  0 
libahci                27214  1 ahci
mii                    13654  1 r8169
floppy                 55416  0 
pc@pc-GA-78LMT-USB3:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed. You can install it by typing:
sudo apt-get install ndiswrapper-common
pc@pc-GA-78LMT-USB3:~$ cat /etc/modprobe.d/blacklist.conf
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

---

### Post by toran2 on 2015-02-02
Really could use Some help anybody???

---

### Post by kurt18947 on 2015-02-02
It's considered good form to wait 24 hours before bumping your own post. You've given good info, I'm sure someone knowledgeable will be along soon to help you.

---

