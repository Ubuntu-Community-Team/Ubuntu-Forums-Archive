---
title: "Unstable wireless connection"
date: 2013-10-27
forum: Networking &amp; Wireless
---

### Post by ujai on 2013-10-27
Hi

Need your assistance with my wireless issue, I can connect to it for a few minutes, then it disconnects, tried to reconnect but failed unless I reboot the machine.


Here's the details

lspci -nnk | grep -iA2 net
```
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
```
lsusb
```
Bus 002 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 004 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
lsmod
```
Module                  Size  Used by
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323534  10 bnep,rfcomm
coretemp               13195  0 
kvm_intel             128218  0 
kvm                   364766  1 kvm_intel
gpio_ich               13229  0 
ppdev                  17391  0 
arc4                   12536  2 
ext2                   63128  1 
rtl8187                56061  0 
mac80211              513247  1 rtl8187
cfg80211              401436  2 mac80211,rtl8187
eeprom_93cx6           13168  1 rtl8187
snd_hda_codec_hdmi     40508  4 
microcode              18830  0 
snd_hda_codec_realtek    45473  1 
i7core_edac            23458  0 
edac_core              51256  2 i7core_edac
serio_raw              13189  0 
snd_hda_intel          42658  5 
snd_hda_codec         164003  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
lpc_ich                16864  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
snd                    60790  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
parport_pc             31981  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
xts                    12749  1 
gf128mul               14503  1 xts
dm_crypt               22280  1 
pata_acpi              12886  0 
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87192  2 hid_generic,usbhid
nouveau               834976  3 
mxm_wmi                12893  1 nouveau
wmi                    18590  2 mxm_wmi,nouveau
video                  18777  1 nouveau
i2c_algo_bit           13197  1 nouveau
ttm                    71886  1 nouveau
drm_kms_helper         46867  1 nouveau
drm                   242354  5 ttm,drm_kms_helper,nouveau
r8169                  61434  0 
pata_jmicron           12662  0 
ahci                   25579  0 
libahci                26554  1 ahci
mii                    13654  1 r8169
floppy                 55378  0
```
iwconfig
```
wlan0     IEEE 802.11bg  ESSID:"abudzar@unifi"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: BC:F6:85:0F:C3:38   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:292   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.
```
ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:7a:37:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50924 (50.9 KB)  TX bytes:50924 (50.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:e0:4c:83:10:5c  
          inet addr:192.168.0.107  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe83:105c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10187420 (10.1 MB)  TX bytes:1320497 (1.3 MB)
```
rfkill list
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```
sudo iwlist scan
```
wlan0     Scan completed :
          Cell 01 - Address: BC:F6:85:0F:C3:38
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"abudzar@unifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000017ad467e582
                    Extra: Last beacon: 320ms ago
                    IE: Unknown: 000D616275647A617240756E696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group 

```

Thanks in advance

---

