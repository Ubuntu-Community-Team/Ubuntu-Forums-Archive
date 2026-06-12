---
title: "Realtek RTL8101E/RTL8102E,  don't have wireless network - Elementary OS"
date: 2013-10-29
forum: Networking &amp; Wireless
---

### Post by blitme on 2013-10-29
Hey

I installed Elementary for 2 days ago and I dont have WIFI, it work if I plug cable but wihtout cable it wont work, a guy told me that I dont have driver and i need to install it wich is realtek.

here are some info that may help you guys to help me , I typed  lsusb and lspci 

```
blitme@Stivan-Laptop-G6:~$ sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 064e:e263 Suyin Corp. 


blitme@Stivan-Laptop-G6:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series]
07:00.0 Network controller: Ralink corp. Device 539b
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
09:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
blitme@Stivan-Laptop-G6:~$
```

---

### Post by Hadaka on 2013-10-29
Hi, from a wired connection connected to the internet,
please do..
```
sudo apt-get update
sudo apt-get upgrade
```
once this is complete, remove the ethernet cable
boot

then do..
```
sudo modprobe rt2800pci
```
thanks.

---

### Post by blitme on 2013-10-29
> **Hadaka said:**
> Hi, from a wired connection connected to the internet,
please do..
```
sudo apt-get update
sudo apt-get upgrade
```
once this is complete, remove the ethernet cable
boot

then do..
```
sudo modprobe rt2800pci
```
thanks.

dont seem to work ://, since last reboot , the network icon is removed 
[IMG]http://i.imgur.com/FNmC9l0.png[/IMG]

sudo modprobe gave me this: WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
I need install ralink driver

---

### Post by Hadaka on 2013-10-29
Hi, the rt2800pci IS a ralink driver.
please post the output of..
```
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/blacklist.conf
```
also..
```
lsmod
```
thanks.

---

### Post by blitme on 2013-10-29
> **Hadaka said:**
> Hi, the rt2800pci IS a ralink driver.
please post the output of..
```
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/blacklist.conf
```
also..
```
lsmod
```
thanks.

blitme@Stivan-Laptop-G6:~$```
 cat /etc/modprobe.d/blacklist
blacklist bcm43xx


blitme@Stivan-Laptop-G6:~$ cat /etc/modprobe.d/blacklist.conf
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










blitme@Stivan-Laptop-G6:~$ lsmod
Module                  Size  Used by
rt2800pci              18715  0 
rt2800lib              58967  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
rt2x00pci              14620  1 rt2800pci
rt2x00lib              55382  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506862  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205774  2 rt2x00lib,mac80211
eeprom_93cx6           12767  1 rt2800pci
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180113  10 rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
fglrx                6725632  99 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    41616  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
psmouse                97519  0 
serio_raw              13211  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
hp_accel               25976  0 
lis3lv02d              19876  1 hp_accel
input_polldev          13896  1 lis3lv02d
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
i915                  478326  2 
wmi                    19256  1 hp_wmi
drm_kms_helper         46978  1 i915
drm                   241971  3 i915,drm_kms_helper
r8169                  62190  0 
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
blitme@Stivan-Laptop-G6:~$
```

---

### Post by Hadaka on 2013-10-29
ok,looks like you have been busy trying things.
please open a terminal   ctrl/alt/t
then do..
```
sudo gedit /etc/modprobe.d/blacklist
```
REMOVE this one line..
```
blacklist bcm43xx
```
save and close gedit.
then do..
```
sudo rmdir /etc/modprobe.d/blacklist
```
please post the output of..
```
cat /etc/modules
```
thanks.

---

### Post by blitme on 2013-10-30
> **Hadaka said:**
> ok,looks like you have been busy trying things.
please open a terminal   ctrl/alt/t
then do..
```
sudo gedit /etc/modprobe.d/blacklist
```
REMOVE this one line..
```
blacklist bcm43xx
```
save and close gedit.
then do..
```
sudo rmdir /etc/modprobe.d/blacklist
```
please post the output of..
```
cat /etc/modules
```
thanks.


what do you mean by ''REMOVE this one line..''`?

---

### Post by blitme on 2013-10-30
> **Hadaka said:**
> ok,looks like you have been busy trying things.
please open a terminal   ctrl/alt/t
then do..
```
sudo gedit /etc/modprobe.d/blacklist
```
REMOVE this one line..
```
blacklist bcm43xx
```
save and close gedit.
then do..
```
sudo rmdir /etc/modprobe.d/blacklist
```
please post the output of..
```
cat /etc/modules
```
thanks.


the last code dont worked (sudo rmdir..)

here outpot:

blitme@Stivan-Laptop-G6:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


lp
rtc

---

### Post by wildmanne39 on 2013-10-30
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by blitme on 2013-10-31
Bumping it up

---

### Post by Hadaka on 2013-10-31
Hi,please post the output of..
```
lsmod
dmesg | grep rt2
```
thanks.

---

### Post by blitme on 2013-11-01
> **Hadaka said:**
> Hi,please post the output of..

```
lsmod
dmesg | grep rt2
```
thanks.

updated to latest kernel and saw that choice: wireless was there! but can't click on any network, when I choose my network , its just goes away
[IMG]http://i.imgur.com/HSeohvG.png[/IMG]


ismod: 
```
 blitme@Stivan-Laptop-G6:~$ lsmodModule                  Size  Used by
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180113  10 rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
fglrx                6725632  88 
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
hp_accel               25976  0 
lis3lv02d              19876  1 hp_accel
snd_rawmidi            30748  1 snd_seq_midi
input_polldev          13896  1 lis3lv02d
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
psmouse                97519  0 
serio_raw              13211  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
mac_hid                13253  0 
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
wmi                    19256  1 hp_wmi
i915                  478326  2 
drm_kms_helper         46978  1 i915
drm                   241971  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
r8169                  62190  0 



```


the 2nd command dont worked, nothing happens

---

### Post by blitme on 2013-11-02
Bumping this, hope i get help asap

---

### Post by blitme on 2013-11-09
Bumping, someone can help me out?

---

