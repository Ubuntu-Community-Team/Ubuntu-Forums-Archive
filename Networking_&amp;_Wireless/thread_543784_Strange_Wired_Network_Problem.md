---
title: "Strange Wired Network Problem"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by twhayes on 2007-09-05
I can't get any network adapter to work on my Linux box running Kubuntu 7.04.  I've tried two adapters -- Realtek 3189 and ADM8511 (USB) with same results.  Both work fine on Win XP on same machine using dual boot, but I can't get them to work when running Kubuntu.

I had the Realtek adapter working a couple of months ago, but then it started to get slower and slower and finally quit.  I first noticed it when Synergy started to have a big lag and the cursor was jumping a lot.  The main symptoms that I get now is I can't ping my default gateway or any other box on my LAN.  I can only ping the installed adapter.

I'm not a total Linux noob, but don't have a tremendous amount of experience with Linux and would appreciate any advice/suggestions.

Results of various applicable commands are below.  (executed with ADM8511 adapter connected).

$ lsmod
Module                  Size  Used by
iptable_filter          3968  0
ip_tables              13796  1 iptable_filter
x_tables               16388  1 ip_tables
cifs                  217080  0
isofs                  36284  1
udf                    85252  0
rfcomm                 40856  0
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
vmnet                  39076  12
vmmon                 113836  0
ppdev                  10116  0
speedstep_lib           6148  0
cpufreq_stats           7360  0
cpufreq_userspace       5408  0
cpufreq_ondemand        9228  0
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0
cpufreq_conservative     8200  0
dev_acpi               12292  0
pcc_acpi               13184  0
tc1100_wmi              8068  0
sony_acpi               6284  0
dock                   10268  0
battery                10756  0
button                  8720  0
asus_acpi              17308  0
backlight               7040  1 asus_acpi
ac                      6020  0
sbs                    15652  0
i2c_ec                  6016  1 sbs
container               5248  0
video                  16388  0
nls_utf8                3072  7
ntfs                  107764  7
nls_iso8859_1           5120  7
nls_cp437               6784  8
vfat                   14208  7
fat                    53916  1 vfat
w83627hf               26256  0
hwmon_vid               4224  1 w83627hf
i2c_isa                 6272  1 w83627hf
ds1621                  9744  0
eeprom                  8336  0
i2c_i801                9356  0
sbp2                   23812  0
lp                     12452  0
snd_intel8x0           34332  1
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nvidia               4713780  22
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pegasus                27536  0
i2c_core               22656  7 i2c_ec,w83627hf,i2c_isa,ds1621,eeprom,i2c_i801,nvidia
serio_raw               7940  0
parport_pc             36388  1
iTCO_wdt               11812  0
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
pcspkr                  4224  0
parport                36936  3 ppdev,lp,parport_pc
psmouse                38920  0
intel_agp              25244  0
agpgart                35400  2 nvidia,intel_agp
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
i82875p_edac            7300  0
edac_mc                23248  1 i82875p_edac
tsdev                   8768  0
ipv6                  268960  10
evdev                  11008  3
ext3                  133128  2
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0
sr_mod                 17060  1
cdrom                  37664  1 sr_mod
sd_mod                 23428  21
generic                 5124  0 [permanent]
usb_storage            72256  1
libusual               17936  1 usb_storage
ata_piix               15492  17
ohci1394               36528  0
floppy                 59524  0
ehci_hcd               34188  0
ieee1394              299448  2 sbp2,ohci1394
ata_generic             9092  0
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata
8139too                27648  0
mii                     6528  2 pegasus,8139too
uhci_hcd               25360  0
usbcore               134280  6 pegasus,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14856  1
processor              31048  1 thermal
fan                     5636  1
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability


$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82875P/E7210 Memory Controller Hub [8086:2578] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82875P Processor to AGP Controller [8086:2579] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV35 [GeForce FX 5900XT] [10de:0332] (rev a1)
02:02.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]
02:07.0 Ethernet controller [0200]: D-Link System Inc RTL8139 Ethernet [1186:1300] (rev 10)


$ ping kubuntu (name of this install)
PING Kubuntu (192.168.1.25) 56(84) bytes of data.
64 bytes from Kubuntu (192.168.1.25): icmp_seq=1 ttl=64 time=0.044 ms
64 bytes from Kubuntu (192.168.1.25): icmp_seq=2 ttl=64 time=0.027 ms
64 bytes from Kubuntu (192.168.1.25): icmp_seq=3 ttl=64 time=0.029 ms

--- Kubuntu ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.027/0.033/0.044/0.008 ms
tim@Kubuntu:~/Desktop$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.25 icmp_seq=2 Destination Host Unreachable
From 192.168.1.25 icmp_seq=3 Destination Host Unreachable
From 192.168.1.25 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5001ms
, pipe 3
tim@Kubuntu:~/Desktop$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.059 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.028 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.028 ms

--- 127.0.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 0.028/0.038/0.059/0.015 ms

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

$ sudo dmesg | tail
[52503.611831] usb 4-2: USB disconnect, address 6
[52507.629451] usb 4-2: new full speed USB device using uhci_hcd and address 7
[52507.818176] usb 4-2: configuration #1 chosen from 1 choice
[52507.833046] pegasus 4-2:1.0: setup Pegasus II specific registers
[52507.952919] pegasus 4-2:1.0: eth1, ADMtek ADM8511 "Pegasus II" USB Ethernet, 00:14:d1:3b:f3:b0
[52507.999885] eth1: set allmulti
[52507.999915] eth1: set allmulti
[52507.999923] eth1: set allmulti
[52518.092938] eth1: no IPv6 routers present

end of /var/log/syslog
Sep  5 21:25:54 Kubuntu kernel: [52503.611831] usb 4-2: USB disconnect, address 6
Sep  5 21:25:54 Kubuntu avahi-daemon[5169]: Interface eth1.IPv4 no longer relevant for mDNS.
Sep  5 21:25:54 Kubuntu avahi-daemon[5169]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.25.
Sep  5 21:25:54 Kubuntu avahi-daemon[5169]: Withdrawing address record for xxxx::214:d1ff:fe3b:xxxx on eth1.
Sep  5 21:25:54 Kubuntu avahi-daemon[5169]: Withdrawing address record for 192.168.1.25 on eth1.
Sep  5 21:25:54 Kubuntu NetworkManager: <debug info>^I[1189041954.264190] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/H
Sep  5 21:25:54 Kubuntu NetworkManager: <debug info>^I[1189041954.266136] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/H
Sep  5 21:25:54 Kubuntu NetworkManager: <debug info>^I[1189041954.268921] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/H
Sep  5 21:25:54 Kubuntu NetworkManager: <debug info>^I[1189041954.271611] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/H
Sep  5 21:25:58 Kubuntu kernel: [52507.629451] usb 4-2: new full speed USB device using uhci_hcd and address 7
Sep  5 21:25:58 Kubuntu kernel: [52507.818176] usb 4-2: configuration #1 chosen from 1 choice
Sep  5 21:25:58 Kubuntu NetworkManager: <debug info>^I[1189041958.421205] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/H
Sep  5 21:25:58 Kubuntu kernel: [52507.833046] pegasus 4-2:1.0: setup Pegasus II specific registers
Sep  5 21:25:58 Kubuntu NetworkManager: <debug info>^I[1189041958.490747] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/H
Sep  5 21:25:58 Kubuntu kernel: [52507.952919] pegasus 4-2:1.0: eth1, ADMtek ADM8511 "Pegasus II" USB Ethernet, 00:14:d1:3b:f3:b0
Sep  5 21:25:58 Kubuntu NetworkManager: <debug info>^I[1189041958.561552] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/H
Sep  5 21:25:58 Kubuntu kernel: [52507.999885] eth1: set allmulti
Sep  5 21:25:58 Kubuntu kernel: [52507.999915] eth1: set allmulti
Sep  5 21:25:58 Kubuntu kernel: [52507.999923] eth1: set allmulti
Sep  5 21:25:58 Kubuntu NetworkManager: <debug info>^I[1189041958.604756] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/H
Sep  5 21:25:59 Kubuntu avahi-daemon[5169]: Registering new address record for xxxx::214:d1ff:xxxx:f3b0 on eth1.*.
Sep  5 21:26:08 Kubuntu kernel: [52518.092938] eth1: no IPv6 routers present
Sep  5 21:26:25 Kubuntu Synergy 1.3.1: WARNING: synergyc.cpp,265: failed to connect to server: cannot connect socket: Network is unreachable
Sep  5 21:26:39 Kubuntu last message repeated 2 times
Sep  5 21:25:54 Kubuntu kernel: [52503.611831] usb 4-2: USB disconnect, address 6
Sep  5 21:25:54 Kubuntu avahi-daemon[5169]: Interface eth1.IPv4 no longer relevant for mDNS.
Sep  5 21:25:54 Kubuntu avahi-daemon[5169]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.25.
Sep  5 21:25:54 Kubuntu avahi-daemon[5169]: Withdrawing address record for fe80::214:d1ff:fe3b:f3b0 on eth1.
Sep  5 21:25:54 Kubuntu avahi-daemon[5169]: Withdrawing address record for 192.168.1.25 on eth1.
Sep  5 21:25:54 Kubuntu NetworkManager: <debug info>^I[1189041954.264190] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/H
Sep  5 21:25:54 Kubuntu NetworkManager: <debug info>^I[1189041954.266136] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/H
Sep  5 21:25:54 Kubuntu NetworkManager: <debug info>^I[1189041954.268921] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/H
Sep  5 21:25:54 Kubuntu NetworkManager: <debug info>^I[1189041954.271611] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/H
Sep  5 21:25:58 Kubuntu kernel: [52507.629451] usb 4-2: new full speed USB device using uhci_hcd and address 7
Sep  5 21:25:58 Kubuntu kernel: [52507.818176] usb 4-2: configuration #1 chosen from 1 choice
Sep  5 21:25:58 Kubuntu NetworkManager: <debug info>^I[1189041958.421205] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/H
Sep  5 21:25:58 Kubuntu kernel: [52507.833046] pegasus 4-2:1.0: setup Pegasus II specific registers
Sep  5 21:25:58 Kubuntu NetworkManager: <debug info>^I[1189041958.490747] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/H
Sep  5 21:25:58 Kubuntu kernel: [52507.952919] pegasus 4-2:1.0: eth1, ADMtek ADM8511 "Pegasus II" USB Ethernet, 00:14:d1:3b:f3:b0
Sep  5 21:25:58 Kubuntu NetworkManager: <debug info>^I[1189041958.561552] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/H
Sep  5 21:25:58 Kubuntu kernel: [52507.999885] eth1: set allmulti
Sep  5 21:25:58 Kubuntu kernel: [52507.999915] eth1: set allmulti
Sep  5 21:25:58 Kubuntu kernel: [52507.999923] eth1: set allmulti
Sep  5 21:25:58 Kubuntu NetworkManager: <debug info>^I[1189041958.604756] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/H
Sep  5 21:25:59 Kubuntu avahi-daemon[5169]: Registering new address record for fe80::214:d1ff:fe3b:f3b0 on eth1.*.
Sep  5 21:26:08 Kubuntu kernel: [52518.092938] eth1: no IPv6 routers present

$ ifconfig
eth1      Link encap:Ethernet  HWaddr xx:14:D1:3B:F3:B0
          inet addr:192.168.1.25  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:d1ff:fe3b:f3b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:3035 (2.9 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5881 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:523540 (511.2 KiB)  TX bytes:523540 (511.2 KiB)

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

---

