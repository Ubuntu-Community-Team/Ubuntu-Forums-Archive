---
title: "Configure Linksys WRT54G2"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by TetonsGulf on 2008-08-20
I'm having trouble connecting my UHardy desktop wireless card to the Linksys WRT54G2 router. I know the network is running, I've gotten a Vista machine, a wired XP machine, another XP which is the other disk on the same hardware as the UHardy and it's running wireless and an EeePc running Xandros with wireless all fired up and good to go.

I've tried to manually configure with 192.168.1.1 and I'm getting the address not found page from Firefox, which I thought was damn near impossible but I guess not. The UHardy OS is seeing the signal as it is an option to connect but is not going through as it has with the others.

Here are the particulars:
Ubuntu 8.04.1
Linksys WRT54G2 Wireless-G Broadband Router; WPA2 security.
Netgear WG311v3 802.11g Wireless Card
ISP is WildBlue Satellite
ndiswrapper is installed

Has anyone had a similar problem and if so, how do you resolve it? The flood of responses I'm sure I'll see will be much appreciated.

---

### Post by caljohnsmith on 2008-08-20
To start off, do you know what wireless chipset your Netgear card uses? And have you tried disabling encryption with your router (if you use it) and seeing if you can connect that way? To give a starting place for troubleshooting, please post the output of the following commands:
```
sudo lshw -C network
lspci
lsmod
ndiswrapper -l
```

---

### Post by TetonsGulf on 2008-08-20
I'm not certain of the chipset, but if you can direct me, I can find it. Also, I have not tried disabling encryption, mainly because the ISP has limits on DL and UL and even though we are "in the sticks", we're in a subdivision.

Output is as follows, and thanks for your help!

sudo lshw -C network

*-network:0             
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: wlan0
       version: 03
       serial: 00:1b:2f:c1:4c:1d
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+mrv8335 driverversion=1.52+Marvell,02/22/2005,3.1.1.7 latency=64 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 10
       serial: 00:1b:b9:a6:24:cd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

lspci

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
01:06.0 Communication controller: Conexant Unknown device 2f40
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

lsmod

Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
binfmt_misc            12808  1 
ppdev                  10372  0 
powernow_k8            16704  0 
cpufreq_ondemand        9740  1 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
container               5632  0 
battery                14212  0 
ipv6                  267780  10 
ndiswrapper           192920  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
evdev                  13056  3 
af_packet              23812  6 
psmouse                40336  0 
pcspkr                  4224  0 
serio_raw               7940  0 
nvidia               7825536  34 
k8temp                  6656  0 
agpgart                34760  1 nvidia
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
shpchp                 34452  0 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
i2c_nforce2             7680  0 
i2c_core               24832  2 nvidia,i2c_nforce2
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sd_mod                 30720  7 
usb_storage            73664  1 
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
libusual               19108  1 usb_storage
sata_nv                27528  3 
pata_amd               14212  0 
pata_acpi               8320  0 
8139cp                 24704  0 
ata_generic             8324  0 
8139too                27520  0 
mii                     6400  2 8139cp,8139too
libata                159344  4 sata_nv,pata_amd,pata_acpi,ata_generic
scsi_mod              151436  5 sd_mod,usb_storage,sg,sr_mod,libata
ehci_hcd               37900  0 
ohci_hcd               25348  0 
usbcore               146028  6 ndiswrapper,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              36872  2 powernow_k8,thermal
fan                     5636  0 
fuse                   50708  5 
vesafb                  8964  1 
fbcon                  42912  72 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit

ndiswrapper -l

mrv8335 : driver installed
	device (11AB:1FAA) present

---

### Post by caljohnsmith on 2008-08-20
That's amazing--you are using the exact same wireless chipset, the Libertas 88w8335, that is on my wireless card, although mine is a Trendnet card instead of Netgear. Well the good news is that mine works great with ndiswrapper, so I think we can get yours going too.

Which Windows wireless driver did you use with ndiswrapper? Did you use the Vista or the XP one? I know mine works great with the XP one, and it could be an issue if you are using the Vista driver. It doesn't look like you have any other drivers interfering with ndiswrapper, so that is good.
> **TetonsGulf said:**
> 
Also, I have not tried disabling encryption, mainly because the ISP has limits on DL and UL and even though we are "in the sticks", we're in a subdivision.
Not sure I get you, but disabling encryption won't hurt your download or upload speeds. If what you mean is you're concerned about your neighbors jumping on your network and using all your DL/UL quota, all I meant was to temporarily disable encryption (just for a few minutes) just to see if you can connect that way. That will tell us if the problem is with using encryption, or if your wireless card is simply not able to connect at all at this point.

---

### Post by TetonsGulf on 2008-08-20
Well, that is good news, something we can fix!

The driver is an XP driver, mrv8335 if I'm not mistaken. I have no problem disabling the encryption, but obviously I can't leave it that way. I had set it up with the level I wanted right out of the box, but I'll try it later tonight as right now work calls.

I'll reset tonight about 10 Eastern when I get back. 

If you have any ideas you want me to try, let me know.

Thanks for your help thus far.

KSH

---

### Post by TetonsGulf on 2008-08-25
I've reset the security on the router and was able to connect without issue, so I reset with a WEP 128 bit password and have been on ever since.

I am curious why the WPA2 wouldn't work, so I'll leave this open for others to explore.

Many thanks to caljohnsmith for the willingness to help and starting me off in the right direction.

KSH

---

### Post by caljohnsmith on 2008-08-25
Glad to hear you got your wireless working, TetonsGulf. :) By the way, if you really want to use WPA/WPA2, you might want to give the network manager program ["WICD"]("http://wicd.sourceforge.net/") a try, as that is often better at handling WPA/WPA2. Are you using DHCP or a static IP to connect to your router? Just curious because static IP + WPA is a known problem for Gnome's network manager.

---

### Post by TetonsGulf on 2008-08-25
I had been using the WICD manager pretty much from the onset of my Ubu experience. WildBlue uses DHCP for assigning the IP, so it made sense to me to go with WICD as well. I really only wanted to go with the WPA2 for the advanced security, but I put in a couple workarounds that I think will keep everything safe.

I stopped the router from broadcasting the SSID, changed the name from the default, disabled wireless access to the managing screen and limited the access to only those MAC's that reside in the house. Anyone else who comes over and wants access can go through me for all the goodies I suppose.

Thanks for your help.

KSH

---

