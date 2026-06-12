---
title: "AR5416 Atheros problem on 13.04"
date: 2013-12-17
forum: Networking &amp; Wireless
---

### Post by teddmeister2 on 2013-12-17
***Note to everyone out there: I learned this through hard experience, but make sure you do all the different things recommended in the wireless sticky and investigate properly.  I forgot to do a dmesg, and after finally discovering a hardware fault by doing dmesg | grep ath, I realized that something had happened when I had had the box open earlier in the week.  I then went in and removed the card, plugged it in again, and now everything works beautifully.  (also use the grep tool wisely, this is how I got my answer, since dmesg was giving way to much to keep it all on the screen so search through.  Anyway, thank you to everyone who helped me in figuring out the problem.***
-Bryan Appley

Somehow through normal updates my 12.04 box's wifi driver (atheros AR5416) dropped or something.  I upgraded all the way to 13.04 hoping the updater would fix it for me, but this didn't happen.  I'm currently without wifi.  Any help for me on how to get the driver up again.
relevant stuff
```
lsmod
Module                  Size  Used by
hidp                   21893  0 
rfcomm                 37420  12 
bnep                   17669  2 
binfmt_misc            17260  1 
dm_crypt               22321  0 
snd_hda_codec_via      45850  1 
ath9k                 134875  0 
snd_hda_intel          38307  3 
ath9k_common           13783  1 ath9k
snd_hda_codec         117617  2 snd_hda_codec_via,snd_hda_intel
ath9k_hw              398477  2 ath9k_common,ath9k
coretemp               13131  0 
kvm_intel             126842  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
ath                    19187  3 ath9k_common,ath9k,ath9k_hw
mac80211              526519  1 ath9k
kvm                   376505  1 kvm_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
joydev                 17097  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
cfg80211              436243  3 ath,ath9k,mac80211
gpio_ich               13236  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
btusb                  17986  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd                    56485  15 snd_hwdep,snd_timer,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
bluetooth             202232  23 bnep,hidp,btusb,rfcomm
microcode              18286  0 
psmouse                81065  0 
soundcore              12600  1 snd
lpc_ich                16925  0 
mac_hid                13037  0 
serio_raw              13031  0 
ppdev                  12817  0 
parport_pc             27504  1 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_generic            12484  0 
usbhid                 41805  0 
hid                    87001  3 hidp,hid_generic,usbhid
i915                  539721  3 
video                  18894  1 i915
i2c_algo_bit           13197  1 i915
drm_kms_helper         47545  1 i915
drm                   228489  4 i915,drm_kms_helper
atl2                   27628  0 

```

lshw
```
lshw -c network
[sudo] password for mrsappley: 
  *-network               
       description: Ethernet interface
       product: Attansic L2 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: a0
       serial: 00:25:11:4c:82:a1
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 duplex=full firmware=L2 ip=192.168.1.7 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:feac0000-feafffff memory:feaa0000-feabffff
  *-network UNCLAIMED
       description: Network controller
       product: AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn]
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:03:04.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=168
       resources: memory:febf0000-febfffff
```
lspci
```
lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Qualcomm Atheros Attansic L2 Fast Ethernet [1969:2048] (rev a0)
	Subsystem: Elitegroup Computer Systems Device [1019:2048]
	Kernel driver in use: atl2
03:04.0 Network controller [0280]: Atheros Communications Inc. AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn] [168c:0023] (rev 01)
	Subsystem: D-Link System Inc Device [1186:3a2d]

```

let me know if you need anything else to help me.  Sorry.  I'm a bit rusty on all this.  Thanks for all your help.

---

### Post by praseodym on 2013-12-17
Deactivate the hardware encryption of the driver:
```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by teddmeister2 on 2013-12-17
After the reboot, The network still comes up as unclaimed in the lshw.  Is there something I do next?
```
lshw
  *-network               
       description: Ethernet interface
       product: Attansic L2 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: a0
       serial: 00:25:11:4c:82:a1
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 duplex=full firmware=L2 ip=192.168.1.7 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:feac0000-feafffff memory:feaa0000-feabffff
  *-network UNCLAIMED
       description: Network controller
       product: AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn]
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:03:04.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=168
       resources: memory:febf0000-febfffff

```
```
iwconfig
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:25:11:4c:82:a1  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:11ff:fe4c:82a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:948 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:469552 (469.5 KB)  TX bytes:124063 (124.0 KB)
          Memory:feac0000-feb00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79731 (79.7 KB)  TX bytes:79731 (79.7 KB)

```

---

### Post by teddmeister2 on 2013-12-18
ath_pci is also blacklisted in /etc/modprobe.d

just upgraded to 13.10. no change

did dmesg | grep ath
Here's the output
```
[   21.806795] ath: phy0: address test failed addr: 0x00008000 - wr:0x00400040 != rd:0x00000040
[   21.806800] ath: phy0: Unable to initialize hardware; initialization status: -19
[   21.806803] ath9k 0000:03:04.0: Failed to initialize device

```
Does this mean I have a hardware issue?  What should I do?

---

