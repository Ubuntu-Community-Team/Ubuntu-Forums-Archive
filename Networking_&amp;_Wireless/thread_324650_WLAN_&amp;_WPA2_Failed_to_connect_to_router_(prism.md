---
title: "WLAN &amp; WPA2: Failed to connect to router (prism chipset, avm fritz!box-router)"
date: 2006-12-24
forum: Networking &amp; Wireless
---

### Post by udok on 2006-12-24
Hi,

I am not new to Linux, but quite new to ubuntu and very new to wlan / wpa2 issues. 

I am using a Thinkpad A31p and want to connect to my home wlan router "FRITZ!Box Fon WLAN 7170, Firmware-Version 29.04.22" using wpa2. I am trying to get this working for now 4 weeks (of course I haven't tried every single day.) It took me a long time to realize, I had to upgrade the firmware of my prism wlan chip and to carry it out.

Recently, I have read and applied the how-to "HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc." but still it is not working. So I hope there is some help for me here.

In the following, You'll find the output of the commands given in the how-to under "Post this if you are stumped".

uname -a
```

Linux gantenbein 2.6.15.7-ubuntu1 #1 PREEMPT Mon Dec 18 17:10:05 CET 2006 i686 GNU/Linux

```

ifconfig -a
```

eth0      Protokoll:Ethernet  Hardware Adresse 00:20:E0:8D:5F:83
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:29 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

eth1      Protokoll:Ethernet  Hardware Adresse 00:D0:59:DA:6D:F4
          inet Adresse:192.168.178.23  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6 Adresse: fe80::2d0:59ff:feda:6df4/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1998 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:1152183 (1.0 MiB)  TX bytes:214751 (209.7 KiB)

irda0     Protokoll:IrLAP  Hardware Adresse 00:00:00:00
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:8
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

sit0      Protokoll:IPv6-nach-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Protokoll:UNSPEC  Hardware Adresse 00-20-E0-8D-5F-83-65-74-00-00-00-00-00-00-00-00
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:3250 (3.1 KiB)  TX bytes:0 (0.0 b)
          Interrupt:11

```

route -n
```

Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.178.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 eth1

```

iwconfig
```

lo        no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"Netofsupermulls"
          Mode:Managed  Frequency:2.422 GHz  Access Point: None
          Bit Rate:2 Mb/s   Sensitivity=1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

irda0     no wireless extensions.

eth0      IEEE 802.11b  ESSID:"Netofsupermulls"
          Mode:Managed  Frequency:2.422 GHz  Access Point: None
          Bit Rate:2 Mb/s   Sensitivity=1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:7  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:198   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

```

ifconfig
```

eth0      Protokoll:Ethernet  Hardware Adresse 00:20:E0:8D:5F:83
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:33 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

eth1      Protokoll:Ethernet  Hardware Adresse 00:D0:59:DA:6D:F4
          inet Adresse:192.168.178.23  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6 Adresse: fe80::2d0:59ff:feda:6df4/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2145 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:1340832 (1.2 MiB)  TX bytes:251146 (245.2 KiB)

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

wifi0     Protokoll:UNSPEC  Hardware Adresse 00-20-E0-8D-5F-83-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:3634 (3.5 KiB)  TX bytes:0 (0.0 b)
          Interrupt:11

```

lsmod
```

Module                  Size  Used by
ipv6                  265856  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
nvram                   9224  1
uinput                  9088  1
capability              5000  0
commoncap               7296  1 capability
ppdev                   9220  0
radeon                116000  1
drm                    73236  2 radeon
speedstep_ich           5260  0
speedstep_lib           4484  1 speedstep_ich
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_ich,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
ibm_acpi               26112  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
nls_utf8                2176  1
ntfs                  103536  1
dm_mod                 58936  1
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
scsi_mod              139496  2 sr_mod,sbp2
lp                     11844  0
af_packet              22920  16
pcmcia                 40508  0
parport_pc             35780  1
e100                   40580  0
irtty_sir               8576  0
parport                36296  3 ppdev,lp,parport_pc
sir_dev                19628  1 irtty_sir
nsc_ircc               23948  0
mii                     5888  1 e100
irda                  187068  3 irtty_sir,sir_dev,nsc_ircc
crc_ccitt               2304  1 irda
floppy                 62148  0
hostap_pci             58384  2
hostap                119428  1 hostap_pci
ieee80211_crypt         6272  1 hostap
pcspkr                  2180  0
yenta_socket           28428  2
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
rtc                    13492  0
psmouse                36100  0
snd_intel8x0           33692  3
snd_ac97_codec         93216  1 snd_intel8x0
serio_raw               7300  0
hw_random               5652  0
snd_ac97_bus            2304  1 snd_ac97_codec
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd                    55268  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
intel_agp              22940  1
agpgart                34888  2 drm,intel_agp
tsdev                   8000  0
evdev                   9856  2
ext3                  135816  2
jbd                    58772  1 ext3
usbhid                 39904  0
ide_generic             1536  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
uhci_hcd               33808  0
usbcore               130820  3 usbhid,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  5
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
vga16fb                13704  0
vgastate               10368  1 vga16fb

```

iwlist scan
```

lo        Interface doesn't support scanning.

wifi0     Scan completed :
          Cell 01 - Address: 00:40:96:54:90:44
                    ESSID:"ecampus"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Signal level=-96 dBm  Noise level=-97 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
          Cell 02 - Address: 00:04:0E:F5:A4:EF
                    ESSID:"Netofsupermulls"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Signal level=-46 dBm  Noise level=-100 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:15:0C:EF:54:7E
                    ESSID:"FRITZ!Box Fon WLAN 7170"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level=-96 dBm  Noise level=-100 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:16:38:41:30:71
                    ESSID:"HomeNet"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

irda0     Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:04:0E:F5:A4:EF
                    ESSID:"Netofsupermulls"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Signal level=-47 dBm  Noise level=-100 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:15:0C:EF:54:7E
                    ESSID:"FRITZ!Box Fon WLAN 7170"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:40:96:54:90:44
                    ESSID:"ecampus"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
          Cell 04 - Address: 00:16:38:41:30:71
                    ESSID:"HomeNet"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

eth1      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

```

cat /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp

# WLAN
auto eth0
iface eth0 inet dhcp
#address 192.168.168.40
#netmask 255.255.255.0
#network 192.168.168.0
#broadcast 192.168.168.255
#gateway 192.168.168.230
#dns-nameservers 192.168.168.230
wpa-driver hostap
wpa-conf managed
wpa-ssid Netofsupermulls
wpa-ap-scan 2
wpa-proto WPA2
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 15b3469accad57a4907a758cba60e097bcf74eb7999a4e5efd46b61d3833f9b3

```

cat /etc/modprobe.d/ndiswrapper
```

cat: /etc/modprobe.d/ndiswrapper: No such file or directory

```

cat /etc/resolv.conf
```

search 7layers.rat.de.local
nameserver 192.168.178.1

```

I would appreciate any help! Please let me know, if more information is needed.

Regards,

Udo.

---

### Post by wieman01 on 2006-12-24
First of all, it appears that you have installed wifi-radar. Please uninstall it before you go ahead along with network-manager or firestarter.

Second, the script says you have disabled broadcast of you network name (ESSID):
> wpa-ap-scan 2
Set it to "1" if your ESSID is not hidden.

Are you using "ndiswrapper" of the native Linux driver for your card?

_**EDIT:**_
Please tell us what your desired configuration is (e.g. hidden ESSID, DHCP, etc.) and what wireless driver you are using. Please be as specific as possible, that will help a lot.

---

### Post by udok on 2006-12-26
Thank you very much for your reply!

I thought I have uninstalled wifi-radar, but it was still installed. Now, uninstalling it, WLAN is up and running.

Sorry, You had to read all the code quoted!

Regards,

Udo.

---

