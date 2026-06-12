---
title: "I am quite new to Unbuntu and I need help setting up Wireless card drivers"
date: 2015-10-19
forum: Networking &amp; Wireless
---

### Post by cory18 on 2015-10-19
So I found a lot of threads on this subject that have been previously solved but none have been working for me and I have not been able to post to those solved threads so i decided to make my own any ways here is the terminal output of my laptop and I was wondering if anyone can help me figure out why other methods have not been working for my wifi thank you for the help :) also my card is : U98Z049.00 wireless mini pCle Card

batman@batman-HP-Pavilion-dv4-Notebook-PC:~$ cat /etc/lisb-release; uname -a
cat: /etc/lisb-release: No such file or directory
Linux batman-HP-Pavilion-dv4-Notebook-PC 3.19.0-30-generic #34~14.04.1-Ubuntu SMP Fri Oct 2 22:09:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
batman@batman-HP-Pavilion-dv4-Notebook-PC:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company U98Z049.00 Wireless Mini PCIe Card [103c:1507]
    Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Kernel driver in use: r8169
batman@batman-HP-Pavilion-dv4-Notebook-PC:~$ lsusb
Bus 002 Device 002: ID 090c:137b Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
batman@batman-HP-Pavilion-dv4-Notebook-PC:~$ iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr : off   Fragment thr : off
          Power Management : off
          
lo        no wireless extensions.

batman@batman-HP-Pavilion-dv4-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
batman@batman-HP-Pavilion-dv4-Notebook-PC:~$ lsmod
Module                  Size  Used by
bnep                   20480  2 
rfcomm                 69632  0 
bluetooth             491520  10 bnep,rfcomm
uvcvideo               90112  0 
snd_hda_codec_hdmi     53248  2 
wl                   6369280  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         53248  1 uvcvideo
snd_hda_codec_idt      61440  1 
v4l2_common            16384  1 videobuf2_core
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_codec_generic    69632  1 snd_hda_codec_idt
media                  24576  2 uvcvideo,videodev
snd_hda_intel          36864  4 snd_hda_codec_hdmi
snd_hda_controller     32768  1 snd_hda_intel
i915                 1048576  4 
snd_hda_codec         143360  5 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
cfg80211              524288  1 wl
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
coretemp               16384  0 
drm_kms_helper        126976  1 i915
snd_rawmidi            32768  1 snd_seq_midi
joydev                 20480  0 
lpc_ich                24576  0 
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
drm                   344064  6 i915,drm_kms_helper
serio_raw              16384  0 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
hp_accel               28672  0 
wmi                    20480  1 hp_wmi
snd                    86016  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_algo_bit           16384  1 i915
ir_lirc_codec          16384  0 
soundcore              16384  2 snd,snd_hda_codec
ir_mce_kbd_decoder     16384  0 
ir_xmp_decoder         16384  0 
ir_rc6_decoder         16384  0 
lirc_dev               20480  1 ir_lirc_codec
ir_nec_decoder         16384  0 
ir_sanyo_decoder       16384  0 
ir_rc5_decoder         16384  0 
ir_jvc_decoder         16384  0 
ir_sharp_decoder       16384  0 
ir_sony_decoder        16384  0 
rc_rc6_mce             16384  0 
lis3lv02d              20480  1 hp_accel
shpchp                 40960  0 
input_polldev          16384  1 lis3lv02d
ene_ir                 24576  0 
rc_core                28672  14 ir_sharp_decoder,ir_xmp_decoder,lirc_dev,ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,ene_ir,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder,rc_rc6_mce
video                  20480  1 i915
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
psmouse               114688  0 
ahci                   36864  2 
libahci                32768  1 ahci
r8169                  81920  0 
mii                    16384  1 r8169

---

### Post by Hadaka on 2015-10-19
hi, from a working wired connection open a terminal ctrl/alt/t 
then COPY and paste each command one at a time-you may get
a not found or error message on some..not to worry- do them any
way..
```
sudo apt-get update && sudo apt-get upgrade
```
then do.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
then do
```
sudo apt-get autoremove && sudo apt-get autoclean
```
reboot--remove wired connection--test wireless

---

