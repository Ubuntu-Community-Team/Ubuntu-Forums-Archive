---
title: "Connecting to a WAN via terminal"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by OldGregory on 2008-11-26
Simply, I just want to be able to connect to an unencrypted wireless network via terminal commands.  I'm not worried about WPA or WEP or anything complicated.

I've tried 
```
sudo ifconfig [interface] down
sudo dhclient -r [interface]
sudo ifconfig [interface] up
sudo iwconfig [interface] essid “ESSID_IN_QUOTES”
sudo iwconfig [interface] mode Managed
sudo dhclient [interface]
```

Which successfully disconnects me, and brings the wireless card back up, but connecting doesn't work.

Is there a way to interface with network-manager via the terminal?

---

### Post by OldGregory on 2008-11-27
Bump.

---

### Post by kevdog on 2008-11-27
Can you post the following:

lspci -nnm
lshw -C network
iwlist <interface> scan

---

### Post by OldGregory on 2008-11-27
This isn't a hardware problem, my wireless works fine, I just want to be able to connect to a wireless network through a script or whatever (python actually, but that's not the point).

Anywhoo:
```
00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "Mobile PM965/GM965/GL960 Memory Controller Hub [2a00]" -r0c "Hewlett-Packard Company [103c]" "Device [30cd]"
00:01.0 "PCI bridge [0604]" "Intel Corporation [8086]" "Mobile PM965/GM965/GL960 PCI Express Root Port [2a01]" -r0c "" ""
00:1a.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB UHCI Controller #4 [2834]" -r03 "Hewlett-Packard Company [103c]" "Device [30cd]"
00:1a.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB UHCI Controller #5 [2835]" -r03 "Hewlett-Packard Company [103c]" "Device [30cd]"
00:1a.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB2 EHCI Controller #2 [283a]" -r03 -p20 "Hewlett-Packard Company [103c]" "Device [30cd]"
00:1b.0 "Audio device [0403]" "Intel Corporation [8086]" "82801H (ICH8 Family) HD Audio Controller [284b]" -r03 "Hewlett-Packard Company [103c]" "Device [30cd]"
00:1c.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801H (ICH8 Family) PCI Express Port 1 [283f]" -r03 "" ""
00:1c.1 "PCI bridge [0604]" "Intel Corporation [8086]" "82801H (ICH8 Family) PCI Express Port 2 [2841]" -r03 "" ""
00:1c.2 "PCI bridge [0604]" "Intel Corporation [8086]" "82801H (ICH8 Family) PCI Express Port 3 [2843]" -r03 "" ""
00:1c.3 "PCI bridge [0604]" "Intel Corporation [8086]" "82801H (ICH8 Family) PCI Express Port 4 [2845]" -r03 "" ""
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB UHCI Controller #1 [2830]" -r03 "Hewlett-Packard Company [103c]" "Device [30cd]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB UHCI Controller #2 [2831]" -r03 "Hewlett-Packard Company [103c]" "Device [30cd]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB UHCI Controller #3 [2832]" -r03 "Hewlett-Packard Company [103c]" "Device [30cd]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB2 EHCI Controller #1 [2836]" -r03 -p20 "Hewlett-Packard Company [103c]" "Device [30cd]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 Mobile PCI Bridge [2448]" -rf3 -p01 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "82801HEM (ICH8M) LPC Interface Controller [2815]" -r03 "Hewlett-Packard Company [103c]" "Device [30cd]"
00:1f.1 "IDE interface [0101]" "Intel Corporation [8086]" "82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [2850]" -r03 -p8a "Hewlett-Packard Company [103c]" "Device [30cd]"
00:1f.2 "SATA controller [0106]" "Intel Corporation [8086]" "82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [2829]" -r03 -p01 "Hewlett-Packard Company [103c]" "Device [30cd]"
00:1f.3 "SMBus [0c05]" "Intel Corporation [8086]" "82801H (ICH8 Family) SMBus Controller [283e]" -r03 "Hewlett-Packard Company [103c]" "Device [30cd]"
01:00.0 "VGA compatible controller [0300]" "nVidia Corporation [10de]" "GeForce 8400M GS [0427]" -ra1 "Hewlett-Packard Company [103c]" "Device [30cd]"
05:00.0 "Ethernet controller [0200]" "Marvell Technology Group Ltd. [11ab]" "88E8039 PCI-E Fast Ethernet Controller [4353]" -r14 "Hewlett-Packard Company [103c]" "Device [30cd]"
07:00.0 "Network controller [0280]" "Intel Corporation [8086]" "PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [4229]" -r61 "Intel Corporation [8086]" "Device [1100]"
08:09.0 "FireWire (IEEE 1394) [0c00]" "Ricoh Co Ltd [1180]" "R5C832 IEEE 1394 Controller [0832]" -r05 -p10 "Hewlett-Packard Company [103c]" "Device [30cd]"
08:09.1 "SD Host controller [0805]" "Ricoh Co Ltd [1180]" "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [0822]" -r22 "Hewlett-Packard Company [103c]" "Device [30cd]"
08:09.2 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C843 MMC Host Controller [0843]" -r12 "Hewlett-Packard Company [103c]" "Device [30cd]"
08:09.3 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C592 Memory Stick Bus Host Adapter [0592]" -r12 "Hewlett-Packard Company [103c]" "Device [30cd]"
08:09.4 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "xD-Picture Card Controller [0852]" -rff -pff "" ""

  *-network
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:53:2d:97
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:48:08:11
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.141 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8e:ca:35:99:46:51
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
       
wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:DA:ED:7A
                    ESSID:"erwin.net"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=87/100  Signal level:-58 dBm  Noise level=-93 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000001ef9524183
                    Extra: Last beacon: 4ms ago

```

I realize the only access point visible at the moment is encrypted, by the way.

---

### Post by OldGregory on 2008-11-28
Ba-Bump.

---

### Post by Ayuthia on 2008-11-28
Do you have network-manager turned off to see if it will connect?  I am just curious if network-manager is fighting with you.  I can't quite remember how network-manager works, but if you bring turn on your card via ifconfig, would network-manager try to connect to it?  If you have it set up to connect via WEP/WPA and you are trying to connect without encryption, I am not for sure how it would turn out.

The commands that you are using should work for a typical unencrypted network.

---

### Post by gnusci on 2008-11-28
Here the way I do this:

```

sudo ifconfig wlan0 up
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 channel 2
sudo iwconfig wlan0 essid "WLAN"
sudo iwconfig wlan0 mode managed 
sudo ifconfig wlan0 up
```

You can also write these command in the **/etc/network/interfaces** like this:

```

iface wlan0 inet dhcp
        pre-up ifconfig wlan0 up
        pre-up ifconfig wlan0 down
        pre-up ifconfig wlan0 up
        pre-up iwconfig wlan0 channel 2
        pre-up iwconfig wlan0 essid "WLAN"
        pre-up iwconfig wlan0 mode managed 
        pre-up ifconfig wlan0 up
```

and then just run:

** sudo /etc/init.d/networking restart**

---

### Post by kevdog on 2008-11-28
Wondering if you could try another scheme other than WPA2.  I'm having problems with WPA2 myself (as are some others depending on the driver of the card).  I don't have an intel chipset myself, but the card you are using has many threads littered with problems.

Also your command set to connect to any encrypted network is totally wrong -- particularly wpa.  You need to specify group, cipher schemes, proto, along with passing the password.

---

### Post by liquid.silver on 2008-11-28
> **kevdog said:**
> Also your command set to connect to any encrypted network is totally wrong -- particularly wpa.  You need to specify group, cipher schemes, proto, along with passing the password.

He did clearly say unencrypted...

I've also tried to connect to unencrypted wireless with a terminal and never managed, would be nice if i could...

You sure channel 2 is the right one btw?

---

### Post by Ayuthia on 2008-11-28
> **liquid.silver said:**
> He did clearly say unencrypted...

I've also tried to connect to unencrypted wireless with a terminal and never managed, would be nice if i could...

You sure channel 2 is the right one btw?

The information that the original poster shows that the site that they are trying to connect is currently set to WPA2.  That is most likely why kevdog made the suggestion.  As for the channel 2, that was an example another poster made.  The original poster has theirs set at channel 6.

However if you are connecting from the Terminal, it is not always necessary to assign the channel.  I almost always connect from the Terminal and have not yet assigned a channel.

---

### Post by liquid.silver on 2008-11-28
> **Ayuthia said:**
> The information that the original poster shows that the site that they are trying to connect is currently set to WPA2.  That is most likely why kevdog made the suggestion.  As for the channel 2, that was an example another poster made.  The original poster has theirs set at channel 6.

However if you are connecting from the Terminal, it is not always necessary to assign the channel.  I almost always connect from the Terminal and have not yet assigned a channel.

Maybe i'm reading wrong, but i read this:
> **OldGregory said:**
> Simply, I just want to be able to connect to an unencrypted wireless network via terminal commands.  I'm not worried about WPA or WEP or anything complicated.

About channel, sorry that was a mistake on my part.

---

### Post by Ayuthia on 2008-11-28
```
wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:DA:ED:7A
                    ESSID:"erwin.net"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=87/100  Signal level:-58 dBm  Noise level=-93 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000001ef9524183
                    Extra: Last beacon: 4ms ago

```[Post #4]("http://ubuntuforums.org/showpost.php?p=6264115&postcount=4") shows that the site is encrypted with WPA2 and we just want to make sure that WPA2 is turned off or else the original poster is not going to be able to connect since they are trying to connect without encryption.

---

### Post by OldGregory on 2008-11-28
Ok, I disabled encryption on my router so I can use it for testing. (I wasn't trying to connect to it in the first place)

Here is the new result for "sudo iwlist wlan0 scan":```
wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:DA:ED:7A
                    ESSID:"erwin.net"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=78/100  Signal level:-56 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000d2821acc4
                    Extra: Last beacon: 1604ms ago
```
I then killed the nm-applet process through the system monitor and executed the following commands:```
gerwin@gerwin-laptop-ubuntu:~$ sudo ifconfig wlan0 down

gerwin@gerwin-laptop-ubuntu:~$ 
gerwin@gerwin-laptop-ubuntu:~$ sudo dhclient -r wlan0 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3b:48:08:11
Sending on   LPF/wlan0/00:1f:3b:48:08:11
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
gerwin@gerwin-laptop-ubuntu:~$ sudo ifconfig wlan0 up
gerwin@gerwin-laptop-ubuntu:~$ sudo iwconfig wlan0 essid "erwin.net"
gerwin@gerwin-laptop-ubuntu:~$ sudo iwconfig wlan0 mode Managed
gerwin@gerwin-laptop-ubuntu:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3b:48:08:11
Sending on   LPF/wlan0/00:1f:3b:48:08:11
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by gnusci on 2008-11-28
Please post the output of the following commands:

```
$ lsmod
$ dmesg
$ iwlist scan wlan0
```

---

### Post by OldGregory on 2008-11-28
I hate to sound stubborn, but this isn't a hardware problem.  I can connect perfectly to an access point through the network manager, encrypted or not.

Anyway, as you wish:```
Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  4 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_ondemand       14988  1 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
pci_slot               12552  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
uvcvideo               62728  0 
compat_ioctl32          9344  1 uvcvideo
iwlagn                 99588  0 
iwlcore                92740  1 iwlagn
videodev               41344  1 uvcvideo
snd_hda_intel         381488  2 
sdhci_pci              15360  0 
rfkill                 17176  2 iwlcore
snd_pcm_oss            46848  0 
led_class              12164  1 iwlcore
joydev                 18368  0 
snd_mixer_oss          22784  1 snd_pcm_oss
v4l1_compat            22404  2 uvcvideo,videodev
sdhci                  23940  1 sdhci_pci
evdev                  17696  16 
mac80211              216820  2 iwlagn,iwlcore
serio_raw              13444  0 
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
iTCO_wdt               18596  0 
cfg80211               32392  3 iwlagn,iwlcore,mac80211
pcspkr                 10624  0 
snd_seq_dummy          10884  0 
psmouse                45200  0 
iTCO_vendor_support    11652  1 iTCO_wdt
mmc_core               58268  1 sdhci
ricoh_mmc              11904  0 
nvidia               6900560  38 
snd_seq_oss            38528  0 
i2c_core               31892  1 nvidia
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
battery                18436  0 
snd_timer              29960  2 snd_pcm,snd_seq
ac                     12292  0 
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              33724  0 
video                  25104  6 
soundcore              15328  1 snd
agpgart                42184  2 nvidia,intel_agp
output                 11008  1 video
wmi                    14504  0 
button                 14224  0 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  0 
ata_generic            12932  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ohci1394               37936  0 
pata_acpi              12160  0 
ahci                   37132  2 
ieee1394               96324  2 sbp2,ohci1394
libata                177312  4 ata_piix,ata_generic,pata_acpi,ahci
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
sky2                   53380  0 
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  5 uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fec0000 (usable)
[    0.000000]  BIOS-e820: 000000007fec0000 - 000000007fedf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fedf000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x7fec0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 37822000 - 37fefec8
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F7E20, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 7FED008F, 0074 (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP 7FEDBC3A, 00F4 (r3 INTEL  CRESTLNE  6040000 ALAN        1)
[    0.000000] ACPI: DSDT 7FED0F6D, AC59 (r2 INTEL  CRESTLNE  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 7FEDEFC0, 0040
[    0.000000] ACPI: HPET 7FEDBD2E, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 7FEDBD66, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA 7FEDBDA2, 0032 (r1 Intel   CRESTLN  6040000          5A52)
[    0.000000] ACPI: TMOR 7FEDBDD4, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: SLIC 7FEDBDFA, 0176 (r1 HPQOEM SLIC-MPC  6040000 HPQ         1)
[    0.000000] ACPI: APIC 7FEDBF70, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 7FEDBFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 7FED0C90, 02DD (r1 SataRe SataAhci     1000 INTL 20061109)
[    0.000000] ACPI: SSDT 7FED0103, 04E6 (r1  PmRef    CpuPm     3000 INTL 20061109)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [0037822000 - 0037fefec8]          RAMDISK ==> [0037822000 - 0037fefec8]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f7e50] 000f7e50
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007fec0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fec0
[    0.000000] On node 0 totalpages: 523871
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 292002 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519265
[    0.000000] Kernel command line: root=UUID=4153e288-2596-46a9-92b9-07039824e844 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2393.967 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2062308k/2095872k available (2572k kernel code, 32252k reserved, 1160k data, 424k init, 1178368k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc03832aa - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03832aa   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.93 BogoMIPS (lpj=9575868)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017563] ACPI: Core revision 20080609
[    0.021177] ACPI: Checking initramfs for custom DSDT
[    0.284231] ENABLING IO-APIC IRQs
[    0.284417] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.326426] CPU0: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz stepping 06
[    0.328020] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4787.94 BogoMIPS (lpj=9575880)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.412643] CPU1: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz stepping 06
[    0.412658] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.416044] Brought up 2 CPUs
[    0.416047] Total of 2 processors activated (9575.87 BogoMIPS).
[    0.416066] CPU0 attaching sched-domain:
[    0.416068]  domain 0: span 0-1 level MC
[    0.416070]   groups: 0 1
[    0.416075] CPU1 attaching sched-domain:
[    0.416077]  domain 0: span 0-1 level MC
[    0.416079]   groups: 1 0
[    0.416145] net_namespace: 840 bytes
[    0.416145] Booting paravirtualized kernel on bare hardware
[    0.416242] Time: 15:23:44  Date: 11/28/08
[    0.416264] NET: Registered protocol family 16
[    0.416280] EISA bus registered
[    0.416280] ACPI: bus type pci registered
[    0.416280] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.416280] PCI: MCFG area at e0000000 reserved in E820
[    0.416280] PCI: Using MMCONFIG for extended config space
[    0.416280] PCI: Using configuration type 1 for base access
[    0.416918] ACPI: EC: Look up EC in DSDT
[    0.422788] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    0.426474] ACPI: Interpreter enabled
[    0.426476] ACPI: (supports S0 S3 S4 S5)
[    0.426483] ACPI: Using IOAPIC for interrupt routing
[    0.426483] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.468272] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.468272] ACPI: EC: driver started in interrupt mode
[    0.468272] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.472093] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.472096] pci 0000:00:01.0: PME# disabled
[    0.472177] PCI: 0000:00:1a.0 reg 20 io port: [1840, 185f]
[    0.472239] PCI: 0000:00:1a.1 reg 20 io port: [1860, 187f]
[    0.472309] PCI: 0000:00:1a.7 reg 10 32bit mmio: [f4505c00, f4505fff]
[    0.472368] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.472373] pci 0000:00:1a.7: PME# disabled
[    0.472419] PCI: 0000:00:1b.0 reg 10 64bit mmio: [f4500000, f4503fff]
[    0.472472] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.472476] pci 0000:00:1b.0: PME# disabled
[    0.472546] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.472550] pci 0000:00:1c.0: PME# disabled
[    0.472619] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.472623] pci 0000:00:1c.1: PME# disabled
[    0.472693] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.472697] pci 0000:00:1c.2: PME# disabled
[    0.472766] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.472771] pci 0000:00:1c.3: PME# disabled
[    0.472820] PCI: 0000:00:1d.0 reg 20 io port: [1880, 189f]
[    0.472882] PCI: 0000:00:1d.1 reg 20 io port: [18a0, 18bf]
[    0.472945] PCI: 0000:00:1d.2 reg 20 io port: [18c0, 18df]
[    0.473015] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f4506000, f45063ff]
[    0.473073] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.473078] pci 0000:00:1d.7: PME# disabled
[    0.473228] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.473232] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.473260] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.473268] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.473276] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.473284] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.473291] PCI: 0000:00:1f.1 reg 20 io port: [1830, 183f]
[    0.473363] PCI: 0000:00:1f.2 reg 10 io port: [1c10, 1c17]
[    0.473371] PCI: 0000:00:1f.2 reg 14 io port: [1c04, 1c07]
[    0.473378] PCI: 0000:00:1f.2 reg 18 io port: [1c08, 1c0f]
[    0.473386] PCI: 0000:00:1f.2 reg 1c io port: [1c00, 1c03]
[    0.473394] PCI: 0000:00:1f.2 reg 20 io port: [18e0, 18ff]
[    0.473401] PCI: 0000:00:1f.2 reg 24 32bit mmio: [f4505000, f45057ff]
[    0.473433] pci 0000:00:1f.2: PME# supported from D3hot
[    0.473438] pci 0000:00:1f.2: PME# disabled
[    0.473458] PCI: 0000:00:1f.3 reg 10 32bit mmio: [0, ff]
[    0.473483] PCI: 0000:00:1f.3 reg 20 io port: [1c20, 1c3f]
[    0.473540] PCI: 0000:01:00.0 reg 10 32bit mmio: [ce000000, ceffffff]
[    0.473546] PCI: 0000:01:00.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    0.473562] PCI: 0000:01:00.0 reg 1c 64bit mmio: [cc000000, cdffffff]
[    0.473568] PCI: 0000:01:00.0 reg 24 io port: [2000, 207f]
[    0.473574] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.473640] PCI: bridge 0000:00:01.0 io port: [2000, 2fff]
[    0.473643] PCI: bridge 0000:00:01.0 32bit mmio: [cc000000, ceffffff]
[    0.473647] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]
[    0.473707] PCI: bridge 0000:00:1c.0 io port: [3000, 3fff]
[    0.473712] PCI: bridge 0000:00:1c.0 32bit mmio: [f2000000, f3ffffff]
[    0.473720] PCI: bridge 0000:00:1c.0 64bit mmio pref: [f0000000, f1ffffff]
[    0.473800] PCI: 0000:05:00.0 reg 10 64bit mmio: [f4000000, f4003fff]
[    0.473811] PCI: 0000:05:00.0 reg 18 io port: [4000, 40ff]
[    0.473871] pci 0000:05:00.0: supports D1
[    0.473872] pci 0000:05:00.0: supports D2
[    0.473874] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.473880] pci 0000:05:00.0: PME# disabled
[    0.473932] PCI: bridge 0000:00:1c.1 io port: [4000, 4fff]
[    0.473937] PCI: bridge 0000:00:1c.1 32bit mmio: [f4000000, f40fffff]
[    0.474102] PCI: 0000:07:00.0 reg 10 64bit mmio: [f4100000, f4101fff]
[    0.474201] pci 0000:07:00.0: PME# supported from D0 D3hot D3cold
[    0.474209] pci 0000:07:00.0: PME# disabled
[    0.474264] PCI: bridge 0000:00:1c.3 32bit mmio: [f4100000, f41fffff]
[    0.474327] PCI: 0000:08:09.0 reg 10 32bit mmio: [f4200000, f42007ff]
[    0.474382] pci 0000:08:09.0: supports D1
[    0.474383] pci 0000:08:09.0: supports D2
[    0.474384] pci 0000:08:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.474389] pci 0000:08:09.0: PME# disabled
[    0.474424] PCI: 0000:08:09.1 reg 10 32bit mmio: [f4200800, f42008ff]
[    0.474479] pci 0000:08:09.1: supports D1
[    0.474480] pci 0000:08:09.1: supports D2
[    0.474482] pci 0000:08:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.474487] pci 0000:08:09.1: PME# disabled
[    0.474521] PCI: 0000:08:09.2 reg 10 32bit mmio: [f4200c00, f4200cff]
[    0.474576] pci 0000:08:09.2: supports D1
[    0.474577] pci 0000:08:09.2: supports D2
[    0.474579] pci 0000:08:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.474584] pci 0000:08:09.2: PME# disabled
[    0.474619] PCI: 0000:08:09.3 reg 10 32bit mmio: [f4201000, f42010ff]
[    0.474674] pci 0000:08:09.3: supports D1
[    0.474675] pci 0000:08:09.3: supports D2
[    0.474677] pci 0000:08:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.474681] pci 0000:08:09.3: PME# disabled
[    0.474716] PCI: 0000:08:09.4 reg 10 32bit mmio: [f4201400, f42014ff]
[    0.474771] pci 0000:08:09.4: supports D1
[    0.474772] pci 0000:08:09.4: supports D2
[    0.474773] pci 0000:08:09.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.474778] pci 0000:08:09.4: PME# disabled
[    0.474824] pci 0000:00:1e.0: transparent bridge
[    0.474832] PCI: bridge 0000:00:1e.0 32bit mmio: [f4200000, f42fffff]
[    0.474873] bus 00 -> node 0
[    0.474879] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.475274] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.475415] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.475547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.475680] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.475812] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.475956] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.476422] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.476422] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.476422] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.480081] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.480192] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.480306] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.480417] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.480529] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.480596] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.480596] pnp: PnP ACPI init
[    0.480596] ACPI: bus type pnp registered
[    0.484236] pnp: PnP ACPI: found 10 devices
[    0.484236] ACPI: ACPI bus type pnp unregistered
[    0.484236] PnPBIOS: Disabled by ACPI PNP
[    0.484236] PCI: Using ACPI for IRQ routing
[    0.484236] NET: Registered protocol family 8
[    0.484236] NET: Registered protocol family 20
[    0.484236] NetLabel: Initializing
[    0.484236] NetLabel:  domain hash size = 128
[    0.484236] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.484236] NetLabel:  unlabeled traffic allowed by default
[    0.484236] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.484236] hpet0: 3 64-bit timers, 14318180 Hz
[    0.485452] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.485455]    actual entries 65620
[    0.485524] AppArmor: AppArmor Filesystem Enabled
[    0.485551] ACPI: RTC can wake from S4
[    0.485562] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.485562] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[    0.485562] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    0.485562] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    0.485562] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.485562] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    0.485562] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    0.485562] system 00:06: iomem range 0xfed00000-0xfed003ff could not be reserved
[    0.485562] system 00:08: ioport range 0x680-0x69f has been reserved
[    0.485562] system 00:08: ioport range 0x800-0x80f has been reserved
[    0.485562] system 00:08: ioport range 0x1000-0x107f has been reserved
[    0.485562] system 00:08: ioport range 0x1180-0x11bf has been reserved
[    0.485562] system 00:08: ioport range 0xfe00-0xfe00 has been reserved
[    0.500681] Switched to high resolution mode on CPU 1
[    0.504032] Switched to high resolution mode on CPU 0
[    0.522161] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
[    0.522163] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.522165] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.522169] pci 0000:00:01.0:   MEM window: 0xcc000000-0xceffffff
[    0.522172] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.522176] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.522179] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.522185] pci 0000:00:1c.0:   MEM window: 0xf2000000-0xf3ffffff
[    0.522190] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.522198] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:05
[    0.522201] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.522207] pci 0000:00:1c.1:   MEM window: 0xf4000000-0xf40fffff
[    0.522211] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.522218] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
[    0.522220] pci 0000:00:1c.2:   IO window: disabled
[    0.522225] pci 0000:00:1c.2:   MEM window: disabled
[    0.522229] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.522236] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:07
[    0.522238] pci 0000:00:1c.3:   IO window: disabled
[    0.522244] pci 0000:00:1c.3:   MEM window: 0xf4100000-0xf41fffff
[    0.522248] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.522255] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
[    0.522257] pci 0000:00:1e.0:   IO window: disabled
[    0.522263] pci 0000:00:1e.0:   MEM window: 0xf4200000-0xf42fffff
[    0.522268] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.522281] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.522284] pci 0000:00:01.0: setting latency timer to 64
[    0.522293] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.522297] pci 0000:00:1c.0: setting latency timer to 64
[    0.522305] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.522309] pci 0000:00:1c.1: setting latency timer to 64
[    0.522318] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.522322] pci 0000:00:1c.2: setting latency timer to 64
[    0.522331] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.522335] pci 0000:00:1c.3: setting latency timer to 64
[    0.522343] pci 0000:00:1e.0: setting latency timer to 64
[    0.522346] bus: 00 index 0 io port: [0, ffff]
[    0.522348] bus: 00 index 1 mmio: [0, ffffffff]
[    0.522350] bus: 01 index 0 io port: [2000, 2fff]
[    0.522351] bus: 01 index 1 mmio: [cc000000, ceffffff]
[    0.522353] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.522355] bus: 01 index 3 mmio: [0, 0]
[    0.522356] bus: 02 index 0 io port: [3000, 3fff]
[    0.522358] bus: 02 index 1 mmio: [f2000000, f3ffffff]
[    0.522360] bus: 02 index 2 mmio: [f0000000, f1ffffff]
[    0.522361] bus: 02 index 3 mmio: [0, 0]
[    0.522363] bus: 05 index 0 io port: [4000, 4fff]
[    0.522364] bus: 05 index 1 mmio: [f4000000, f40fffff]
[    0.522366] bus: 05 index 2 mmio: [0, 0]
[    0.522368] bus: 05 index 3 mmio: [0, 0]
[    0.522369] bus: 06 index 0 mmio: [0, 0]
[    0.522370] bus: 06 index 1 mmio: [0, 0]
[    0.522372] bus: 06 index 2 mmio: [0, 0]
[    0.522373] bus: 06 index 3 mmio: [0, 0]
[    0.522375] bus: 07 index 0 mmio: [0, 0]
[    0.522376] bus: 07 index 1 mmio: [f4100000, f41fffff]
[    0.522378] bus: 07 index 2 mmio: [0, 0]
[    0.522379] bus: 07 index 3 mmio: [0, 0]
[    0.522381] bus: 08 index 0 mmio: [0, 0]
[    0.522382] bus: 08 index 1 mmio: [f4200000, f42fffff]
[    0.522384] bus: 08 index 2 mmio: [0, 0]
[    0.522385] bus: 08 index 3 io port: [0, ffff]
[    0.522387] bus: 08 index 4 mmio: [0, ffffffff]
[    0.522393] NET: Registered protocol family 2
[    0.533039] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.533224] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.533517] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.533668] TCP: Hash tables configured (established 131072 bind 65536)
[    0.533671] TCP reno registered
[    0.537047] NET: Registered protocol family 1
[    0.537131] checking if image is initramfs... it is
[    1.110602] Freeing initrd memory: 7991k freed
[    1.110775] Simple Boot Flag at 0x36 set to 0x1
[    1.111575] audit: initializing netlink socket (disabled)
[    1.111590] type=2000 audit(1227885824.109:1): initialized
[    1.116596] highmem bounce pool size: 64 pages
[    1.116601] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.118418] VFS: Disk quotas dquot_6.5.1
[    1.118492] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.118582] msgmni has been set to 1743
[    1.118679] io scheduler noop registered
[    1.118681] io scheduler anticipatory registered
[    1.118683] io scheduler deadline registered
[    1.118693] io scheduler cfq registered (default)
[    1.118837] pci 0000:01:00.0: Boot video device
[    1.118937] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.118969] pcieport-driver 0000:00:01.0: found MSI capability
[    1.118998] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.119035] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.119066] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.119141] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.119189] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.119235] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.119268] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.119297] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.119397] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.119444] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.119490] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.119521] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.119552] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.119651] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.119698] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.119744] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.119776] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.119808] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.119906] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.119954] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.120000] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.120032] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.120065] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.120354] isapnp: Scanning for PnP cards...
[    1.474281] isapnp: No Plug & Play device found
[    1.500662] hpet_resources: 0xfed00000 is busy
[    1.500712] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.502469] brd: module loaded
[    1.502523] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.502618] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.502951] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.503024] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.503028] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.503031] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.503033] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.503035] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.503319] mice: PS/2 mouse device common for all mice
[    1.503420] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    1.503448] rtc0: alarms up to one month, y3k, hpet irqs
[    1.503546] EISA: Probing bus 0 at eisa.0
[    1.503552] Cannot allocate resource for EISA slot 1
[    1.503555] Cannot allocate resource for EISA slot 2
[    1.503556] Cannot allocate resource for EISA slot 3
[    1.503558] Cannot allocate resource for EISA slot 4
[    1.503574] EISA: Detected 0 cards.
[    1.503577] cpuidle: using governor ladder
[    1.503579] cpuidle: using governor menu
[    1.503991] TCP cubic registered
[    1.504012] Using IPI No-Shortcut mode
[    1.504153] registered taskstats version 1
[    1.504269]   Magic number: 0:549:387
[    1.504344] rtc_cmos 00:09: setting system clock to 2008-11-28 15:23:45 UTC (1227885825)
[    1.504346] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.504348] EDD information not available.
[    1.504567] Freeing unused kernel memory: 424k freed
[    1.504597] Write protecting the kernel text: 2576k
[    1.504619] Write protecting the kernel read-only data: 936k
[    1.506425] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.659225] fuse init (API version 7.9)
[    1.821420] ACPI: SSDT 7FED090C, 02BC (r1  PmRef  Cpu0Ist     3000 INTL 20061109)
[    1.821765] ACPI: SSDT 7FED05E9, 029E (r1  PmRef  Cpu0Cst     3001 INTL 20061109)
[    1.839204] Monitor-Mwait will be used to enter C-1 state
[    1.839208] Monitor-Mwait will be used to enter C-2 state
[    1.839210] Monitor-Mwait will be used to enter C-3 state
[    1.853119] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.853165] processor ACPI0007:00: registered as cooling_device0
[    1.853467] ACPI: SSDT 7FED0BC8, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20061109)
[    1.853785] ACPI: SSDT 7FED0887, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20061109)
[    1.854517] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.854555] processor ACPI0007:01: registered as cooling_device1
[    1.857150] Marking TSC unstable due to TSC halts in idle
[    1.865357] thermal LNXTHERM:01: registered as thermal_zone0
[    1.872734] ACPI: Thermal Zone [TZS0] (31 C)
[    1.876029] thermal LNXTHERM:02: registered as thermal_zone1
[    1.878419] ACPI: Thermal Zone [TZS1] (31 C)
[    2.099141] usbcore: registered new interface driver usbfs
[    2.099160] usbcore: registered new interface driver hub
[    2.105771] usbcore: registered new device driver usb
[    2.114085] USB Universal Host Controller Interface driver v3.0
[    2.114128] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.114138] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.114143] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.114177] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.114220] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001840
[    2.114345] usb usb1: configuration #1 chosen from 1 choice
[    2.114367] hub 1-0:1.0: USB hub found
[    2.114372] hub 1-0:1.0: 2 ports detected
[    2.217254] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.217263] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.217267] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.217289] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.217324] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001860
[    2.217400] usb usb2: configuration #1 chosen from 1 choice
[    2.217423] hub 2-0:1.0: USB hub found
[    2.217428] hub 2-0:1.0: 2 ports detected
[    2.321280] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.321294] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.321298] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.321324] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[    2.325233] ehci_hcd 0000:00:1a.7: debug port 1
[    2.325240] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.325253] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf4505c00
[    2.343279] No dock devices found.
[    2.354628] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.354751] usb usb3: configuration #1 chosen from 1 choice
[    2.354774] hub 3-0:1.0: USB hub found
[    2.354781] hub 3-0:1.0: 4 ports detected
[    2.385933] SCSI subsystem initialized
[    2.421689] libata version 3.00 loaded.
[    2.467850] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.467860] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.467864] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.467885] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    2.467921] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
[    2.468031] usb usb4: configuration #1 chosen from 1 choice
[    2.468054] hub 4-0:1.0: USB hub found
[    2.468060] hub 4-0:1.0: 2 ports detected
[    2.572292] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.572304] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.572308] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.572329] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[    2.572366] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
[    2.572446] usb usb5: configuration #1 chosen from 1 choice
[    2.572468] hub 5-0:1.0: USB hub found
[    2.572473] hub 5-0:1.0: 2 ports detected
[    2.776512] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.776523] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.776527] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.776548] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[    2.776577] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
[    2.776657] usb usb6: configuration #1 chosen from 1 choice
[    2.776679] hub 6-0:1.0: USB hub found
[    2.776685] hub 6-0:1.0: 2 ports detected
[    2.880608] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.880623] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.880626] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.880643] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    2.884557] ehci_hcd 0000:00:1d.7: debug port 1
[    2.884563] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.884568] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf4506000
[    2.896254] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.896385] usb usb7: configuration #1 chosen from 1 choice
[    2.896405] hub 7-0:1.0: USB hub found
[    2.896410] hub 7-0:1.0: 6 ports detected
[    3.000240] Clocksource tsc unstable (delta = -316406201 ns)
[    3.104587] sky2 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.104596] sky2 0000:05:00.0: setting latency timer to 64
[    3.104617] sky2 0000:05:00.0: v1.22 addr 0xf4000000 irq 17 Yukon-2 FE rev 3
[    3.105001] sky2 eth0: addr 00:1d:72:53:2d:97
[    3.105527] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.105557] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    3.105569] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    3.105590] ahci 0000:00:1f.2: version 3.0
[    3.105600] ahci 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    3.105686] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    3.105689] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    3.105694] ahci 0000:00:1f.2: setting latency timer to 64
[    3.106590] scsi0 : ahci
[    3.106713] scsi1 : ahci
[    3.106801] scsi2 : ahci
[    3.106889] ata1: SATA max UDMA/133 abar m2048@0xf4505000 port 0xf4505100 irq 217
[    3.106892] ata2: SATA max UDMA/133 abar m2048@0xf4505000 port 0xf4505180 irq 217
[    3.106896] ata3: SATA max UDMA/133 abar m2048@0xf4505000 port 0xf4505200 irq 217
[    3.272237] usb 7-5: new high speed USB device using ehci_hcd and address 3
[    3.417441] usb 7-5: configuration #1 chosen from 1 choice
[    3.428044] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.428999] ata1.00: _GTF unexpected object type 0x1
[    3.429004] ata1.00: ATA-7: ST9120822AS, 3.BHE, max UDMA/100
[    3.429006] ata1.00: 234441648 sectors, multi 16: LBA48 
[    3.430153] ata1.00: _GTF unexpected object type 0x1
[    3.430162] ata1.00: configured for UDMA/100
[    3.656247] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    3.764249] ata2: SATA link down (SStatus 0 SControl 300)
[    3.834712] usb 5-2: configuration #1 chosen from 1 choice
[    3.972324] usbcore: registered new interface driver hiddev
[    3.986731] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb5/5-2/5-2:1.0/input/input2
[    3.986934] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2
[    4.016717] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb5/5-2/5-2:1.1/input/input3
[    4.017697] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2
[    4.017716] usbcore: registered new interface driver usbhid
[    4.017719] usbhid: v2.6:USB HID core driver
[    4.100244] ata3: SATA link down (SStatus 0 SControl 300)
[    4.117401] scsi 0:0:0:0: Direct-Access     ATA      ST9120822AS      3.BH PQ: 0 ANSI: 5
[    4.119144] ohci1394 0000:08:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.171837] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f4200000-f42007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.179411] ata_piix 0000:00:1f.1: version 2.12
[    4.179420] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.179459] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.179524] scsi3 : ata_piix
[    4.179589] scsi4 : ata_piix
[    4.180186] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1830 irq 14
[    4.180189] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1838 irq 15
[    4.184244] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.193784] Driver 'sd' needs updating - please use bus_type methods
[    4.193869] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.193888] sd 0:0:0:0: [sda] Write Protect is off
[    4.193890] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.193921] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.193984] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.194002] sd 0:0:0:0: [sda] Write Protect is off
[    4.194004] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.194036] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.194040]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    4.242535] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.344657] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T20L, NC08, max MWDMA2
[    4.360591] ata4.00: configured for MWDMA2
[    4.531097] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20L  NC08 PQ: 0 ANSI: 5
[    4.531251] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[    4.553087] Driver 'sr' needs updating - please use bus_type methods
[    4.564309] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.564315] Uniform CD-ROM driver Revision: 3.20
[    4.564440] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    4.844366] PM: Starting manual resume from disk
[    4.844369] PM: Resume from partition 8:3
[    4.844370] PM: Checking hibernation image.
[    4.844490] PM: Resume from disk failed.
[    4.888880] kjournald starting.  Commit interval 5 seconds
[    4.888903] EXT3-fs: mounted filesystem with ordered data mode.
[    5.449399] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08e40a00983b5015]
[   11.072067] udevd version 124 started
[   11.436095] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.468521] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.496257] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   11.521027] ACPI: Power Button (FF) [PWRF]
[   11.521096] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   11.521849] ACPI: Lid Switch [LID0]
[   11.521895] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input6
[   11.548035] ACPI: Sleep Button (CM) [SLPB]
[   11.548173] ACPI: WMI: Mapper loaded
[   11.584092] Linux agpgart interface v0.103
[   11.684958] acpi device:05: registered as cooling_device2
[   11.685266] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input7
[   11.709035] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   11.709673] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/input/input8
[   11.741022] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   11.847319] ACPI: AC Adapter [ADP1] (off-line)
[   11.997587] ACPI: Battery Slot [BAT0] (battery present)
[   12.539616] nvidia: module license 'NVIDIA' taints kernel.
[   12.794070] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.794077] nvidia 0000:01:00.0: setting latency timer to 64
[   12.794245] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
[   12.795771] ricoh-mmc: Ricoh MMC Controller disabling driver
[   12.795776] ricoh-mmc: Copyright(c) Philip Langdale
[   12.795922] ricoh-mmc: Ricoh MMC controller found at 0000:08:09.2 [1180:0843] (rev 12)
[   12.795940] ricoh-mmc: Controller is now disabled.
[   12.845645] iTCO_vendor_support: vendor-support=0
[   12.903015] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   12.996992] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.075124] sdhci: Secure Digital Host Controller Interface driver
[   13.075127] sdhci: Copyright(c) Pierre Ossman
[   13.142410] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input10
[   13.239928] sdhci-pci 0000:08:09.1: SDHCI controller found [1180:0822] (rev 22)
[   13.239946] sdhci-pci 0000:08:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   13.240390] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input11
[   13.243652] mmc0: SDHCI controller on PCI [0000:08:09.1] using PIO
[   13.296432] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   13.296669] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.364258] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.364283] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.375168] Linux video capture interface: v2.00
[   13.412788] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   13.412791] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   13.442231] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.442241] iwlagn 0000:07:00.0: setting latency timer to 64
[   13.442269] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   13.488074] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.499835] iwlagn 0000:07:00.0: PCI INT A disabled
[   13.500275] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.538344] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b016)
[   13.546119] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb7/7-5/7-5:1.0/input/input12
[   13.568176] usbcore: registered new interface driver uvcvideo
[   13.568180] USB Video Class driver (v0.1.0)
[   14.153600] lp: driver loaded but no devices found
[   14.317404] Adding 2096472k swap on /dev/sda3.  Priority:-1 extents:1 across:2096472k
[   14.337163] EXT3 FS on sda2, internal journal
[   14.745628] type=1505 audit(1227903838.740:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4473
[   14.867214] type=1505 audit(1227903838.861:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4478
[   14.867401] type=1505 audit(1227903838.861:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4478
[   15.011560] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.216273] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   16.277954] apm: BIOS not found.
[   16.439657] ppdev: user-space parallel port driver
[   19.195843] Bluetooth: Core ver 2.13
[   19.197722] NET: Registered protocol family 31
[   19.197734] Bluetooth: HCI device and connection manager initialized
[   19.197741] Bluetooth: HCI socket layer initialized
[   19.226537] Bluetooth: L2CAP ver 2.11
[   19.226549] Bluetooth: L2CAP socket layer initialized
[   19.249065] Bluetooth: SCO (Voice Link) ver 0.6
[   19.249079] Bluetooth: SCO socket layer initialized
[   19.286020] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.286037] Bluetooth: BNEP filters: protocol multicast
[   19.344916] Bridge firewalling registered
[   19.345831] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   19.374350] Bluetooth: RFCOMM socket layer initialized
[   19.376427] Bluetooth: RFCOMM TTY layer initialized
[   19.376441] Bluetooth: RFCOMM ver 1.10
[   23.528290] sky2 eth0: enabling interface
[   23.633354] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   23.633436] iwlagn 0000:07:00.0: restoring config space at offset 0x1 (was 0x40100102, writing 0x40100106)
[   23.635601] firmware: requesting iwlwifi-4965-2.ucode
[   23.905240] Registered led device: iwl-phy0:radio
[   23.905436] Registered led device: iwl-phy0:assoc
[   23.905582] Registered led device: iwl-phy0:RX
[   23.905724] Registered led device: iwl-phy0:TX
[   25.209265] NET: Registered protocol family 17
[   26.679492] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[   26.681399] wlan0: authenticated
[   26.681414] wlan0: associate with AP 00:16:b6:da:ed:7a
[   26.683667] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=3)
[   26.683680] wlan0: associated
[   26.741334] wlan0: disassociating by local choice (reason=3)
[   48.497191] wlan0: associate with AP 00:16:b6:da:ed:7a
[   48.499628] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=3)
[   48.499635] wlan0: associated
[   48.504569] wlan0: disassociating by local choice (reason=3)
[   58.063858] CPU0 attaching NULL sched-domain.
[   58.063879] CPU1 attaching NULL sched-domain.
[   58.066720] CPU0 attaching sched-domain:
[   58.066732]  domain 0: span 0-1 level MC
[   58.066738]   groups: 0 1
[   58.066748]   domain 1: span 0-1 level CPU
[   58.066754]    groups: 0-1
[   58.066763] CPU1 attaching sched-domain:
[   58.066768]  domain 0: span 0-1 level MC
[   58.066773]   groups: 1 0
[   58.066781]   domain 1: span 0-1 level CPU
[   58.066787]    groups: 0-1
[   59.454755] wlan0: associate with AP 00:16:b6:da:ed:7a
[   59.458937] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[   59.460736] wlan0: authenticated
[   59.460749] wlan0: associate with AP 00:16:b6:da:ed:7a
[   59.462944] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=3)
[   59.462951] wlan0: associated
[   71.032444] NET: Registered protocol family 10
[   71.035159] lo: Disabled Privacy Extensions
[   71.037851] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   81.853242] wlan0: no IPv6 routers present
[  445.246728] iwlagn: Radio Frequency Kill Switch is On:
[  445.246735] Kill switch must be turned off for wireless networking to work.
[  448.122196] ACPI: EC: missing confirmations, switch off interrupt mode.
[  448.335414] Registered led device: iwl-phy0:radio
[  448.335467] Registered led device: iwl-phy0:assoc
[  448.335508] Registered led device: iwl-phy0:RX
[  448.335546] Registered led device: iwl-phy0:TX
[  448.338009] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[  448.340119] wlan0: authenticated
[  448.340136] wlan0: associate with AP 00:16:b6:da:ed:7a
[  448.342369] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=3)
[  448.342383] wlan0: associated
[  457.480083] wlan0: disassociating by local choice (reason=3)
[  457.483537] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[  457.487188] wlan0: authenticated
[  457.487204] wlan0: associate with AP 00:16:b6:da:ed:7a
[  457.489323] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=3)
[  457.489330] wlan0: associated
[  467.307565] wlan0: disassociating by local choice (reason=3)
[  467.328497] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[  467.330440] wlan0: authenticated
[  467.330454] wlan0: associate with AP 00:16:b6:da:ed:7a
[  467.332549] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=3)
[  467.332564] wlan0: associated
[  467.341205] wlan0: disassociating by local choice (reason=3)
[  478.577907] wlan0: associate with AP 00:16:b6:da:ed:7a
[  478.580199] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=3)
[  478.580215] wlan0: associated
[  478.592217] wlan0: disassociating by local choice (reason=3)
[  499.100838] iwlagn 0000:07:00.0: PCI INT A disabled
[  511.700733] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  511.700818] iwlagn 0000:07:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[  511.902447] Registered led device: iwl-phy0:radio
[  511.904658] Registered led device: iwl-phy0:assoc
[  511.906566] Registered led device: iwl-phy0:RX
[  511.908037] Registered led device: iwl-phy0:TX
[  511.911960] iwlagn: TX Power requested while scanning!
[  511.914074] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1072.046556] iwlagn 0000:07:00.0: PCI INT A disabled
[ 1209.727126] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 1209.727249] iwlagn 0000:07:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 1209.926098] Registered led device: iwl-phy0:radio
[ 1209.928293] Registered led device: iwl-phy0:assoc
[ 1209.928773] Registered led device: iwl-phy0:RX
[ 1209.929199] Registered led device: iwl-phy0:TX
[ 1209.933065] iwlagn: TX Power requested while scanning!
[ 1209.937440] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1471.283331] iwlagn 0000:07:00.0: PCI INT A disabled
[ 1482.047049] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 1482.047170] iwlagn 0000:07:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 1482.245753] Registered led device: iwl-phy0:radio
[ 1482.246105] Registered led device: iwl-phy0:assoc
[ 1482.246418] Registered led device: iwl-phy0:RX
[ 1482.246954] Registered led device: iwl-phy0:TX
[ 1482.249547] iwlagn: TX Power requested while scanning!
[ 1482.263028] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1710.159649] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 1710.165348] wlan0: authenticated
[ 1710.165362] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 1710.167561] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 1710.167568] wlan0: associated
[ 1710.176096] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1710.176895] wlan0: disassociating by local choice (reason=3)
[ 1720.460255] wlan0: no IPv6 routers present
[ 1768.497491] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 1768.500586] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 1768.500601] wlan0: associated
[ 1768.511584] wlan0: disassociating by local choice (reason=3)
[ 1828.708539] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 1828.711856] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 1828.711872] wlan0: associated
[ 1828.722192] wlan0: disassociating by local choice (reason=3)
[ 1888.715204] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 1888.718113] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 1888.718127] wlan0: associated
[ 1888.724827] wlan0: disassociating by local choice (reason=3)
[ 1948.721343] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 1948.724683] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 1948.724696] wlan0: associated
[ 1948.730839] wlan0: disassociating by local choice (reason=3)
[ 2008.727142] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 2008.729610] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 2008.729627] wlan0: associated
[ 2008.739558] wlan0: disassociating by local choice (reason=3)
[ 2068.733544] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 2068.735842] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 2068.735856] wlan0: associated
[ 2068.743630] wlan0: disassociating by local choice (reason=3)
[ 2128.740109] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 2128.742511] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 2128.742525] wlan0: associated
[ 2128.749103] wlan0: disassociating by local choice (reason=3)
[ 2188.745697] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 2188.748193] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 2188.748207] wlan0: associated
[ 2188.759848] wlan0: disassociating by local choice (reason=3)
[ 2232.163199] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 2232.167242] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 2232.167257] wlan0: associated
[ 2232.173690] wlan0: disassociating by local choice (reason=3)
[ 2248.752597] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 2248.754951] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 2248.754968] wlan0: associated
[ 2248.765292] wlan0: disassociating by local choice (reason=3)
[ 2308.758066] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 2308.760655] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 2308.760670] wlan0: associated
[ 2308.765922] wlan0: disassociating by local choice (reason=3)
[ 2368.764250] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 2368.766788] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 2368.766804] wlan0: associated
[ 2368.777508] wlan0: disassociating by local choice (reason=3)
[ 2427.378526] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 2427.380704] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 2427.380720] wlan0: associated
[ 2427.391276] wlan0: disassociating by local choice (reason=3)
[ 2540.103909] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 2540.105825] wlan0: authenticated
[ 2540.105841] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 2540.108064] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 2540.108079] wlan0: associated
[ 2540.234388] wlan0: disassociating by local choice (reason=3)
[ 2548.782916] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 2548.785537] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 2548.785550] wlan0: associated
[ 2548.795966] wlan0: disassociating by local choice (reason=3)
[ 2608.790020] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 2608.792818] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 2608.792831] wlan0: associated
[ 2608.799462] wlan0: disassociating by local choice (reason=3)
[ 2615.734035] iwlagn 0000:07:00.0: PCI INT A disabled
[ 2650.413995] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 2650.414122] iwlagn 0000:07:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 2650.614040] Registered led device: iwl-phy0:radio
[ 2650.615081] Registered led device: iwl-phy0:assoc
[ 2650.617257] Registered led device: iwl-phy0:RX
[ 2650.617313] Registered led device: iwl-phy0:TX
[ 2650.621066] iwlagn: TX Power requested while scanning!
[ 2650.624245] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3037.109683] iwlagn 0000:07:00.0: PCI INT A disabled
[ 3046.254255] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 3046.254375] iwlagn 0000:07:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 3046.457538] Registered led device: iwl-phy0:radio
[ 3046.458118] Registered led device: iwl-phy0:assoc
[ 3046.458712] Registered led device: iwl-phy0:RX
[ 3046.459255] Registered led device: iwl-phy0:TX
[ 3046.469252] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3235.393227] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 3235.395194] wlan0: authenticated
[ 3235.395206] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 3235.397388] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 3235.397399] wlan0: associated
[ 3235.405088] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3246.252246] wlan0: no IPv6 routers present
[ 3443.006053] wlan0: deauthenticated
[ 3444.004320] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 3444.006227] wlan0: authenticated
[ 3444.006240] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 3444.008425] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 3444.008431] wlan0: associated
[ 3479.197652] wlan0: disassociating by local choice (reason=3)
[ 3479.199339] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 3479.201569] wlan0: authenticated
[ 3479.201575] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 3479.203775] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 3479.203782] wlan0: associated
[ 3479.211682] wlan0: disassociating by local choice (reason=3)
[ 3487.786228] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 3487.788088] wlan0: authenticated
[ 3487.788104] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 3487.792185] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 3487.792202] wlan0: associated
[ 3487.798113] wlan0: disassociating by local choice (reason=3)
[ 3512.798637] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 3512.800592] wlan0: authenticated
[ 3512.800607] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 3512.802684] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 3512.802691] wlan0: associated
[ 3512.808611] wlan0: disassociating by local choice (reason=3)
[ 3519.347820] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 3521.410601] iwlagn 0000:07:00.0: PCI INT A disabled
[ 3523.597788] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 3523.597907] iwlagn 0000:07:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 3523.800142] Registered led device: iwl-phy0:radio
[ 3523.800907] Registered led device: iwl-phy0:assoc
[ 3523.801575] Registered led device: iwl-phy0:RX
[ 3523.802191] Registered led device: iwl-phy0:TX
[ 3523.810580] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 3523.813624] wlan0: authenticated
[ 3523.813634] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 3523.814497] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3523.817011] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 3523.817017] wlan0: associated
[ 3523.822752] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3523.841853] wlan0: disassociating by local choice (reason=3)
[ 3530.805372] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 3530.809686] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 3530.811681] wlan0: authenticated
[ 3530.811698] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 3530.814120] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 3530.814133] wlan0: associated
[ 3534.440249] wlan0: no IPv6 routers present
[ 3570.174022] iwlagn 0000:07:00.0: PCI INT A disabled
[ 3586.933157] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 3586.933285] iwlagn 0000:07:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 3587.133799] Registered led device: iwl-phy0:radio
[ 3587.135887] Registered led device: iwl-phy0:assoc
[ 3587.138108] Registered led device: iwl-phy0:RX
[ 3587.140044] Registered led device: iwl-phy0:TX
[ 3587.141872] iwlagn: TX Power requested while scanning!
[ 3587.147567] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3587.147621] wlan0: disassociating by local choice (reason=3)
[ 3595.573790] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 3595.575704] wlan0: authenticated
[ 3595.575721] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 3595.577843] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 3595.577856] wlan0: associated
[ 3595.586547] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3606.292228] wlan0: no IPv6 routers present
[ 3621.113630] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080609]
[ 3621.113666] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.GBST] (Node f741a9f0), AE_TIME
[ 3621.113789] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f741aae0), AE_TIME
[ 3621.113900] ACPI Exception (battery-0360): AE_TIME, Evaluating _BST [20080609]
[ 3621.124716] iwlagn 0000:07:00.0: PCI INT A disabled
[ 3643.206588] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 3643.206708] iwlagn 0000:07:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 3643.406167] Registered led device: iwl-phy0:radio
[ 3643.408442] Registered led device: iwl-phy0:assoc
[ 3643.408502] Registered led device: iwl-phy0:RX
[ 3643.408542] Registered led device: iwl-phy0:TX
[ 3643.411196] iwlagn: TX Power requested while scanning!
[ 3643.423263] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3780.228280] wlan0: disassociating by local choice (reason=3)
[ 3881.646135] compiz.real[6004]: segfault at 54504952 ip 08055c8c sp bfe0e660 error 4 in compiz.real[8048000+34000]
[ 3919.640888] CPU0 attaching NULL sched-domain.
[ 3919.640896] CPU1 attaching NULL sched-domain.
[ 3919.652311] CPU0 attaching sched-domain:
[ 3919.652319]  domain 0: span 0-1 level MC
[ 3919.652321]   groups: 0 1
[ 3919.652325]   domain 1: span 0-1 level CPU
[ 3919.652327]    groups: 0-1
[ 3919.652331] CPU1 attaching sched-domain:
[ 3919.652333]  domain 0: span 0-1 level MC
[ 3919.652335]   groups: 1 0
[ 3919.652338]   domain 1: span 0-1 level CPU
[ 3919.652339]    groups: 0-1
[ 3921.167654] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 3921.173524] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 3921.173579] wlan0: authenticated
[ 3921.173587] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 3921.177681] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 3921.177696] wlan0: associated
[ 3921.184588] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3931.728258] wlan0: no IPv6 routers present
[ 3936.898239] wlan0: disassociating by local choice (reason=3)
[ 3936.901287] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 3936.903459] wlan0: authenticated
[ 3936.903476] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 3938.936808] iwlagn 0000:07:00.0: PCI INT A disabled
[ 3942.133977] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 3942.134094] iwlagn 0000:07:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 3942.334236] Registered led device: iwl-phy0:radio
[ 3942.336352] Registered led device: iwl-phy0:assoc
[ 3942.338083] Registered led device: iwl-phy0:RX
[ 3942.339469] Registered led device: iwl-phy0:TX
[ 3942.348801] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 3942.350816] wlan0: authenticated
[ 3942.350834] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 3942.352734] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3942.355137] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 3942.355152] wlan0: associated
[ 3942.389636] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3942.429264] wlan0: disassociating by local choice (reason=3)
[ 3952.897109] wlan0: no IPv6 routers present
[ 3965.726695] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 3965.728956] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 3965.728964] wlan0: associated
[ 3965.735395] wlan0: disassociating by local choice (reason=3)
[ 3995.729272] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 3995.731826] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 3995.731841] wlan0: associated
[ 3995.737873] wlan0: disassociating by local choice (reason=3)
[ 4035.666082] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 4035.668743] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 4035.668762] wlan0: associated
[ 4035.674319] wlan0: disassociating by local choice (reason=3)
[ 4085.738494] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 4085.740977] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 4085.740991] wlan0: associated
[ 4085.748923] wlan0: disassociating by local choice (reason=3)
[ 4100.813466] wlan0: authenticate with AP 00:1e:2a:74:40:8e
[ 4100.822944] wlan0: authenticated
[ 4100.822960] wlan0: associate with AP 00:1e:2a:74:40:8e
[ 4100.831629] wlan0: RX AssocResp from 00:1e:2a:74:40:8e (capab=0x401 status=0 aid=1)
[ 4100.831640] wlan0: associated
[ 4100.841911] wlan0: disassociating by local choice (reason=3)
[ 4214.298295] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 4214.300191] wlan0: authenticated
[ 4214.300206] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 4214.302376] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 4214.302391] wlan0: associated
[ 4214.308884] wlan0: disassociating by local choice (reason=3)
[ 4224.843454] wlan0: authenticate with AP 00:1e:2a:74:40:8e
[ 4224.846684] wlan0: authenticated
[ 4224.846702] wlan0: associate with AP 00:1e:2a:74:40:8e
[ 4225.044286] wlan0: associate with AP 00:1e:2a:74:40:8e
[ 4225.048967] wlan0: RX AssocResp from 00:1e:2a:74:40:8e (capab=0x401 status=0 aid=1)
[ 4225.048979] wlan0: associated
[ 4225.056499] wlan0: disassociating by local choice (reason=3)
[ 4359.288986] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 4359.290817] wlan0: authenticated
[ 4359.290831] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 4359.292933] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 4359.292947] wlan0: associated
[ 4359.300884] wlan0: disassociating by local choice (reason=3)
[ 4385.564488] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 4385.567548] wlan0: RX ReassocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 4385.567563] wlan0: associated
[ 4385.576085] wlan0: disassociating by local choice (reason=3)
[ 4435.131144] wlan0: authenticate with AP 00:16:b6:da:ed:7a
[ 4435.133295] wlan0: authenticated
[ 4435.133315] wlan0: associate with AP 00:16:b6:da:ed:7a
[ 4435.135583] wlan0: RX AssocResp from 00:16:b6:da:ed:7a (capab=0x401 status=0 aid=1)
[ 4435.135599] wlan0: associated

wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:DA:ED:7A
                    ESSID:"erwin.net"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=82/100  Signal level:-61 dBm  Noise level=-94 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000049e9e183
                    Extra: Last beacon: 40ms ago
```

---

### Post by OldGregory on 2008-11-28
Look at this, what on earth could be the problem?
```
gerwin@gerwin-laptop-ubuntu:~$ sudo iwconfig wlan0 
wlan0     IEEE 802.11abgn  ESSID:"erwin.net"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:DA:ED:7A   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality=100/100  Signal level:-51 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gerwin@gerwin-laptop-ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:DA:ED:7A
                    ESSID:"erwin.net"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=97/100  Signal level:-53 dBm  Noise level=-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000000d467183
                    Extra: Last beacon: 76ms ago

gerwin@gerwin-laptop-ubuntu:~$ sudo dhclient wlan0 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3b:48:08:11
Sending on   LPF/wlan0/00:1f:3b:48:08:11
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by Ayuthia on 2008-11-28
You might try turning off network manager just for this session:
```
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
```and then try to connect.  If you can then it is NetworkManager that is causing it.

---

### Post by gnusci on 2008-11-28
Try after stopping the network manager:

**$ /etc/init.d/NetworkManager stop**

Sorry but could you post the output of:

**$ uname -mr**
**$ lsb_release -d**

---

### Post by OldGregory on 2008-11-28
/etc/init.d/NetworkManger stop didn't help. Those other two won't auto-complete.

2.6.27-7-generic i686
Description:	Ubuntu 8.10

---

### Post by gnusci on 2008-11-28
I see your system is using the driver **iwlagn**

>  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:48:08:11
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.141 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn



but intellinuxwireless.org suggest use **iwlwifi** for the **4965AGN**

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)
[http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi)

What is a little bit odd it is that the **iwlwifi** should be use by your Intel Wireless WiFi Link 4965AGN. Since kernels 2.6.24 and up already have it. I can see that the **dmesg** shows

**[ 23.635601] firmware: requesting iwlwifi-4965-2.ucode**

I think it is looking for **iwlwifi-4965-2.ucode** and it is not there. So I think you should install **iwlwifi**. Another solution can be that your system is using the wrong module, so just try removing 

**$ sudo rmmod iwlagn**

and use iwlwifi

**$ sudo modprobe iwlwifi**

---

### Post by OldGregory on 2008-11-28
Well, **sudo modprobe iwlwifi** doesn't work: *FATAL: Module iwlwifi not found.*

I don't understand why I should bother switching drivers if **iwlagn** works perfectly with network-manager.  How does network-manager connect to a network anyway?

---

### Post by OldGregory on 2008-11-28
OK, I think I've figured it out.

I had been disconnecting from my wireless network by deleting the connection entry inside the nm-applet, and no matter what, I could not connect to a wireless network via the terminal. 

I tried **sudo /etc/init.d/NetworkManager stop** one more time and, finally, it worked.  
Sure enough, if I started the Network Manager back up, and disconnected the same way as before, I couldn't connect via the terminal.  

So then I tried unchecking **Enable Wireless** in the nm-applet and now I could connect via the terminal. 

Well, thanks for the help guys.  I hate it when I spend several days on a problem when something as stupid as this is causing it.

Oh, and I believe it might be a good idea to add disabling the Network Manager as a step to your guide, KevDog.  I dunno how obvious that step is; it wasn't to me.

---

