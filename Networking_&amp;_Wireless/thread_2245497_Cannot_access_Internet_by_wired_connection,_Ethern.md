---
title: "Cannot access Internet by wired connection, Ethernet Network disconnected."
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by mycityofsky on 2014-09-24
network manager display: Ethernet Network disconnected.
 It also doesn't work even after "sudo dhclient eth0", the address it assigned wasn't correct.

The result of relevant commands are as follows(without "sudo dhclient eht0" executed), thank you for your help:

ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:17:a4:d7:ff:7c  
          inet6 addr: fe80::217:a4ff:fed7:ff7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:709666 (709.6 KB)  TX bytes:458 (458.0 B)
          Interrupt:16 

```

cat /etc/network/interfaces:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

lsmod:
```
Module                  Size  Used by
ctr                    12905  3 
ccm                    17496  3 
bnep                   18895  2 
rfcomm                 58045  0 
bluetooth             387157  10 bnep,rfcomm
6lowpan_iphc           18262  1 bluetooth
arc4                   12536  2 
hp_wmi                 13741  0 
sparse_keymap          13708  1 hp_wmi
pcmcia                 51828  0 
coretemp               13201  0 
kvm_intel             137052  0 
kvm                   388225  1 kvm_intel
snd_hda_codec_si3054    12928  1 
snd_hda_codec_analog    14537  1 
snd_hda_codec_generic    62873  1 snd_hda_codec_analog
radeon               1303920  2 
microcode              19511  0 
snd_hda_intel          29252  3 
joydev                 17113  0 
ttm                    76972  1 radeon
snd_hda_controller     29944  1 snd_hda_intel
drm_kms_helper         55007  1 radeon
snd_hda_codec         120371  5 snd_hda_codec_si3054,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller,snd_hda_codec_analog
lpc_ich                16877  0 
serio_raw              13251  0 
snd_hwdep              13272  1 snd_hda_codec
drm                   255469  5 ttm,drm_kms_helper,radeon
yenta_socket           40215  0 
snd_pcm                87194  4 snd_hda_codec_si3054,snd_hda_codec,snd_hda_intel,snd_hda_controller
tifm_7xx1              13182  0 
pcmcia_rsrc            18319  1 yenta_socket
b43                   369555  0 
bcma                   46331  1 b43
mac80211              559033  1 b43
tifm_core              15133  1 tifm_7xx1
snd_seq_midi           13324  0 
cfg80211              418811  2 b43,mac80211
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
ssb_hcd                12764  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i2c_algo_bit           13197  1 radeon
snd_rawmidi            25722  1 snd_seq_midi
snd_seq                56592  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28648  2 snd_pcm,snd_seq
snd                    66670  17 snd_hda_codec_si3054,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog
shpchp                 32143  0 
soundcore              14599  2 snd,snd_hda_codec
wmi                    18689  1 hp_wmi
tpm_infineon           16979  0 
hp_accel               25778  0 
lis3lv02d              19500  1 hp_accel
video                  19475  0 
parport_pc             32021  1 
input_polldev          14247  1 lis3lv02d
ppdev                  17391  0 
lp                     13299  0 
mac_hid                13059  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12503  0 
usbhid                 47042  0 
hid                    87754  2 hid_generic,usbhid
psmouse                91171  0 
sdhci_pci              18608  0 
firewire_ohci          35647  0 
sdhci                  38345  1 sdhci_pci
firewire_core          61867  1 firewire_ohci
ahci                   25622  7 
libahci                26970  1 ahci
pata_acpi              12901  0 
crc_itu_t              12627  1 firewire_core
tg3                   156351  0 
ssb                    51835  2 b43,ssb_hcd
ptp                    18861  1 tg3
pps_core               18799  1 ptp

```

lspci -nnk | grep -iA2 net:
```
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express [14e4:16fd] (rev 21)
    Subsystem: Hewlett-Packard Company Compaq nw8440 [103c:30a3]
    Kernel driver in use: tg3
10:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel driver in use: b43-pci-bridge

```

---

### Post by ben222qmz7 on 2014-09-24
I have the same problem. It started about a week ago after some automatic updtes.
Before that there was no difficulties.
I beleive it must be something wrong with that particular update propably on 17th September.
Only important security updates accepted.
My setup is Xubuntu 12.04 and WinXP Pro  with dualboot alternative on HP 6735s laptop.
Ethernet connection does not work on Windows either.

Wireless connection is OK.

---

### Post by nedkelly on 2014-12-16
Hi

I have same problem, cannot find a solution, found any?

---

