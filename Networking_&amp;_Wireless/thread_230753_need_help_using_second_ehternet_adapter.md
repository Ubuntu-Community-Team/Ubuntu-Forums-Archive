---
title: "need help using second ehternet adapter"
date: 2006-08-06
forum: Networking &amp; Wireless
---

### Post by d.j.schroeder on 2006-08-06
I seem to be having a problem getting a second ethernet adapter to work.  eth0, onboard adapter, works fine connects to the internet fine.  eth1 is an Intel PRO/1000 GT pci adapter.  ifconfig returns:

eth0      Link encap:Ethernet  HWaddr 00:15:F2:25:0C:BF
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe25:cbf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1080774 (1.0 MiB)  TX bytes:222635 (217.4 KiB)
          Interrupt:217 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:0E:0C:B6:7A:CC
          inet6 addr: fe80::20e:cff:feb6:7acc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21067 (20.5 KiB)  TX bytes:6066 (5.9 KiB)
          Base address:0xa000 Memory:db020000-db040000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:820 (820.0 b)  TX bytes:820 (820.0 b)

and lsmod returns:

Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
lp                     11844  0
radeon                116000  1
drm                    73236  2 radeon
agpgart                34888  1 drm
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ac                      5252  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
sg                     37920  0
tsdev                   8000  0
ipv6                  265600  6
serio_raw               7300  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
psmouse                36228  0
i2c_nforce2             6912  0
floppy                 62148  0
analog                 12320  0
gameport               15496  1 analog
pcspkr                  2180  0
rtc                    13492  0
af_packet              22920  4
snd_intel8x0           33692  1
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mpu401              6728  0
snd_mpu401_uart         7808  1 snd_mpu401
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  1 snd_rawmidi
i2c_core               21904  2 i2c_acpi_ec,i2c_nforce2
snd_timer              25220  1 snd_pcm
snd                    55268  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
evdev                   9856  1
e1000                 118840  0
squashfs               44980  1
unionfs                89884  1
loop                   17288  2
nls_cp437               5888  1
isofs                  37688  1
ide_generic             1536  0
forcedeth              23428  0
ohci1394               35124  0
ieee1394              299832  1 ohci1394
ehci_hcd               32008  0
ohci_hcd               21892  0
usbcore               129668  3 ehci_hcd,ohci_hcd
ide_cd                 33028  1
cdrom                  38560  1 ide_cd
generic                 5124  0
sd_mod                 19984  2
amd74xx                15132  0 [permanent]
sata_nv                 9604  4
libata                 78992  1 sata_nv
scsi_mod              139496  3 sg,sd_mod,libata
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

e1000 is the driver on Intel's site for this adapter so it looks like it is using the right driver.

The problem is that the adapter doesn't actually seem to do anything.  It can't ping anything, won't return pings, won't acquire an IP address from any router I connect it to.  Even if I manually assign a number it won't accept or send pings.  The GUI networking tool claims that both eth0 and eth1 are active.

Any ideas, please really spell 'em out for me, I'm not too good with linux still.

Thanks in advance for your help

---

### Post by d.j.schroeder on 2006-08-07
Seriously no one?  Someone has to know how to get another adapter to work.

---

### Post by caffine_fizz on 2006-08-08
I'm only new to linux but i'm also trying to do the same thing, a nic for the net and another for home network. A gurus guide in this area would be a releif, fell as though i've looked through the whole forum.
If i do find anything anywhere i'll let you know about it and post a link.

---

### Post by ohgod on 2006-08-08
So I'm assuming you're setting up a router (eg, one nic connected to the local network & the other connected to the internet).  If so, this thread should help:

[http://ubuntuforums.org/showthread.php?t=119787&highlight=multiple+nic](http://ubuntuforums.org/showthread.php?t=119787&highlight=multiple+nic)

---

### Post by afilonov on 2006-08-08
Check:

1. If you have hardware link (lights on the NIC and on a router should be up).
2. It would help if you post part of the syslog right after you start eth1.
3. If you have a router log, it would help even more.

Strangely, you have some packets in your ifconfig output and no errors...

---

