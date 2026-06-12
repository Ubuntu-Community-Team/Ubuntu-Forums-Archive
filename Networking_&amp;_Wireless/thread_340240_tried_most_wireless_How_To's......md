---
title: "tried most wireless How To's....."
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by Tocilog Time on 2007-01-16
still don't have this thing working, wish i could remember the links i used. im using a dlink dwl650+. ive downloaded the latest acx100 drivers. i have ndiswrapper and Network Manager installed. Network Manager can see networks in the area so that part works, but i cant connect to any of them.

now for ndiswrapper: i installed the windows drivers for it, but it doesnt see the card. when i check this the ethernet cable is unplugged. 

im using dapper, have the latest updates. what else do you guys need to know?

---

### Post by dmizer on 2007-01-16
we need chipset information ... with the card inserted, post the output of:
```
lspci
```

if it's an acx card, you shouldn't need ndiswrapper.  at most, you may need to chanage the firmware.

---

### Post by Tocilog Time on 2007-01-18
```
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1420
0000:00:0a.1 CardBus bridge: Texas Instruments PCI1420
0000:00:0b.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
0000:00:0b.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
0000:00:0d.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
0000:06:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface

```

---

### Post by Tocilog Time on 2007-01-22
heres some more info. the wireless card is in of course.

```

wlan0
wlan0     IEEE 802.11b+  ESSID:"STAAB49AB"  Nickname:"acx v0.3.21"
          Mode:Managed  Channel:1  Access Point: Not-Associated
          Bit Rate:22 Mb/s   Tx-Power=18 dBm   Sensitivity=187/255
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:04:75:18:F1:0A
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::204:75ff:fe18:f10a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8689 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12973016 (12.3 MiB)  TX bytes:1235587 (1.1 MiB)
          Interrupt:10 Base address:0x2400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:80:C8:AB:49:AB
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x1c00
```

tried ur suggestion with the wrong drivers. all 3 driver versions do not even detect the hardware,but it shows up here.

---

### Post by dmizer on 2007-01-22
try this:
```
sudo ifdown eth0&& sudo ifdown wlan0
sudo iwlist wlan0 scan
```

also post the output of:
```
lsmod
```

and if you're still trying to make the card work with ndiswrapper, post the output of:
```
sudo ndiswrapper -l
```

you MIGHT (might) get lucky with this method, but i can't garantee it, and it's a real pain ... [http://www.ubuntuforums.org/showthread.php?t=324148](http://www.ubuntuforums.org/showthread.php?t=324148)

---

### Post by Tocilog Time on 2007-01-25
[here's one of the websites i used to try to connect to my router.]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html") it affects the code u gave me,  just thought this info would help somewhat.

so after configuring wlan0 & eth0 this came up: 

```

sudo ifdown eth0&& sudo ifdown wlan0


Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:04:75:18:f1:0a
Sending on   LPF/eth0/00:04:75:18:f1:0a
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:80:c8:ab:49:ab
Sending on   LPF/wlan0/00:80:c8:ab:49:ab
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

```

with this do i need to turn off all security settingsfor my router for it to connect? cuz with my current setup i need to post those results on another day. 

```

lsmod

Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
ipv6                  265856  6
af_packet              22920  6
speedstep_lib           4484  0
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
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
acx                   101132  0
joydev                 10048  0
tsdev                   8000  0
pcmcia                 40508  0
snd_maestro3           25380  2
snd_ac97_codec         93216  1 snd_maestro3
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  2 snd_pcm_oss
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
rtc                    13492  0
snd_pcm                89864  4 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd_page_alloc         10632  1 snd_pcm
floppy                 62148  0
snd                    55268  7 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  2 snd
pcspkr                  2180  0
psmouse                36100  0
serio_raw               7300  0
3c59x                  45608  0
mii                     5888  1 3c59x
yenta_socket           28428  3
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4               9104  0
i2c_core               21904  2 i2c_acpi_ec,i2c_piix4
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  1 intel_agp
evdev                   9856  2
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33808  0
usbcore               130820  3 acx,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  3
piix                   11012  1
generic                 5124  0
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

```

```
sudo ndiswrapper -l
```

just says that theres invalid drivers. i downloaded the XP version of the drivers. if this happened is it a safe bet that the wireless card is broken?

---

### Post by dmizer on 2007-01-28
it's probably better (for testing purposes at least) to start without the security turned on.  once you know your card works and can connect, then you can focus on making security work.  but right now, your problem is more basic than wireless security.

if ndiswrapper -l shows that there are invalid drivers, then ndiswrapper is not driving your card correctly.  they need to say "driver installed, hardware present" in order for it to be working.  you might try alternate drivers for your card ... the win2000 driver, or nt driver or any of the others may be functional for you.

if all else fails, go through the .inf files and make sure all the .sys file names referred to in the .ini file have the same letter case (uppercase or lowercase).

---

### Post by Tocilog Time on 2007-02-09
sorry replies take a week or so, ive been busy n stuff. tried connecting to my neighbors security free network, didnt work. currently trying new drivers.

---

### Post by AAM on 2007-02-09
Just a small point that had me stumped for a long time. You upload the INF file with ndiswrapper ... BUT you must have the other files (SYS) in the same directory when you do that. Capitals make a difference also as *dmizer* says.

Get the ndiswrapper loading first.

Sorry if you have already done this.

---

