---
title: "Broadcom BCM4318"
date: 2014-05-24
forum: Networking &amp; Wireless
---

### Post by ooober60 on 2014-05-24
Hi everybody,

I am trying to revive an old laptop that I had lying around by installing Xubuntu on it. Unfortunately it isn't going all too well. I am running into a lot of errors when trying to get the wireless card working. I am running into similar problems to the person in this post [http://ubuntuforums.org/showthread.php?t=2215661](http://ubuntuforums.org/showthread.php?t=2215661). Whenever I try to enable the driver through the additional drivers application it crashes with error invalid opcode 0000 #1 smp. Same thing when trying to run dpkg --configure -a.

After trying what was posted in that previous thread, I don't even see the wireless option anymore, it only shows wired. 

How can I fix this? Thanks

---

### Post by Hadaka on 2014-05-24
Hi, please open a terminal...ctrl/alt/t and do..
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list all
grep -v lp /etc/motd
```
post the output of each command and use code tags
thanks

---

### Post by ooober60 on 2014-05-24
```
lspci -nnk | grep -iA3 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01c9]
    Kernel driver in use: b44
    Kernel modules: b44
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: wl, ssb

```

```
 lsmod
Module                  Size  Used by
bnep                   17830  2 
snd_hda_codec_idt      60251  1 
rfcomm                 38139  0 
bluetooth             158447  10 bnep,rfcomm
snd_hda_intel          32719  4 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
parport_pc             32114  0 
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
ppdev                  12849  0 
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
dell_laptop            17767  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
i915                  428213  2 
dcdbas                 14098  1 dell_laptop
drm_kms_helper         45466  1 i915
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   197641  3 i915,drm_kms_helper
snd                    62218  17 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                96744  0 
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
serio_raw              13027  0 
b44                    31412  0 
ssb                    50691  1 b44


```

```

rfkill list all
No output

```

```
grep -v lp /etc/motd
Welcome to Ubuntu 12.04.4 LTS (GNU/Linux 3.2.0-58-generic i686)


```

Thanks!

---

### Post by Hadaka on 2014-05-24
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Hadaka on 2014-05-24
hi, while connected to the ethernet cable please do
```
sudo apt-get update
sudo modprobe -rf ssb
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf #ignore any moans and groans
```
BOOT
then do.
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```

---

### Post by ooober60 on 2014-05-24
When trying to run ```
 sudo apt-get update 
``` it says I need to run ```
 dpkg --configure -a 
``` to continue. When doing that, it crashes with an error invalid opcode 0000 #1 smp error code. 

How do I get around this?[IMG]http://i.imgur.com/viqeNOD.jpg[/IMG]

---

### Post by Hadaka on 2014-05-24
hi, try this then re-run those commands
```
sudo rm -rf /var/lib/apt/lists/lock
sudo dpkg -r bcmwl-kernel-source
```
thanks.

---

### Post by ooober60 on 2014-05-24
That fixed everything! Thanks!

So I'm guessing that package was corrupt or something like that? How did you know that that was the problem?

---

### Post by Hadaka on 2014-05-24
hi, glad that worked for you !!!

bcmwl-kernel-source is not the correct driver for your card.
your card requires the linux-nonfree driver...b43,,,,not wl
have fun !!

---

