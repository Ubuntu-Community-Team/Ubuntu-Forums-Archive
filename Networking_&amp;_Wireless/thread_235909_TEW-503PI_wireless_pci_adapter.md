---
title: "TEW-503PI wireless pci adapter"
date: 2006-08-13
forum: Networking &amp; Wireless
---

### Post by tastefulasever on 2006-08-13
This is my first time trying to set up wireless networking.  I need to install 7 of these adapters.  Here we go.  Supposedly these use an Atheros AR5414 chipset.  Should work out of the box with the madwifi drivers, but I couldn't get them to.  I'm trying to use the windows drivers with ndiswrapper now, but I can't call up wlan0 with iwconfig.

```
mtspurr@mtspurr01:~$ sudo iwconfig wlan0 essid linksys
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.[CODE]

However dmesg says it's there.

[CODE]mtspurr@mtspurr01:~$ dmesg | grep wlan
[17179608.664000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179608.700000] wlan: 0.8.4.2 (svn 2006-07-10)
[17180334.780000] wlan0: vendor: ''
[17180334.780000] wlan0: ndiswrapper ethernet device 00:14:a5:3c:7f:82 using driver net5211, 168C:001B:17F9:000C.5.conf
[17180334.780000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK[CODE]

Once again, iwconfig can't see it.

[CODE]mtspurr@mtspurr01:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:DA:D6:DF
          Bit Rate:54 Mb/s
          Power Management min timeout:0us  mode:All packets received
          Link Quality:0/100  Signal level:-46 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Also, lspci doesn't recognize the chipset for whatever reason.

```
mtspurr@mtspurr01:~$ lspci | grep Eth
0000:01:09.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001b (rev 01)

```

Finally, here is the output from lsmod

```
mtspurr@mtspurr01:~$ lsmod
Module                  Size  Used by
ndiswrapper           177364  0
nls_cp437               5888  1
isofs                  37688  1
udf                    88452  0
new_wlan_wep            7296  0
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
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
ipv6                  265728  6
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
af_packet              22920  2
snd_ens1371            24672  1
gameport               15496  1 snd_ens1371
snd_rawmidi            25504  1 snd_ens1371
snd_seq_device          8716  1 snd_rawmidi
snd_ac97_codec         93088  1 snd_ens1371
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  1 snd_pcm
3c59x                  45608  0
mii                     5888  1 3c59x
new_wlan_scan_sta      15232  0
new_wlan              204892  2 new_wlan_wep,new_wlan_scan_sta
wlan                  144924  0
snd_ac97_bus            2304  1 snd_ac97_codec
tsdev                   8000  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
rtc                    13492  0
pcspkr                  2180  0
serio_raw               7300  0
psmouse                36100  0
floppy                 62148  0
hw_random               5652  0
intel_agp              22940  1
agpgart                34888  2 intel_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
i2c_i810                5252  0
i2c_algo_bit            9608  1 i2c_i810
i2c_core               21904  2 i2c_acpi_ec,i2c_algo_bit
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33680  0
usbcore               130692  3 ndiswrapper,uhci_hcd
ide_cd                 33028  1
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


Help is greatly appreciated.  I have 7 of these to install, I'm feeling slightly frantic.  Please let me know if I can be more informative, and feel free to poke fun at my ignorance.  Meanwhile, there's a fair possibility I'll stumble across an answer on my own.  Thanks.

---

### Post by tastefulasever on 2006-08-14
Go ahead and disregard that last post.  I have these working using madwifi driver now.  Using wireless assistant I can connect to the network.  For anyone else having trouble with this device, here's what I did. Make sure you have access to the universe repositories.

```
~# sudo apt-get install wlassistant dhcpcd
~# sudo wlassistant
```

Configure your adapter in wlassistant and try to connect.  Make sure to hit the refresh button if you change your wireless router settings.

Also, here is my /etc/network/interfaces file.

```

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wireless-essid youressid
wireless-channel yourrouterchannel
wireless-mode managed
```

---

### Post by tastefulasever on 2006-08-14
One more thing.  To configure a connection in wireless assistant, right click the network that you wish to connect to and select the configure and connect option or the edit settings options. Good luck.

---

