---
title: "Can see SSID, but don't get any DHCPOFFERS"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by mpref on 2008-04-27
After Upgrading to 8.04, I'm trying hard to get my USB-WLAN-Stick up and running again (worked perfectly fine under 7.10). 

Installation of the stick via NDISWRAPPER worked fine and the stick can apparently see the Router:

```

zieglerk@Apollo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"CasaMama"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:2A:29:58:19
          Bit Rate=54 Mb/s   Tx-Power:20 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

On the other hand a ping leaves no reply and 

```

zieglerk@Apollo:~$ ping -c 4 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3009ms 

```

and I don't get any DHCPOFFERS -- which is probably the real problem.

```
zieglerk@Apollo:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6978
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:15:47:e0:c5
Sending on   LPF/wlan0/00:19:15:47:e0:c5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I'd be thankful for any suggestions.

---

### Post by kevdog on 2008-04-27
You tried a manual connection I see -- did you specify the correct ESSID and did you connect with any security parameters (best to troubleshoot with no wep/wpa initially).

---

### Post by mpref on 2008-04-27
Yes, I've got the PSK for the WPA2 Encryption in the wpa_supplicant.conf

If I'd like to connect without Encryption, I'd have to change the internal settings of the router, too, isn't it?!

---

### Post by mpref on 2008-04-27
Changed the Enryption of the Router to WEP and that's what I got:

```
zieglerk@Apollo:~$ sudo ifconfig wlan0 down
zieglerk@Apollo:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 7705
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:15:47:e0:c5
Sending on   LPF/wlan0/00:19:15:47:e0:c5
Sending on   Socket/fallback
zieglerk@Apollo:~$ sudo ifconfig wlan0 up
zieglerk@Apollo:~$ sudo iwconfig wlan0 essid "CasaMama"
zieglerk@Apollo:~$ sudo iwconfig wlan0 key AFAFAFAFAF
zieglerk@Apollo:~$ sudo iwconfig wlan0 mode Managed
zieglerk@Apollo:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:15:47:e0:c5
Sending on   LPF/wlan0/00:19:15:47:e0:c5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
zieglerk@Apollo:~$  
```

---

### Post by mpref on 2008-04-27
This is, what I got, when I used no encryption at all. The DHCPOFFER made me happy, but the Internetconnection didn't work anyways. Does that make sense to any of you?

```
zieglerk@Apollo:~$ sudo ifconfig wlan0 down
zieglerk@Apollo:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 7100
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:15:47:e0:c5
Sending on   LPF/wlan0/00:19:15:47:e0:c5
Sending on   Socket/fallback
zieglerk@Apollo:~$ sudo ifconfig wlan0 up
zieglerk@Apollo:~$ sudo iwconfig wlan0 essid "CasaMama"
zieglerk@Apollo:~$ sudo iwconfig wlan0 mode Managed
zieglerk@Apollo:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:15:47:e0:c5
Sending on   LPF/wlan0/00:19:15:47:e0:c5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.2.100 from 192.168.2.1
DHCPREQUEST of 192.168.2.100 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.100 from 192.168.2.1
bound to 192.168.2.100 -- renewal in 171948 seconds.

```

---

### Post by kevdog on 2008-04-27
At least its giving you an IP address at this point.  Can you list lsmod perhaps?  Im not sure why it wont work with WEP.

---

### Post by mpref on 2008-04-27
Here comes lsmod. I was wondering if it could be useful to turn off the network manager? (That's the tool giving me the network-symbol in the status bar, right?!)

```
zieglerk@Apollo:~$ lsmod
Module                  Size  Used by
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
via                    43648  2
drm                    82580  3 via
ppdev                  10372  0
powernow_k7             9000  0
cpufreq_conservative     8712  0
cpufreq_ondemand        9740  1
cpufreq_powersave       2688  0
cpufreq_userspace       5284  0
cpufreq_stats           7104  0
freq_table              5536  3 powernow_k7,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0
sbshc                   7680  1 sbs
dock                   11280  0
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
nls_iso8859_1           4992  3
nls_cp437               6656  3
vfat                   14464  3
fat                    54556  1 vfat
ipv6                  267780  8
ndiswrapper           192920  0
sbp2                   24072  0
lp                     12324  0
joydev                 13120  0
pcmcia                 40876  0
video                  19856  0
output                  4736  1 video
snd_via82xx            29464  3
gameport               16008  1 snd_via82xx
snd_mpu401_uart         9728  1 snd_via82xx
container               5632  0
evdev                  13056  7
snd_seq_dummy           4868  0
parport_pc             36260  1
parport                37832  3 ppdev,lp,parport_pc
led_class               6020  0
wmi_acer                9644  0
af_packet              23812  6
psmouse                40336  0
serio_raw               7940  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
battery                14212  0
button                  9232  0
ac                      6916  0
i2c_viapro              9876  0
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_via82xx_modem      16264  0
snd_ac97_codec        101028  2 snd_via82xx,snd_via82xx_modem
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
ac97_bus                3072  1 snd_ac97_codec
i2c_core               24832  1 i2c_viapro
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm                78596  5 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0
via_ircc               27796  0
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
yenta_socket           27276  1
rsrc_nonstatic         13696  1 yenta_socket
snd_timer              24836  2 snd_seq,snd_pcm
via_agp                11136  1
agpgart                34760  2 drm,via_agp
irda                  203068  1 via_ircc
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    56996  18 snd_via82xx,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_seq_device,snd_timer
crc_ccitt               3072  1 irda
snd_page_alloc         11400  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore               8800  1 snd
ext3                  136712  1
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0
sr_mod                 17956  0
cdrom                  37408  1 sr_mod
sd_mod                 30720  6
floppy                 59588  0
pata_via               13316  5
pata_acpi               8320  0
ata_generic             8324  0
libata                159344  3 pata_via,pata_acpi,ata_generic
via_rhine              26632  0
mii                     6400  1 via_rhine
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0
uhci_hcd               27024  0
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd
ohci1394               33584  0
ieee1394               93752  2 sbp2,ohci1394
thermal                16796  0
processor              36872  3 powernow_k7,thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1

```

---

### Post by kevdog on 2008-04-27
Nothing unusual in lsmod - sorry -- try rebooting the router, turning off nm, and then try by hand again.

---

### Post by mpref on 2008-04-27
Just to make sure, that I understood correctly. I should remove the packages network-manager and network-manager-gnome in the package management. Is that going to affect my LAN?

---

### Post by Felix222pc on 2008-04-27
Have you tried not getting an IP through DHCP but setting it manually?

---

### Post by mpref on 2008-04-28
Thanks for the idea. I'll try that right now. I'm just wondering what settings I have to use.

wieman01 proposes in his to add
```

address 192.168.168.40
gateway 192.168.168.230
dns-nameservers 192.168.168.230
netmask 255.255.255.0

```
and claims that all self-explanatory. Unfortunately,that's not the case for me. I guess, I can keep netmask. And I have to take for dns-nameservers the value of my router. But what about gateway and address. Can I choose them randomly (starting with 192.168)?

---

### Post by wieman01 on 2008-04-28
"gateway" & "dns-nameservers" should be identical with your router's IP address. "address" is your own, pick any one you like (first 3 token must be identical e.g. 192.168.168.xxx). Leave "netmask" unchanged.

---

### Post by mpref on 2008-04-30
Thanks for the hints on choosing the IPs properly. That's what my /etc/network/interfaces looks like right now. (The IP of the router ist 192.168.2.1)

```

auto wlan0
# iface wlan0 inet dhcp
#       wpa-conf /etc/wpa_suppliant/wpa_supplicant.conf
iface wlan0 inet static
        address 192.168.2.2
        gateway 192.168.2.1
        dns-nameservers 192.168.2.1
        netmask 255.255.255.0
        wpa-driver wext
        wpa-ssid CasaMama
        wpa-ap-scan 1
        wpa-proto RSN
        wpa-pairwise TKIP
        wpa-group TKIP
        wpa-key-mgmt WPA-PSK
        wpa-psk ed6b0cd9c97a18d943d472f82592052182100b6457d4801a69851251876c95d4

```

Unfortunately, still not successful. Any ideas, what could be the problem, since I can perfectly "see" the router using iwlist scanning, but can't even ping it?!

---

### Post by wieman01 on 2008-04-30
Please try this:
>  wpa-proto RSN WPA
        wpa-pairwise CCMP TKIP
        wpa-group CCMP TKIP

Any better? If not, post:
> sudo iwlist scan
> sudo lshw -C network

---

### Post by mpref on 2008-04-30
Unfortunately, still no difference. Here are the results of the two commands.

```

zieglerk@Apollo:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:2A:29:58:19
                    ESSID:"CasaMama"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

```

```

zieglerk@Apollo:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:c0:9f:31:ea:49
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:15:47:e0:c5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+prisma02 driverversion=1.52+T-Com,10/19/2005, 3.03.36.0 ip=192.168.2.2 link=no multicast=yes wireless=IEEE 802.11g

```

Probably, only the WLAN part is relevant, but I'll post it all. Thanks for taking a look.

---

### Post by wieman01 on 2008-04-30
Please post the current "/etc/network/interfaces".

Then issue:
> sudo ifdown -v wlan0
> sudo ifup -v wlan0

---

### Post by mpref on 2008-04-30
The complete /etc/network/interfaces looks like the following. I'll disconnect the LAN now and try, what you proposed.

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
# iface wlan0 inet dhcp
#       wpa-conf /etc/wpa_suppliant/wpa_supplicant.conf
iface wlan0 inet static
        address 192.168.2.2
        gateway 192.168.2.1
        dns-nameservers 192.168.2.1
        netmask 255.255.255.0
        wpa-driver wext
        wpa-ssid CasaMama
        wpa-ap-scan 1
        wpa-proto RSN WPA
        wpa-pairwise CCMP TKIP
        wpa-group CCMP TKIP
        wpa-key-mgmt WPA-PSK
        wpa-psk ed6b0cd9c97a18d943d472f82592052182100b6457d4801a69851251876c95d4

```

---

### Post by wieman01 on 2008-04-30
Please also post the results of the above commands. They will help a lot.

---

### Post by mpref on 2008-04-30
Here is the listing of the -- unsuccessful -- ifdown and ifup. There are quite a lot of "OK"s in the second one. But apparently not enough. Still no connection.

```

zieglerk@Apollo:~$ sudo ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: wpa-ap-scan 1 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "CasaMama" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: wpa-pairwise CCMP TKIP -- OK
wpa_supplicant: wpa-group CCMP TKIP -- OK
wpa_supplicant: wpa-key-mgmt WPA-PSK -- OK
wpa_supplicant: wpa-proto RSN WPA -- OK
wpa_supplicant: enabling network block 0 -- OK

ifconfig wlan0 192.168.2.2 netmask 255.255.255.0                up
 route add default gw 192.168.2.1 metric 100 wlan0
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant

zieglerk@Apollo:~$ sudo ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: wpa-ap-scan 1 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "CasaMama" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: wpa-pairwise CCMP TKIP -- OK
wpa_supplicant: wpa-group CCMP TKIP -- OK
wpa_supplicant: wpa-key-mgmt WPA-PSK -- OK
wpa_supplicant: wpa-proto RSN WPA -- OK
wpa_supplicant: enabling network block 0 -- OK

ifconfig wlan0 192.168.2.2 netmask 255.255.255.0                up
 route add default gw 192.168.2.1 metric 100 wlan0
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant

```

---

### Post by wieman01 on 2008-04-30
What if you ping your router now:
> ping 192.168.2.1
Also do:
> route

---

### Post by mpref on 2008-04-30
The pings didn't suceed, but there are some 192.168.2.0 entries after the route. Are they supposed to be there?

```
zieglerk@Apollo:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.101 icmp_seq=2 Destination Host Unreachable
From 192.168.2.101 icmp_seq=3 Destination Host Unreachable
From 192.168.2.101 icmp_seq=5 Destination Host Unreachable
From 192.168.2.101 icmp_seq=6 Destination Host Unreachable
From 192.168.2.101 icmp_seq=8 Destination Host Unreachable
From 192.168.2.101 icmp_seq=9 Destination Host Unreachable
From 192.168.2.101 icmp_seq=10 Destination Host Unreachable
From 192.168.2.101 icmp_seq=11 Destination Host Unreachable
From 192.168.2.101 icmp_seq=12 Destination Host Unreachable

--- 192.168.2.1 ping statistics ---
13 packets transmitted, 0 received, +9 errors, 100% packet loss, time 12042ms
, pipe 3
zieglerk@Apollo:~$ route
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
192.168.2.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.2.1     0.0.0.0         UG    100    0        0 wlan0
default         192.168.2.1     0.0.0.0         UG    100    0        0 eth0

```

---

### Post by wieman01 on 2008-04-30
Strange.

Could you switch to DHCP for the time being and run "ifup" and "ifdown" once again? Perhaps that wil yield something at least.

---

### Post by mpref on 2008-04-30
Doesn't work either. Here's the output.

```
zieglerk@Apollo:~$ sudo ifdown -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/wpasupplicant
wpa_supplicant: cannot read contents of /etc/wpa_suppliant/wpa_supplicant.conf
run-parts: /etc/network/if-down.d/wpasupplicant exited with return code 1
dhclient3 -r -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.l
eases wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:15:47:e0:c5
Sending on   LPF/wlan0/00:19:15:47:e0:c5
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67
ifconfig wlan0 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant
wpa_supplicant: cannot read contents of /etc/wpa_suppliant/wpa_supplicant.conf
run-parts: /etc/network/if-post-down.d/wpasupplicant exited with return code 1
zieglerk@Apollo:~$ sudo ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: cannot read contents of /etc/wpa_suppliant/wpa_supplicant.conf
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dh
client.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:15:47:e0:c5
Sending on   LPF/wlan0/00:19:15:47:e0:c5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant
wpa_supplicant: cannot read contents of /etc/wpa_suppliant/wpa_supplicant.conf
run-parts: /etc/network/if-up.d/wpasupplicant exited with return code 1

```

---

### Post by wieman01 on 2008-04-30
Very strange, now what exact model have you got again? You did not configure IP tables (Linux firewall) or something like that? And you are on a 32-bit system, right?

We ought to check with Kevdog, perhaps he has smart idea...

---

### Post by mpref on 2008-04-30
The Laptop is an Acer Aspire 1350 and the WLAN-USB-Stick is a Speedport W100. The router is a Speedport W500.

I didn't touch the IP tables or anything like that. I just upgraded from 7.10 (32-bit) where everyhting worked just fine to 8.04. I even did the upgrade via WLAN but after the reboot (coming with the upgrade) the WLAN-connection was lost.

---

### Post by mpref on 2008-04-30
By the way. Thanks for hanging with me all the time.

---

### Post by mpref on 2008-04-30
All right, I give in. I'll "update" back to 7.10. Thanks for all the help.

---

### Post by wieman01 on 2008-05-01
I am sorry I cannot give you anymore advice. Again, Kevdog might be able to help here, but I am seriously running out of ideas. Frankly I have also toyed with the idea of downgrading on a couple of occasions, but I could avoid it eventually. But wireless is crucial, so I understand your situation.

Perhaps a fresh install helps? Have you loaded the Live CD and checked if wireless is OK on a default installation?

---

