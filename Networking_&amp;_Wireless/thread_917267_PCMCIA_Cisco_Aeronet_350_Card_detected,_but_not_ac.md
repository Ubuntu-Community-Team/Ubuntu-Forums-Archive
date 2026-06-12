---
title: "PCMCIA Cisco Aeronet 350 Card detected, but not active."
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by Dezran on 2008-09-11
I'm fairly new to Linux/Ubuntu, but not a complete n00b.
I've done a number of searches here and on Google, but haven't found anything that seems to quite fit with my problem.  

I have a tested and functional PCMCIA Cisco Aeronet 350 Wireless card with the latest internal firmware from Cisco.  However, Ubuntu seems to see the card, but the card isn't powering up and not showing up in the network connections.  As I said, I know the card works, and it is listed as natively supported by airo or airo_cs.  So, any thoughts on how I can get it working?

Here's my lspci:
```
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:0a.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
01:0a.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0e.0 FireWire (IEEE 1394): Fujitsu Limited. Unknown device 2010 (rev 01)

```

The ifconfig:
```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.xxx  Mask:255.255.255.0
          inet6 addr: fe80::2e0:ff:fe7e:86d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2540741 (2.4 MB)  TX bytes:268030 (261.7 KB)
          Interrupt:11 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:168700 (164.7 KB)  TX bytes:168700 (164.7 KB)

```
OK, so it's not showing up there... 

However, if I do: lspcmcia
```
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:01:0a.0)
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:01:0a.1)
Socket 1 Device 0:	[airo_cs]		(bus ID: 1.0)

```
So it does see the card there... but the card isn't getting any power or being activated.

Next I tried: lsmod | grep airo_cs
```
airo_cs                 7168  2 
airo                   73884  1 airo_cs
pcmcia                 40876  1 airo_cs
pcmcia_core            40596  4 airo_cs,pcmcia,yenta_socket,rsrc_nonstatic
```

Now... if I do a _modprobe airo_cs_ nothing happens.  It just drops to the next line and I have to break the operation to do anything else.


I don't mind poking around, but I'm kinda lost as to where to go from here... Any pointers would be greatly appreciated.

Thanks!

Edit:
A little more info:
sudo lshw -C network
```
  *-network               
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 1
       resources: irq:3
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: eth0
       version: 10
       serial: 00:e0:00:7e:86:d5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.106 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

```

Edit #2:
Cause I misspelled Aironet...

---

### Post by louvann on 2008-09-12
Same problem.
I have the same card and results and I am at the same experience level as the first lister.
Cisco 350 card, IBM A22p, Hardy 8.04, fresh install plus my feeble attempts at some of the confg.

Watching the power-up with via dmesg and visually, The lights on the card momentarily come on, then extinguish for all future times.

The card is not being given an interface name.

louv@louv-laptop:~$ sudo lshw -C network
[sudo] password for louv: 
  *-network               
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 1
       resources: irq:3

louv@louv-laptop:~$ dmesg

 . . . . . .
[   45.614443] Yenta: CardBus bridge found at 0000:00:02.0 [1014:0130]
[   45.614476] Yenta: Using INTVAL to route CSC interrupts to PCI
[   45.614483] Yenta: Routing CardBus interrupts to PCI
[   45.614492] Yenta TI: socket 0000:00:02.0, mfunc 0x00001000, devctl 0x66
[   45.849799] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   45.849810] Socket status: 30000006
[   45.986513] Yenta: CardBus bridge found at 0000:00:02.1 [1014:0130]
[   45.986540] Yenta: Using INTVAL to route CSC interrupts to PCI
[   45.986547] Yenta: Routing CardBus interrupts to PCI
[   45.986556] Yenta TI: socket 0000:00:02.1, mfunc 0x00001000, devctl 0x66
 . . . . . . .

[   58.451771] pcmcia: registering new device pcmcia1.0
[   60.111089] airo(): Probing for PCI adapters
[   60.111289] airo(): Finished probing for PCI adapters
[   60.514373] airo(): cmd:111 status:7f11 rsp0:2 rsp1:0 rsp2:0
[   60.514392] airo(): Doing fast bap_reads

What is the next steps in getting this going?

---

### Post by mgwalk on 2008-09-14
I also have a cisco card: Air-CB21AG-A-K9 card 
and the OS sees it but no connection...

---

### Post by Dezran on 2008-09-22
Any pointers would be helpful.
Thanks!

---

### Post by Dezran on 2008-09-23
Looking back at this, it looks like it's not activating the PCMCIA slots... even though it's aware they exist, they don't appear to be active.

---

### Post by Dezran on 2008-09-24
A friend asked to check my lsmod:
```
Module                  Size  Used by
isofs                  36388  1 
udf                    88612  0 
ipv6                  267780  8 
i915                   32512  2 
drm                    82452  3 i915
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_ich           6288  0 
speedstep_lib           6532  1 speedstep_ich
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
freq_table              5536  3 speedstep_ich,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8712  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
lp                     12324  0 
geode_aes               7196  1 
blkcipher               8324  1 geode_aes
airo_cs                 7168  2 
airo                   73884  1 airo_cs
joydev                 13120  0 
pcmcia                 40876  1 airo_cs
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
evdev                  13056  6 
irda                  203068  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
crc_ccitt               3072  1 irda
serio_raw               7940  0 
snd_seq_dummy           4868  0 
psmouse                40336  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
video                  19856  0 
output                  4736  1 video
yenta_socket           27276  4 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  4 airo_cs,pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                  4224  0 
battery                14212  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                      6916  0 
button                  9232  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34452  0 
intel_agp              25492  1 
pci_hotplug            30880  1 shpchp
agpgart                34760  3 drm,intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
pata_acpi               8320  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
floppy                 59588  0 
ata_piix               19588  3 
ohci1394               33584  0 
8139too                27520  0 
libata                159344  3 ata_generic,pata_acpi,ata_piix
ieee1394               93752  2 sbp2,ohci1394
8139cp                 24704  0 
mii                     6400  2 8139too,8139cp
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
uhci_hcd               27024  0 
usbcore               146028  3 usbhid,uhci_hcd
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```

The consensus among those I've been discussing this with, is that possibly the PCMCIA isn't using the right driver... or if it is, there is an incompatibility.

---

### Post by dondiablo on 2008-09-27
Same boat here - Orange/solid activity light - drivers show but no connectivity.  Sad thing is that it worked like a charm in Ubuntu 7.10 without me having to do a thing!

Someone out there has to know the answer - PLEASE help!

Thanks

---

### Post by Mr. Architect on 2008-09-29
Okay people...  Through a few searches outside of this community, and testing suggested scenarios, I have confirmed a fix for all of us who have Cisco Aironet 350 wireless cards.

Here's what you need to do.



**Add** the following lines to your [COLOR="Blue"]/etc/modprobe.d/blacklist file[/COLOR]:
---------------------------------------------
# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes
----------------------------------------------
-Save
-Reboot
& all will be good, (I hope for you), did for me!

This fixed the wireless Cisco Aironet 350 on my IBM Thinkpad T30.

Special thanks to Fred L Bug Fix#189398

---

### Post by dondiablo on 2008-09-29
I had tried editing the blacklist file, 'sudo modprobe airo_cs' - still no luck.  The addition of the statement in the blacklist file did prevent the hardware hangup upon boot.

H/w - Armada e500, 512Mb, Ubuntu 8.04 desktop

Thanks.

---

### Post by Clockwinder on 2008-09-29
> **Mr. Architect said:**
> Okay people...  Through a few searches outside of this community, and testing suggested scenarios, I have confirmed a fix for all of us who have Cisco Aironet 350 wireless cards.

Here's what you need to do.



**Add** the following lines to your [COLOR="Blue"]/etc/modprobe.d/blacklist file[/COLOR]:
---------------------------------------------
# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes
----------------------------------------------
-Save
-Reboot
& all will be good, (I hope for you), did for me!

This fixed the wireless Cisco Aironet 350 on my IBM Thinkpad T30.

Special thanks to Fred L Bug Fix#189398


Thank you !!:D worked perfectly for me!!:D

---

### Post by outkast44 on 2008-10-18
> **Mr. Architect said:**
> Okay people...  Through a few searches outside of this community, and testing suggested scenarios, I have confirmed a fix for all of us who have Cisco Aironet 350 wireless cards.

Here's what you need to do.



**Add** the following lines to your [COLOR="Blue"]/etc/modprobe.d/blacklist file[/COLOR]:
---------------------------------------------
# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes
----------------------------------------------
-Save
-Reboot
& all will be good, (I hope for you), did for me!

This fixed the wireless Cisco Aironet 350 on my IBM Thinkpad T30.

Special thanks to Fred L Bug Fix#189398

I spent quite some time trying to figure this out before running into this post.  Thanks so much, I am all set now!

---

### Post by petebarchetta on 2009-03-20
a big thanks to this post!!!
i can confirm that this fix also works for the Cisco Aironet 340 PCMCIA cards too,they also use the airo_cs driver.
 it sorted my problem
a big thanks to these people:D:D:D:KS
i now have a working wifi card
i also have a 3-Com 3c589 wired Nic PCMCIA card, any thoughts to get that working?

---

### Post by aliamondano on 2009-04-22
> **Mr. Architect said:**
> Okay people...  Through a few searches outside of this community, and testing suggested scenarios, I have confirmed a fix for all of us who have Cisco Aironet 350 wireless cards.

Here's what you need to do.



**Add** the following lines to your [COLOR="Blue"]/etc/modprobe.d/blacklist file[/COLOR]:
---------------------------------------------
# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes
----------------------------------------------
-Save
-Reboot
& all will be good, (I hope for you), did for me!

This fixed the wireless Cisco Aironet 350 on my IBM Thinkpad T30.

Special thanks to Fred L Bug Fix#189398
Hey Mr Arcuitect, Thank you very much!!! You saved me.

I was thinking leave Ubuntu... :P

---

