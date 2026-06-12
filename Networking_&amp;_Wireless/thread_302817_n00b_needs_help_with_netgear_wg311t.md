---
title: "n00b needs help with netgear wg311t"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by Synnove on 2006-11-19
I've installed 6.10 and i'm trying to get my wireless working. I've tried [https://help.ubuntu.com/community/WifiDocs/WirelessNetworking]("https://help.ubuntu.com/community/WifiDocs/WirelessNetworking")using this guide but no luck on a wep,wpa or unsecure connection. I've poked around the forums but i'm not really sure what i'm looking for. I'm using a netgear wg311t pci card. If someone could talk me through it it would be ace. ](*,)

---

### Post by hal10000 on 2006-11-19
After upgrading to 6.10 my wireless card (Netgear 311MA PCI) didn't work.
I figured out that the problem was the wrong driver was loaded (prism2_pci).

Maybe your problem is the same if you have a prism 2.5 (or similar) card.

Run [COLOR="Red"]lspci[/COLOR] in a xterm and look if there is something like:
```
00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
```
If so, then first look if this driver is loaded:
```
lsmod | grep prism
```
If you get a line where the prism2 driver is mentioned than this may be your problem. So remove the driver: [COLOR="Red"]sudo rmmod prism2_pci[/COLOR] and any other prism2 driver you found with lsmod |grep prism and load the orinoco_pci driver (with my card this driver works fine): [COLOR="Red"]sudo modprobe orinoco_pci[/COLOR].
Next reload your network-settins: [COLOR="Red"]sudo /etc/init.d/network stop [/COLOR] and [COLOR="Red"]sudo /etc/init.d/network start[/COLOR].
Type [COLOR="Red"]iwconfig[/COLOR] to see if your card works and if it gets your access point. 
On my pc it looks like:
```

eth0      IEEE 802.11b  ESSID:"myessid"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:50:FC:BA:16:3A
          Bit Rate:11 Mb/s   Sensitivity=1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=34/70  Signal level=-66 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:759  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1197   Missed beacon:0
```
With [COLOR="Red"]ifconfig [/COLOR] you can see if it got an ip-address:
```
eth0      Protokoll:Ethernet  Hardware Adresse 00:09:5B:74:67:B3
          inet Adresse:192.168.2.105  Bcast:192.168.2.255  Maske:255.255.255.0
          inet6 Adresse: fe80::209:5bff:fe74:67b3/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14286 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:4900064 (4.6 MiB)  TX bytes:2177196 (2.0 MiB)
          Interrupt:11
```.
Next, try [COLOR="Red"]ping [www.google.com](www.google.com)[/COLOR] (or any other internet-address you like, [www.nasa.gov](www.nasa.gov) or [www.kde.org](www.kde.org) ....).
If you get an answer like:
```

PING www.l.google.com (209.85.135.104) 56(84) bytes of data.
64 bytes from mu-in-f104.google.com (209.85.135.104): icmp_seq=1 ttl=246 time=34.7 ms
64 bytes from mu-in-f104.google.com (209.85.135.104): icmp_seq=2 ttl=246 time=30.4 ms
64 bytes from mu-in-f104.google.com (209.85.135.104): icmp_seq=3 ttl=246 time=33.1 ms
64 bytes from mu-in-f104.google.com (209.85.135.104): icmp_seq=4 ttl=246 time=30.4 ms

```
then your network setting are o.k. The onla thing you have to do now is to prevent the prism2_pci from being loaded at next boot-time. Choose an text-editor you like (gedit, nano, kate or any other) and type: [COLOR="Red"]sudo gedit /etc/modprobe.d/blacklist [/COLOR]. At the end of this file add a new line with:
```
blacklist prism2_pci
```. This prevents the prism2_pci driver from being loaded next time you boot.
If it works, be happy .... if not, then your problem might be another as mine. In this case if would be helpful if you post the outputs of the following commands/files:

1. lspci
2. iwconfig
3. ifconfig
4. the content of the file /etc/network/interfaces
5. lsmod

With this Information we can try your card getting work.

---

### Post by Synnove on 2006-11-19
thanks for the reply i'll try this out.

---

### Post by hal10000 on 2006-11-19
I have forgotten a small detail:

If you fugure out which kernel modules are already loaded, you should also look for the orinoco_pci and orinoco module:
[COLOR="Red"]lsmod | grep orino[/COLOR]
If it is loaded, you must first unload both orinoco and all prism2 modules:

[COLOR="Red"]sudo rmmod prism2_pci orinoco_pci orinoco[/COLOR]

and then reload the orinoco_pci: [COLOR="Red"]sudo modprobe orinoco_pci[/COLOR] and then go further with restarting your network (see above).

---

### Post by Synnove on 2006-11-19
i didn't find "00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)"

i had "00:07.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)"

i'm posting the outputs you asked for here:

```

phil@phil-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:07.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc R350 AH [Radeon 9800]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800] (Secondary)


phil@phil-desktop:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"126HOME"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:785  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


phil@phil-desktop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:6C:32:96:3C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:303 (303.0 b)  TX bytes:468 (468.0 b)

eth0      Link encap:Ethernet  HWaddr 00:0C:76:57:C0:8C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:436 (436.0 b)  TX bytes:436 (436.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-14-6C-32-96-3C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13810 errors:0 dropped:0 overruns:0 frame:53297
          TX packets:12979 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:2387245 (2.2 MiB)  TX bytes:642740 (627.6 KiB)
          Interrupt:185 Memory:e08e0000-e08f0000



contents of /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


iface ath0 inet dhcp
wireless-essid 126HOME
wireless-key 

auto wlan0
iface wlan0 inet dhcp




auto ath0 


phil@phil-desktop:~$ lsmod
Module                  Size  Used by
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
radeon                118816  2 
drm                    74644  3 radeon
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
nls_utf8                3200  1 
ntfs                  112116  1 
af_packet              24584  4 
lp                     12964  0 
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
i2c_viapro              9876  0 
i2c_core               23424  2 i2c_ec,i2c_viapro
snd_seq_midi            9984  0 
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tsdev                   9152  0 
via_ircc               28948  0 
snd_via82xx            30360  1 
gameport               17160  1 snd_via82xx
snd_ac97_codec         97696  1 snd_via82xx
snd_ac97_bus            3456  1 snd_ac97_codec
irda                  214332  1 via_ircc
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
serio_raw               8452  0 
evdev                  11392  1 
pcspkr                  4352  0 
crc_ccitt               3200  1 irda
snd_pcm                84612  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_seq,snd_pcm
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart        10240  1 snd_via82xx
snd_rawmidi            27264  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    58372  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
psmouse                41352  0 
via_agp                11264  1 
agpgart                34888  2 drm,via_agp
wlan_scan_sta          15744  1 
soundcore              11232  1 snd
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
floppy                 63044  0 
via_rhine              26116  0 
mii                     6912  1 via_rhine
ath_pci               100000  0 
ath_rate_sample        16512  1 ath_pci
wlan                  207580  4 wlan_scan_sta,ath_pci,ath_rate_sample
ath_hal               192976  3 ath_pci,ath_rate_sample
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  3 ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  4 
via82cxxx              10500  0 [permanent]
generic                 5764  0 
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

```

---

