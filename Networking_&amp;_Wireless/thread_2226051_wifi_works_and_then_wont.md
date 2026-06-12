---
title: "wifi works and then wont"
date: 2014-05-24
forum: Networking &amp; Wireless
---

### Post by joshua20 on 2014-05-24
ok so i have 14.04 LTS ubuntu and when i get online wifi works and then just disconnects if someone could help that would be great and i have a poor connection in my house but still it should be connecting and is there a program to make it connect no mater how many bars there are

---

### Post by praseodym on 2014-05-25
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
cat /etc/resolv.conf
ifconfig -a
sudo iwlist scan
```
Does LAN work?

---

### Post by joshua20 on 2014-05-25
```
Uname -a says         
3.13.0-24-generic #47-ubuntu SMP fri may 2 23:31:42 UTC 2014 i686 i686 i686 GNU/linux


[COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep -iA2 net  says    [/FONT][/COLOR]09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
	Subsystem: Dell Device [1028:01f9]
	Kernel driver in use: tg3
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation Device [8086:1020]
	Kernel driver in use: iwl3945





[COLOR=#000000][FONT=Ubuntu Mono]lsusb says   [/FONT][/COLOR]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub





lsmod says       Module                  Size  Used by
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342263  10 bnep,rfcomm
binfmt_misc            13140  1 
snd_hda_codec_idt      48877  1 
gpio_ich               13229  0 
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
snd_hda_intel          42730  3 
dell_laptop            17808  0 
dcdbas                 14448  1 dell_laptop
snd_hda_codec         164067  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
coretemp               13195  0 
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
pcmcia                 51828  0  
kvm                   388083  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
joydev                 17101  0 
serio_raw              13230  0 
arc4                   12536  2 
yenta_socket           40201  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
pcmcia_rsrc            18319  1 yenta_socket
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
iwl3945                63619  0 
lpc_ich                16864  0 
iwlegacy               88016  1 iwl3945
mac80211              545990  2 iwl3945,iwlegacy
snd                    60871  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mac_hid                13037  0 
i915                  705396  4 
cfg80211              409394  3 iwl3945,iwlegacy,mac80211
drm_kms_helper         46907  1 i915
drm                   243792  5 i915,drm_kms_helper
parport_pc             31981  0 
soundcore              12600  1 snd
wmi                    18673  1 dell_wmi
video                  18903  1 i915
i2c_algo_bit           13197  1 i915
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
psmouse                91033  0 
firewire_ohci          35529  0 
tg3                   152132  0 
firewire_core          61867  1 firewire_ohci
ptp                    18445  1 tg3
crc_itu_t              12627  1 firewire_core
pps_core               18799  1 ptp



 

[COLOR=#000000][FONT=Ubuntu Mono]iwconfig  says     [/FONT][/COLOR]wlan0     IEEE 802.11abg  ESSID:"Marcie340"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1A:2B:AE:0F:B1   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=20/70  Signal level=-90 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:13  Invalid misc:120   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.


[COLOR=#000000][FONT=Ubuntu Mono]cat /etc/resolv.conf  says    [/FONT][/COLOR]# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1






[COLOR=#000000][FONT=Ubuntu Mono]ifconfig -a  says   [/FONT][/COLOR] Link encap:Ethernet  HWaddr 00:21:70:a5:a4:f3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:17935 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1827903 (1.8 MB)  TX bytes:1827903 (1.8 MB)


wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:b2:9d:e1  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:feb2:9de1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:120509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124969 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:141368601 (141.3 MB)  TX bytes:15456455 (15.4 MB) 






[COLOR=#000000][FONT=Ubuntu Mono]sudo iwlist scan  says    [/FONT][/COLOR]wlan0     Failed to read scan data : Resource temporarily unavailable


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.






[COLOR=#000000]and is there a program to make it connect no mater how many bars there are[/COLOR]
```

---

### Post by praseodym on 2014-05-26
Deactivate IPv6 in the wireless profile ("Ignore") and reconnect.

---

### Post by joshua20 on 2014-05-26
ok so i looked how to do it and i did now what is  that it

---

### Post by wildmanne39 on 2014-05-26
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

