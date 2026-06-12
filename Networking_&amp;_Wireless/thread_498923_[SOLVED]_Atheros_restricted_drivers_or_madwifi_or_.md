---
title: "[SOLVED] Atheros restricted drivers or madwifi or windows"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by tava0002 on 2007-07-12
I am really confused between madwifi, restricted and windows drivers for Atheros chipsets on an Orinoco/Proxim card.  I know it was recognized and probably was using the restricted drivers.

(Side note: I did get it working, but it only worked if the laptop was 4ft from the router, I figured I'd try different drivers)

Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

**My questions:**

1. What is the command  to tell what drivers my wireless card is using?  
2. How do you change the driver the card uses?
3. Which would be the best madwifi, restricted or windows(ndiswrapper) drivers?

ndiswrapper -l

ntpr11ag : driver installed
        device (168C:0013) present (alternate driver: ath_pci)

So how do I use this driver over the restricted?  I disabled them under Apps - System - Restricted Driver Manager but it still  says "status - In Use".

---

### Post by kevdog on 2007-07-12
lshw -C network

This will show you the current driver that your card is using

To disable the current driver, put an entry in /etc/modprobe.d/blacklist  (gksu gedit /etc/modprobe.d/blacklist)
blacklist ******* <---driver name like, ath_pci, madwifi, ndiswrapper

I think you have to reboot after doing this.


Then bring your interface down
sudo ifconfig wlan0 <---or appropriate interface name

Load the new driver you want (Im not sure how to do this with madwifi, but with ndiswrapper)
sudo depmod -a
sudo modprobe ndiswrapper

Restart the interface:
sudo /etc/init.d/dbus restart

As far as your overall question, which driver is better to use, I really dont know.  Im hoping that you could possibly try all 3 and then tell up what you think.

---

### Post by tava0002 on 2007-07-12
Great! Thanks for the info, I'll post what I find.

---

### Post by tava0002 on 2007-07-13
Your tips worked great, I was able to disable the ath_pci drivers and use ndiswrapper Windows drivers.

I can now use wireless on the other side of the house, before I had to be a few feet from the router.

I can definitely say that the ndiswrapper drivers work better than the ath_pci.....for me.  I have not yet tried the madwifi drivers.

---

### Post by gmoney on 2007-07-17
I too have been having a bit of trouble with my Atheros wifi card.  Even though my card is a bit different (AR5006X) than the one this post focuses on, I'd like to reply to this post in particular, since y'all have had some success!

A little history on my situation... Before I found this post, I had already tried to install  the driver via the following:

[LIST=1]
[*]restricted-modules
[*]madwifi
[*]ndiswrapper
[/LIST]

I followed the complete advice of kevdog (I did everything the post mentioned).

After I entered this into bash...
```
sudo lshw -C network
```

In the section for my wifi card, it says
```
*-network:0 UNCLAIMED
```

It doesn't mention anything about a driver being installed.  
It also says
```
physical id: 0
```
I guess this means one of two things: either it means that it's plugged into my first pci slot, or it means that there is no physical id (like a boolean zero).  I'm guessing it's not the latter, but it won't hurt to include that info in my post.

After that, I did:
```
sudo ifconfig wlan0
```
It returned:
```
wlan0: error fetching interface information: Device not found
```

By the way, I dunno if wlan0 is the correct one or not.  I remember seeing ath0 for my card on another post, so I tried that too.  No luck.

After following all of kevdog's instructions, I rebooted and restarted the network as well.  I still can't get the device to be found.




It seems that you guys have the paradox of the Atheros card figured out.  Does anybody have advice?  Your help is greatly appreciated!

---

### Post by kevdog on 2007-07-17
Is that the whole message you received when entering:
lshw -C network

Assuming you have a pci card can you also post the following with the card plugged in:
lspci -nn

---

### Post by gmoney on 2007-07-17
> **kevdog said:**
> Is that the whole message you received when entering:
lshw -C network

Assuming you have a pci card can you also post the following with the card plugged in:
lspci -nn

Kevdog,

No, that was not the whole message i received when entering : lshw -C network.  I pulled out (what I thought to be) the vital information.  Here's the whole message:

```
 *-network
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@00:19.0
       logical name: eth0
       version: 02
       serial: 00:1b:fc:5f:9b:27
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=1.1-0 ip=192.168.1.107 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:fdfc0000-fdfdffff iomemory:fdfff000-fdffffff ioport:ff00-ff1f irq:21
  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: AR5006X 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=28 mingnt=10
       resources: iomemory:fdee0000-fdeeffff irq:5
  *-network:1 UNCLAIMED
       description: Network controller
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 4
       bus info: pci@03:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32
       resources: ioport:df00-df1f iomemory:fdefe000-fdefefff iomemory:fded0000-fdedffff irq:7

```

Also, here's what I get in return for typing lspci -nn

```
00:00.0 Host bridge [0600]: Intel Corporation 82P965/G965 Memory Controller Hub
[8086:29a0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82P965/G965 PCI Express Root Port [
8086:29a1] (rev 02)
00:19.0 Ethernet controller [0200]: Intel Corporation 82566DC Gigabit Network Co
nnection [8086:104b] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #
4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #
5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI
#2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Con
troller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Po
rt 1 [8086:283f] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #
1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #                                                     2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #                                                     3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI                                                      #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev f                                                     2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HH (ICH8DH) LPC Interface Cont                                                     roller [8086:2812] (rev 02)
00:1f.2 RAID bus controller [0104]: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH                                                     ) SATA RAID Controller [8086:2822] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8                                                     086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7300 LE [10                                                     de:01d1] (rev a1)
02:00.0 Multimedia video controller [0400]: Conexant Unknown device [14f1:8880]                                                      (rev 0f)
03:00.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5006X 802.11a                                                     bg NIC [168c:001b] (rev 01)
03:01.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW323 [11c1:5811] (rev 70)
03:04.0 Network controller [0280]: Texas Instruments ACX 100 22Mbps Wireless Int                                                     erface [104c:8400]

```

By the way, I do have a second wifi card plugged into this box.  I haven't even attempted to configure that card (I thought about it, but had some trouble with that card on linux in the past).

Thanks again for your help!:)

--GMoney

---

### Post by kevdog on 2007-07-17
Give me until tomorrow -- I need to do some research on your card.  The reason its coming back unclaimed is because there is no driver associated with the card.  I need to hunt down what driver is supported by your card.

---

### Post by kevdog on 2007-07-18
Couple of questions

Does your wireless card have a brand name -- like Dlink, Linksys etc?

Can you post: lsmod

I believe (I could be wrong) that the driver for this card is acx_pci, which I thought was contained within linux.
What happens when you type
modinfo acx_pci

---

### Post by gmoney on 2007-07-18
> **kevdog said:**
> Couple of questions

Does your wireless card have a brand name -- like Dlink, Linksys etc?

Can you post: lsmod

I believe (I could be wrong) that the driver for this card is acx_pci, which I thought was contained within linux.
What happens when you type
modinfo acx_pci

The wireless card I've been trying to set up is:

Atheros Communications, Inc.
AR5006X 802.11abg NIC

I also have another wireless card in this box, so you may have noticed this when I posted lshw -C network on an earlier message:

Texas Instruments
ACX 100 22Mbps Wireless Interface

The Texas Instruments card is actually a DLINK card, but I'm not trying to get that one to work at the moment (It is eventually going to go in a different computer altogether).


Here's my lsmod:

```
lsmod
```

```

Module                  Size  Used by
nls_cp437               6784  1
isofs                  36156  1
udf                    84996  0
rfcomm                 40856  0
l2cap                  25856  5 rfcomm
bluetooth              55652  4 rfcomm,l2cap
ppdev                  10116  0
acpi_cpufreq           10056  0
cpufreq_ondemand        9228  2
cpufreq_powersave       2688  0
cpufreq_userspace       5408  0
cpufreq_conservative     8200  0
cpufreq_stats           7360  0
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
dev_acpi               12164  0
sony_acpi               6284  0
pcc_acpi               13184  0
tc1100_wmi              8068  0
ac                      6020  0
video                  16260  0
container               5248  0
asus_acpi              17308  0
dock                   10268  0
battery                10756  0
sbs                    15524  0
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
button                  8720  0
backlight               6784  1 asus_acpi
ipv6                  273600  12
ndiswrapper           194224  0
fuse                   46612  3
sbp2                   24196  0
parport_pc             36644  0
lp                     12324  0
parport                36808  3 ppdev,parport_pc,lp
af_packet              23688  2
snd_hda_intel          22040  1
snd_hda_codec         204800  1 snd_hda_intel
snd_pcm_oss            44416  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
serio_raw               7940  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52464  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               11940  0
snd                    53892  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25372  1
agpgart                35528  1 intel_agp
soundcore               8672  1 snd
pcspkr                  4224  0
psmouse                38920  0
shpchp                 34452  0
pci_hotplug            32448  1 shpchp
snd_page_alloc         11016  2 snd_hda_intel,snd_pcm
tsdev                   8768  0
evdev                  11008  3
ext3                  132872  2
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     35996  0
sr_mod                 17060  1
cdrom                  37536  1 sr_mod
sd_mod                 23300  5
usb_storage            72128  0
libusual               17936  1 usb_storage
ahci                   22148  5
ehci_hcd               34572  0
uhci_hcd               25488  0
libata                125848  1 ahci
scsi_mod              142220  6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata
ohci1394               36656  0
ieee1394              299320  2 sbp2,ohci1394
e1000                 126528  0
usbcore               134408  6 ndiswrapper,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14856  0
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability

```

When I type:
```

modinfo acx_pci

```
Here is what I get:
```

modinfo: could not find module acx_pci

```

Thanks once again for all of your help!

---

### Post by kevdog on 2007-07-18
Ok, what about
modinfo ath_pci

Last thing -- I notice that one of the device drivers listed in lsmod is ndiswrapper.  Have you tried installing and using this???

Have you ever installed restricted drivers using Synaptic???

What I want you to do is to go into Synaptic, then perform a search for "restricted".  You will find a lot of lines beginning with linux-restricted-modules-x.x.xx-xx.

You want to know the version of your kernel which can be found at command line with:
uname -r

You then want to match the kernel version with the linux-restricted-modules version.  If you click on the restricted modules, you will see a notice non-free linux modules and below listed:
madwifi
fglrx
nvdia
...etc

Another way of doing this is:
First determine your kernel version
uname -r

Then:
sudo apt-cache search madwifi

You will be presented a list of linux-restriced-modules.
You want to install the correct package if not already installed.
This can be done by 
sudo aptitude install linux-restricted-modules-xxxxxxx

---

### Post by rojanu on 2007-07-21
I have installed everything and was working OK but one day I can't remember what I did wifi stopped working now ath_pci module is loaded but there is no wireless device created for some reason
```
modinfo ath_pci
filename:       /lib/modules/2.6.22-8-generic/madwifi/ath_pci.ko
license:        Dual BSD/GPL
version:        0.9.3.1
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     D33427613CC54A874D9A746
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.22-8-generic SMP mod_unload 586 
parm:           countrycode:Override default country code (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)
```
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```
```
 lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
08:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
```
```
 dmesg | grep -i ath
[   38.929995] ath_hal: module license 'Proprietary' taints kernel.
[   38.932465] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   39.068091] ath_pci: 0.9.4.5 (0.9.3.1)
```
```
sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:16:36:a1:43:c5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 4
       bus info: pci@0000:08:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
```any ideas?

---

### Post by pro003 on 2008-01-06
Shouldn't you type:

# modinfo ath_pci

???


Am having too problems after installing the driver for my ati hd 2400, after successful installation i got my ath0 or ath_pci disappeared from network interfaces, and now I can't or better to say don't know how to re-enable my ath_pci or ath0 network interface?

If kevdog, respectfully, or someone else knows how to resolve this issue I'd be very very thankful.

proo003

---

### Post by kusiu on 2008-01-16
I have the same problem as rojanu has. Does anybody know how to force it?

Thanks:
kusiu

---

