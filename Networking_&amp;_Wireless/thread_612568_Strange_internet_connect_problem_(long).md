---
title: "Strange internet connect problem (long)"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by Unka'George on 2007-11-14
Strange Internet connection problem

Apparently successful installation of 7.10 Gutsy Gibbon Ubuntu using download from Ubuntu website as iso file that I used to burn a cd under both windows and 7.10 ubunto.

Both cds checked OK when using the self test option during the initial install.

I had just upgraded about a week before to a 10 MBS wireless link, and decided to go ahead and try Linux.

In order to provide maximum flexibility I installed a WRT54GS router.  Currently I have the router connected via cable to the existing Ethernet port [eth0] on my computer.  M7VGA  BioStar motherboard and 2 gig ram. The wireless connection is turned off.

The Linksys router was easily configured using Unbutu/Firefox by accessing [http://192.168.1.1](http://192.168.1.1).
This gave a far better setup menu that the install disk did under Windows 2000. 
è HOWEVER BE ADVISED THAT IF YOU ACCESS THIS URL UNDER WINDOWS USING EITHER EXPLORER OR FIREFOX MOST OF THE INFORMATION DOES NOT DISPLAY, AND THIS DEACTIVATES THE RELTEC8139 ETHERNET DEVICE.  You will have to use the “settings >  control panel > add/remove hardware program” to reactivate it. 

The ISP tech staff had suggested setting the Internet Connect Type to ppp0, but this totally shut down internet access in both Unbunty and Windows.  This was reset to DHCP automatic configuration and full windows / partial Ubuntu access was restored.

Computer/wireless link/router works perfectly with Firefox 2.0, Thunderbird, Miro and Forte Free Agent under Windows 2K.

However when I boot Ubuntu, the only way I can get a webpage to load in Firefox is to enter the URL in the IPV4 format.  For example [http://www.72.14.205.147](http://www.72.14.205.147) loads fine, I cannot load http:/www.google.com and I get a server not found error.  Anything on the google page with a IPV4 format address loads fine and links to a IPV4 address load fine, even if it shows as [http://www.72.14.205.147/stuff/more-stuff](http://www.72.14.205.147/stuff/more-stuff) . Other apps [mail/newsreader/software update] that require internet access are also not operational.

I can ping and get responses from IPV4 addresses but not the names.

I thought this was a DNS problems, but when I enter my ISP server [http://64.254.34.12](http://64.254.34.12) this won’t load either, but the URL is almost instantly translated (correctly) into [http://home.terraworld.net](http://home.terraworld.net), and then I get a server not found screen.







I have run lsmod [after determining it starts with a lowercase ell and not an capital eye.] with the following results.

========= 
Module                  Size  Used by
nls_iso8859_1           5120  4 
nls_cp437               6784  5 
vfat                   14080  4 
isofs                  36412  2 
fat                    54300  1 vfat
udf                    87204  0 
savage                 34176  2 
drm                    83348  3 savage
ppdev                  10244  0 
sg                     36764  0 
cpufreq_ondemand        9612  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
button                  8976  0 
ac                      6148  0 
video                  18060  0 
sbs                    19592  0 
dock                   10656  0 
container               5504  0 
battery                11012  0 
sd_mod                 30336  6 
sr_mod                 17828  1 
ipv6                  273892  10 
lp                     12580  0 
joydev                 11328  0 
snd_usb_audio          81024  0 
snd_usb_lib            17920  1 snd_usb_audio
snd_hwdep              10244  1 snd_usb_audio
snd_via82xx            29336  1 
snd_ac97_codec        100644  1 snd_via82xx
snd_mpu401              9640  0 
analog                 13344  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
pwc                    86400  0 
snd_pcm                80388  4 snd_usb_audio,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9600  2 snd_via82xx,snd_mpu401
snd_seq_dummy           4740  0 
compat_ioctl32          2304  1 pwc
gameport               16776  2 snd_via82xx,analog
videodev               29312  1 pwc
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev
snd_seq_oss            33152  0 
usbhid                 29536  0 
usb_storage            73024  4 
snd_seq_midi            9600  0 
snd_rawmidi            25728  3 snd_usb_lib,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
irtty_sir               9856  0 
sir_dev                17412  1 irtty_sir
hid                    28928  1 usbhid
pcspkr                  4224  0 
psmouse                39952  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
libusual               18448  1 usb_storage
via_ircc               27668  0 
irda                  202300  3 irtty_sir,sir_dev,via_ircc
usblp                  15104  0 
crc_ccitt               3072  1 irda
serio_raw               8068  0 
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  16 snd_usb_audio,snd_hwdep,snd_via82xx,snd_ac97_codec,snd_mpu401,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
i2c_viapro             10004  0 
i2c_prosavage           5248  0 
i2c_algo_bit            7428  1 i2c_prosavage
i2c_core               26112  3 i2c_viapro,i2c_prosavage,i2c_algo_bit
shpchp                 34580  0 
parport_pc             37412  2 
parport                37448  3 ppdev,lp,parport_pc
via_agp                11264  1 
agpgart                35016  2 drm,via_agp
pci_hotplug            32704  1 shpchp
af_packet              24840  2 
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  1 
cdrom                  37536  2 sr_mod,ide_cd
ide_disk               18560  5 
via82cxxx              10372  0 [permanent]
ide_core              116804  4 usb_storage,ide_cd,ide_disk,via82cxxx
8139too                27776  0 
floppy                 60004  1 
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  5 sg,sd_mod,sr_mod,usb_storage,libata
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  10 snd_usb_audio,snd_usb_lib,pwc,usbhid,usb_storage,libusual,usblp,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  5 
apparmor               40728  0 
commoncap               8320  1 apparmor

Piping to grep and looking for eth0 or net or Network disclosed *NO* entries.


The applicable sections [I think] of lspci -n are
===============
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 00b2
	Flags: bus master, medium devsel, latency 32, IRQ 19
	I/O ports at b400 [size=256]
	Memory at ef010000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 80000000 [disabled] [size=64K]
	Capabilities: [50] Power Management version 2


Ifconfig returns the following

=============

eth0      Link encap:Ethernet  HWaddr 00:E0:4C:88:2A:54  
inet addr:192.168.1.100  Bcast:192.168.1.255                     Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe88:2a54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6233 (6.0 KB)  TX bytes:11119 (10.8 KB)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



Per the suggestions of some other news groups the following was inserted at the start of the /etc/modules file (however I could not tell any difference but no errors indicated either).

genrtc

bmac


The /etc/network/interfaces file was also changed 

===== From ====
auto lo
iface lo inet loopbacv

iface ppp0 inet ppp
provider ppp0

===== to =========
auto lo
iface lo inet loopback

auto eth0
iface etho inet dhcp

iface eth0 inet dhcp <line is repeated ??>
gateway 192.168.1.1


Does anyone have a suggestion???

---

### Post by Unka'George on 2007-11-23
Feedback on this problem.

I reinstalled from the live cd that I had burned.  This solved the problem.  Ubuntu reinstalled in the old linux partition then downloaded/installed the updates.  I also have full internet connection.

FWIW -- when running applications that indicate the transfer rate, it appears that Linux is about 20-30% *FASTER* than Windows 2k for the same types of files, mainly large videos via Miro.

Thanks for the email suggestions.

---

