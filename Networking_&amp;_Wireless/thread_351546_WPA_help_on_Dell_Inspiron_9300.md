---
title: "WPA help on Dell Inspiron 9300"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by Zerileous on 2007-02-02
I am pretty new to linux.  I have tried a few times and been turned off by not being able to get stuff to work right, but I don't really know what I am doing.  I am using Dapper right now, had Horay a while ago but didnt get far on it either.

I am trying to connect to a WPA secured network (Linksys router).  This uses the ipw2200 driver, which I am pleased to find working in dapper.  Also, the touchpad works perfectly out of the box.  I am impressed.  It would be very dificult to use manual configuration for the network, because I dont have access to the router cp.  I have tried just about everything I can find for getting wpa  support going and its not working.  I have installed NetworkManager Applet 0.6.2, but it doesn't do anything except say "no network devices have been found".  It worked for a while with the wired connection, but now it just doesnt work at all.  I have tried numerous tutorials and /etc/network/interface configurations. 

Im really not sure what to do, but I need to be able to access alot of wifi networks because I my laptop travels around a college town.

One of the tutorials said to post the following if stumped:

zoidberg@zoidberg-laptop:~$ uname -a
Linux zoidberg-laptop 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686 GNU/Linux

zoidberg@zoidberg-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:12:3F:D7:52:BC
          inet addr:192.168.1.118  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fed7:52bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6950380 (6.6 MiB)  TX bytes:1532261 (1.4 MiB)
          Interrupt:209

eth1      Link encap:Ethernet  HWaddr 00:12:F0:88:94:D8
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xa000 Memory:dcffd000-dcffdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3290 (3.2 KiB)  TX bytes:3290 (3.2 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

zoidberg@zoidberg-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

zoidberg@zoidberg-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:"linksys_SES_33376"
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

zoidberg@zoidberg-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:D7:52:BC
          inet addr:192.168.1.118  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fed7:52bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8519 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6952818 (6.6 MiB)  TX bytes:1532261 (1.4 MiB)
          Interrupt:209

eth1      Link encap:Ethernet  HWaddr 00:12:F0:88:94:D8
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xa000 Memory:dcffd000-dcffdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3290 (3.2 KiB)  TX bytes:3290 (3.2 KiB)

zoidberg@zoidberg-laptop:~$ lsmod
Module                  Size  Used by
arc4                    2048  0
ieee80211_crypt_wep     5120  0
ipv6                  265856  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
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
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
nls_utf8                2176  1
ntfs                  103536  1
af_packet              22920  8
dm_mod                 58936  1
md_mod                 72532  0
pcmcia                 40508  0
sbp2                   24196  0
joydev                 10048  0
tsdev                   8000  0
sdhci                  14848  0
mmc_core               30104  1 sdhci
pcspkr                  2180  0
rtc                    13492  0
ipw2200               107308  0
ieee80211              37064  1 ipw2200
ieee80211_crypt         6272  2 ieee80211_crypt_wep,ieee80211
ieee80211_1_1_13       38216  0
ieee80211_1_1_13_crypt     6784  1 ieee80211_1_1_13
parport_pc             35780  0
usbhid                 39904  0
nvidia               4551028  0
i2c_core               21904  2 i2c_acpi_ec,nvidia
b44                    25740  0
mii                     5888  1 b44
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
psmouse                36100  0
serio_raw               7300  0
intel_agp              22940  1
snd_intel8x0           33692  1
agpgart                34888  2 nvidia,intel_agp
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
sg                     37920  0
sr_mod                 16932  0
cdrom                  38560  1 sr_mod
evdev                   9856  2
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
uhci_hcd               33808  0
usbcore               130820  4 usbhid,ehci_hcd,uhci_hcd
sd_mod                 19984  4
generic                 5124  0
ata_piix               11012  6
ahci                   17284  0
libata                 78992  2 ata_piix,ahci
scsi_mod              139496  6 sbp2,sg,sr_mod,sd_mod,ahci,libata
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

zoidberg@zoidberg-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.

zoidberg@zoidberg-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid linksys_SES_33376
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <censored>

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

zoidberg@zoidberg-laptop:~$ cat /etc/modprobe d/ndiswrapper
cat: /etc/modprobe: No such file or directory
cat: d/ndiswrapper: No such file or directory

zoidberg@zoidberg-laptop:~$ cat /etc/resolv.conf
search domain_not_set.invalid
nameserver 192.168.0.1

Any help would be greatly appreciated,
justin

---

### Post by wieman01 on 2007-02-02
"iwlist scan" suggests that your card has not been recognized. Could you edit "/etc/network/interfaces" and paste this:
> auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
Then save the file, restart the network:
> sudo /etc/init.d/networking restart
Now scan once again using another terminal window:
> iwlist scan
Please post the results of the scan.

---

### Post by tribaal on 2007-02-02
**Edit:** Yeah hum ok I re-read your iwconfig output... :)

Silly answer, but errr... did you turn on the wireless chip? 
The bluetooth LED should be flashing blue if the card is turned on (I don't know why my wifi LED doesn't seem to work on my inspiron 9300).

The keyboard shortcut to turn on wireless is "Fn-F2" on Inspirons.

Just trying to rule out a possible cause of the problem =)

- trib'

---

### Post by Zerileous on 2007-02-02
here is the content of /etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


Restarting the network leads to the same problem.  I believe the problem is with getting DHCP from the router.  Here is what is shown when attemting to restart the network (the relevant portion of output):
Listening on LPF/eth1/00:12:f0:88:94:d8
Sending on   LPF/eth1/00:12:f0:88:94:d8
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

The router should be familiar with my MAC address, it has connected for a while with no issues via windows.

Fn-f2 produces no noticed response in Gnome or keyboard lighting.  However, it does change iwlist scan.  Restarting the network still does not allow get any DHCPOFFERS from the router.iwli

Here is the iwlist scan for eth1 (wifi active...):
zoidberg@zoidberg-laptop:~$ iwlist scan
eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:19:B0:43
                    ESSID:"linksys_SES_33376"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=82/100  Signal level=-48 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1888ms ago

Note: eth0 is my wired connection which is working perfectly.  eth1 is the wifi.  Every time i run /etc/init.d/networking restart, i then have to hit fn+f2 and wait a few seconds, before iwlist scan will provide these results rather than the <etho...No scan results>,  

In about an hour I will be able to test the wifi on a WEP network, will update.

peace
justin

---

### Post by Strider42 on 2007-02-02
> **tribaal said:**
> **Edit:** Yeah hum ok I re-read your iwconfig output... :)

Silly answer, but errr... did you turn on the wireless chip? 
The bluetooth LED should be flashing blue if the card is turned on
- trib'

Not sure that's entirely true on all Inspirons.  I have an 8600 and the blue LED is never lit and when it was running XP it was always connected via WiFi.  It might be that my light is duff.

---

### Post by wieman01 on 2007-02-05
Zerileous:

Are you running any of these programs? If so, uninstall them first and try to connect to an unsecured network. From there we will set up WPA(2).

1. (gnome-)network-manager
2. wifi-radar
3. firestarter

Once you have done so, try the HOWTO in my signature (WPA1, TKIP, DHCP). DHCP is enabled, right?

_**EDIT:**_
Again, post your "interfaces" configuration file if anything goes wrong.

---

