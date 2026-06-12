---
title: "D-Link AirPlus G+ in Edgy"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by NickL87 on 2007-01-24
Hi all

I have just installed Ubuntu Edgy on my laptop, but I can't seem to get my wireless network-card working. It Worked fine in Ubuntu Dapper, and it is also showed in the device manager, but it is however not diplayed in network-manager.

lspci output:

```
nick@nick-b:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:02.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 8b)
01:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface[CODE]
```[/CODE]

---

### Post by tturrisi on 2007-01-24
02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)

---

### Post by NickL87 on 2007-01-24
I have tried to do the following     

*  An easier solution is to add the following line to /etc/modprobe.d/options, which will instruct the card to load the correct firmware on startup: 

options acx firmware_ver=1.2.1.34

but this didn't work.

It is still not displayed in the network-manager?

---

### Post by NickL87 on 2007-01-24
```
nick@nick-b:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

```
nick@nick-b:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:D0:65:E1:0B  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe65:e10b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9715546 (9.2 MiB)  TX bytes:787570 (769.1 KiB)
          Interrupt:3 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

```

---

### Post by tturrisi on 2007-01-24
Are you sure you have the drivers and are they loaded?
do:
~# lsmod

---

### Post by NickL87 on 2007-01-29
I do not actually think that it is loaded, so that is probably the problem, here is my lsmod output:

```
Module                  Size  Used by
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
i915                   21632  2 
drm                    74644  3 i915
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
nls_utf8                3200  1 
ntfs                  112116  1 
af_packet              24584  2 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
acx                   102540  0 
pcmcia                 40380  0 
via_rhine              26116  0 
yenta_socket           28812  2 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
mii                     6912  1 via_rhine
joydev                 11200  0 
tsdev                   9152  0 
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
evdev                  11392  2 
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
pcspkr                  4352  0 
psmouse                41352  0 
intel_agp              26012  1 
agpgart                34888  3 drm,intel_agp
serio_raw               8452  0 
ext3                  142728  1 
jbd                    62228  1 ext3
usbhid                 45152  0 
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  5 acx,usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  4 
piix                   11780  1 
generic                 6276  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

```

how do I load the driver? I have never tried that before.

---

### Post by tturrisi on 2007-01-29
to see if it's loaded"
dmesg | grep acx

to load the driver:
modprobe acx

---

### Post by NickL87 on 2007-01-29
```
nick@nick-b:~$ modprobe acx
nick@nick-b:~$ dmesg | grep acx
[17179592.240000] acx: Loaded combined PCI/USB driver, firmware_ver=1.2.1.34
[17179592.240000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[17179592.288000] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:11, phymem1:0xE2020000, phymem2:0xE2000000, mem1:0xce968000, mem1_size:8192, mem2:0xceac0000, mem2_size:131072
[17179592.364000] acx: firmware image 'acx/1.2.1.34/tiacx111c16' was not provided. Check your hotplug scripts
[17179592.368000] acx: firmware image 'acx/1.2.1.34/tiacx111' was not provided. Check your hotplug scripts
[17179592.368000] acx: reset_dev() FAILED
[17179592.384000] acx_pci: probe of 0000:02:00.0 failed with error -5
[17179592.384000] usbcore: registered new driver acx_usb

```

What does this mean?

---

### Post by bartwaw on 2007-02-17
hey, i've got the same problem in 6.10 with DWL-G520+.

---

### Post by bartwaw on 2007-02-19
enyone can help us ??
My DWL-G520+ making me mad !!

I've read that DWL-G520+ is supported by 6.10 "out of the box" but my card dont know that.

---

### Post by mxreader on 2007-04-15
I've had this same problem for the past 6 months... wasted many hours looking for solution, one of the two reasons why i am not using ubuntu.  Sadly I can only chyme in asking for help here, and not to provide a solution.

edit:
I am reading in an earlier post a link to say that the most current version of Ubuntu should fix this now.   So I will try and see if that works later.
Ciao

---

