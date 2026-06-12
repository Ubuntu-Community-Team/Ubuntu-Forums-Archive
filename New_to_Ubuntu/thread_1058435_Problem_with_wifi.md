---
title: "Problem with wifi"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by NYIsles007 on 2009-02-02
Hi, I'm new to Ubuntu and I have a problem with connecting to wireless internet.

If I try to connect to wireless, I am unable to find any networks. Even when I sit in a room that is 20 feet away from the router, I still get no sign of a network... I have been connected once, when I was sitting literally right in front of the router, but it was after I had removed the Ethernet cable (which I am using now), and it lasted for about 1 second  with 0% connection strength.

If it helps, I am running Ubuntu (which I just installed) on an HP Pavilion zv5000. It used to run windows, but after numerous problems, I decided to install Ubuntu.

Thanks.
-NYIsles

---

### Post by Cope57 on 2009-02-02
[Bluetooth Wireless Technology Basics]("http://h10032.www1.hp.com/ctg/Manual/c00186949.pdf")

[HP Pavilion zx5000 Notebook PC, HP Pavilion zv5000 Notebook PC, Compaq Presario R3000 Notebook PC, HP Compaq nx9100 Notebook PC - Maintenance and Service Guide]("http://h10032.www1.hp.com/ctg/Manual/c00212209.pdf")

[Reference Guide]("http://h10032.www1.hp.com/ctg/Manual/c00248746.pdf")

[Expansion Base Reference Guide]("http://h10032.www1.hp.com/ctg/Manual/c00222488.pdf")

[Reference Guide HP Notebook Expansion Base]("http://h10032.www1.hp.com/ctg/Manual/c00714504.pdf")

[Hard Drive White Paper]("http://h10032.www1.hp.com/ctg/Manual/c00133452.pdf")

[Expansion Base - Maintenance and Service Guide]("http://h10032.www1.hp.com/ctg/Manual/c00072829.pdf")

[Hardware Guide]("http://h10032.www1.hp.com/ctg/Manual/c00090106.pdf")

[Software Guide]("http://h10032.www1.hp.com/ctg/Manual/c00090105.pdf")

[Getting Started]("http://h10032.www1.hp.com/ctg/Manual/c00090104.pdf")

[HP USB Digital Drive]("http://h10032.www1.hp.com/ctg/Manual/c00193901.pdf")


Location of links can be found here.
[HP Pavilion zv5000 Notebook PC: Manuals]("http://h10025.www1.hp.com/ewfrf/wc/manualCategory?cc=us&dlc=en&product=385148&lc=en&jumpid=reg_R1002_USEN")

You will most likely need to enable restricted repositories, and enable your driver.
If you want a step-by-step how-to, someone else will be along shortly to give you a hand.

---

### Post by Crafty Kisses on 2009-02-02
Post the results of this command:
```
lspci
```

---

### Post by NYIsles007 on 2009-02-03
Here are the results:

00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

---

### Post by Neural oD on 2009-02-03
have you tried this on the command line: sudo iwlist scan

---

### Post by handydan918 on 2009-02-03
This is the line you need to know about. 

```
Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
```

The 43xx broadcom series cards are notorious. They should "just work" now, for the most part, so let's see if you can give us some more info. 
Let's have the output of ```
lsmod
```

and ```
ifconfig
```

Also, you may want to check out the restricted software/proprietary drivers 
section of synaptic...look for bcm43 or so.

EDIT: ahh, here it is. [Wiki entry]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") on the driver in question...

---

### Post by NYIsles007 on 2009-02-03
Results for lsmod:

Module                  Size  Used by
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
powernow_k8            16704  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ipv6                  267908  8 
lp                     12324  0 
joydev                 13120  0 
pcmcia                 40876  0 
af_packet              23812  2 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
serio_raw               7940  0 
b43legacy             127776  0 
mac80211              165652  1 b43legacy
cfg80211               15112  1 mac80211
evdev                  13056  6 
psmouse                40336  0 
pcspkr                  4224  0 
yenta_socket           27276  2 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
k8temp                  6656  0 
video                  19856  0 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
output                  4736  1 video
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
battery                14212  0 
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
container               5632  0 
snd_seq_dummy           4868  0 
ac                      6916  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
wmi_acer                9644  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_nforce2             7680  0 
amd64_agp              13444  1 
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
i2c_core               24832  1 i2c_nforce2
agpgart                34760  1 amd64_agp
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
usbhid                 32128  0 
hid                    38784  1 usbhid
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
b44                    28432  0 
pata_amd               14212  3 
pata_acpi               8320  0 
8139cp                 24704  0 
floppy                 59588  0 
ata_generic             8324  0 
ssb                    34308  2 b43legacy,b44
8139too                27520  0 
mii                     6400  3 b44,8139cp,8139too
libata                159600  3 pata_amd,pata_acpi,ata_generic
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
ohci_hcd               26640  0 
usbcore               146412  4 usbhid,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              36488  3 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

Results for ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:0f:b0:08:b3:79  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe08:b379/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2313 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3012458 (2.8 MB)  TX bytes:243253 (237.5 KB)
          Interrupt:17 Base address:0x7000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1918 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1918 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:95900 (93.6 KB)  TX bytes:95900 (93.6 KB)

---

### Post by Neural oD on 2009-02-04
I'd say that this is the line that is relivant to your wireless card: b43legacy 127776 0 
although i could be wrong not too sure on the broadcom side of things.

try: sudo ifconfig -a
this will show all the interfaces - even if they are down

---

