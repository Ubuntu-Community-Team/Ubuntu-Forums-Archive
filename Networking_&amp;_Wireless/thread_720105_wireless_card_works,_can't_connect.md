---
title: "wireless card works, can't connect???"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by Monstroxus on 2008-03-09
Hi guys/gals,

Previously wireless (the infamous broadcom) was working. But I mostely had to make several attempts to connect... however it worked. Yesterday I thought to improve the connection, but it got actually worse (after messing around)... now I can't connect anymore. I reinstalled the driver (ndiswrapper), card works, I can see a whole bunch of connections. It connect SUCCESFULLY to an open connection (FON), however when I want to connect to my own wireless signal, it doesn't connect? Any ideas? Thanks!

---

### Post by handydan918 on 2008-03-09
If you are running encryption on your network, turn it off and troubleshoot from there.

If not, try posting the output of ```
lspci | grep -i net
```
and ```
lsmod
```
and ```
iwconfig
```

---

### Post by Monstroxus on 2008-03-09
how to turn of encryption?

---

### Post by handydan918 on 2008-03-10
Most likely at your WAP. If you have a router, you can get into the web-based interface by typing 192.168.1.1 (or what ever the ip is-that is a common one) and entering the administrator name and password.There should be a setting somewhere to turn off or disable encryption. 
Sorry, I can't tell you how, specifically. Every router is different. Check your documentation if unsure.

---

### Post by Monstroxus on 2008-03-11
ok after switching of the encryption...no problems when connecting to my unprotected wireless signal... however as soon as wap/wep is enabled, it doesn't work.

vandelaak@vandelaak-laptop:~$ sudo lshw -C network
Password:
  *-network               
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 01
       serial: 00:16:cf:b4:35:63
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Broadcom,10/12/2006, 4.100.15.5 latency=0 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d0000000-d0003fff irq:16
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@05:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:ce:36:b8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.101 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:2000-20ff iomemory:d0100000-d01000ff irq:21

vandelaak@vandelaak-laptop:~$ lspci | grep -i net
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

vandelaak@vandelaak-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ipv6                  269088  10 
ppdev                  10116  0 
i915                   25472  2 
drm                    81044  3 i915
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  0 
cpufreq_userspace       5408  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
sony_acpi               6284  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
container               5248  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
ac                      6020  0 
battery                10756  0 
video                  16388  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
dock                   10268  0 
button                  8720  0 
af_packet              23816  2 
ndiswrapper           194608  0 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
joydev                 10816  0 
snd_hda_intel          22552  0 
snd_hda_codec         229376  1 snd_hda_intel
snd_pcm_oss            44800  0 
snd_mixer_oss          17792  1 snd_pcm_oss
pcmcia                 39212  0 
snd_pcm                81028  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            35200  0 
snd_seq_midi_event      8576  1 snd_seq_oss
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq                54128  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  2 snd_seq_oss,snd_seq
snd                    56452  9 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
serio_raw               7940  0 
intel_agp              26140  1 
psmouse                38920  0 
sdhci                  18700  0 
mmc_core               26756  1 sdhci
agpgart                35400  3 drm,intel_agp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
evdev                  11008  5 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
usbhid                 26592  0 
hid                    27392  1 usbhid
ata_piix               15492  2 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
8139cp                 25088  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
generic                 5124  0 [permanent]
8139too                27648  0 
mii                     6528  2 8139cp,8139too
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

vandelaak@vandelaak-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by handydan918 on 2008-03-11
I can't go a lot further with this because I don't use encryption. I do know that people bump their heads on the passphrase a lot. Linux handles spaces differently, so a passphrase that has spaces may not be read correctly. IIRC, you can handle spaces by quoting the passphrase, i.e., "my really great passphrase" or by escaping the space a la my\ really\ great\ passphrase.

Also IIRC, some ndiswrapper drivers don't handle WPA. 
If you can't get any encryption running, you can at least use MAC filtering. It ain't much; any cracker can beat it, but it keeps the honest people honest...

---

### Post by Monstroxus on 2008-03-11
Thanks for the info. Unfortunately I still doesn't work, it works perfectly when connecting to the un-encrypted connection. Furthermore, previously (before I reinstalled the ndiswrapper/driver, because I wanted to make it work better.. ahum) it worked... wap etc. No problem, it only took several tries to connect, that was the reason why I wanted to reinstall ndiswrapper... bummer. It only became worse. Anyone else an idea...? (to connect with encryption to my wireless network?)

---

### Post by Monstroxus on 2008-03-12
I just was thinking... can it be that the driver used by ndiswrapper is outdated, that it perhaps cannot handle WAP?

Driver = Broadcom,10/12/2006 (somewhere mentioned in the listings above...

Anyone any idea?

---

### Post by uberlube on 2008-03-12
Try the howto in my sig :)

---

### Post by Monstroxus on 2008-03-12
Thanks I will try that... actually I did try it before, but I think that time I didn't change it to eth1. I also didn't uninstall the previous inf file first... i will try that later.

---

