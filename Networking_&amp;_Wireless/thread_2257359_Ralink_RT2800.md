---
title: "Ralink RT2800"
date: 2014-12-19
forum: Networking &amp; Wireless
---

### Post by itAyXD on 2014-12-19
Hi I've been using ubuntu for really long time now, and my wireless card always worked just fine. Recently it just stopped working, I can't see wlan0 on ifconfing anymore and can't use the card.
Hopefully you can help me debug the problem. The card I'm using is based on Ralink 2860. Below is all the information I think might help, if you need to see something else just tell me.
Here's the output of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:84:f0:aa  
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe84:f0aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22327 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:31964610 (31.9 MB)  TX bytes:2609342 (2.6 MB)
          Memory:dbfc0000-dc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:263826 (263.8 KB)  TX bytes:263826 (263.8 KB)
```

And here's the output of lshw -c network:
```
  *-network               
       description: Ethernet interface
       product: Attansic L2 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: a0
       serial: 00:1f:c6:84:f0:aa
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 duplex=full firmware=L2 ip=192.168.2.104 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:dbfc0000-dbffffff memory:dbfa0000-dbfbffff
  *-network UNCLAIMED
       description: Network controller
       product: RT2800 802.11n PCI
       vendor: Ralink corp.
       physical id: 1
       bus info: pci@0000:01:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=4 mingnt=2
       resources: memory:dbaf0000-dbafffff

```

uname output:
```
Linux 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:44 UTC 2014 i686 i686 i686 GNU/Linux
```

and finally, when I run dmesg | grep rt2 i get these errors:
```
ieee80211 phy0: rt2800_probe_rt: Error - Invalid RT chipset 0x2820, rev 0101 detected
ieee80211 phy0: rt2x00lib_probe_dev: Error - Failed to allocate device

```

Thanks in advnace;
Itay

---

### Post by chili555 on 2014-12-19
May we also see:```
lspci -nn | grep 0280
```Thanks.

---

### Post by itAyXD on 2014-12-19
Of course - 
lspci -nn| grep 0280:
```
01:01.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
```

---

### Post by sbnwl on 2014-12-19
Look into modules loaded currently:
```
lsmod
```

---

### Post by itAyXD on 2014-12-19
lsmod:
```
Module                  Size  Used by
rt2800pci              13374  0 
rt2800mmio             16189  1 rt2800pci
rt2800lib              83150  2 rt2800pci,rt2800mmio
rt2x00pci              13111  1 rt2800pci
rt2x00mmio             13395  2 rt2800pci,rt2800mmio
rt2x00lib              48886  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              546051  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              409394  2 mac80211,rt2x00lib
eeprom_93cx6           13168  1 rt2800pci
crc_ccitt              12627  1 rt2800lib
nls_utf8               12493  1 
udf                    83847  1 
crc_itu_t              12627  1 udf
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm
binfmt_misc            13140  1 
gpio_ich               13229  0 
joydev                 17101  0 
kvm_intel             132651  0 
snd_hda_codec_realtek    59259  1 
ppdev                  17391  0 
rt5390sta            1368922  0 
kvm                   388310  1 kvm_intel
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              13230  0 
snd_rawmidi            25135  1 snd_seq_midi
lpc_ich                16864  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
nvidia              10333941  70 
snd                    60939  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   244037  1 nvidia
soundcore              12600  1 snd
parport_pc             31981  1 
asus_atk0110           18201  0 
mac_hid                13037  0 
hwmon_vid              12687  0 
coretemp               13195  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47070  0 
hid                    87604  2 hid_generic,usbhid
floppy                 55416  0 
atl2                   27628  0 

```

---

### Post by chili555 on 2014-12-19
A quick Google search of "Invalid RT chipset 0x2820" seems to indicate that there is only one occurrence of this in the universe; you!

If you interrupt the boot process with the right shift key, access the GRUB menu and select an earlier kernel version, does it work correctly? If so, in which kernel is it working? [http://cdn5.howtogeek.com/wp-content/uploads/2007/09/image55.png](http://cdn5.howtogeek.com/wp-content/uploads/2007/09/image55.png)

I am beginning to wonder if the card is in some way defective. I hope not.

---

### Post by sbnwl on 2014-12-19
Your kernel doesn't seem to have the module loaded for your wireless card.

Can you reboot your machine into any previous kernel and check?

 (At GRUB screen choose any of the last working kernels by using up-down arrow, while booting)
To get the GRUB screen you need to keep the left side SHIFT key when turning on your computer.

---

### Post by chili555 on 2014-12-19
> **sbnwl said:**
> Your kernel doesn't seem to have the module loaded for your wireless card.

Can you reboot your machine into any previous kernel and check?

 (At GRUB screen choose any of the last working kernels by using up-down arrow, while booting)
To get the GRUB screen you need to keep the left side SHIFT key when turning on your computer.*It absolutely **is** loaded*:> rt2800pci              13374  0 
rt2800mmio             16189  1 rt2800pci
rt2800lib              83150  2 rt2800pci,rt2800mmio
rt2x00pci              13111  1 rt2800pci
rt2x00mmio             13395  2 rt2800pci,rt2800mmio
rt2x00lib              48886  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              546051  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              409394  2 mac80211,rt2x00lib
eeprom_93cx6           13168  1 rt2800pci
crc_ccitt              12627  1 rt2800libHis device is covered by the module:```
$ modinfo rt2800pci | grep 0601
alias:          pci:v0000[COLOR="#FF0000"]1814[/COLOR]d0000[COLOR="#FF0000"]0601[/COLOR]sv*sd*bc*sc*i*
```

---

### Post by itAyXD on 2014-12-19
I'll try running older kernel and report back here

---

### Post by itAyXD on 2014-12-19
Ok so I tried running both 3.5.0-27, and 3.8.0-30, I got the same error on both of them.
I'll check if it works on win7, maybe the problem is the card?

---

### Post by sbnwl on 2014-12-19
> *It absolutely **is** loaded*:

Thanks for the info.

---

### Post by itAyXD on 2014-12-21
Ok so it didn't work on win7 either so I plugged it out and cleaned everything with vacuum cleaned, and it just worked!

---

### Post by chili555 on 2014-12-21
Awesome! We're glad it's working by whatever means. Have fun.

---

