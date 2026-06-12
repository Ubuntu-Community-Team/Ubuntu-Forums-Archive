---
title: "Installing Linksys WRT54G2 router in Ubuntu 8.04"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by medusasbedhead on 2009-01-02
OK, here's my problem.  I recently received the WRT54G2 router for an Xmas gift, and I'd love to use it w/my Ubuntu box.  Problem is, I'm just an end-user, and not a terribly advanced one at that.  The included CD-Rom is no help, and when I've taken some of the advice from similar threads and gone to [http://192.168.1.1](http://192.168.1.1) in order to manually configure everything, I get nothing but a page load error message.  (I also have ndiswrapper installed, as an aside.)  Please help!  Here are the particulars from my machine:

From the iwconfig command:

lo        no wireless extensions.

eth0      no wireless extensions.

From the lspci command: 

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

From the lspci -n command:

00:00.0 0600: 8086:3580 (rev 02)
00:00.1 0880: 8086:3584 (rev 02)
00:00.3 0880: 8086:3585 (rev 02)
00:02.0 0300: 8086:3582 (rev 02)
00:02.1 0380: 8086:3582 (rev 02)
00:1d.0 0c03: 8086:24c2 (rev 03)
00:1d.1 0c03: 8086:24c4 (rev 03)
00:1d.2 0c03: 8086:24c7 (rev 03)
00:1d.7 0c03: 8086:24cd (rev 03)
00:1e.0 0604: 8086:2448 (rev 83)
00:1f.0 0601: 8086:24cc (rev 03)
00:1f.1 0101: 8086:24ca (rev 03)
00:1f.3 0c05: 8086:24c3 (rev 03)
00:1f.5 0401: 8086:24c5 (rev 03)
00:1f.6 0703: 8086:24c6 (rev 03)
02:02.0 0200: 14e4:4401 (rev 01)
02:04.0 0200: 17fe:2220
02:06.0 0607: 104c:8031

From the lsmod command:

Module                  Size  Used by
isofs                  36388  1 
udf                    88612  0 
ipv6                  267780  8 
af_packet              23812  2 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
loop                   18948  2 
ppdev                  10372  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
dock                   11280  0 
container               5632  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
pcmcia                 40876  0 
snd_intel8x0           35356  2 
snd_ac97_codec        101028  1 snd_intel8x0
sbs                    15112  0 
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
sbshc                   7680  1 sbs
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
video                  19856  0 
output                  4736  1 video
snd_seq_oss            35584  0 
serio_raw               7940  0 
snd_seq_midi            9376  0 
led_class               6020  0 
evdev                  13056  6 
wmi_acer                9644  0 
snd_rawmidi            25760  1 snd_seq_midi
psmouse                40336  0 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
soundcore               8800  1 snd
pcspkr                  4224  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
intel_agp              25492  1 
shpchp                 34452  0 
agpgart                34760  3 drm,intel_agp
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pci_hotplug            30880  1 shpchp
ext3                  136840  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
pata_acpi               8320  0 
b44                    28432  0 
ata_piix               19588  3 
ssb                    34308  1 b44
mii                     6400  1 b44
libata                159344  3 ata_generic,pata_acpi,ata_piix
ehci_hcd               37900  0 
uhci_hcd               27024  0 
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
usbcore               146412  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              37384  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3

---

### Post by LowSky on 2009-01-02
if its a router you first need to connect to it by ethernet cable (should have had recieved  one in the box), the router should just work, with no extra set up. If you need wireless then you eed to configure that while being connected first.

The CD is for windows users not much help for someone on Linux, just peel off the back sticker and plug into it. then type that IP address into a browser and it should work

---

### Post by abn91c on 2009-01-02
If this is the first time setting up the router goto [http://192.168.1.1](http://192.168.1.1) enter password **admin**, NO USER NAME to access the router set up then enter all your ISP information, create an** SSID** and wireless passkey. Also change the router password. Use no less than WPA security

---

### Post by medusasbedhead on 2009-01-02
> **LowSky said:**
> if its a router you first need to connect to it by ethernet cable (should have had recieved  one in the box), the router should just work, with no extra set up. If you need wireless then you eed to configure that while being connected first.

The CD is for windows users not much help for someone on Linux, just peel off the back sticker and plug into it. then type that IP address into a browser and it should work

Yeah, the router doesn't work right out of the box w/Ubuntu, so it looks like I need help w/the configuration.  Any advice?

---

### Post by medusasbedhead on 2009-01-02
> **abn91c said:**
> If this is the first time setting up the router goto [http://192.168.1.1](http://192.168.1.1) enter password **admin**, NO USER NAME to access the router set up then enter all your ISP information, create an** SSID** and wireless passkey. Also change the router password. Use no less than WPA security

Right, I've tried that, but I just get a page load error message.

---

### Post by amaroKer on 2009-01-02
You need to probably manually connect your ethernet card if you don't use it often.  Click on the Network Applet (where you would normally connect to wireless) and select wired network.  You HAVE to get a connection if you do that, elsewise your ethernet card is not configured.

---

### Post by LowSky on 2009-01-02
does your internet work if you plug directly into your cable/dsl modem?

---

### Post by qamelian on 2009-01-02
> **medusasbedhead said:**
> Right, I've tried that, but I just get a page load error message.
Some routers (mine, for example) default to 192.168.0.1 instead. Try that.

---

### Post by medusasbedhead on 2009-01-02
> **LowSky said:**
> does your internet work if you plug directly into your cable/dsl modem?

Yep, the 'net works fine when it's a direct wired connection; it's the wireless thing that makes the whole system give me the finger.

---

### Post by medusasbedhead on 2009-01-02
> **amaroKer said:**
> You need to probably manually connect your ethernet card if you don't use it often.  Click on the Network Applet (where you would normally connect to wireless) and select wired network.  You HAVE to get a connection if you do that, elsewise your ethernet card is not configured.

I don't think my card is configured; if you'll refer to my "iwconfig" info. on the original post, it came back w/"no wireless extensions."  Ideas?  *hangs n00b head in shame*  :confused:

---

### Post by medusasbedhead on 2009-01-02
> **qamelian said:**
> Some routers (mine, for example) default to 192.168.0.1 instead. Try that.

:(  Same page load error message as before, but thanks for the help!

---

### Post by amaroKer on 2009-01-02
Connect the router to ethernet

Connect to router using Network Applet

Check Default Route address under connection information to connect to router configuration page.

---

### Post by handydan918 on 2009-01-02
You ARE connected with a wire now, aren't you? If not, get 'er done! You ain't goin' nowhere without doin' that..

---

### Post by amaroKer on 2009-01-02
Your ethernet card is obviously configured correctly if you can get on the internet with it.  You just need to find out the IP address if your gateway.  I urge using Connection Information from right-clicking on the network applet.

---

### Post by abn91c on 2009-01-02
if you cant connect reset the router, press the reset button in the back of the box. power off computer, power of router(pull ac plug out). power on router, wait 10 seconds. power on computer wait at least 30 seconds before connecting to the computer

---

### Post by medusasbedhead on 2009-01-02
> **amaroKer said:**
> Connect the router to ethernet

Connect to router using Network Applet

Check Default Route address under connection information to connect to router configuration page.

:(  Nothing but page load errors when connected directly, and "you are not connected" messages when the cable modem is plugged into the router.

---

### Post by medusasbedhead on 2009-01-02
> **handydan918 said:**
> You ARE connected with a wire now, aren't you? If not, get 'er done! You ain't goin' nowhere without doin' that..

Yes; I can't connect at all unless I'm plugged in directly.

---

### Post by amaroKer on 2009-01-02
How do you connect to the internet?

---

### Post by medusasbedhead on 2009-01-02
> **amaroKer said:**
> How do you connect to the internet?

By directly plugging the computer into the cable modem, as opposed to the new router.

---

### Post by medusasbedhead on 2009-01-02
> **abn91c said:**
> if you cant connect reset the router, press the reset button in the back of the box. power off computer, power of router(pull ac plug out). power on router, wait 10 seconds. power on computer wait at least 30 seconds before connecting to the computer

Damn... no dice!

---

### Post by amaroKer on 2009-01-02
What is the address of the default route (or gateway) that you're getting when you are connected to router only?

---

### Post by anjilslaire on 2009-01-02
OK, so you need to go
cable modem -> router -> PC

To ensure all IPs are refreshed, turn off everything. Then 
turn on modem, wait30 sec (to be safe)
turn on router, wait 30 sec
turn on PC.
Give the following cmd, and provide us with the output:
```

ifconfig eth0

```

---

### Post by handydan918 on 2009-01-02
While connected to the router by wire, open a terminal and do ```
sudo dhclient
``` and post any errors or failures.

---

### Post by crjackson on 2009-01-02
Hook it all up and reboot with a live CD and see if it's the same.

---

### Post by medusasbedhead on 2009-01-02
> **anjilslaire said:**
> OK, so you need to go
cable modem -> router -> PC

To ensure all IPs are refreshed, turn off everything. Then 
turn on modem, wait30 sec (to be safe)
turn on router, wait 30 sec
turn on PC.
Give the following cmd, and provide us with the output:
```

ifconfig eth0

```

Ok, here goes:

eth0      Link encap:Ethernet  HWaddr 00:c0:9f:54:f8:00  
          inet addr:74.76.51.150  Bcast:255.255.255.255  Mask:255.255.224.0
          inet6 addr: fe80::2c0:9fff:fe54:f800/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2815237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:304411952 (290.3 MB)  TX bytes:18391764 (17.5 MB)
          Interrupt:6

---

### Post by medusasbedhead on 2009-01-02
> **handydan918 said:**
> While connected to the router by wire, open a terminal and do ```
sudo dhclient
``` and post any errors or failures.

Ok, here we go:

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:c0:9f:54:f8:00
Sending on   LPF/eth0/00:c0:9f:54:f8:00
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 74.76.51.150 from 10.233.192.1
DHCPREQUEST of 74.76.51.150 on eth0 to 255.255.255.255 port 67
DHCPACK of 74.76.51.150 from 10.233.192.1
bound to 74.76.51.150 -- renewal in 23986 seconds.

---

### Post by medusasbedhead on 2009-01-02
> **amaroKer said:**
> What is the address of the default route (or gateway) that you're getting when you are connected to router only?

I've attached screenshots of both the ethernet and loopback readings when connected via wire to this post; any ideas?

---

### Post by handydan918 on 2009-01-02
> **medusasbedhead said:**
> Ok, here we go:

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:c0:9f:54:f8:00
Sending on   LPF/eth0/00:c0:9f:54:f8:00
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 74.76.51.150 from 10.233.192.1
DHCPREQUEST of 74.76.51.150 on eth0 to 255.255.255.255 port 67
DHCPACK of 74.76.51.150 from 10.233.192.1
bound to 74.76.51.150 -- renewal in 23986 seconds.
Well, that worked! You should be able to ping your router, at least.

---

### Post by handydan918 on 2009-01-02
> **medusasbedhead said:**
> I've attached screenshots of both the ethernet and loopback readings when connected via wire to this post; any ideas?

This is not while you are connected to the router, is it?

---

### Post by medusasbedhead on 2009-01-02
> **handydan918 said:**
> Well, that worked! You should be able to ping your router, at least.

*blush*

Ummm... yeah, I suck that much at this kind of thing.  How do you go about pinging a router?

---

### Post by medusasbedhead on 2009-01-02
> **handydan918 said:**
> This is not while you are connected to the router, is it?

No, just directly to my cable modem.

The router won't let me connect to *anything.*

---

### Post by handydan918 on 2009-01-02
> **medusasbedhead said:**
> *blush*

Ummm... yeah, I suck that much at this kind of thing.  How do you go about pinging a router?

No worries. No one is born knowing this stuff. 
Assuming your router IP is 192.18.1.1, open a terminal and do ```
ping -c 4 192.18.1.1
```

You should get something like this...

```
ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.984 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.926 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.976 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.978 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3027ms
rtt min/avg/max/mdev = 0.926/0.966/0.984/0.023 ms

```

HTH!

EDIT: This time, connect the router...and try it again.

---

### Post by abn91c on 2009-01-02
try this from the linksys website: [http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=3956](http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=3956)

---

### Post by medusasbedhead on 2009-01-02
> **handydan918 said:**
> No worries. No one is born knowing this stuff. 
Assuming your router IP is 192.18.1.1, open a terminal and do ```
ping -c 4 192.18.1.1
```

You should get something like this...

```
ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.984 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.926 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.976 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.978 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3027ms
rtt min/avg/max/mdev = 0.926/0.966/0.984/0.023 ms

```

HTH!

Ah, ok!  Thanks!  This is what I get when I pinged the same address:

PING 192.18.1.1 (192.18.1.1) 56(84) bytes of data.
64 bytes from 192.18.1.1: icmp_seq=1 ttl=242 time=139 ms
64 bytes from 192.18.1.1: icmp_seq=2 ttl=242 time=100 ms
64 bytes from 192.18.1.1: icmp_seq=3 ttl=242 time=101 ms
64 bytes from 192.18.1.1: icmp_seq=4 ttl=242 time=119 ms

--- 192.18.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 100.528/115.293/139.571/15.901 ms

---

### Post by Old_Grey_Wolf on 2009-01-02
What port on the router are you using to connect to the modem? WAN? Uplink? Other?

---

### Post by medusasbedhead on 2009-01-02
> **handydan918 said:**
> No worries. No one is born knowing this stuff. 
Assuming your router IP is 192.18.1.1, open a terminal and do ```
ping -c 4 192.18.1.1
```

You should get something like this...

```
ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.984 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.926 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.976 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.978 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3027ms
rtt min/avg/max/mdev = 0.926/0.966/0.984/0.023 ms

```

HTH!

Damn... connected to the router (instead of the modem, where the last post came from,) and got this error message:

connect: Network is unreachable

---

### Post by medusasbedhead on 2009-01-02
> **Old_Gray_Wolf said:**
> What port on the router are you using to connect to the modem? WAN? Uplink? Other?

I've tried connecting the router to the modem both via the "ethernet 1" port and the "internet" port on the former.  The modem only has one available port for an ethernet cable.

---

### Post by handydan918 on 2009-01-02
> **medusasbedhead said:**
> Ah, ok!  Thanks!  This is what I get when I pinged the same address:

PING 192.18.1.1 (192.18.1.1) 56(84) bytes of data.
64 bytes from 192.18.1.1: icmp_seq=1 ttl=242 time=139 ms
64 bytes from 192.18.1.1: icmp_seq=2 ttl=242 time=100 ms
64 bytes from 192.18.1.1: icmp_seq=3 ttl=242 time=101 ms
64 bytes from 192.18.1.1: icmp_seq=4 ttl=242 time=119 ms

--- 192.18.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 100.528/115.293/139.571/15.901 ms

Fascinating. You shouldn't have gotten anything from 192.18.1.1. There should have been a 6 between the 1 and the 8...typo?

In any case, that seems to indicate that you are now connected to the router...

---

### Post by medusasbedhead on 2009-01-02
Man... I hate to do this, but I *really* have to get going right now, and I'll be away from my computer 'til tomorrow, most likely.  If you guys have any further suggestions, (And thanks SO much for all your help thus far,) please let me know, and I'll let you know the verdict as soon as I try everything out!  Cheers!

---

### Post by handydan918 on 2009-01-02
Okay.
One more time, with feeling!

Connect the router. 

Open a terminal.

Do ```
sudo dhclient

```

Post the output of the above command.

Whew.

---

### Post by medusasbedhead on 2009-01-02
> **handydan918 said:**
> Fascinating. You shouldn't have gotten anything from 192.18.1.1. There should have been a 6 between the 1 and the 8...typo?

In any case, that seems to indicate that you are now connected to the router...

Yeeeah...  that was while I had a wired connection.  When I tried it correctly, via the router, I got nuttin'.  :(  BBL, but thanks a bunch for your help!

---

### Post by handydan918 on 2009-01-02
What is "nuttin"? 

We need the error output.

---

### Post by medusasbedhead on 2009-01-02
> **handydan918 said:**
> Okay.
One more time, with feeling!

Connect the router. 

Open a terminal.

Do ```
sudo dhclient

```

Post the output of the above command.

Whew.

Ooof.  Ok, this is what I got:

There is already a pid file /var/run/dhclient.pid with pid 9609
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:c0:9f:54:f8:00
Sending on   LPF/eth0/00:c0:9f:54:f8:00
Sending on   Socket/fallback
DHCPREQUEST of 74.76.51.150 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 74.76.51.150 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 74.76.51.150 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
Trying recorded lease 74.76.51.150
PING 74.76.32.1 (74.76.32.1) 56(84) bytes of data.

--- 74.76.32.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

...And now I really do have to jet!

---

### Post by medusasbedhead on 2009-01-02
> **handydan918 said:**
> What is "nuttin"? 

We need the error output.

Specifically, this:  

connect: Network is unreachable

---

### Post by Old_Grey_Wolf on 2009-01-02
> **medusasbedhead said:**
> I've tried connecting the router to the modem both via the "ethernet 1" port and the "internet" port on the former.  The modem only has one available port for an ethernet cable.

Is there a port on the router labeled WAN?

---

### Post by DarkReaper79 on 2009-01-02
Im a bit of a noob too, and I had to read the post a few times. So Im going to try to help if I can.

 I can assume that you have all the cables in the correct places. Like you modem cable in the internet plug, your computer in any of slots of 1-4. Then find the reset button and hold it down (with a pen or a pin) The lights in front should blink off then on. Since you can get connection with the modem directly pluged in, Im assuming that your Ethernet card it active. 

So with the reset do as previous posters said and to to 192.168.1.1 and admin as password. If you have DSL you will need your user name and password you set up with your provider. Cable, need to do nothing(depending where you are from) 

Now if you can access the router, but cant still get internet connection, some cable providers dont allow routers unless the install them. But you can do it your self. On the router there is a setting MAC cloning. You take the MAC address from your PC and clone it to your router. The process should be listed in the router manual. It makes the modem think your router is your pc and allows connection. 

I hope this makes sense. Good luck:D

---

### Post by caro on 2009-01-02
I have the same router as you so I'll give you a few things to check.  While I'm here, I'll just go ahead and repeat some things you have probably already done just so you can double check.  There have been times when I had something wrong and it took me several times to notice, so no offense intended.

I've attached screenshots of my router settings so you can check yours.  

BTW, my DSL provider is BellSouth/ATT.  Their modem uses an IP scheme (192.168.1.X) for their DHCP that conflicts with the IP scheme the Linksys router wants to use.  For my router to assign IP addresses to computers I had to change my router's IP scheme to 192.168.10.x.  See attached screen shot.  Without this change, my computers could see the router but not the gateway (i.e. the internet).  This took me a while to track down the first time. 

I believe the default user is admin and leave the password empty.  You will want to change this later.  

Basic troubleshooting to eliminate any other issues:
Modem connected to telephone outlet and powered up.  Ethernet cable from modem to Internet port (next to the power point) on the router and the router powered up.  Cable from port 1 (or 2, 3, or 4) to the network connection on you computer.  

If you have other computers in the house, have you checked to make sure the cable modem is working?  Can they access the internet?  If yes, then the modem works.

If you have multiple computers connected to the router, can they see each other?  If yes, then the router works.

Power everything down.  Make the connections described above.  Power up the modem.  Make sure the lights on the front indicate it is working.  Now power up the router and make sure the lights on the front indicate it is working.  

If everything is OK so far, use another computer (if you have one) and check the router settings and see if that computer can access the internet.  

That's enough to check for now.  Good luck.

---

