---
title: "Can't get WPA to work with netgear MA521 pcmcia card"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by kakashi on 2007-03-11
i have managed to connect to unencrypted connections but cannot connect to the WPA one. 
```
uname -a

Linux ubuntu 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

root@ubuntu:~# ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:D0:59:2F:B7:9A  

          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::2d0:59ff:fe2f:b79a/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:1294 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1262 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:1009134 (985.4 KiB)  TX bytes:189413 (184.9 KiB)



lo        Link encap:Local Loopback  

          LOOPBACK  MTU:16436  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



sit0      Link encap:IPv6-in-IPv4  

          NOARP  MTU:1480  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



wlan0     Link encap:Ethernet  HWaddr 00:09:5B:8A:A1:3A  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:256 (256.0 b)

          Interrupt:11 Memory:d094c000-d094c100 



root@ubuntu:~# route -n

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

root@ubuntu:~# ifconfig

eth0      Link encap:Ethernet  HWaddr 00:D0:59:2F:B7:9A  

          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::2d0:59ff:fe2f:b79a/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:1294 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1262 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:1009134 (985.4 KiB)  TX bytes:189413 (184.9 KiB)



wlan0     Link encap:Ethernet  HWaddr 00:09:5B:8A:A1:3A  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:10 overruns:0 frame:0

          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:1728 (1.6 KiB)

          Interrupt:11 Memory:d094c000-d094c100 



root@ubuntu:~# lsmod

Module                  Size  Used by

ipv6                  272288  8 

binfmt_misc            13448  1 

rfcomm                 42260  0 

l2cap                  27136  5 rfcomm

bluetooth              53476  4 rfcomm,l2cap

speedstep_lib           5764  0 

cpufreq_userspace       5408  0 

cpufreq_stats           7744  0 

freq_table              6048  1 cpufreq_stats

cpufreq_powersave       2944  0 

cpufreq_ondemand        8876  0 

cpufreq_conservative     8712  0 

video                  17540  0 

tc1100_wmi              8324  0 

sbs                    16804  0 

sony_acpi               6412  0 

pcc_acpi               14080  0 

i2c_ec                  6272  1 sbs

hotkey                 11556  0 

dock                    8716  0 

dev_acpi               12292  0 

button                  7952  0 

battery                11652  0 

container               5632  0 

ac                      6788  0 

asus_acpi              17688  0 

af_packet              24584  6 

lp                     12964  0 

r818x                  95372  0 

ieee80211_rtl          85640  1 r818x

joydev                 11200  0 

tsdev                   9152  0 

radio_maestro           8448  0 

pcmcia                 40380  0 

compat_ioctl32          2432  1 radio_maestro

videodev               10752  1 radio_maestro

irtty_sir              10112  0 

sir_dev                18308  1 irtty_sir

snd_es1968             32160  1 

gameport               17160  1 snd_es1968

irda                  214332  2 irtty_sir,sir_dev

snd_ac97_codec         97696  1 snd_es1968

snd_ac97_bus            3456  1 snd_ac97_codec

i2c_piix4              10000  0 

i2c_core               23424  2 i2c_ec,i2c_piix4

crc_ccitt               3200  1 irda

snd_pcm_oss            47360  0 

snd_mixer_oss          19584  1 snd_pcm_oss

evdev                  11392  2 

snd_pcm                84612  3 snd_es1968,snd_ac97_codec,snd_pcm_oss

snd_timer              25348  1 snd_pcm

snd_page_alloc         11400  2 snd_es1968,snd_pcm

snd_mpu401_uart        10240  1 snd_es1968

snd_rawmidi            27264  1 snd_mpu401_uart

snd_seq_device          9868  1 snd_rawmidi

floppy                 63044  0 

shpchp                 42144  0 

pci_hotplug            32828  1 shpchp

yenta_socket           28812  3 

rsrc_nonstatic         15360  1 yenta_socket

pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic

pcspkr                  4352  0 

e100                   38020  0 

snd                    58372  11 snd_es1968,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device

psmouse                41352  0 

serio_raw               8452  0 

parport_pc             37796  1 

parport                39496  2 lp,parport_pc

mii                     6912  1 e100

soundcore              11232  1 snd

intel_agp              26012  1 

agpgart                34888  1 intel_agp

ext3                  142856  3 

jbd                    62228  1 ext3

uhci_hcd               24968  0 

usbcore               134912  2 uhci_hcd

ide_generic             2432  0 

ide_cd                 33696  0 

cdrom                  38944  1 ide_cd

ide_disk               18560  5 

piix                   11780  1 

generic                 6276  0 

thermal                15624  0 

processor              31560  1 thermal

fan                     6020  0 

fbcon                  41504  0 

tileblit                3840  1 fbcon

font                    9344  1 fbcon

bitblit                 7168  1 fbcon

softcursor              3328  1 bitblit

vesafb                  9244  0 

capability              5896  0 

commoncap               8704  1 capability

root@ubuntu:~# iwlist scan

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



sit0      Interface doesn't support scanning.



wlan0     Scan completed :

          Cell 01 - Address: 00:14:6C:23:A9:1E

                    ESSID:"opteron"

                    Protocol:IEEE 802.11bg

                    Mode:Master

                    Channel:7

                    Encryption key:on

                    Bit Rates:54 Mb/s

                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 

                    Quality:134  Signal level:0  Noise level:21

                    Extra: Last beacon: 44ms ago

          Cell 02 - Address: 00:0F:66:D5:3A:05

                    ESSID:"Andrew"

                    Protocol:IEEE 802.11b

                    Mode:Master

                    Channel:6

                    Encryption key:on

                    Bit Rates:11 Mb/s

                    Extra: Rates (Mb/s): 1 2 5.5 11 

                    Quality:152  Signal level:0  Noise level:41

                    Extra: Last beacon: 691ms ago

          Cell 03 - Address: 00:14:95:00:A7:69

                    ESSID:"2WIRE970"

                    Protocol:IEEE 802.11bg

                    Mode:Master

                    Channel:6

                    Encryption key:on

                    Bit Rates:54 Mb/s

                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 

                    Quality:195  Signal level:0  Noise level:86

                    Extra: Last beacon: 857ms ago

          Cell 04 - Address: 00:18:3F:53:E4:11

                    ESSID:"2WIRE140"

                    Protocol:IEEE 802.11bg

                    Mode:Master

                    Channel:6

                    Encryption key:on

                    Bit Rates:54 Mb/s

                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 

                    Quality:146  Signal level:0  Noise level:33

                    Extra: Last beacon: 846ms ago

          Cell 05 - Address: 00:18:39:66:A2:52

                    ESSID:"rudra"

                    Protocol:IEEE 802.11bg

                    Mode:Master

                    Channel:6

                    Encryption key:on

                    Bit Rates:54 Mb/s

                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 

                    Quality:197  Signal level:0  Noise level:87

                    Extra: Last beacon: 849ms ago

          Cell 06 - Address: 00:14:BF:34:D6:20

                    ESSID:"simon"

                    Protocol:IEEE 802.11bg

                    Mode:Master

                    Channel:6

                    Encryption key:on

                    Bit Rates:54 Mb/s

                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 

                    Quality:199  Signal level:0  Noise level:89

                    Extra: Last beacon: 881ms ago

          Cell 07 - Address: 00:18:39:55:49:34

                    ESSID:"Davidcont"

                    Protocol:IEEE 802.11bg

                    Mode:Master

                    Channel:6

                    Encryption key:on

                    Bit Rates:54 Mb/s

                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 

                    Quality:180  Signal level:0  Noise level:69

                    Extra: Last beacon: 981ms ago

          Cell 08 - Address: 00:14:95:53:D8:7A

                    ESSID:"2WIRE626"

                    Protocol:IEEE 802.11bg

                    Mode:Master

                    Channel:6

                    Encryption key:on

                    Bit Rates:54 Mb/s

                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 

                    Quality:148  Signal level:0  Noise level:34

                    Extra: Last beacon: 869ms ago

          Cell 09 - Address: 00:16:B6:B1:5C:83

                    ESSID:"linksys"

                    Protocol:IEEE 802.11bg

                    Mode:Master

                    Channel:6

                    Encryption key:on

                    Bit Rates:54 Mb/s

                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 

                    Quality:148  Signal level:0  Noise level:34

                    Extra: Last beacon: 845ms ago

          Cell 10 - Address: 00:13:46:A1:A0:FC

                    ESSID:"<hidden>"

                    Protocol:IEEE 802.11bg

                    Mode:Master

                    Channel:6

                    Encryption key:on

                    Bit Rates:54 Mb/s

                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 

                    Quality:144  Signal level:0  Noise level:32

                    Extra: Last beacon: 897ms ago

          Cell 11 - Address: 00:18:39:EB:96:A4

                    ESSID:"Austin"

                    Protocol:IEEE 802.11bg

                    Mode:Master

                    Channel:11

                    Encryption key:on

                    Bit Rates:54 Mb/s

                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 

                    Quality:220  Signal level:0  Noise level:98

                    Extra: Last beacon: 6ms ago

          Cell 12 - Address: 4E:43:8A:0D:65:AE

                    ESSID:"production"

                    Protocol:IEEE 802.11b

                    Mode:Ad-Hoc

                    Channel:11

                    Encryption key:off

                    Bit Rates:11 Mb/s

                    Extra: Rates (Mb/s): 1 2 5.5 11 

                    Quality:151  Signal level:0  Noise level:34

                    Extra: Last beacon: 18ms ago

          Cell 13 - Address: 00:13:46:C7:8A:4E

                    ESSID:"<hidden>"

                    Protocol:IEEE 802.11bg

                    Mode:Master

                    Channel:1

                    Encryption key:on

                    Bit Rates:54 Mb/s

                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 

                    Quality:142  Signal level:0  Noise level:31

                    Extra: Last beacon: 1458ms ago

          Cell 14 - Address: 00:16:B6:22:78:11

                    ESSID:"<hidden>"

                    Protocol:IEEE 802.11bg

                    Mode:Master

                    Channel:6

                    Encryption key:on

                    Bit Rates:54 Mb/s

                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 

                    Quality:179  Signal level:0  Noise level:65

                    Extra: Last beacon: 882ms ago



root@ubuntu:~# cat /etc/network/interfaces

# This file describes the network interfaces available on your system

# and how to activate them. For more information, see interfaces(5).



# The loopback network interface

#auto lo

#iface lo inet loopback



# The primary network interface



#iface eth0 inet dhcp



auto wlan0

iface wlan0 inet dhcp

wpa-driver wext

wpa-conf managed

wpa-ssid opteron

wpa-ap-scan 1

wpa-proto RSN

wpa-pairwise CCMP

wpa-group CCMP

wpa-key-mgmt WPA-PSK

wpa-psk 009a2f5c51bd64848bdb590fdd45d4c02ac239becafd5d69f6d571615812775a

root@ubuntu:~# cat /etc/modprobe.d/ndiswrapper

cat: /etc/modprobe.d/ndiswrapper: No such file or directory

root@ubuntu:~# cat /etc/resolv.conf

nameserver 192.168.1.1

root@ubuntu:~# 
```
> the above was the info i was told to post from thi thread [http://www.ubuntuforums.org/showthread.php?t=318539](http://www.ubuntuforums.org/showthread.php?t=318539) 


i am not using the ndiswrapper driver. instead i am trying to use th r818x module in the kernel.
i do nothing to get the card detected, as in i don't modprobe any modules, ubuntu automatically load the r818x module. it might be that i am supposed to load some other modules but i don't kow which ones. 

please help
any help is very much appreciated since i have spent the last 2 days on this and am at my limit now. 

Thank you for reading the long post.

---

### Post by siciliancasanova on 2007-03-12
Have you tried using [wpa_supplicant]("http://hostap.epitest.fi/wpa_supplicant/")?

It should be found in Synaptic as well.

---

### Post by wieman01 on 2007-03-12
You had best try to connect to unsecured networks in the first place, otherwise this is a moving target. Don't try to figure out two things at a time if you know what I mean.

---

