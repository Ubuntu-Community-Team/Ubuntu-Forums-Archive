---
title: "PRO/Wireless 3945ABG problem in Ubuntu 8.10"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by seriousstorm85 on 2008-11-21
I have upgraded my Ubuntu 8.04 to 8.10 via my wireless network connection.

Everything seemed fine however in 8.10, I could not see my Wirless Router in the list of others.

I then looked for the model of the wirless card and the driver it uses.

The model is PRO/Wireless 3945ABG [Golan] Network Connection and it uses iwl3945

I have looked at several posts and could find the solution. So I decided to format my ubuntu partition and install 8.10 fresh incase something upgrade broke it.

With the freshly installed Ubuntu 8.10 I still have the same problem. This problem did not happen to me in 8.04 or 7.10.

The only thing I have changed in this fresh install is that I have changed is the iwl3495 file in etc/modprobe.d using these instructions

> 1.sudo su

2.echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945


3.reboot 


Still no change, I can't see my wireless router

Detail from my installation

To Follow

---

### Post by seriousstorm85 on 2008-11-21
List of displayed wireless routers

> 
elmi@elmi-laptop:~$ sudo iwlist wlan0 scan
    

(My home router doesn't appear its called “NETGEAR”, connecting to a friends router called “leeb” doesn't work even though the password and other details were correct)

wlan0     Scan completed :

          Cell 01 - Address: 00:14:BF:C4:AF:85

                    ESSID:"leeb"

                    Mode:Master

                    Channel:6

                    Frequency:2.437 GHz (Channel 6)

                    Quality=74/100  Signal level:-60 dBm  Noise level=-127 dBm

                    Encryption key:on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s

                              12 Mb/s; 48 Mb/s

                    Extra:tsf=000000739c581322

                    Extra: Last beacon: 1384ms ago

          Cell 02 - Address: 00:1F:9F:04:5A:DD

                    ESSID:"BTHomeHub-727B"

                    Mode:Master

                    Channel:11

                    Frequency:2.462 GHz (Channel 11)

                    Quality=46/100  Signal level:-81 dBm  Noise level=-127 dBm

                    Encryption key:on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s

                              12 Mb/s; 48 Mb/s

                    Extra:tsf=0000011f05b1618d

                    Extra: Last beacon: 1240ms ago

          Cell 03 - Address: 00:1E:2A:EB:6F:AA

                    ESSID:"PRIMAGUI"

                    Mode:Master

                    Channel:11

                    Frequency:2.462 GHz (Channel 11)

                    Quality=46/100  Signal level:-81 dBm  Noise level=-127 dBm

                    Encryption key:on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s

                              12 Mb/s; 48 Mb/s

                    Extra:tsf=00000012f565a4ba

                    Extra: Last beacon: 1228ms ago

          Cell 04 - Address: 00:1F:E2:9C:03:E2

                    ESSID:"BTHomeHub2-CNWF"

                    Mode:Master

                    Channel:1

                    Frequency:2.412 GHz (Channel 1)

                    Quality=49/100  Signal level:-79 dBm  Noise level=-127 dBm

                    Encryption key:on

                    IE: WPA Version 1

                        Group Cipher : TKIP

                        Pairwise Ciphers (2) : CCMP TKIP

                        Authentication Suites (1) : PSK

                    IE: IEEE 802.11i/WPA2 Version 1

                        Group Cipher : TKIP

                        Pairwise Ciphers (2) : CCMP TKIP

                        Authentication Suites (1) : PSK

                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s

                              12 Mb/s; 48 Mb/s

                    Extra:tsf=0000011f63c7c04e

                    Extra: Last beacon: 1788ms ago

          Cell 05 - Address: 00:1F:33:05:B4:04

                    ESSID:"SKY39694"

                    Mode:Master

                    Channel:11

                    Frequency:2.462 GHz (Channel 11)

                    Quality=52/100  Signal level:-77 dBm  Noise level=-127 dBm

                    Encryption key:on

                    IE: WPA Version 1

                        Group Cipher : TKIP

                        Pairwise Ciphers (1) : TKIP

                        Authentication Suites (1) : PSK

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s

                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s

                              36 Mb/s; 48 Mb/s; 54 Mb/s

                    Extra:tsf=00000001982461c5

                    Extra: Last beacon: 1236ms ago


---

### Post by seriousstorm85 on 2008-11-21
Details of my network cards

> 

elmi@elmi-laptop:~$ sudo lshw -C Network



[sudo] password for elmi: 

  *-network               

       description: Wireless interface

       product: PRO/Wireless 3945ABG [Golan] Network Connection

       vendor: Intel Corporation

       physical id: 0

       bus info: pci@0000:0c:00.0

       logical name: wmaster0

       version: 02

       serial: 00:1b:77:a8:4e:f4

       width: 32 bits

       clock: 33MHz

       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless

       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

  *-network

       description: Ethernet interface

       product: BCM4401-B0 100Base-TX

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:03:00.0

       logical name: eth0

       version: 02

       serial: 00:1c:23:8d:68:94

       size: 10MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s

  *-network DISABLED

       description: Ethernet interface

       physical id: 2

       logical name: pan0

       serial: f2:37:c0:32:1d:c3

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



---

### Post by seriousstorm85 on 2008-11-21
.
> elmi@elmi-laptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1c:23:8d:68:94  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:17 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:278 errors:0 dropped:0 overruns:0 frame:0

          TX packets:278 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:17784 (17.7 KB)  TX bytes:17784 (17.7 KB)



wlan0     Link encap:Ethernet  HWaddr 00:1b:77:a8:4e:f4  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-A8-4E-F4-00-00-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)





---

### Post by seriousstorm85 on 2008-11-21
.
> elmi@elmi-laptop:~$ lsmod


Module                  Size  Used by

nls_iso8859_1          12032  1 

nls_cp437              13696  1 

vfat                   18816  1 

fat                    57376  1 vfat

usb_storage            81728  2 

libusual               27156  1 usb_storage

af_packet              25728  2 

binfmt_misc            16904  1 

sco                    18308  2 

rfcomm                 44432  0 

bridge                 56980  0 

stp                    10628  1 bridge

bnep                   20480  2 

l2cap                  30464  6 rfcomm,bnep

bluetooth              61924  6 sco,rfcomm,bnep,l2cap

kvm                   142912  0 

ppdev                  15620  0 

acpi_cpufreq           15500  1 

cpufreq_conservative    14600  0 

cpufreq_userspace      11396  0 

cpufreq_ondemand       14988  1 

cpufreq_stats          13188  0 

cpufreq_powersave       9856  0 

freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats

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

snd_hda_intel         381488  5 

snd_pcm_oss            46848  0 

snd_mixer_oss          22784  1 snd_pcm_oss

arc4                    9984  2 

ecb                    10880  2 

crypto_blkcipher       25476  1 ecb

snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss

uvcvideo               62728  0 

iwl3945                98804  0 

snd_seq_dummy          10884  0 

compat_ioctl32          9344  1 uvcvideo

rfkill                 17176  2 iwl3945

joydev                 18368  0 

snd_seq_oss            38528  0 

mac80211              216820  1 iwl3945

videodev               41344  1 uvcvideo

serio_raw              13444  0 

snd_seq_midi           14336  0 

psmouse                45200  0 

snd_rawmidi            29824  1 snd_seq_midi

pcspkr                 10624  0 

dcdbas                 15008  0 

led_class              12164  1 iwl3945

snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi

v4l1_compat            22404  2 uvcvideo,videodev

evdev                  17696  19 

snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

nvidia               6900560  44 

cfg80211               32392  2 iwl3945,mac80211

sdhci_pci              15360  0 



sdhci                  23940  1 sdhci_pci

i2c_core               31892  1 nvidia

mmc_core               58268  1 sdhci

ricoh_mmc              11904  0 

snd_timer              29960  2 snd_pcm,snd_seq

snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

snd                    63268  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

video                  25104  10 

output                 11008  1 video

soundcore              15328  1 snd

wmi                    14504  0 

intel_agp              33724  0 

ac                     12292  0 

button                 14224  0 

snd_page_alloc         16136  2 snd_hda_intel,snd_pcm

battery                18436  0 

iTCO_wdt               18596  0 

iTCO_vendor_support    11652  1 iTCO_wdt

agpgart                42184  2 nvidia,intel_agp

shpchp                 37908  0 

pci_hotplug            35236  1 shpchp

ext3                  133384  1 

jbd                    55444  1 ext3

mbcache                16004  1 ext3

sr_mod                 22212  0 

cdrom                  43168  1 sr_mod

sd_mod                 42264  6 

crc_t10dif              9984  1 sd_mod

sg                     39732  0 

ata_piix               24580  2 

pata_acpi              12160  0 

usbhid                 35840  0 

hid                    50560  1 usbhid

b44                    35984  0 

ata_generic            12932  0 

ohci1394               37936  0 

libata                177312  3 ata_piix,pata_acpi,ata_generic

scsi_mod              155212  6 usb_storage,sbp2,sr_mod,sd_mod,sg,libata

ieee1394               96324  2 sbp2,ohci1394

dock                   16656  1 libata

ssb                    40580  1 b44

mii                    13440  1 b44

ehci_hcd               43276  0 

uhci_hcd               30736  0 

usbcore               148848  7 usb_storage,libusual,uvcvideo,usbhid,ehci_hcd,uhci_hcd

dm_mirror              26880  0 

dm_log                 17924  1 dm_mirror

dm_snapshot            26276  0 

dm_mod                 63432  3 dm_mirror,dm_log,dm_snapshot

thermal                23708  0 

processor              42156  4 acpi_cpufreq,thermal

fan                    12548  0 

fbcon                  47648  0 

tileblit               10880  1 fbcon

font                   16512  1 fbcon

bitblit                13824  1 fbcon

softcursor              9984  1 bitblit

fuse                   60828  5 





---

### Post by iponeverything on 2008-11-21
First. log on to your wireless router and try to change the channel to something less than 10.

next add this to 
```
sudo echo options cfg80211 ieee80211_regdom=EU >> /etc/modprobe.d/options

```

and reboot and give it try.

ref:

[http://www.linux-solved.com/post/solved-iwl3945-problem-after-upgrading-to-2-6-27-29338.html](http://www.linux-solved.com/post/solved-iwl3945-problem-after-upgrading-to-2-6-27-29338.html)

---

