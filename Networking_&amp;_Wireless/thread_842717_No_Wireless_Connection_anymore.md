---
title: "No Wireless Connection anymore"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by CarlWalters on 2008-06-27
Hi, 

I am running Ubuntu 8.04 on a Dell Inspiron 6400 laptop and up until a day or so ago the wireless connection was working just fine. I always let the system download updates and I think the kernel is now showing version -19. But my wireless connection has suddenly stopped working. I've done a clean re-install of 8.04 and let the system download any updates but haven't added any new programs. It wanted to download a driver for the wireless card (which it did last time) so I let it do this. However all I get when I click the network icon are the options

Wired Network (currently checked)
    Wireless Networks (unable to select this)
Connect to other Wireless Network...
Create New Wireless Network...
Connect to 802.1x Protected Wired Network..
Manual Configuration...

I don't get any network bars in the top panel as I used to and if I try
Connect to other Wireless Network...
and enter my NetworkName and WEP key then it thinks for a minute or so and keeps asking for the same information.

Any help greatfully received as I'm completely stuck here. I can't understand how something so easy to set up before is now broken.

---

### Post by qlucy on 2008-06-27
Yes, please, please.  Anyone?  I'm having the same problem and can't seem to find an answer anywhere.  New Ubuntu user, loving it and it worked perfectly upon installation, then magically started exhibiting the same behavior mentioned above.

It's worth noting that I can maintain a connection to an unsecured network without problem; the issue seems to be specific to WEP.  Carl, is this true for you, too?

I'm using a Dell Inspiron 8600 and Hardy Heron.  Hope you don't mind me doubling your question....I've only found this issue in one other spot (on Launchpad) and the thread was closed since no one answered.  This really is the one stumbling block that keeps me from dumping XP entirely.

Fingers crossed....

---

### Post by Midwest-Linux on 2008-06-27
I have asked the mods to put up a "sticky" warning Ubuntu users of this problem of doing updates and possibly losing funtions. 


I had the same problem with losing wireless after the updates. I re did the commands that I used - to install wireless in the first place and it worked. 

 My concern is not so much just replacing wireless with some commands...it can be done. There are many helpful and fine people on this forum ready to help.

But my main concern if someone installed Ubuntu for a new user on a laptop and the new user thinking they did the right thing and did the updates and lost functions....it doesn't make for a good first impression.

 Not only that, but this is something the Linux critics will instantly latch upon. Frankly I am tired (as others are) of hearing that "Linux is not ready for desktop" mantra over and over again. It is ready for desktop, but some glitches need to be worked out and new users should be at least be given a fair warning.

Especially after someone who has been using Windows for a long time and downloading updates and never lost functions.

 If I come across of being critical, thats not my intention. I just think the update situation needs to be addressed.

---

### Post by 801 on 2008-06-27
Hi,

Just back from a meeting with friends. I mentioned this problem, and a friend did a (wireless!) update to test if this was indeed the problem. The moment the update was finished, he lost his wireless.
So now he's mad at me for suggesting the test ;-).
This is very bad. Updates are supposed to update your machine, not downgrade! Please fix this ASAP!

---

### Post by qlucy on 2008-06-27
Thank you....I couldn't agree more -  now that I know it was an update I've done a little more searching and see this is certainly widespread!

So it sounds like a clean install will fix the problem....But (please pardon the newbie question...) any idea which updates are the problem? Is it all of them?  Or is there a specific type of update we should ignore?

Thanks very much.

---

### Post by entropy_ on 2008-06-27
Can you post the results of lspci and lsmod please? My inspiron 6400 is working fine.

---

### Post by 801 on 2008-06-27
@Entropy: any section in particular? Both are rather long....

---

### Post by entropy_ on 2008-06-27
> **801 said:**
> @Entropy: any section in particular? Both are rather long....

Put them in .txt files and attach them.

---

### Post by 801 on 2008-06-27
output from lsmod:

> Module                  Size  Used by
binfmt_misc            12936  1
i915                   25856  2
drm                    83348  3 i915
ppdev                  10244  0
cpufreq_powersave       2688  0
cpufreq_stats           7232  0
cpufreq_userspace       5280  0
cpufreq_ondemand        9612  0
cpufreq_conservative     8072  0
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
video                  18060  0
container               5504  0
sbs                    19592  0
button                  8976  0
dock                   10656  0
ac                      6148  0
battery                11012  0
ipv6                  273892  8
parport_pc             37412  0
lp                     12580  0
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0
uvcvideo               48644  0
compat_ioctl32          2304  1 uvcvideo
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
psmouse                39952  0
pcspkr                  4224  0
serio_raw               8068  0
iTCO_wdt               11940  0
iTCO_vendor_support     4868  1 iTCO_wdt
snd_hda_intel         263840  2
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
atl2                   33304  0
snd_seq_midi            9600  0
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 34580  0
pci_hotplug            32704  1 shpchp
intel_agp              25620  1
agpgart                35016  3 drm,intel_agp
evdev                  11136  6
usb_storage            73152  0
ide_core              116804  1 usb_storage
reiserfs              248704  1
libusual               18448  1 usb_storage
sg                     36764  0
sd_mod                 30336  3
ata_piix               17540  2
ahci                   23300  0
ata_generic             8452  0
libata                125168  3 ata_piix,ahci,ata_generic
scsi_mod              147084  4 usb_storage,sg,sd_mod,libata
ehci_hcd               36492  0
uhci_hcd               26640  0
usbcore               138632  6 uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14344  0
processor              32072  1 thermal
fan                     5764  0
fuse                   47124  1
apparmor               40728  0
commoncap               8320  1 apparmor


output from lspci:

> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)


I hope this helps

---

### Post by entropy_ on 2008-06-27
You have a different wireless card to me, so there isn't much I can do. Try ```
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta

```
Then reboot. I'm not sure what else to do, best wait for someone to come along who has installed its drivers themselves. Also, what kernel are you running (uname -r)

---

### Post by 801 on 2008-06-27
@Entropy:
kernel 2.6.22-15-generic
which is weird, I remember updating to ....19. I'll dig into grub to see what's happening there.

Both ath_pci and wlan_scan_sta modprobe give:
FATAL: Module (...) not found.

Thanks anyway, I'll be back to tell what grub gives.

---

### Post by 801 on 2008-06-27
Hmmmm.... kernel (...)19 is on my Kubuntu laptop. The machine with the wifi problems (an EEEpc with Xubuntu) is indeed running kernel (...)15.
Should I do an upgrade to Xubuntu 8.04 LTS? Need to be sure on this, I'll better wait what happens to/with the other posters or updates, since the problem doesn't seem to be related to any single platform.
Nevertheless, thank you for trying!

---

### Post by entropy_ on 2008-06-27
The kernel 2.6.2**2** is about a year old, rather than the current 2.6.2**4**-19 release. Upgrading would probably solve the problem, assuming that there is nothing keeping you using the old version. Can you do ```
ls /lib/modules/2.6.22-15-generic
ls /lib/modules/2.6.22-15-generic/madwifi
``` to determine if you have the drivers installed (which ship with newer kernels). This stopped working when you tried to update, correct? strange...

---

### Post by 801 on 2008-06-27
@Entropy:
Ouch. I hadn't even noticed I was on 22 instead of 24. Good for you.

No madwifi directory in /lib(etc), so there's no point in posting the output of both ls.

Is anybody else with this problem on kernel ...22 like me? CarlWalters? qlucy? Because if they are, it seems like we tackled the problem.
I'll wait with upgrading until we know for sure.

@Entropy: yes, but the problem occurred not when I *tried* to update, but when the update *succeeded*. Small but significant difference ;-).

---

### Post by Apex-jb on 2008-06-27
I am getting this same problem on a Inspiron 6000. One day, after some updates, my wirless went away. I tried a fresh install and now it will simply not work period. I have my restricted drivers enabled and still nothing.

---

### Post by Grone1985 on 2008-06-27
Same here on Ubuntu Hardy 64x on a Dell Inspiron 1501.
Help please!!

---

### Post by entropy_ on 2008-06-27
Can anyone else who can't get their wireless to work after the updates post the results of ```
uname -r
lspci
ls /lib/modules
```

and make sure you haven't accidentially hit the wireless kill switch (fn + F2 on inspirons), ive spent hours trying to find out why wireless had stopped working just to press 2 buttons and get it back :lol:

@801

Could you do ls /lib/modules too. I want to see what kernel you were running before this. And, what version of (x)ubuntu are you running? I cant see why you would get downgraded (I dont even know if that is possible).

If you need wireless in the meantime you can install the madwifi drivers yourself or upgrade the kernel by installing one of the linux-image packages from the repos

@Carl

Does it work when you try to connect to unsecure networks. I'm going to change my network to WEP to test myself when I can. Can you post ```
uname -r
lspci
iwconfig
``` please?

@qlucy

Can you post 
```
uname -r
lspci
iwconfig
``` too? This started happening after a update, correct?

---

### Post by Grone1985 on 2008-06-28
Ok entropy_... Here are the outputs for the commands...

```
maitreyi@maitreyi-laptop:~$ uname -r
2.6.24-19-generic

maitreyi@maitreyi-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

maitreyi@maitreyi-laptop:~$ ls /lib/modules
2.6.24-16-generic  2.6.24-17-generic  2.6.24-18-generic  2.6.24-19-generic
```

Hope that helps

---

### Post by Gsundbrunn on 2008-06-28
Similar issue here - still probs with WLAN - either no connection possible (autoatic connection) or - after creating it manually - it looses accidently the connection and cannot reconnect or, if connected, cannot go to internet or internal adresses.

Thats really annoying :-(

What I would like to try is to uninstall any! wlan settings and programs and reinstall them - how can I do this? Any help appreciated :-)

Thanks in advance!

Stefan

---

### Post by deleonjavier on 2008-06-28
the update to kernel 2.6.22-15 seems to be the problem luckily the option in grub bootloader lets me load kernel 2.6.22-14. but why.

---

### Post by 801 on 2008-06-28
Indeed deleonjavier, it's a kernel-related problem. That friend of mine found out that if you load the previous kernel using grub everything is OK again. I tested it on my machine, and presto!

---

### Post by CarlWalters on 2008-06-28
> **entropy_ said:**
> 

@Carl

Does it work when you try to connect to unsecure networks. I'm going to change my network to WEP to test myself when I can. Can you post ```
uname -r
lspci
iwconfig
``` please?

@qlucy


Hi Entropy,sorry I've been out all day. Here are the results of the three commands

```

carl@carl-laptop:~$ uname -r
2.6.24-19-generic
carl@carl-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
carl@carl-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

carl@carl-laptop:~$ 

```

Does that help? It doesn't mean a lot to me I'm afraid :(

---

### Post by stringkarma on 2008-06-28
You guys may want to chime in or at least pay attention to the bug page that has been started for this. Adding people to the list having this problem may bring more attentino to the problem to the developers.

[https://bugs.launchpad.net/ubuntu/+bug/242876](https://bugs.launchpad.net/ubuntu/+bug/242876)

---

### Post by entropy_ on 2008-06-28
@ CarlWalters & Grone1985
It seems that everyone affected by this is either running broadcom or athros cards. Is wireless turned on (FN + F2)? Is the driver still showing in the restricted drivers dialog? Can you post the output of ```
lshw -C network
``` please? Try the steps at [http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495") to connect to the network and post any errors

> 
[https://bugs.launchpad.net/ubuntu/+bug/242876](https://bugs.launchpad.net/ubuntu/+bug/242876)
Thanks for bringing that to our attention. It's probably best to let them handle it.

---

### Post by Apex-jb on 2008-06-28
> **entropy_ said:**
> Can anyone else who can't get their wireless to work after the updates post the results of ```
uname -r
lspci
ls /lib/modules
```

and make sure you haven't accidentially hit the wireless kill switch (fn + F2 on inspirons), ive spent hours trying to find out why wireless had stopped working just to press 2 buttons and get it back :lol:



uname -r
```
2.6.24-19-generic
```

lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

ls /lib/modules
```
2.6.24-16-generic  2.6.24-19-generic

```

---

### Post by entropy_ on 2008-06-28
Can you post the output of

lshw -C network

too please? Try the steps at [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495) to connect to the network and post any errors. I dont know what else I can do to solve the problem, just get your wireless working again and wait for the devs to find out why this happened and fix it at the core.

---

### Post by Grone1985 on 2008-06-28
Here is my output for "lshw -C network"

```
maitreyi@maitreyi-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:5e:2f:8a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.2.9 latency=64 module=ssb multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:06:9e:01
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

---

### Post by CarlWalters on 2008-06-28
> **entropy_ said:**
> @ CarlWalters & Grone1985
It seems that everyone affected by this is either running broadcom or athros cards. Is wireless turned on (FN + F2)? Is the driver still showing in the restricted drivers dialog? Can you post the output of ```
lshw -C network
``` please? Try the steps at [http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495") to connect to the network and post any errors


Thanks for bringing that to our attention. It's probably best to let them handle it.

Wireless is still turned on (at least the light is on on the laptop), not quite sure how to check the restricted drivers though. The ouput of lshw -C is

```

 lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8b:41:7b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.6 latency=64 module=ssb multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:26:16:ef:c4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
carl@carl-laptop:~$ 
carl@carl-laptop:~$ 
carl@carl-laptop:~$ 

```

It looks from this as though there is no driver installed for the wireless interface. Although when I go to System->Administration->Hardware Drivers it shows "Broadcom B43 Wireless Driver" enabled and in use (although the box also says "No proprietary drivers are in use on this system"

If I try the instructions at [http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495") substituting wlan0 for <network> (not certain if this is correct?) then I get 

```

carl@carl-laptop:~$ 
carl@carl-laptop:~$ 
carl@carl-laptop:~$ sudo ifconfig wlan0 down
carl@carl-laptop:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1c:26:16:ef:c4
Sending on   LPF/wlan0/00:1c:26:16:ef:c4
Sending on   Socket/fallback
carl@carl-laptop:~$ sudo ifconfig wlan0 up
carl@carl-laptop:~$ sudo iwconfig wlan0 essid "CarlWilliamWalters"
carl@carl-laptop:~$ sudo iwconfig wlan0 key MYLONGHEXKEYTHING
carl@carl-laptop:~$ sudo iwconfig wlan0 key open
carl@carl-laptop:~$ sudo iwconfig wlan0 mode Managed
carl@carl-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1c:26:16:ef:c4
Sending on   LPF/wlan0/00:1c:26:16:ef:c4
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
carl@carl-laptop:~$ 


```

so that doesn't look hopeful :(

---

### Post by entropy_ on 2008-06-28
Because of what qlucy said about being able to connect to unsecured networks I think its more of a wep issue. A bit of searching has brought up [http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318+ndiswrapper](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318+ndiswrapper) ([https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/139812](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/139812)). Can you do the quoted part and retry connecting. I'm pretty sure that your drivers are all working fine.

EDIT: Yes, wlan0 is correct.

---

### Post by starcannon on 2008-06-28
I love Ubuntu don't get me wrong, but I to have been frustrated with updates breaking things.

A kernel update should come with a caveat, or the ability to specifically not do kernel updates would be fine (if we can already do that I haven't figured out how yet)

Regression testing is a must, especially where internet connections are concerned. The only good reason I can think of for not regression testing would be in the rare case where there is a security flaw that outweighs the endusers need to have a pain free wifi experience (yeah I'd rather fight with ndis wrapper than my credit card company, suddenly dealing with stubborn hardware seems easy when in that context no?)

Anyway. Keep up the good work Canonical, but slow down, enjoy the ride, if its not an urgent security update, then please take your time.

---

### Post by CarlWalters on 2008-06-29
> **entropy_ said:**
> Because of what qlucy said about being able to connect to unsecured networks I think its more of a wep issue. A bit of searching has brought up [http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318+ndiswrapper](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318+ndiswrapper) ([https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/139812](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/139812)). Can you do the quoted part and retry connecting. I'm pretty sure that your drivers are all working fine.

EDIT: Yes, wlan0 is correct.

no go I'm afraid. I tried 

```

sudoedit /etc/network/interfaces
add the line
iface wlan0 inet dhcp

```

(I'm glad I could remember a few vi commands from years ago :) )

and then 

```

carl@carl-laptop:~$ sudo iwconfig wlan0 essid CarlWilliamWalters key 01234567890123456789ABCDEF sudo ifup wlan0  
iwconfig: unknown command "sudo"

so I tried splitting the line in two 

carl@carl-laptop:~$ sudo iwconfig wlan0 essid CarlWilliamWalters key 01234567890123456789ABCDEF  
carl@carl-laptop:~$ sudo ifup wlan0  
Ignoring unknown interface wlan0=wlan0.

```

so I'm still confused...

---

### Post by CarlWalters on 2008-06-29
well my wireless connection now seems to be working so I'm doubly confused. I did notice that after my last post the wifi light had gone off on the laptop (it was on before I'm certain) so I dif FN+F2 to enable it and tried again to connect. Hey presto it worked. What on earth could have changed?

Here are the new outputs of all the commands that I posted before - maybe someone can make some sense of what exactly has changed.

```

carl@carl-laptop:~$ 
carl@carl-laptop:~$ lsmod
Module                  Size  Used by
af_packet              23812  4 
ipv6                  267780  10 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
rfkill_input            5504  0 
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
aes_i586               33536  0 
dm_crypt               15364  0 
dm_mod                 62660  1 dm_crypt
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
dcdbas                  9504  0 
b43                   144420  0 
evdev                  13056  9 
rfkill                  8592  3 rfkill_input,b43
snd_hda_intel         344728  6 
serio_raw               7940  0 
mac80211              165652  1 b43
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
psmouse                40336  0 
sdhci                  19076  0 
pcspkr                  4224  0 
cfg80211               15112  1 mac80211
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
ricoh_mmc               4352  0 
mmc_core               51460  1 sdhci
led_class               6020  1 b43
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
input_polldev           5896  1 b43
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  19856  0 
snd                    56996  21 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                  4736  1 video
wmi_acer                9644  0 
ac                      6916  0 
battery                14212  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
button                  9232  0 
soundcore               8800  1 snd
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  3 
cdrom                  37408  1 sr_mod
pata_acpi               8320  0 
usb_storage            73664  0 
libusual               19108  1 usb_storage
ata_piix               19588  2 
ata_generic             8324  0 
ohci1394               33584  0 
b44                    28432  0 
mii                     6400  1 b44
ieee1394               93752  2 sbp2,ohci1394
libata                159344  3 pata_acpi,ata_piix,ata_generic
scsi_mod              151436  6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  5 usb_storage,libusual,ehci_hcd,uhci_hcd
ssb                    34308  2 b43,b44
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
carl@carl-laptop:~$ 

```
```

carl@carl-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
carl@carl-laptop:~$ 


```
```

carl@carl-laptop:~$ uname -r
2.6.24-19-generic
carl@carl-laptop:~$ 
carl@carl-laptop:~$ 
carl@carl-laptop:~$ ls /lib/modules
2.6.24-16-generic  2.6.24-19-generic


```
```

carl@carl-laptop:~$ 
carl@carl-laptop:~$ 
carl@carl-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"CarlWilliamWalters"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:EE:DA:26   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=96/100  Signal level=-38 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
carl@carl-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8b:41:7b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:26:16:ef:c4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.4 multicast=yes wireless=IEEE 802.11g
carl@carl-laptop:~$ 
carl@carl-laptop:~$ 
carl@carl-laptop:~$ 


```

---

### Post by entropy_ on 2008-06-29
> **CarlWalters said:**
> well my wireless connection now seems to be working so I'm doubly confused. I did notice that after my last post the wifi light had gone off on the laptop (it was on before I'm certain) so I dif FN+F2 to enable it and tried again to connect. Hey presto it worked. What on earth could have changed?

Here are the new outputs of all the commands that I posted before - maybe someone can make some sense of what exactly has changed.


:guitar: :guitar: :guitar:

I think editing /etc/network/interfaces did it, but I should have told you to do sudo /etc/init.d/networking restart, which would have been done when you rebooted (maybe when you fn + F2 too? nothing has changed from what you posted anyway). Anyway, good to know what the problem is. 

Can anyone else having this problem do the quoted part under hardy in [this thread]("http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318+ndiswrapper"), then ```
sudo /etc/init.d/networking restart
``` then try to reconnect and report back

---

### Post by Apex-jb on 2008-06-29
So is there any work around I can use right now to fix this? So many people are doing different things I am kind of getting lost.

---

### Post by CarlWalters on 2008-06-29
> **entropy_ said:**
> :guitar: :guitar: :guitar:

I think editing /etc/network/interfaces did it, but I should have told you to do sudo /etc/init.d/networking restart, which would have been done when you rebooted (maybe when you fn + F2 too? nothing has changed from what you posted anyway). Anyway, good to know what the problem is. 

Can anyone else having this problem do the quoted part under hardy in [this thread]("http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318+ndiswrapper"), then ```
sudo /etc/init.d/networking restart
``` then try to reconnect and report back

that could be it as I did power off/on in between. Thanks to everyone for all their help especially entropy_ :)

---

### Post by entropy_ on 2008-06-29
> **Apex-jb said:**
> So is there any work around I can use right now to fix this? So many people are doing different things I am kind of getting lost.

Do
[QUOTE=DrSpirograph]```
sudo nano /etc/network/interfaces
add the line
iface wlan0 inet dhcp
```
[/QUOTE]
then
```

sudo /etc/init.d/networking restart

```

---

### Post by Apex-jb on 2008-06-29
> **entropy_ said:**
> Do

then
```

sudo /etc/init.d/networking restart

```

Thanks man, that did it.

---

### Post by qlucy on 2008-07-01
Thank you all so much for your help! Entropy, thank you especially, and I apologize for disappearing; I was away from my computer for a few days. 

After reading all the posts I ran:
lshw -C network

the end said wireless=unassociated

tried Fn + F2, then lshw -C network again

this time it said wireless=disabled

did Fn + F2 to turn it back on, did the same thing and got wireless=unassociated again.

rebooted.

lshw -C network

now it says wireless=IEEE 802.11g

yay!!!

so far, so good...I've been online for awhile now and it's still connected.  If it acts up again, I'll be sure to try the other fix, but it seems like it just needed to reinitialize and turning it off and on did it. I'm a bit surprised by this since I one of the first things tried was right-clicking on the wireless icon and disabling then enabling it, then rebooting....but I'll take it.

thank you again! this changes my world. :)

---

### Post by Grone1985 on 2008-07-02
So my wireless is still not working after trying the workaround of editing interfaces.

Also the updates from today didn't help.

Any help or other ideas?

Thanks in advance!

---

