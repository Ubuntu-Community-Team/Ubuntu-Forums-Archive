---
title: "Wifi Compaq Presario C500 not working Ubuntu 14"
date: 2015-06-12
forum: Networking &amp; Wireless
---

### Post by ludo5 on 2015-06-12
Hi  Everyone, 


Thank you for this forum, I have trouble since 2 years with my Wifi which is not working... But here is the thing, I need my wifi to be active as quickly as possible so I have made some research and I have understood that the soft is private and if I want it to be active I need to activate it manually.

Here is some information about my laptop:

```

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:18 memory:40400000-40403fff
  *-network
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:be:c5:40
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:2000(size=256) memory:d0100000-d01000ff


06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)


Module                  Size  Used by
snd_hda_codec_conexant    47785  1 
snd_hda_intel          42730  3 
hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
snd_hda_codec         164067  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342263  10 bnep,rfcomm
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
coretemp               13195  0 
snd_rawmidi            25135  1 snd_seq_midi
joydev                 17101  0 
wl                   3999690  1 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
i915                  705574  4 
serio_raw              13230  0 
binfmt_misc            13140  1 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
lpc_ich                16864  0 
drm_kms_helper         47182  1 i915
lib80211               14040  1 wl
snd_timer              28584  2 snd_pcm,snd_seq
drm                   244037  5 i915,drm_kms_helper
cfg80211              409394  1 wl
snd                    60871  16 snd_hwdep,snd_timer,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
parport_pc             31981  0 
video                  18903  1 i915
ppdev                  17391  0 
wmi                    18673  1 hp_wmi
mac_hid                13037  0 
i2c_algo_bit           13197  1 i915
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
soundcore              12600  1 snd
ahci                   25579  3 
libahci                26754  1 ahci
psmouse                91033  0 
8139too                32571  0 
8139cp                 27171  0 
mii                    13654  2 8139cp,8139too


lo        no wireless extensions.


eth0      no wireless extensions.

```

The idea is now to find a way to activate it (without ethernet if possible as I cannot connect in the library). The forum did not give me the answer on how I should proceed so please give me some tips for ubuntu 14.04.

Thank you

---

### Post by wildmanne39 on 2015-06-12
Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
Then go to the following link and do what post 4 says.
[http://ubuntuforums.org/showthread.php?t=2269411&highlight=b43+zip](http://ubuntuforums.org/showthread.php?t=2269411&highlight=b43+zip)
Thanks

---

### Post by ludo5 on 2015-06-12
Thank you Wild Man for your help,

Here is what I did:

```

sudo apt-get purgebcmwl-kernel-source
sudo cp Desktop/b43/* /lib/firmware/b43
sudo modprobe -rvb43 
sudo modprobe -v b43

```

The main problems that I have met were with this command:
```

sudo mkdir/lib/firmware/b43

```
Cannot create directory, files exists
I had to use the name of the file b43

And now it seems that the terminal is stuck and the last command is not ending...

Should I kill the terminal?

Thank you very much.
Ludo

---

### Post by ludo5 on 2015-06-13
Ok, I gave up waiting for the terminal to debug, I rebooted, set up the wifi, reboot and the second time it worked, thank you!

---

### Post by Bucky Ball on 2015-06-13
Good news. Please mark the thread as solved by looking at the second link in my signature.

Just a note: This:

```
sudo apt-get purgebcmwl-kernel-source
```

Is wrong. I presume it was a typo. It should be:

```
sudo apt-get purge bcmwl-kernel-source
```

:)

---

