---
title: "Help Networking"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by J Cleveland on 2006-07-24
I am running Ubuntu linux 6.06, and I have a Netgear WG311v2 wireless card in the PCI slot. I can not get it to work. I have tried wifi drivers. I do not have access to the internet and I don't have any progams like fedora. I have a Dlink router, but I cannot connect to it. I know the IP of the router. The 3 things that show up in network connections are wlan0, eth0 and eth1. Any help on getting my wireless card configured using terminal commands and such to get it to pick up my router???

---

### Post by dbott67 on 2006-07-24
From the command line, you can type:

```
dbott@dapperdrake:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:40:05:XX:XX:XX
                    ESSID:"bott"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-41 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:13:46:EF:DD:3A
                    ESSID:"default"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-91 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

dbott@dapperdrake:~$


```

There's also 'wifi radar' in the repositories, which is GUI for managing your wireless connections.

-Dave

---

### Post by J Cleveland on 2006-07-24
I know, I have Wi-Fi Radar. But it doesn't connect to my router. None of the bars are lit up .

---

### Post by J Cleveland on 2006-07-25
Please help!

---

### Post by wog on 2006-07-25
I'm not absolutely certain, but I think the above command line example was a request for information. Just saying "I know" to the example is often the equivalent of saying "leave me alone".

Just FYI in case you really want help.

And if you don't have Internet access, pipe your result to a text file and post that from the machine you do have Internet access with.

---

### Post by philippe_carlo on 2006-07-25
Hi, if you want us to help out, we will need more info. 

Post the results of all commands below.
Also Answer following questions?

Does your router use DHCP?
Do you use WEP/WPA?
Do you know which driver you need?

```

sudo ifconfig
sudo iwconfig
sudo lsmod
sudo iwlist eth1 scan
sudo iwlist wlan0 scan

```

---

### Post by J Cleveland on 2006-07-25
I do not know what drivers I need. I need an .inf file, which madwifi doesn't have. 

Here's the results::


```
jay@jonscomputer:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"Deckman"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Encryption key:off
          Power Management:off
          Link Quality=36/100  Signal level=11/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

```
jay@jonscomputer:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:29:D5:B1:AA
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:233 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:01:29:D5:B1:C7
          inet6 addr: fe80::201:29ff:fed5:b1c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21926 (21.4 KiB)  TX bytes:492 (492.0 b)
          Interrupt:66

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:623 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:51004 (49.8 KiB)  TX bytes:51004 (49.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:06:DE:E2
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:74 Base address:0xc000


```


```
jay@jonscomputer:~$ sudo lsmod
Module                  Size  Used by
rfcomm                 44512  0
l2cap                  29376  5 rfcomm
bluetooth              58116  4 rfcomm,l2cap
ipv6                  298240  10
ppdev                  10760  0
cpufreq_userspace       8544  0
cpufreq_stats           7624  0
freq_table              5888  1 cpufreq_stats
cpufreq_powersave       2688  0
cpufreq_ondemand        9128  0
cpufreq_conservative    10408  0
video                  18248  0
tc1100_wmi              8520  0
sony_acpi               6548  0
pcc_acpi               15488  0
hotkey                 13128  0
dev_acpi               14724  0
container               5696  0
button                  8288  0
acpi_sbs               24024  0
battery                11656  1 acpi_sbs
i2c_acpi_ec             6400  1 acpi_sbs
ac                      6600  1 acpi_sbs
ext2                   74064  1
dm_mod                 62536  1
md_mod                 76152  0
af_packet              27020  2
sbp2                   27268  0
psmouse                39748  0
parport_pc             40176  0
lp                     14464  0
parport                43532  3 ppdev,parport_pc,lp
nvidia               5432600  12
floppy                 73544  0
tsdev                   9600  0
irtty_sir              10688  0
sir_dev                23480  1 irtty_sir
irda                  220524  2 irtty_sir,sir_dev
crc_ccitt               3008  1 irda
pcspkr                  3016  0
shpchp                 50720  0
pci_hotplug            32592  1 shpchp
sk98lin               166880  0
usbhid                 42400  0
snd_intel8x0           37800  1
snd_ac97_codec        109628  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
acx                   102992  0
skge                   43152  0
snd_pcm_oss            58784  0
snd_mixer_oss          19968  1 snd_pcm_oss
snd_pcm               104008  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              28424  1 snd_pcm
snd                    68000  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              12640  1 snd
i2c_nforce2             8640  0
snd_page_alloc         13328  2 snd_intel8x0,snd_pcm
i2c_core               26048  3 i2c_acpi_ec,nvidia,i2c_nforce2
sr_mod                 19108  0
sg                     43056  0
evdev                  13888  3
xfs                   546592  1
exportfs                7488  1 xfs
usb_storage            81344  0
ide_generic             2176  0
ehci_hcd               35592  0
ohci_hcd               23044  0
usbcore               146428  6 usbhid,acx,usb_storage,ehci_hcd,ohci_hcd
ohci1394               36684  0
ieee1394              368472  2 sbp2,ohci1394
forcedeth              27268  0
ide_cd                 35104  0
cdrom                  40568  2 sr_mod,ide_cd
generic                 6724  0
sd_mod                 20864  4
amd74xx                16304  0 [permanent]
sata_nv                11780  6
libata                 84960  1 sata_nv
scsi_mod              159928  6 sbp2,sr_mod,sg,usb_storage,sd_mod,libata
thermal                15884  0
processor              28584  1 thermal
fan                     5832  0
capability              6536  0
commoncap               9088  1 capability
vga16fb                14480  1
cfbcopyarea             4544  1 vga16fb
vgastate                9792  1 vga16fb
cfbimgblt               3584  1 vga16fb
cfbfillrect             5184  1 vga16fb
fbcon                  42496  72
tileblit                3520  1 fbcon
font                    9344  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3136  1 bitblit


```

```

jay@jonscomputer:~$ sudo iwlist eth1 scan
eth1      Interface doesn't support scanning.


jay@jonscomputer:~$ sudo iwlist wlan0 scan
wlan0     No scan results





```



Also, I've bought a bunch of ethernet cords and connectors, and ran them up to my computer. The cords and the connectors work because I've plugged them into my windows computer and got a connection, but when I run them to my computer, I still get the network icon with the slash through it, saying I have no network connection. The green light over the port in the back of my computer is lit up, meaning that my mobo recognizes it, but Ubuntu won't connect.

---

### Post by J Cleveland on 2006-07-25
I really need this. My mom is losing trust in Ubuntu.

---

