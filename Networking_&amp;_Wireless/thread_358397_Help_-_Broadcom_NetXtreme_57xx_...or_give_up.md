---
title: "Help - Broadcom NetXtreme 57xx ...or give up?"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by tananaBrian on 2007-02-10
Hi All and thanks in advance for your kindly advice.

Question 1:  Which network cards will work in my new Dell Optiplex 745?

Question 2:  I'm about to give up on getting my Broadcom NetXtreme 57xx Gigabit Controller network interface card to work ...I might be close to an answer, but I'm no Linux administrator so I though that I'd ask here first just in case ...before I disable the card and buy one that's more naturally supported ...if that's the case?  I have a feeling that I'm missing one little key to the puzzle, but don't know what it is.  Here's what I tried and what system info I was able to get from lspci, ifconfig, lsmod, and the output from my `.../network restart`:

Thanks,
Brian


Tried:
=======
- Network Manager => No wired card shows up, but there I do have the card listed above and it works fine under XP (like right now.)  Judging by the location of the port on the back of the machine, it might be integral to the motherboard for all I know.  Haven't opened up my new box yet.
- modprobe tg3  (Broadcom claims tg3 is the right driver and that bcm5700 and bnx2 are going away)
- Added tg3 to /etc/modules to make sure tg3 is loaded at boot
- /etc/init.d/networking restart, but no lucky... output is below

System Analysis:
==============

From lspci:
----------------
0000:00:00.0 Host bridge: Intel Corporation: Unknown device 2990 (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation: Unknown device 2991 (rev 02)
0000:00:1a.0 USB Controller: Intel Corporation: Unknown device 2834 (rev 02)
0000:00:1a.1 USB Controller: Intel Corporation: Unknown device 2835 (rev 02)
0000:00:1a.7 USB Controller: Intel Corporation: Unknown device 283a (rev 02)
0000:00:1b.0 0403: Intel Corporation: Unknown device 284b (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation: Unknown device 283f (rev 02)
0000:00:1c.4 PCI bridge: Intel Corporation: Unknown device 2847 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation: Unknown device 2830 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation: Unknown device 2831 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation: Unknown device 2832 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation: Unknown device 2836 (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
0000:00:1f.0 ISA bridge: Intel Corporation: Unknown device 2810 (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation: Unknown device 2820 (rev 02)
0000:00:1f.3 SMBus: Intel Corporation: Unknown device 283e (rev 02)
0000:00:1f.5 IDE interface: Intel Corporation: Unknown device 2825 (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7183
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 71a3
0000:03:00.0 Ethernet controller: Broadcom Corporation: Unknown device 167a (rev 02)

From ifconfig:
-------------------
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19293 (18.8 KiB)  TX bytes:19293 (18.8 KiB)

From lsmod:
-------------------
Module                  Size  Used by
rfcomm                 40216  0 
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ipv6                  265856  8 
ppdev                   9220  0 
speedstep_centrino      8400  0 
cpufreq_userspace       4696  1 
cpufreq_stats           5636  0 
freq_table              4740  2 speedstep_centrino,cpufreq_stats
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
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
af_packet              22920  0 
nls_utf8                2176  2 
ntfs                  103536  2 
nls_iso8859_1           4224  2 
nls_cp437               5888  2 
vfat                   13440  2 
fat                    53020  1 vfat
dm_mod                 58936  1 
md_mod                 72532  0 
tg3                   101764  0 
lp                     11844  0 
tsdev                   8000  0 
usbhid                 39904  1 
psmouse                36100  0 
serio_raw               7300  0 
floppy                 62148  0 
pcspkr                  2180  0 
parport_pc             35780  1 
parport                36296  3 ppdev,lp,parport_pc
rtc                    13492  0 
snd_hda_intel          18964  1 
snd_hda_codec         157616  1 snd_hda_intel
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
hw_random               5652  0 
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
shpchp                 45632  0 
pci_hotplug            29236  1 shpchp
evdev                   9856  1 
sr_mod                 16932  0 
cdrom                  38560  1 sr_mod
sg                     37920  0 
ext3                  135816  1 
jbd                    58772  1 ext3
ide_generic             1536  0 
ehci_hcd               34184  0 
uhci_hcd               33808  0 
usbcore               130820  5 usbhid,ehci_hcd,uhci_hcd
sd_mod                 19984  8 
generic                 5124  0 
ata_piix               11012  12 
libata                 78992  1 ata_piix
scsi_mod              139496  4 sr_mod,sg,sd_mod,libata
thermal                13576  0 
processor              23360  2 speedstep_centrino,thermal
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

From .../network restart:
-----------------------------------
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

(Plus error messages stating that eth0, eth1, etc failed to start)

---

### Post by tananaBrian on 2007-02-10
PS: I'm running Dapper Drake, latest upgrade from last weekend so it's all up to speed at this point ...except my Internet access that is.

---

### Post by tananaBrian on 2007-02-11
TTT

Helppp!!!  Certainly somebody can help?  What does the output listed in the first post mean?  What am I doing wrong?  Should I give up?

Thx,
Brian

---

### Post by pkarjala on 2007-04-26
Brian-

You may want to try downloading the specific driver for this NIC from Broadcom's website.  It's located at [http://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php]("http://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php").  This will require you to have a second computer to download the driver onto, then transfer it to your Ubuntu box via a USB keychain drive or burn to a CD.

I have about a dozen Optiplex 745 (SFF) sitting here in my office, so I'll snag one to test an install on and see if I can get you more detailed instructions on installing the driver.  Can you let me know which version of Ubuntu you're currently running?

---

