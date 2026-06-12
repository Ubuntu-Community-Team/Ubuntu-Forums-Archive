---
title: "wireless encryption noob"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by mills on 2007-04-23
your gonna have to bear with me here, iam new to wireless and have just had to do a reinstall
after messing something up (probably the interface file,it looked a total state after i was finished) and getting the brown screen of death while following and messing up the encryption tutorial sticky

first of all i'll post some outputs

> alex@alex-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra1       Scan completed :
          Cell 01 - Address: 00:14:7F:64:62:09
                    ESSID:"SpeedTouchC78D2E"
                    Mode:Managed
                    Channel:1
                    Encryption key:off  #HOW DO I TURN THIS ON????????
                    Quality:100/100  Signal level:-37 dBm  Noise level:-256 dBm
          Cell 02 - Address: 00:14:6C:64:69:F8
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Quality:0/100  Signal level:-79 dBm  Noise level:-256 dBm

the netgear is not mine

> alex@alex-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra1       RT61 Wireless  ESSID:"SpeedTouchC78D2E"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:7F:64:62:09   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-40 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

interfaces
> iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ra1 inet dhcp
wireless-essid SpeedTouchC78D2E
wireless-key ********- 



auto eth0

auto ra1

i think thats should be enough info there

as you can see from the iwlist scan i have no encryption and want to use the "wpa2,dhcp,essid broadcast enabled" configuration into my interface file but now iam trying to be ultra careful and seek advice and/or confirmation before i do anything


1) where _exactly_ should i place the enryption (the one below in Ps) in my interface file because the iface ra1 inet dhcp bit is kind of contradicting the tutorial when it says replace auto wlan0, my connection seems to on the "iface ra1 inet dhcp" segment

2) can someone confirm that my wpa-driver should read rt61?

3)can the owner of that netgear log on to my wireless signal since i don't have encryption?

4) is there anything else i should know about or take into consideration

normally i would just jump in and have a crack at it but I've done 2 reinstalls in the last 12 hours 
and a third isnt appealing 

any help is appreciated

Ps; this is the encryption i want

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <your_essid>
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key> [IMPORTANT: See "WPA-PSK key generation"]

---

### Post by mills on 2007-04-23
maybe there's another way to get some kind of basic encryption sorted out

any ideas

---

### Post by mills on 2007-04-23
bump

do you need more info, if so just ask :)

---

### Post by mills on 2007-04-23
**alex@alex-desktop:~$ uname -r**
2.6.20-15-generic
**alex@alex-desktop:~$ ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:0D:61:E3:B9:8B  
          inet6 addr: fe80::20d:61ff:fee3:b98b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2616462 (2.4 MiB)  TX bytes:555967 (542.9 KiB)
          Interrupt:22 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

ra1       Link encap:Ethernet  HWaddr 00:19:5B:8A:4C:FB  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:5bff:fe8a:4cfb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36965 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5801 errors:27 dropped:27 overruns:0 carrier:0
          collisions:64 txqueuelen:1000 
          RX bytes:6466567 (6.1 MiB)  TX bytes:684346 (668.3 KiB)
          Interrupt:22 

**alex@alex-desktop:~$ route -n**
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ra1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ra1
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 ra1
**alex@alex-desktop:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

ra1       RT61 Wireless  ESSID:"SpeedTouchC78D2E"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:7F:64:62:09   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=97/100  Signal level:-42 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**alex@alex-desktop:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:0D:61:E3:B9:8B  
          inet6 addr: fe80::20d:61ff:fee3:b98b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2616462 (2.4 MiB)  TX bytes:555967 (542.9 KiB)
          Interrupt:22 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

ra1       Link encap:Ethernet  HWaddr 00:19:5B:8A:4C:FB  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:5bff:fe8a:4cfb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5823 errors:27 dropped:27 overruns:0 carrier:0
          collisions:64 txqueuelen:1000 
          RX bytes:6528465 (6.2 MiB)  TX bytes:686807 (670.7 KiB)
          Interrupt:22 

**alex@alex-desktop:~$ lsmod**
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
radeon                124576  2 
drm                    81044  3 radeon
speedstep_lib           6148  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
video                  16388  0 
asus_acpi              17308  0 
button                  8720  0 
battery                10756  0 
container               5248  0 
backlight               7040  1 asus_acpi
ac                      6020  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
dock                   10268  0 
ipv6                  268704  8 
nls_utf8                3072  1 
ntfs                  107764  1 
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  0 
sg                     36252  0 
snd_intel8x0           34204  1 
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
sd_mod                 23428  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
psmouse                38920  0 
rt61                  245128  1 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sis_agp                 9604  1 
agpgart                35400  2 drm,sis_agp
serio_raw               7940  0 
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  2 
evdev                  11008  4 
tsdev                   8768  0 
ext3                  133128  2 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  5 
sata_sis               10500  0 
ata_generic             9092  0 
pata_sis               14220  1 sata_sis
libata                125720  3 sata_sis,ata_generic,pata_sis
usbhid                 26592  0 
hid                    27392  1 usbhid
usb_storage            72256  0 
scsi_mod              142348  5 sbp2,sg,sd_mod,libata,usb_storage
libusual               17936  1 usb_storage
floppy                 59524  0 
sis900                 24704  0 
mii                     6528  1 sis900
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
sis5513                14856  0 [permanent]
ohci_hcd               22532  0 
usbcore               134280  6 usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
**alex@alex-desktop:~$ iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra1       Scan completed :
          Cell 01 - Address: 00:14:7F:64:62:09
                    ESSID:"SpeedTouchC78D2E"
                    Mode:Managed
                    Channel:1
                    Encryption key:off
                    Quality:97/100  Signal level:-41 dBm  Noise level:-256 dBm

**alex@alex-desktop:~$ cat /etc/network/interfaces**
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ra1 inet dhcp
wpa-driver rt61
wpa-ssid SpeedTouchC78D2E
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 202cc4536c627d9f7f751fa0bd7d981a4842aa3192fd76a2406a1fbe50441ca8


auto ra1
**alex@alex-desktop:~$ cat /etc/modprobe.d/ndiswrapper**
cat: /etc/modprobe.d/ndiswrapper: No such file or directory
**alex@alex-desktop:~$ cat /etc/resolv.conf**
search lan
nameserver 192.168.1.254

---

### Post by kevdog on 2007-04-23
Just a few things:

1. What type of wireless card are you using???  This is to ensure the wpa-driver wext statement is correct.

2. Can you connect to the router with encryption turned off??

3. If yes, I found through my own experience TKIP can only be used with WPA Personal or WPA1 and AES with WPA2.  (At least with my linksys wrt54gs router).  

So do you want WPA2 or WPA 1 encryption?

For WPA2 encryption here is my interfaces file:
auto eth0
iface eth0 inet static
wpa-driver wext
wpa-ssid ****
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <key here>

For WPA1 encrytion it would be (this has been tested and verified)
auto eth0
iface eth0 inet static
wpa-driver wext
wpa-ssid ****
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <key here>

I would guess you would have to change eth0 to your respective adapter

---

### Post by mills on 2007-04-23
iam using a d-link dwl-g510 with the rt61 drivers

iam conecting and surfing with wireless as we speak

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface ra1 inet dhcp
wpa-driver rt61
wpa-ssid SpeedTouchC78D2E
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 202cc4536c627d9f7f751fa0bd7d981a4842aa3192fd76a2406a1fbe50441ca8
```

this is my interface file, looks good but encryption aint workin.
not sure what you mean by adapter?

just tried putting wpa1 in the eth0 section

```
alex@alex-desktop:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:6: duplicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:6: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"
```

and then put it back to how it was (i think)

```
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.ra1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra1/00:19:5b:8a:4c:fb
Sending on   LPF/ra1/00:19:5b:8a:4c:fb
Sending on   Socket/fallback
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.254
DHCPREQUEST on ra1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
bound to 192.168.1.64 -- renewal in 39889 seconds.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0d:61:e3:b9:8b
Sending on   LPF/eth0/00:0d:61:e3:b9:8b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

am i doing some thing wrong here?

---

### Post by mills on 2007-04-23
surely there should just be an encryption button somewhere](*,)

---

### Post by kevdog on 2007-04-23
Please post the results of ifconfig.

Do you want to use WPA1 or WPA2??

---

### Post by mills on 2007-04-23
```
eth0      Link encap:Ethernet  HWaddr 00:0D:61:E3:B9:8B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xc000 

eth0:avah Link encap:Ethernet  HWaddr 00:0D:61:E3:B9:8B  
          inet addr:169.254.9.20  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:718 (718.0 b)  TX bytes:718 (718.0 b)

ra1       Link encap:Ethernet  HWaddr 00:19:5B:8A:4C:FB  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:5bff:fe8a:4cfb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4958 errors:1 dropped:1 overruns:0 carrier:0
          collisions:40 txqueuelen:1000 
          RX bytes:5784694 (5.5 MiB)  TX bytes:926778 (905.0 KiB)
          Interrupt:22 
```

i dont know the difference between wpa 1 or 2 so whatever is easier i suppose, you choose

---

### Post by kevdog on 2007-04-23
Encryption Type --

What does it say in your router via the setup page??? It should specifiy wpa (wpa personal or wpa1) or wpa2.

---

### Post by mills on 2007-04-23
ok i had a damn good search through my router page and nothing about wpa

but wmn and wds are there and enabled if thats means anything

EDIT found wep and enabled it, encryption is on, but not sure if it strong encryption but iam happy for now, 

thanks for the help kevdog really appreciate it

---

### Post by wieman01 on 2007-04-23
Mills, 
> wpa-driver rt61
...is definitely not correct. There are only a number of wpa-drivers, check out my HOWTO. My closest guess in your case would be "wext".

However, I am afraid your card/driver does not really support WPA in the way others do (Ralink). Check for solutions here:

[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page")

_**EDIT:**_
Install "ndiswrapper" if you want to go this way nonetheless and replace the RT driver for your card.

---

### Post by mills on 2007-04-23
cheers for the advice wieman

i'll bookmark the link and have a good look another day

ive had enough networkning for 1 day :-/

---

