---
title: "Unable to setup WPA on ubuntu with EDIMAX 54mbps PCI card"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by recon69 on 2007-05-06
Yep, been trying to get this to connect for a while now, no luck. 
Think i got everything working except for the encription. Can dectect my wireless router but cant connect, 
Get no IP address from the DHCP. 

Been trying lots of things so my setup is probably a real mess now. 
anyway, any help welcome :) 

here is some hard info on the setup atm 

Regards

```

mec@mec-desktop:~$  uname -a
Linux mec-desktop 2.6.15-28-386 #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007 i686 GNU/Linux

mec@mec-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0B:6A:62:35:0B
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6aff:fe62:350b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:804036 (785.1 KiB)  TX bytes:189263 (184.8 KiB)
          Interrupt:201 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

ra0       Link encap:Ethernet  HWaddr 00:0E:2E:A2:B7:11
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:90663 (88.5 KiB)  TX bytes:0 (0.0 b)
          Interrupt:201

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

mec@mec-desktop:~$

mec@mec-desktop:~$ route -n
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
mec@mec-desktop:~$


mec@mec-desktop:~$ iwconfig
lo        no wireless extensions.

ra0       RT61 Wireless  ESSID:"Belkin_G_Plus_MIMO_ADSL"
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

mec@mec-desktop:~$
mec@mec-desktop:~$  ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

ra0       Link encap:Ethernet  HWaddr 00:0E:2E:A2:B7:11
          inet6 addr: fe80::20e:2eff:fea2:b711/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:140876 (137.5 KiB)  TX bytes:0 (0.0 b)
          Interrupt:201

mec@mec-desktop:~$ lsmod
Module                  Size  Used by
af_packet              22920  6
binfmt_misc            12296  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppp_synctty            10112  0
ppdev                   9220  0
ipv6                  265856  12
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
ext2                   68488  1
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   13440  1
fat                    53020  1 vfat
nls_utf8                2176  1
ntfs                  103536  1
dm_mod                 58936  1
md_mod                 72532  0
pppoatm                 6400  0
ppp_generic            30100  2 ppp_synctty,pppoatm
slhc                    7424  1 ppp_generic
psmouse                36100  0
lp                     11844  0
cx88_blackbird         20124  0
cx8800                 32268  1 cx88_blackbird
cx88_dvb               10244  0
cx8802                 11780  2 cx88_blackbird,cx88_dvb
cx88xx                 62368  4 cx88_blackbird,cx8800,cx88_dvb,cx8802
mt352                   6788  1 cx88_dvb
or51132                10244  1 cx88_dvb
video_buf_dvb           6660  1 cx88_dvb
dvb_core               82984  1 video_buf_dvb
i2c_algo_bit            9608  1 cx88xx
nxt200x                13444  1 cx88_dvb
video_buf              22148  6 cx88_blackbird,cx8800,cx88_dvb,cx8802,cx88xx,video_buf_dvb
ir_common               9988  1 cx88xx
sis900                 22912  0
lgdt330x                8092  1 cx88_dvb
cx22702                 6404  1 cx88_dvb
dvb_pll                11012  4 cx88_dvb,or51132,nxt200x,cx22702
tveeprom               15248  1 cx88xx
v4l1_compat            14468  1 cx8800
v4l2_common             6016  1 cx8800
btcx_risc               5128  3 cx8800,cx8802,cx88xx
tsdev                   8000  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
mii                     5888  1 sis900
nvidia               6822420  22
videodev                9856  3 cx88_blackbird,cx8800,cx88xx
analog                 12320  0
rt61                  249096  1
pcspkr                  2180  0
floppy                 62148  0
gameport               15496  1 analog
rtc                    13492  0
snd_intel8x0           33692  1
usbhid                 39904  0
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
i2c_sis96x              5764  0
i2c_core               21904  12 i2c_acpi_ec,cx88_dvb,cx88xx,mt352,or51132,i2c_algo_bit,nxt200x,lgdt330x,cx22702,tveeprom,nvidia,i2c_sis96x
sis_agp                 8708  1
agpgart                34888  2 nvidia,sis_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
evdev                   9856  2
ext3                  135944  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130820  4 usbhid,ehci_hcd,ohci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  8
sis5513                17032  1
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
mec@mec-desktop:~$
mec@mec-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:18:4D:15:E9:8A
                    ESSID:"SKY60957"
                    Mode:Managed
                    Channel:1
                    Encryption key:on
                    Quality:0/100  Signal level:-66 dBm  Noise level:-256 dBm
          Cell 02 - Address: 00:17:3F:15:E3:06
                    ESSID:"Belkin_G_Plus_MIMO_ADSL"
                    Mode:Managed
                    Channel:6
                    Encryption key:on
                    Quality:0/100  Signal level:-24 dBm  Noise level:-256 dBm
          Cell 03 - Address: 00:16:CE:7C:DE:50
                    ESSID:"Livebox-22B0"
                    Mode:Managed
                    Channel:1
                    Encryption key:on
                    Quality:0/100  Signal level:-84 dBm  Noise level:-256 dBm

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

mec@mec-desktop:~$
mec@mec-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
iface eth0 inet dhcp
        up ip route add 192.168.2.0/24 dev eth0
iface eth1 inet dhcp
iface eth2 inet dhcp
iface ath0 inet dhcp
iface wlan0 inet dhcp
#
iface ra0 inet dhcp
#

mec@mec-desktop:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper
mec@mec-desktop:~$

mec@mec-desktop:~$  cat /etc/resolv.conf
search Belkin
nameserver 192.168.2.1
mec@mec-desktop:~$

```


WPA-Supplicant.conf

```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

## Single key 128bit WEP
#network={
#        ssid="Belkin_G_Plus_MIMO_ADSL2"
#       key_mgmt=NONE
#	wep_key0=1A3CCDEEBA05F6772EA31DA421
#	wep_tx_keyidx=0
#	priority=5
#}

# WPA-PSK
network={
        ssid="Belkin_G_Plus_MIMO_ADSL"
	proto=WPA
        key_mgmt=WPA-PSK
	pairwise=TKIP
#	psk="furby666"
        psk=fc5a70092d9ad93925405373ce210da798e281c95469abeaf18ef0a38e4e7f92
 	priority=4
}

# Coffee shop / Open
#network={
#        ssid="Belkin_G_Plus_MIMO_ADSL"
#        key_mgmt=NONE
#	priority=2
#}
#

#network={
#        ssid="Belkin_G_Plus_MIMO_ADSL"
#        #psk="furby666"
#        psk=fc5a70092d9ad93925405373ce210da798e281c95469abeaf18ef0a38e4e7f92
#}


```

---

### Post by edonia on 2007-05-06
what version of ubuntu are you using?

setting up the network by hand, looks on my system like this:

in my home is the .wpa_supplicant.conf file:

```
 
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=0

network={
    ssid="inhouse"
    psk="fc5a70092d9ad93925405373ce210da798e281c95469abeaf18ef0a38e4e7f92"
    priority=5
}

```you see already some difference to yours. I "quoted" the key...

Now, to bring up my network with wpa (my device is called ath0):

```


# Atheros madwifi load driver
modprobe ath_pci
modprobe ath_rate_onoe

# load wpa_supplicant with the atheros driver
wpa_supplicant -iath0 -c~/.wpa_supplicant.conf -Bw -Dmadwifi

# give the local address
ifconfig ath0 add address 192.168.1.4

# set the default route
route del default
route add default gw 192.168.1.1 ath0

```
Maybe it will help you, to get on

Uwe

---

