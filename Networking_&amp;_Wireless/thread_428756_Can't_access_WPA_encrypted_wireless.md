---
title: "Can't access WPA encrypted wireless"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by brim4brim on 2007-04-30
Right so I followed the howto on this thread:
[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

and substituted wext with ipw for my driver but although I can see the router and it says it is sending/recieving packets, I'm not able to access the web or even the router using its ip in firefox.

Can someone give me a clue as to what is wrong or what I need to do to get information about what is wrong.  I can ping the router using network tools so it seems its just the WPA setup.

I'm using 6.06LTS so do I need to install later version of ipw2200 drivers or are the ones distributed with 6.06 good enough?

---

### Post by brim4brim on 2007-04-30
So I've tried to follow the stickied howto thread now too so here is the output from the sections that say what to do if it isn't working:

> 
uname -a
Linux brian-laptop 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:12:F0:62:0B:CD
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2027 errors:0 dropped:0 overruns:0 frame:0
          TX packets:666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0xc000 Memory:dfbff000-dfbfffff

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

iwconfig
no output

lsmod
Module                  Size  Used by
nls_utf8                2176  1
vfat                   13440  1
fat                    53020  1 vfat
usb_storage            74176  1
isofs                  37688  1
udf                    88452  0
ipv6                  265600  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
fglrx                 399916  9
speedstep_centrino      8400  1
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
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ac                      5252  1 acpi_sbs
nls_cp437               5888  2
ntfs                  103536  1
dm_mod                 58936  1
md_mod                 72532  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
xircom_cb              11520  0
xircom_tulip_cb        18864  0
pcmcia                 40508  0
tg3                   102020  0
snd_intel8x0           33692  3
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
ipw2200               107308  0
yenta_socket           28428  2
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
joydev                 10048  0
tsdev                   8000  0
snd_pcm                89864  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
rtc                    13492  0
ieee80211              37064  1 ipw2200
ieee80211_crypt         6272  1 ieee80211
pcspkr                  2180  0
snd                    55268  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
psmouse                36228  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  2 fglrx,intel_agp
serio_raw               7300  0
hsfmc97ich             67216  0
hsfserial              23204  1 hsfmc97ich
hsfengine            1300500  2 hsfmc97ich,hsfserial
hsfosspec             102632  6 hsfmc97ich,hsfserial,hsfengine
hsfsoar                85256  1 hsfmc97ich
sg                     37920  0
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               32008  0
uhci_hcd               33680  0
usbcore               129668  5 usb_storage,hsfosspec,ehci_hcd,uhci_hcd
sr_mod                 16932  1
cdrom                  38560  1 sr_mod
sd_mod                 19984  6
generic                 5124  0
ata_piix               11012  8
ahci                   17668  0
libata                 78992  2 ata_piix,ahci
scsi_mod              139496  6 usb_storage,sg,sr_mod,sd_mod,ahci,libata
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

iwlist scan
eth1      Scan completed :
          Cell 01 - Address: 00:11:50:FE:37:09
                    ESSID:"Belkin_G_Plus_MIMO_FE3709"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=84/100  Signal level=-46 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 395ms ago

cat /etc/network/interfaces
eth1      Scan completed :
          Cell 01 - Address: 00:11:50:FE:37:09
                    ESSID:"Belkin_G_Plus_MIMO_FE3709"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=84/100  Signal level=-46 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 395ms ago

cat /etc/modprobe.d/ndiswrapper
no such file or directory

cat /etc/resolve.conf
no output


I've tried it with the ipw driver and the generic driver.  After following this howto, the notification area that gives info on connections says it is disconnected.

The router has DHCP enabled and is using WPA PSK encryption.  It is working fine in windows.

---

### Post by brim4brim on 2007-05-01
Fixed it and am typing this from Ubuntu wireless connection.  I installed Network-Manager-Gnome by downloading the relevant packages from packages.ubuntu.com from windows.

---

