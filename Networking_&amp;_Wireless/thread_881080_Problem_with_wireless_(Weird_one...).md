---
title: "Problem with wireless? (Weird one...)"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by Miyavix3 on 2008-08-05
I have a Del 1450 usb adapter and I can connect to my neighbor's wifi but not mine. I'm using dd-wrt.com on my router 'cause my friend put it there. I'm wondering if I need to change anything in my router settings. Also, anything else you can suggest would be phenomenal too.

When I click my router name, it says connecting and has been doing that for about five minutes now, but when I choose a different network... it works.:confused:

---

### Post by pytheas22 on 2008-08-05
If you post the output of:
```

iwlist scan
```

it will tell show the configuration settings on all the routers in range.  Please do that and maybe we can make suggestions about what to change on your router in order to be able to connect (please mention the names of your network and your neighbor's network so we know which router is which).

---

### Post by Miyavix3 on 2008-08-05
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results


Um...

o.O

If anyone would like to help me faster, you could possibly talk to me via AIM
Aim name: t3hubern00b

(I'm auto idling to avoid someone, so I'm here)

---

### Post by pytheas22 on 2008-08-05
That's strange.  Can you try running the command a few times please?  Sometimes iwlist doesn't pick things up on the first scan.  Also, you are seeing these networks listed in Network Manager (the applet is the system tray), right?

---

### Post by Miyavix3 on 2008-08-05
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:B5:89:B4
                    ESSID:"LOLWTF"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Signal level=66/127  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000002a76761d7
          Cell 02 - Address: 00:12:17:B5:89:B4
                    ESSID:"dd-wrt_vap"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Signal level=66/127  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000002a767682f
          Cell 03 - Address: 00:18:39:82:81:BE
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Signal level=66/127  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000294d34a0188
```


My router is LOLWTF.And uh... I'm somehow connected to the internet. but it says "Wireless network connecton to '(unknown)' (48%)"

So I assume that's not mine.


EDIT: I was working fine on ubuntu until I hit Submit Reply. Then it lost connection and wouldn't come back.
This sucks dick :[


EDIT: I've narrowed it down to my computer. I put the install disk into my laptop, and I'm able to connect to the internet.
Thinkpad ftw.

So I think it might be my dell 1450 wireless usb adapter.

---

### Post by Ayuthia on 2008-08-05
It looks like all the routers in your area are on channel 6.  Have you tried changing the channel on yours?

---

### Post by Miyavix3 on 2008-08-05
> **Ayuthia said:**
> It looks like all the routers in your area are on channel 6.  Have you tried changing the channel on yours?

Mine is LOLWTF
```
Cell 01 - Address: 00:12:17:B5:89:B4
                    ESSID:"LOLWTF"
                    Mode:Master
                    **Channel:6**

```
That one^


EDIT:
I'm getting a new wireless adapater. Ironically, it seems my current one is not working with ubuntu and it a common problem. (That I'm seeing.)
So, to make this so much easier... What's a good alternative? I have the Dell 1450 Wireless USB Adapter, and that's not an expensive product but it works fine. So the equivalent of that somewhere under $40.

I'm sure this will be easier then fixing it. o.o

---

### Post by Ayuthia on 2008-08-05
Yes, I was thinking that you might be getting interference from other routers so by changing the channel (something instead of channel 6), you might be able to get the signal better.  Even though it works well in Windows, the drivers are different in Linux so you might not always get the same results.

---

### Post by Miyavix3 on 2008-08-05
> **Ayuthia said:**
> Yes, I was thinking that you might be getting interference from other routers so by changing the channel (something instead of channel 6), you might be able to get the signal better.  Even though it works well in Windows, the drivers are different in Linux so you might not always get the same results.

Ohhhhh, ok. Can you further help me on aim?

---

### Post by Ayuthia on 2008-08-05
> **Miyavix3 said:**
> Ohhhhh, ok. Can you further help me on aim?

Sorry, I can't tonight.  However, if you are able to access your router (Usually it is some IP address like 192.168.1.1), you usually can change the channel of the router to something else.

---

### Post by Miyavix3 on 2008-08-05
> **Ayuthia said:**
> Sorry, I can't tonight.  However, if you are able to access your router (Usually it is some IP address like 192.168.1.1), you usually can change the channel of the router to something else.

I changed it, didn't work... but I am impressed with the member help and the speed of it. This is better than lots of places I've been to. I'm really liking Ubuntu.

EDIT: Woo, it's working. I'll post if it dies again, and how much time has elapsed before it died.

Update: Time elapsed 5 minutes... I had internet for 5 minutes... -_-

EDIT: Whee, it works now! I've restarted and can say with 85% certainty that it will work fine. Thanks for your patience and your help.

---

### Post by pytheas22 on 2008-08-06
I'm glad you got it sort of working.  If you want to try to figure out if there's a way to make your card work more reliably, post the output of:
```

lspci -nn
lsusb
lshw -C Network
```

I don't know which driver you're using now, but you might be able to make the card work better by using a more up-to-date version of the driver or switching to a different one.

---

### Post by Miyavix3 on 2008-08-06
What does that do?

---

### Post by pytheas22 on 2008-08-06
> What does that do?

Those commands will just give information about your wireless card and the drivers that you're currently using, so that we can figure out if there might be a way to make your card work more reliably.  If you're happy enough with how it works now, that's fine, but if you'd like to try to figure out why it sometimes dies on you, the output of those commands will help.

Don't worry, they won't make any changes to your system--they just display information.

---

### Post by Miyavix3 on 2008-08-06
```
00:00.0 Memory controller [0580]: nVidia Corporation CK804 Memory Controller [10de:005e] (rev a3)
00:01.0 ISA bridge [0601]: nVidia Corporation CK804 ISA Bridge [10de:0050] (rev a3)
00:01.1 SMBus [0c05]: nVidia Corporation CK804 SMBus [10de:0052] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005a] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005b] (rev a3)
00:04.0 Multimedia audio controller [0401]: nVidia Corporation CK804 AC'97 Audio Controller [10de:0059] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation CK804 IDE [10de:0053] (rev f2)
00:07.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0054] (rev f3)
00:08.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0055] (rev f3)
00:09.0 PCI bridge [0604]: nVidia Corporation CK804 PCI Bridge [10de:005c] (rev a2)
00:0a.0 Bridge [0680]: nVidia Corporation CK804 Ethernet Controller [10de:0057] (rev a3)
00:0b.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0c.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0d.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0e.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:06.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
01:0a.0 Multimedia audio controller [0401]: Creative Labs SB Audigy LS [1102:0007]
05:00.0 VGA compatible controller [0300]: ATI Technologies Inc R430 [Radeon X800 (PCIE)] [1002:554f]
05:00.1 Display controller [0380]: ATI Technologies Inc R430 [Radeon X800] (PCIE) (Secondary) [1002:556f]
miyavi@miyavi-desktop:~$ lsusb
Bus 002 Device 003: ID 413c:8104 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 001 Device 001: ID 0000:0000  











Bus 002 Device 003: ID 413c:8104 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 001 Device 001: ID 0000:0000  


















WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:58:b4:b2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.133 multicast=yes wireless=IEEE 802.11g



```

---

### Post by pytheas22 on 2008-08-06
Are you using ndiswrapper (if so you would have had to install it)?  I think your card has an Atheros chipset that doesn't have native drivers (no native support for Atheros USB...).  If you aren't sure, please post:
```

lshw -C Network
```

If you are in fact using some kind of native driver, then switching to ndiswrapper may help.  If you're already using ndiswrapper, there might be a way to make it work better, but that will be difficult.

---

### Post by Miyavix3 on 2008-08-06
PCI (sysfs)  
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:58:b4:b2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.133 multicast=yes wireless=IEEE 802.11g

---

### Post by pytheas22 on 2008-08-06
Sorry to ask for more information but lshw doesn't mention which driver you're using.  Could you please also post:
```

lsmod | grep ndis
```

I promise it will be the last request.

---

### Post by acreech on 2008-08-06
I have an Acer Aspire 7520-5185 computer with an Atheros AR5BXB63 wireless network card. I can not connect to the wireless card with the Network settings. 

i have ran the following codes to get information that I believe will make getting help easier. 

> 
iwlist scan


> 
acreech@acreech-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

acreech@acreech-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

acreech@acreech-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


> 
 lspci -nn


> 
00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7000M (rev a2) [10de:0533] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:04.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
01:04.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
01:04.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
01:04.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)


> 
lsusb


> 
Bus 004 Device 002: ID 046d:c51b Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 064e:a101 Suyin Corp. 
Bus 001 Device 001: ID 0000:0000  


> 
lshw -C Network


> 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:c8:1c:d2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.64 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0


> 
lsmod | grep ndis


There is no out put from the last command. 

I have ndiswrapper installed. Under System<Administration<hardware Drivers it does list the Atheros hardware access layer (HAL) and Support for Atheros 802.11 Wireless LAN Cards. 

Any help with this would be appreciated.

---

### Post by Miyavix3 on 2008-08-06
```
Module                  Size  Used by
aes_x86_64             26920  2 
aes_generic            27712  0 
af_packet              27272  4 
isofs                  39464  1 
udf                    91048  0 
ipv6                  311848  10 
radeon                131360  2 
drm                   105896  3 radeon
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
cpufreq_userspace       6180  0 
cpufreq_conservative    10632  0 
cpufreq_ondemand       11152  0 
cpufreq_stats           8416  0 
freq_table              6464  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       3200  0 
container               6656  0 
dock                   12960  0 
video                  23444  0 
output                  5632  1 video
sbs                    17808  0 
sbshc                   8960  1 sbs
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
arc4                    3456  2 
ecb                     5248  2 
blkcipher               9476  1 ecb
p54usb                 18560  0 
p54common              15488  1 p54usb
evdev                  14976  3 
mac80211              192532  2 p54usb,p54common
cfg80211               17680  1 mac80211
snd_usb_audio         100384  1 
snd_usb_lib            21120  1 snd_usb_audio
snd_hwdep              12552  1 snd_usb_audio
snd_intel8x0           40872  2 
snd_seq_dummy           5764  0 
psmouse                46236  0 
serio_raw               9092  0 
snd_ca0106             41728  3 
snd_ac97_codec        123224  2 snd_intel8x0,snd_ca0106
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  3 snd_usb_lib,snd_ca0106,snd_seq_midi
snd_pcm                92168  6 snd_usb_audio,snd_intel8x0,snd_ca0106,snd_ac97_codec,snd_pcm_oss
ac97_bus                3840  1 snd_ac97_codec
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
sr_mod                 20132  1 
cdrom                  41512  1 sr_mod
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 10912  0 
pcspkr                  4992  0 
snd                    70856  26 snd_usb_audio,snd_usb_lib,snd_hwdep,snd_intel8x0,snd_seq_dummy,snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              10400  1 snd
k8temp                  7680  0 
i2c_nforce2             8704  0 
snd_page_alloc         13200  3 snd_intel8x0,snd_ca0106,snd_pcm
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
i2c_core               28544  1 i2c_nforce2
ext3                  149264  2 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sd_mod                 33280  7 
pata_amd               16772  2 
sata_nv                31752  4 
pata_acpi               9856  0 
floppy                 69096  0 
ohci1394               36532  0 
ata_generic             9988  0 
ieee1394              106968  2 sbp2,ohci1394
forcedeth              55564  0 
libata                176432  4 pata_amd,sata_nv,pata_acpi,ata_generic
ehci_hcd               41996  0 
ohci_hcd               27524  0 
scsi_mod              178488  5 sbp2,sr_mod,sg,sd_mod,libata
usbcore               169904  6 p54usb,snd_usb_audio,snd_usb_lib,ehci_hcd,ohci_hcd
thermal                19744  0 
processor              41448  1 thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  7 
```

---

### Post by pytheas22 on 2008-08-06
@ acreech,

You're in luck because I was just involved in a thread yesterday dealing with wireless on the same exact card (ID 168c:001c) that you have.  We solved it using ndiswrapper--there are a few extra tricks that you need to make it work.  Take a look at the last post [here]("http://ubuntuforums.org/showthread.php?t=873980&page=7"); the original poster wrote out a draft of instructions (in a Word document attachment) to getting her card working.  She lists step-by-step what you need to do to get your wireless up.  Please follow the directions in the Word document and see if it fixes your problem; if not, let us know.

---

### Post by Miyavix3 on 2008-08-07
Does that apply to me too?

---

### Post by pytheas22 on 2008-08-07
> Does that apply to me too? 

No, unfortunately not, as your card doesn't have the same chipset, as far as I know...all I know about it is that the device ID is 413c:8104, which I think has some kind of Atheros chipset, but I'm not sure.  This [page]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/") says that your card works with ndiswrapper, but doesn't give a link to the Windows drivers that were used; it just says, "Driver: DELLNIC.INF as shipped on CD" (do you have the CD that came with it?).

But I want to make sure you're not using ndiswrapper already, because if that's the case, reinstalling it probably isn't going to make a difference.  What is the output of:
```

ndiswrapper -l
lsmod | grep ndis
```

---

### Post by Miyavix3 on 2008-08-07
> **pytheas22 said:**
> No, unfortunately not, as your card doesn't have the same chipset, as far as I know...all I know about it is that the device ID is 413c:8104, which I think has some kind of Atheros chipset, but I'm not sure.  This [page]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/") says that your card works with ndiswrapper, but doesn't give a link to the Windows drivers that were used; it just says, "Driver: DELLNIC.INF as shipped on CD" (do you have the CD that came with it?).

But I want to make sure you're not using ndiswrapper already, because if that's the case, reinstalling it probably isn't going to make a difference.  What is the output of:
```

ndiswrapper -l
lsmod | grep ndis
```


For ndiswrapper -l it gave me this...(Probably source of problem)
```
bcmwl5 : invalid driver!
```

I followed a guide, and it said to get bmcl5.inf. 

[IMG]http://img524.imageshack.us/img524/2540/screenshotwirelessnetwofv4.png[/IMG]

---

### Post by pytheas22 on 2008-08-07
Yeah, bcmwl5 would be for a Broadcom card, and I don't think anyone ever put Broadcom chipsets in USB wireless cards, so your stick is not Broadcom...I'm pretty sure it's Atheros.  There are Windows drivers [here]("http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R94313&SystemID=PLX_PNT_P4_GX260&servicetag=&os=WW1&osl=en&deviceid=7546&devlib=0&typecnt=0&vercnt=4&catid=&impid=&formatcnt=1&libid=0&fileid=122277"); please try downloading them.  After the download is finished, you have to extract them; you can use cabextract, which you can install with:
```

sudo apt-get install cabextract
```

then extract the .exe with:
```

cabextract ~/Desktop/R94313.EXE
```

Once it's extracted, look in the folder for a file named DELLNIC.inf and try to load it into ndiswrapper, and see if it works.

If you can't find the right file, let me know and I'll download it and look (I don't want to now because it's a big download and I have a slow connection).  Also I probably won't be back till tomorrow, but we can continue then.

---

### Post by Miyavix3 on 2008-08-07
then extract the .exe with:
```

cabextract ~/Desktop/R94313.EXE
```
[/QUOTE]

```
/home/miyavi/Desktop/R94313.EXE: no valid cabinets found

All done, errors in processing 1 file(s)

```

T_T

---

### Post by Ayuthia on 2008-08-07
> **Miyavix3 said:**
> then extract the .exe with:
```

cabextract ~/Desktop/R94313.EXE
```


```
/home/miyavi/Desktop/R94313.EXE: no valid cabinets found

All done, errors in processing 1 file(s)

```

T_T[/QUOTE]
You could try and unzip the file:
```
unzip ~/Desktop/R94313.EXE
```Sometimes that works.

---

### Post by Miyavix3 on 2008-08-07
@Ayuthia
It unziped into an exe o.o
I don't think it worked.

Damn, I suck. :[

---

### Post by pytheas22 on 2008-08-07
Through a combination of wine, unzip and cabextract I got that file opened up; unfortunately it turned out to apparently contain only some utility to control the wireless card, not the drivers (at least, there was no .inf file, only some .dll stuff).

I found another driver download from Dell that does contain an .inf.  Curiously there's no .sys file, although there is a .cat (ndiswrapper generally needs all three to work, even though you only have to actually load the .inf; it finds the others itself).  I uploaded the relevant files to [http://burnthesorbonne.com/files/dell_driver1.tar.gz](http://burnthesorbonne.com/files/dell_driver1.tar.gz) .  You can download it and extract with:
```

tar -xzvf dell_driver1.tar.gz
```

and you should find a file named msxmlx.inf; try loading that into ndiswrapper and see what happens (check the output of "ndiswrapper -l" to see if ndiswrapper thinks the file was the correct one).  I have no idea whether it will actually work, but it's the best thing I can think to try now.

---

### Post by Miyavix3 on 2008-08-07
[IMG]http://img391.imageshack.us/img391/7885/screenshotwirelessnetwopd9.png[/IMG]

---

### Post by pytheas22 on 2008-08-07
That's no good I suppose; I just thought it might be worth a shot.  My only other suggestion is to use the drivers that came with your wireless card, if you still have the CD.  Otherwise, I don't know what else to try, as I'm still not positive which kind of card you have.  Living with the wireless as it is may be the only option, unless someone else has more suggestions.

---

### Post by Miyavix3 on 2008-08-07
Thanks, I'm supposed to be giving this back to my friend but I haven't yet. Which means I'll probably have to get a new one... What do you suggest for a new one, that works well with both windows/linux?

I use G, btw.

---

### Post by pytheas22 on 2008-08-07
If you want a USB adapter, I use a [DWL-G122]("http://www.amazon.com/D-Link-AirPlus-DWL-G122-Network-Hi-Speed/dp/B000EXDQDQ/ref=sr_1_1?ie=UTF8&s=electronics&qid=1218139261&sr=1-1") **ver C1** (other versions may have completely different chipsets so check on that before you buy) and it works well out of the box on my Hardy 64-bit system.  I used to have some issues with it crashing after a while on Gutsy, but installing the drivers from [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com) solved that problem.

On Hardy it appears to work fine, although I haven't used it much myself, as I gave it to my brother shortly after upgrading to Hardy.  He uses Hardy 32-bit and says the connection drops once in a while, but I think it's because the router is far away and/or he doesn't know Linux at all and may be missing something simple.  Overall, it's a nice, cheap card that works, at least reasonably well, out-of-the-box, and works 100% if you install the drivers from serialmonkey.

There are plenty of other good USB sticks out there, too; take a look [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") for a long list.

---

### Post by acreech on 2008-08-17
> **pytheas22 said:**
> @ acreech,

You're in luck because I was just involved in a thread yesterday dealing with wireless on the same exact card (ID 168c:001c) that you have.  We solved it using ndiswrapper--there are a few extra tricks that you need to make it work.  Take a look at the last post [here]("http://ubuntuforums.org/showthread.php?t=873980&page=7"); the original poster wrote out a draft of instructions (in a Word document attachment) to getting her card working.  She lists step-by-step what you need to do to get your wireless up.  Please follow the directions in the Word document and see if it fixes your problem; if not, let us know.

Thanks for the suggestion. That file was very detailed, however it did not solve the problem with my key board. I have never located a "Wireless Switch" on my ACER Aspire 7520. I am attempting to see if it has such a switch that may be causing me a problem.

---

