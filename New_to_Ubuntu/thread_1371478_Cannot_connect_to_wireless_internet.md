---
title: "Cannot connect to wireless internet"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by Feline Monstrosity on 2010-01-03
Hi. I have a Samsung N130 netbook and I dual boot Windows XP with Ubuntu Netbook Remix. On my Windows side I have absolutely no problem connecting to the internet, wirelessly or otherwise, so it can't be a problem with my hardware. However on Ubuntu I can't connect to the internet wirelessly. This is not just a problem at home, I have been elsewhere and it hasn't been able to detect any wireless networks at all. I can however connect when I plug directly into the router with an ethernet cable, so it is an issue with the wireless capabilities of my OS only.
I found a script on another forum, here: [http://www.linuxforums.org/forum/wireless-internet/137532-wireless-setup-start-here.html](http://www.linuxforums.org/forum/wireless-internet/137532-wireless-setup-start-here.html)

Here is the output of the script:
```
============ lspci ============
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
	Kernel driver in use: i915
	Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
	Kernel modules: iTCO_wdt, intel-rng
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
	Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
	Kernel modules: i2c-i801
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8192] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Kernel driver in use: r8169
	Kernel modules: r8169

============ lsusb ============
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0ac8:c33f Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

============ lsmod ============
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3100  0 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
v4l1_compat            14496  2 uvcvideo,videodev
joydev                 10272  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
lp                      8964  0 
parport                35340  2 ppdev,lp
psmouse                56180  0 
serio_raw               5280  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usbhid                 38208  0 
r8169                  32064  0 
mii                     5212  1 r8169
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

============ dmesg-firmware ============

============ kernel version ============
2.6.31-14-generic

============ ifconfig ============
eth0      Link encap:Ethernet  HWaddr 00:24:54:0c:e2:a8  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:54ff:fe0c:e2a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5057 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4789 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4710695 (4.7 MB)  TX bytes:701615 (701.6 KB)
          Interrupt:26 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


============ iwconfig ============

```

---

### Post by dmaxel on 2010-01-03
I'm not sure if this is exactly your problem or not, but at least this problem occurred in my Ubuntu Desktop edition. It didn't have any wireless connections added, so you'll have to do it manually. For me, I just had to add a new wireless connection and then put in the MAC address, which I found by looking in my Windows.

---

### Post by isaacj87 on 2010-01-03
I found this post. Hopefully, it will be of use to you.

[http://ubuntuforums.org/showpost.php?p=8448187&postcount=5]("http://ubuntuforums.org/showpost.php?p=8448187&postcount=5")

If you get stuck trying to install the drivers, I will be more than happy to help. :)

---

### Post by totoff on 2010-01-03
you don't have the wireless driver installed. otherwise it would show up as for example eth02 when you check ifconfig. what you can see is your network card eth0. go and install the proprietary driver: system, systemadministration, hardware drivers. you need to have cable connection to do so. when the driver is found click activate. then check in the status bar with LEFT mouse click for a list of available networks. hope this helps.

---

### Post by derekmbarnes on 2010-01-03
> **Feline Monstrosity said:**
> 
```

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8192] (rev 01)

```


This should work for you: [http://ubuntuforums.org/showthread.php?t=1367871](http://ubuntuforums.org/showthread.php?t=1367871)

---

### Post by razorj7 on 2010-01-03
I had the same issue when I installed both UNR and the desktop version. All I had to do:

Run the update manager 

restart

activate the Broadcom STA wireless proprietary driver

restart

then you should be able to detect wireless

---

### Post by Feline Monstrosity on 2010-01-04
> **razorj7 said:**
> 
activate the Broadcom STA wireless proprietary driver

How do you do that part?

---

### Post by bkratz on 2010-01-04
> **Feline Monstrosity said:**
> How do you do that part?



The STA driver is only for some Broadcom units, yours is not a Broadcom. I believe you should look at the posting by derekmbarnes
just above.

---

### Post by Feline Monstrosity on 2010-01-25
Hi. It's a long time since I last posted in this thread, but I tried all the steps in the post linked by derekmbarnes (including the note at the end which says to make sure the driver is installed) and it still hasn't worked.

I don't know what might have went wrong, can someone please help?

---

### Post by bkratz on 2010-01-25
> **Feline Monstrosity said:**
> Hi. It's a long time since I last posted in this thread, but I tried all the steps in the post linked by derekmbarnes (including the note at the end which says to make sure the driver is installed) and it still hasn't worked.

I don't know what might have went wrong, can someone please help?

So, was the driver installed, what was the output of 
lsmod |grep r8192se_pci

You might post the output of 
sudo lshw -C network


Also did the file make without errors?

---

### Post by Feline Monstrosity on 2010-01-25
The file appeared to make without errors. 
"lsmod |grep r8192se_pci" gave no output.

Here is the output of "sudo lshw -C network":

```
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:54:0c:e2:a8
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.64 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:3000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)

```

---

### Post by caravel on 2010-01-25
I think you have to use vendor (proprietary) drivers for that chipset (r8192e).

---

### Post by bkratz on 2010-01-25
since you didn't see anything with the first command try:

modprobe r8192se_pci
iwconfig


Do you now have a wireless interface, wlan0, perhaps? Can you click the Network Manager and connect?

---

