---
title: "No Connection, Wired OR Wireless. Ubuntu 10.10 Netbook Remix"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by Charlie: on 2011-01-26
First off, my name is Stefan, and thank tech-heaven there's a whole forum dedicated to the noobs!

I installed Ubuntu 10.10 Netbook Remix, dual-boot with *Windows XP Home* on my Acer One netbook Sunday night. Since then, I've been frustrated trying to figure out my connection issues.

From my searches on this forum I can tell lots of people are having problems with the Broadcom Wireless connection, same here. The twist is, I can't get the B43 proprietary drivers installed without a connection. When hardwired, Ubuntu has no connection, and my router doesn't show that the ethernet port is active. (Blinking lights and such aren't on) *This happens on my desk, connected to the same router as my XP desktop, while I'm surfing on that machine*. I'm not sure what's happening. :confused: *Both wired and wireless work just fine when I boot into XP on the netbook.* (Posting from my living room right now in Windows, unfortunately)

_The night of my installation I could connect with ethernet, and I followed a page on the ubuntu site that took me step-by-step through installing the firmware with terminal, but it didn't get the wireless working. After I restarted, all connections have stopped working._ 

**HERE IS SOME USEFUL INFORMATION:**

charlie@Charlie-Book:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
03:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
charlie@Charlie-Book:~$



charlie@Charlie-Book:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 002: ID 04f2:b084 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



charlie@Charlie-Book:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



charlie@Charlie-Book:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:17:2f:71  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13256 (13.2 KB)  TX bytes:13256 (13.2 KB)



charlie@Charlie-Book:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
usb_storage            40172  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   218227  1 
binfmt_misc             6599  1 
joydev                  8767  0 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
i915                  294989  5 
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
drm_kms_helper         30200  1 i915
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm                   168092  5 i915,drm_kms_helper
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
intel_agp              26694  2 i915
psmouse                59033  0 
videodev               43098  1 uvcvideo
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13359  2 uvcvideo,videodev
serio_raw               4022  0 
led_class               2633  0 
soundcore                880  1 snd
agpgart                32011  2 drm,intel_agp
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19198  2 
libahci                21664  1 ahci
atl1c                  29949  0 
ssb                    39288  0 



**Firmware stuff**: 
File 1: broadcom-wl-4.150.10.5.tar.bz2
File 2: wl_apsta-3.130.20.0.o


If this has been addressed and I just looked over it in my searching, please facepalm with a complimentary 'Solved' link!

That's all for now.
-Stefan

---

### Post by jtarin on 2011-01-26
What is you connection...DSL, cable etc;?
Try this.
```
Networking

If the ethernet device was knocked out during installation:

ensure that /etc/network/interfaces contains no hotplug entry for eth0 or wlan0
shutdown netbook and remove the power cord
remove battery and let sit for a minute or so
restore power to netbook and startup
lspci -v | grep net reveals the ethernet device (Atheros Communications AR8132 Fast Ethernet)
bring up the interface... [CODE]ifconfig eth0 up
``` and ```
dhclient eth0
```[/CODE]

---

### Post by Charlie: on 2011-01-26
Ah, forgot to mention..

I have Comcast Cable.

EDIT:
charlie@Charlie-Book:~$ ifconfig eth0 up
SIOCSIFFLAGS: Permission denied
charlie@Charlie-Book:~$ sudo ifconfig eth0 up
[sudo] password for charlie: 
charlie@Charlie-Book:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:26:22:17:2f:71
Sending on   LPF/eth0/00:26:22:17:2f:71
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by jtarin on 2011-01-27
With or without a modem?
When you do ifconfig eth0 up
Check ifconfig to see if your eth0 has an ip address.

---

### Post by Charlie: on 2011-01-27
With a modem. 

Wall -> modem -> router -> desktop/wireless
I've had my desktop and PS3 hooked in since August with no problems. I bought this netbook last week for the sole purpose of learning about Linux.

Haha, I'm so green it's not even funny! I'll come back in a minute with the results.

Thanks for the help so far jtarin!

After that, 

eth0      Link encap:Ethernet  HWaddr 00:26:22:17:2f:71  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 
same result except for different numbers:
3
5
9
9
9
11
11
4

No IP as far as I can tell..
--Stefan

---

### Post by jtarin on 2011-01-27
> **Charlie: said:**
> With a modem. 

Wall -> modem -> router -> desktop/wireless
I've had my desktop and PS3 hooked in since August with no problems. I bought this netbook last week for the sole purpose of learning about Linux.

Haha, I'm so green it's not even funny! I'll come back in a minute with the results.

Thanks for the help so far jtarin!

After that, 

eth0      Link encap:Ethernet  HWaddr 00:26:22:17:2f:71  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 
same result except for different numbers:
3
5
9
9
9
11
11
4

No IP as far as I can tell..
--Stefan

Ok I'm approaching this problem from the standpoint of the wired connection and your lsmod command shows the module loaded for your ehternet card..."atl1c 29949 0". Possibly this is the wrong module even though it is an Atheros module. Let me search for problems withthis and get back.

---

### Post by jtarin on 2011-01-27
OK I found this.
```
To fix LAN. I have an Atheros AR8131 Ethernet card.

From a terminal:
1) sudo gedit /etc/default/grub

In gedit:
2) Replace the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
with
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=use_crs"
then save and close.

From a terminal:
3) sudo update-grub

4) Reboot your system
```

---

### Post by Charlie: on 2011-01-27
Thanks for another try.

I followed instructions, and after the reboot it's still the same story.
No IP from ifconfig, and dhclient eth0 still returns nothing.

I'm thinking a fresh install might be simpler, any other thoughts?

EDIT:
I installed from a live-flash drive, if there might be something on there I should dig for.. I'm pretty illiterate when it comes to anything Linux.

---

### Post by jtarin on 2011-01-28
Before installing see if you can get online using the live CD/Flashdrive.

---

### Post by Charlie: on 2011-01-28
No luck, as usual. I'm gonna try to figure out ndiswrapper again tonight, maybe I skipped a step last time :/

---

### Post by Charlie: on 2011-02-05
Had a bit of luck tonight with this:

sudo modprobe -r b43 ssb

then

sudo modprobe b43

It seems like Ubuntu recognized my network card because instead of listing (from the icon on the toolbar, left-click)"Wired connections - none available" alone, it also said "Wireless connections - firmware missing".

Seems like I'm getting closer.. Still no cigar though :(

I've got some time tonight though so I'll finally get around to trying ndiswrapper. Cross your fingers!

---

### Post by Charlie: on 2011-02-07
Last post for this thread.

Tonight I installed Ubuntu 10.04, had a rocky start but after a little work in the command line (from GRUB) I was able to get a stable boot every time. Installed STA driver from additional hardware and it works like a charm!

I appreciate the help, and I'm sure I'll be back for more shortly.

Any suggestions what to go after first with my shiny new Linux?

---

### Post by wep940 on 2011-02-07
I saw a couple of posts back that you were thinking of trying ndiswrapper again - this brings to mind a few tips, and since you've solved you problem this will be for others reading this thread:
 
- if you install ndiswrapper and try to use it, then try to use one of the restricted drivers, you will get a conflict.  For Broadcom wireless, *IF* you use ndiswrapper you will need to black list b43, ssa, etc., or they will make anything you do in ndiswrapper not work.  The best option is to always try to the restricted drivers first - if they don't work and you have no other way to get on the net, only then install ndiswrapper (and be sure to include the GUI for it - ndisgtk).  After you are online, do a sudo apt-get update, then check in restricted drivers again to see if something else comes up.  If so, enable it and REMOVE ndiswrapper and ndisgtk, and REBOOT before trying the new driver out.

---

### Post by Charlie: on 2011-02-10
Thanks wep940! That's a much simpler explanation than I got from the tutorials.

On another note since I have my netbook up and running 10.04 with no problems, this thread can probably be deleted.

---

