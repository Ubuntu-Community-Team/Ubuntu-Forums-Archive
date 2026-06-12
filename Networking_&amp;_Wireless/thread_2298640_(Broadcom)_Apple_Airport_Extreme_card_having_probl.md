---
title: "(Broadcom) Apple Airport Extreme card having problems working on Kubuntu 15.04 vivid."
date: 2015-10-12
forum: Networking &amp; Wireless
---

### Post by viktorahlstrom on 2015-10-12
I've been trying to work my Broadcom BCM4321 card and it is not working. I have tried `b43` and the STA driver - any help?
Here's the output of some commands:
```
[FONT=monospace][COLOR=#000000]revenge@kubuntu:~$ lspci -vvnn | grep -A 9 Network  [/COLOR]
03:00.0 Network[COLOR=#000000] controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)[/COLOR]
        Subsystem: Apple Inc. AirPort Extreme [106b:0087]
        Physical Slot: 1
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 256 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at c8200000 (64-bit, non-prefetchable) [size=16K]
        Region 2: Memory at c8000000 (64-bit, prefetchable) [size=1M]
        Capabilities: <access denied>
revenge@kubuntu:~$ 
[/FONT]

```
```
[FONT=monospace][COLOR=#000000]revenge@kubuntu:~$ ifconfig[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:19:e3:41:70:50   
          inet addr:192.168.255.47  Bcast:192.168.255.255  Mask:255.255.255.0
          inet6 addr: fe80::219:e3ff:fe41:7050/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:166995 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000  
          RX bytes:229240341 (229.2 MB)  TX bytes:10116675 (10.1 MB)
          Interrupt:16  

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2911 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0  
          RX bytes:385404 (385.4 KB)  TX bytes:385404 (385.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:63:17:6e:c7   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

revenge@kubuntu:~$ 
[/FONT]

```
```
[FONT=monospace][COLOR=#000000]eth0      no wireless extensions.[/COLOR]

wlan0     IEEE 802.11abg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
           
lo        no wireless extensions.


[/FONT]

```
```
[FONT=monospace][COLOR=#000000]revenge@kubuntu:~$ iwlist wlan0 scan[/COLOR]
wlan0     No scan results

revenge@kubuntu:~$ 

[/FONT]

```
```
[FONT=monospace][COLOR=#000000]revenge@kubuntu:~$ lsmod[/COLOR]
Module                  Size  Used by
b43                   421888  0  
bcma                   57344  1 b43
mac80211              724992  1 b43
cfg80211              540672  2 b43,mac80211
binfmt_misc            20480  1  
rfcomm                 69632  8  
bnep                   20480  2  
isight_firmware        16384  0  
arc4                   16384  2  
snd_hda_codec_idt      65536  1  
snd_hda_codec_generic    69632  1 snd_hda_codec_idt
snd_hda_intel          36864  5  
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  4 snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
btusb                  40960  0  
bluetooth             491520  22 bnep,btusb,rfcomm
coretemp               16384  0  
kvm_intel             151552  0  
snd_usb_audio         180224  2  
snd_usbmidi_lib        32768  1 snd_usb_audio
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
kvm                   483328  1 kvm_intel
applesmc               20480  0  
input_polldev          16384  1 applesmc
hid_appleir            16384  0  
joydev                 20480  0  
snd_pcm               106496  5 snd_usb_audio,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           16384  0  
ssb_hcd                16384  0  
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    90112  25 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_
generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  2 snd,snd_hda_codec
lpc_ich                24576  0  
shpchp                 40960  0  
apple_bl               16384  0  
mac_hid                16384  0  
parport_pc             32768  0  
ppdev                  20480  0  
lp                     20480  0  
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2  
hid_apple              16384  0  
hid_generic            16384  0  
usbhid                 53248  0  
hid                   110592  4 hid_generic,usbhid,hid_appleir,hid_apple
amdkfd                 81920  1  
amd_iommu_v2           20480  1 amdkfd
firewire_ohci          45056  0  
radeon               1556480  11  
pata_acpi              16384  0  
video                  20480  0  
firewire_core          69632  1 firewire_ohci
i2c_algo_bit           16384  1 radeon
ttm                    98304  1 radeon
crc_itu_t              16384  1 firewire_core
ssb                    65536  2 b43,ssb_hcd
drm_kms_helper        126976  1 radeon
drm                   344064  14 ttm,drm_kms_helper,radeon
sky2                   61440  0  
revenge@kubuntu:~$ 

[/FONT]

```

---

### Post by Hadaka on 2015-10-12
Hi, try this..from a working wired connection
do each command even if there are errors,,
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install --reinstall firmware-b43-installer
sudo modprobe b43
```
remove the wired connection...reboot...test wireless

*If you still have no wireless...go here, read carefully
and post the wireless-info.txt file. It will be in your home directory
[http://ubuntuforums.org/showthread.php?t=370108&](http://ubuntuforums.org/showthread.php?t=370108&)

---

### Post by viktorahlstrom on 2015-10-12
Many thanks to you, good sir!

---

### Post by Hadaka on 2015-10-12
You are welcome, glad that worked for you !

---

