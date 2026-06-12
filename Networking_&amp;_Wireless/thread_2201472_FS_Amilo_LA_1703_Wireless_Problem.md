---
title: "FS Amilo LA 1703 Wireless Problem"
date: 2014-01-24
forum: Networking &amp; Wireless
---

### Post by Andrew_Tsioutsias on 2014-01-24
Good evening, 
I'm happy to finally be a part of this community. I always wanted to use  a Linux based OS on one of my comuters but i never had th courage to  leave windows. 
I just installed Ubuntu on an old laptop that i had for dead. As it  turns out i works perfectly. It had win Vista installed by default but i  was so slow it was impossible to use. The only issue that i have is the  fact that it seems that the wireless card doesn't work. It doesn't  detect any network. However when it comes to wired connection it works  like a charm.
If anyone could help me that would be great.
Thanks in advance.

---

### Post by praseodym on 2014-01-24
Hi,

please open a terminal and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Andrew_Tsioutsias on 2014-01-25
thanks you for your respond, i run the commands and these are the results:

andrew@andrew-AMILO-La1703:~$ uname -a
Linux andrew-AMILO-La1703 3.8.0-35-generic #50~precise1-Ubuntu SMP Wed Dec 4 17:25:51 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
andrew@andrew-AMILO-La1703:~$ lspci -nnk | grep -iA2 net
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 7c)
            Subsystem: Fujitsu Technology Solutions Device [1734:10d9]
            Kernel driver in use: via-rhine
andrew@andrew-AMILO-La1703:~$ lsusb
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 002 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
andrew@andrew-AMILO-La1703:~$ lsmod
Module                  Size  Used by
vesafb                 13876  1
bnep                   18399  2
rfcomm                 47922  0
bluetooth             247324  10 bnep,rfcomm
parport_pc             28284  0
ppdev                  17113  0
arc4                   12573  2
rtl8187                65191  0
mac80211              631450  1 rtl8187
snd_hda_codec_si3054    13008  1
snd_hda_codec_via      51859  1
snd_hda_intel          44339  3
snd_hda_codec         141761  3 snd_hda_codec_si3054,snd_hda_codec_via,snd_hda_intel
cfg80211              526422  2 rtl8187,mac80211
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0
eeprom_93cx6           13344  1 rtl8187
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_core              62754  0
snd                    69533  16 snd_hda_codec_si3054,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17613  0
k8temp                 13064  0
edac_mce_amd           23343  0
psmouse                97902  0
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
i2c_viapro             13153  0
serio_raw              13215  0
video                  19652  0
mac_hid                13253  0
shpchp                 37201  0
lp                     17799  0
parport                46562  3 parport_pc,ppdev,lp
hid_generic            12540  0
usbhid                 47346  0
hid                   105826  2 hid_generic,usbhid
via_rhine              28031  0
pata_acpi              13038  0
pata_via               13712  0
sata_via               13810  2
andrew@andrew-AMILO-La1703:~$ iwconfig
eth0      no wireless extensions.
 
lo        no wireless extensions.
 
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
         
andrew@andrew-AMILO-La1703:~$ rfkill list
0: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: yes
andrew@andrew-AMILO-La1703:~$

---

### Post by praseodym on 2014-01-25
The driver is loaded, but wireless is switched off (see "hard blocked: yes"). Any button switch/key/key combination? Checked the BIOS-settings?

---

### Post by Andrew_Tsioutsias on 2014-01-25
You're right. It was disabled from the BIOS.  Thank you so much!! Now i might even put an ssd on this machine. it works great.

---

