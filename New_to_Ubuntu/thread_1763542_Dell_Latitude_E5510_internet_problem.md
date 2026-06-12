---
title: "Dell Latitude E5510 internet problem"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by aam-aadmi on 2011-05-20
Hi All,

I installed Ubuntu 10.04 on a Dell Latitude E5510 right now. I am having problems with the networking. Neither wired, nor wireless seems to be working. The wireless "light" does not light up when I boot into Ubuntu; so the wireless hardware is not being detected. But when I tried connecting with a wired connection even that did not work.

Here is the output from ifconfig -a, lsmod and lspci. Any advice will be greatly appreciated.

```
basu15@basu15-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:9e:38:91  
          inet6 addr: fe80::f24d:a2ff:fe9e:3891/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74897 (74.8 KB)  TX bytes:3606 (3.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10960 (10.9 KB)  TX bytes:10960 (10.9 KB)


```

and

```
basu15@basu15-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_idt      52010  1 
i915                  287458  3 
snd_hda_intel          22005  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         29329  1 i915
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54180  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
intel_agp              24375  2 i915
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  1 sdhci
psmouse                63245  0 
serio_raw               3978  0 
dell_wmi                1793  0 
dcdbas                  5422  0 
drm                   162409  4 i915,drm_kms_helper
agpgart                31724  2 intel_agp,drm
i2c_algo_bit            5028  1 i915
parport_pc             25962  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
ahci                   32200  2 
tg3                   109324  0 
ieee1394               81181  1 ohci1394

```

and

```
basu15@basu15-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 03)
03:00.4 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 03)
0b:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe (rev 10)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

### Post by underdog512 on 2011-05-20
It looks like you have a broadcom chipset. So you will need to install those drivers.  Do you have anything showing up in the restricted drivers?

System -> Administration -> Restricted Drivers

---

### Post by aam-aadmi on 2011-05-20
No, nothing is showing up. It says there are no proprietary drivers installed in the system.

---

### Post by josephmills on 2011-05-20
could you please open your terminal and type in ```
lspci -vnn | grep 14e4 
``` and paste here thanks

---

### Post by aam-aadmi on 2011-05-20
Here is the output:

```
basu15@basu15-laptop:~$ lspci -vnn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4353] (rev 01)
0b:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe [14e4:1680] (rev 10)


```

---

### Post by josephmills on 2011-05-20
> **aam-aadmi said:**
> Here is the output:

```
basu15@basu15-laptop:~$ lspci -vnn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4353] (rev 01)
0b:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe [14e4:1680] (rev 10)


```
hi again you need the b43sta mods lets ftry this open your terminal and type in ```
sudo apt-get install broadcom-sta-source && broadcom-sta-common && firmware-b43-installer && bcmwl-kernel-source
``` then reboot then let us see a ```
lsmod | grep wl
```and a ```
dmesg | grep wl 
``` thanks again

---

### Post by aam-aadmi on 2011-05-20
When I try to install the broadcom-sta I get the following message:

```
Couldn't find package broadcom-sta
```

Since my machine is not connecting to the internet I don't see how we can use apt-get to install the broadcom drivers.

Thanks.

Aam-aadmi

---

### Post by josephmills on 2011-05-20
I am sorry but I do not know how to install it with out the internet I am sure that it is like this get the driver and firmware then make a folder called wirelesss rthen move that folder to you firmware folder extract and you will have wireless but I have no clue where to get the b43sta and its dep in one package?

---

### Post by aam-aadmi on 2011-05-20
When I switched off the wireless, then I could connect to the internet via the wired connection. Then I downloaded the broadcom drivers. Once I installed the drivers, the wireless started working. Thanks.

Aam-aadmi

---

### Post by josephmills on 2011-05-20
WOOT WOOT I am glad that you got it working have fun with your wireless and Ubuntu 
Joseph Mills

---

