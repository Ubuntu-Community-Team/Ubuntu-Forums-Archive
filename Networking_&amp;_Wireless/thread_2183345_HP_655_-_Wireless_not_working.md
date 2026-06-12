---
title: "HP 655 - Wireless not working"
date: 2013-10-24
forum: Networking &amp; Wireless
---

### Post by Theodore_Hill on 2013-10-24
Hello, my wireless stopped working after installing the latest KERNEL 3.2.0-55
I switched back to 3.2.0-54-generic & it's working fully again.
What should I do? It also says: UNCLAIMED
Thank you!

---

### Post by Hadaka on 2013-10-24
Hi,please post the output of..
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list all
```
thanks

---

### Post by Theodore_Hill on 2013-10-24
lspci -nnk | grep -iA3 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1885]
    Kernel driver in use: r8169
    Kernel modules: r8169
04:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
04:00.1 Bluetooth [0d11]: Ralink corp. RT3290 Bluetooth [1814:3298]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]


lsmod
Module                  Size  Used by
vesafb                 13844  1 
rfcomm                 47604  12 
snd_hda_codec_realtek    73901  1 
parport_pc             32866  0 
bnep                   18281  2 
snd_hda_codec_hdmi     36516  1 
ppdev                  17113  0 
joydev                 17693  0 
snd_hda_intel          33605  5 
binfmt_misc            17540  1 
snd_hda_codec         139218  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
fglrx                4718170  86 
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72627  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
dm_multipath           23275  0 
k10temp                13166  0 
psmouse                97519  0 
serio_raw              13211  0 
snd                    79041  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rts5229               306691  0 
rtbth                  76648  3 
videodev               98259  1 uvcvideo
video                  19651  0 
mac_hid                13253  0 
soundcore              15091  1 snd
bluetooth             180113  23 rfcomm,bnep,rtbth
v4l2_compat_ioctl32    17128  1 videodev
wmi                    19105  1 hp_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
i2c_piix4              13301  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
r8169                  62190  0 
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20961  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 653061  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs


rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by wildmanne39 on 2013-10-24
I see you jumped ship.:P

---

### Post by Hadaka on 2013-10-24
Hi, please continue to work with the Wild Man as he has
delt with this issue before. also refer to thread..
[http://askubuntu.com/questions/364530/hp-655-notebook-ubuntu-12-04-wireless-internet-disabled-after-running-updates/364756?noredirect=1#comment466872_364756](http://askubuntu.com/questions/364530/hp-655-notebook-ubuntu-12-04-wireless-internet-disabled-after-running-updates/364756?noredirect=1#comment466872_364756)
thanks.

---

### Post by wildmanne39 on 2013-10-24
Hi, @ Hadaka feel free to help this person, I was just razzing him.

You can do what is in this link and it should get your wireless working but you will have to do this process every time there is a kernel update, I personally prefer to lock the kernel from being updated.
[http://ubuntuforums.org/showthread.php?t=2159334&page=2](http://ubuntuforums.org/showthread.php?t=2159334&page=2)
Thanks

---

