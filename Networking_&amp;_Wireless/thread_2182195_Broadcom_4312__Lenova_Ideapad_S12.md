---
title: "Broadcom 4312 / Lenova Ideapad S12"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by seasalt8 on 2013-10-20
[FONT=Verdana]Hello,  I am a newish user of Ubuntu and just installed Lubuntu 13.10 on an  older machine, the Lenova Ideapad S12. The problem is that my wifi is  not working. My wireless card is a Broadcom 4312. I do know how to access  a terminal and type and post back command lines and results.[/FONT]

I temporarily have the computer connected to the internet via ethernet which is working fine (I am typing this post on it).

Any help would be greatly appreciated!

Thank you

---

### Post by leclerc65 on 2013-10-20
Try installing 'firmware-b43-installer' then reboot.

---

### Post by Hadaka on 2013-10-20
Hi, you probably loaded the proprietary driver and that may
be blacklisting some of the modules you need. Let's give this
a try and see what transpires. Please do..From a wired connection
to the internet..
(*these may take some time to run)
```
sudo atp-get update
sudo apt-get upgrade
```
once complete..please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
disconnect the wired cable and boot.
*If this does NOT ativate your wireless ..please post the output of..
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list all
```
thanks.

---

### Post by seasalt8 on 2013-10-20
Thanks leclerc65. I know how to access the terminal but don't know which command to use to install firmware-b43-installer. I will try Hadaka's advise and report back.

---

### Post by seasalt8 on 2013-10-20
Thanks Hadaka that worked! I am posting this through a wifi connnection! I really appreciate your help. I will mark this as closed.

---

### Post by Hadaka on 2013-10-20
Great !, gald that worked for you.
thanks.

---

### Post by ziegler-g on 2013-12-20
I have nearly the same problem, but Hadaka's solution does not completely work for me. The WiFi light on my Dell Inspiron 1525 is turned on after boot, but I do not have WLAN access. It is driving me nuts. Only when I issue a "sudo modprobe b43" by hand in a terminal, the WLAN connects after, say, 20 seconds.

Here is what I have, according to Hadaka's recipe (bcmwl-kernel-source* is not installed*, linux-firmware-nonfree *is installed*):

```
ziegler@linspiron1525:~$ lsmod | grep b43
(no output)

ziegler@linspiron1525:~$ sudo modprobe b43
(no output)

ziegler@linspiron1525:~$ lspci -nnk | grep -iA3 net
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
    Subsystem: Dell Device [1028:022f]
    Kernel driver in use: sky2
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1395 WLAN Mini-Card [1028:000b]
    Kernel driver in use: b43-pci-bridge

ziegler@linspiron1525:~$ lsmod
Module                  Size  Used by
arc4                   12536  2 
b43                   356285  0 
bcma                   40966  1 b43
mac80211              513247  1 b43
cfg80211              401436  2 b43,mac80211
zram                   18070  1 
parport_pc             31981  0 
ppdev                  17391  0 
rfcomm                 53664  0 
bnep                   18893  2 
bluetooth             323622  10 bnep,rfcomm
joydev                 17097  0 
coretemp               13195  0 
snd_hda_codec_idt      44605  1 
gpio_ich               13229  0 
snd_hda_codec_hdmi     40373  1 
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
dell_laptop            17161  0 
dcdbas                 14383  1 dell_laptop
snd_hda_intel          42658  1 
snd_hda_codec         164003  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
r852                   17925  0 
microcode              18830  0 
sm_common              16772  1 r852
snd_rawmidi            25094  1 snd_seq_midi
nand                   58914  2 r852,sm_common
nand_ecc               13136  1 nand
psmouse                90642  0 
serio_raw              13189  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
nand_bch               13067  1 nand
r592                   17711  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
nand_ids                8547  1 nand
snd_timer              24447  2 snd_pcm,snd_seq
lpc_ich                16864  0 
memstick               16008  1 r592
bch                    17197  1 nand_bch
i915                  589697  2 
mtd                    52735  2 nand,sm_common
snd                    60790  13 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
mac_hid                13037  0 
drm_kms_helper         46867  1 i915
drm                   242354  3 i915,drm_kms_helper
wmi                    18590  1 dell_wmi
i2c_algo_bit           13197  1 i915
video                  18777  1 i915
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
sdhci_pci              18481  0 
firewire_ohci          35257  0 
ssb                    51596  1 b43
ahci                   25579  4 
libahci                26554  1 ahci
sdhci                  37468  1 sdhci_pci
firewire_core          57656  1 firewire_ohci
sky2                   52910  0 
crc_itu_t              12627  1 firewire_core

ziegler@linspiron1525:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

ziegler@linspiron1525:~$ lsmod | grep b43
b43                   356285  0 
bcma                   40966  1 b43
mac80211              513247  1 b43
cfg80211              401436  2 b43,mac80211
ssb                    51596  1 b43
(now WiFi is working)


```

---

