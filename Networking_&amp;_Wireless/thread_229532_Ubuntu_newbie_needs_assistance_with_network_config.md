---
title: "Ubuntu newbie needs assistance with network config"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by electri on 2006-08-04
I am new at TCP/IP troubleshooting and would appreciate some help.

I've been reading Ubuntu forum postings for several days trying to 
figure out what's wrong with my network configuration, to no avail.

When booted into Windows XP Professional at:

1) Home (D-Link DI-604 router and Comcast cable modem)

                       -and-

2) Work (Corporate gateway and Internet proxy server)

my Toshiba Tecra A4 laptop successfully obtains an IP address 
(via DHCP) and I can get out to the Internet just fine.

However, I have not been able to get DHCP *or* static IP to work 
in Ubuntu (which is installed in a separate disk partition and 
accessed via Grub).

Forget about DHCP, though.  I can't even figure out how to get my laptop
to ping my router (at home) or gateway (at work).  After several days of
trying unsuccessfully, I would be happy just to be able to do THAT!

Can anyone possibly help me by seeing a problem in the data 
provided below?


= = = = = = = = = = = = = = = 


The following is what Windows XP sees:

ipconfig /all

Windows IP Configuration          
Host Name . . . . . . . . . . . . : TOSHIBA-PC         
Primary Dns Suffix  . . . . . . . :          
Node Type . . . . . . . . . . . . : Unknown         
IP Routing Enabled. . . . . . . . : No         
WINS Proxy Enabled. . . . . . . . : No         
DNS Suffix Search List. . . . . . : wsa.faa.gov  

Ethernet adapter Wireless Network:          
Media State . . . . . . . . . . . : Media disconnected         
Description . . . . . . . . . . . : Intel(R) PRO/Wireless 2915ABG Network Connection         
Physical Address. . . . . . . . . : 00-0E-35-E7-41-7F  

Ethernet adapter Home LAN:
Connection-specific DNS Suffix  . : wsa.faa.gov         
Description . . . . . . . . . . . : Marvell Yukon 88E8053 PCI-E Gigabit Ethernet Controller         
Physical Address. . . . . . . . . : 00-A0-D1-BC-CB-A6         
Dhcp Enabled. . . . . . . . . . . : Yes         
Autoconfiguration Enabled . . . . : Yes         
IP Address. . . . . . . . . . . . : 10.16.56.139         
Subnet Mask . . . . . . . . . . . : 255.255.255.0         
Default Gateway . . . . . . . . . : 10.16.56.1         
DHCP Server . . . . . . . . . . . : 10.16.56.11         
DNS Servers . . . . . . . . . . . : 172.18.2.40                                             
172.18.115.36                                             
172.18.2.41         
Lease Obtained. . . . . . . . . . : Friday, August 04, 2006 4:54:21 PM         
Lease Expires . . . . . . . . . . : Tuesday, August 08, 2006 4:54:21 PM


[Note:  I am able to ping 10.16.56.1 successfully under Windows . . . ]


= = = = = = = = = = = = = = = 


The following is diagnostic output from Ubuntu . . . 


Toshiba-Laptop:~$ uname -a

Linux Toshiba-Laptop 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux



Toshiba-Laptop:~$ lspci

0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
0000:01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 Gigabit Ethernet Controller (rev 15)
0000:05:04.0 Network controller: Intel Corporation PRO/Wireless 2915ABG MiniPCI Adapter (rev 05)
0000:05:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:05:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:05:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:05:06.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller



Toshiba-Laptop:~$ cat /etc/network/interfaces

auto lo
iface lo inet loopback

# auto eth0
# iface eth0 inet dhcp

auto eth0
iface eth0 inet static
address 10.16.56.139
netmask 255.255.255.0
# broadcast 10.16.56.255
gateway 10.16.56.1 

# auto eth1
# iface eth1 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp



Toshiba-Laptop:~$ lsmod

Module                  Size  Used by
ipv6                  265600  6 
rfcomm                 40216  0 
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0 
i915                   20608  1 
drm                    73236  2 i915
acpi_cpufreq            6792  1 
cpufreq_userspace       4696  1 
cpufreq_stats           5636  0 
freq_table              4740  2 acpi_cpufreq,cpufreq_stats
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
nls_utf8                2176  2 
ntfs                  103536  2 
dm_mod                 58936  1 
md_mod                 72532  0 
sbp2                   24196  0 
lp                     11844  0 
joydev                 10048  0 
pcmcia                 40508  0 
parport_pc             35780  1 
parport                36296  3 ppdev,lp,parport_pc
tsdev                   8000  0 
usbhid                 38368  0 
sdhci                  14848  0 
mmc_core               30104  1 sdhci
ipw2200               107308  0 
rtc                    13492  0 
ieee80211              37064  1 ipw2200
ieee80211_crypt         6272  1 ieee80211
sky2                   37504  0 
yenta_socket           28428  1 
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           33692  1 
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
psmouse                36228  0 
serio_raw               7300  0 
intel_agp              22940  1 
shpchp                 45632  0 
pci_hotplug            29236  1 shpchp
agpgart                34888  3 drm,intel_agp
evdev                   9856  3 
sg                     37920  0 
ext3                  135688  1 
jbd                    58772  1 ext3
ide_generic             1536  0 
ehci_hcd               32008  0 
ohci1394               35124  0 
ieee1394              299832  2 sbp2,ohci1394
uhci_hcd               33680  0 
usbcore               129668  4 usbhid,ehci_hcd,uhci_hcd
sr_mod                 16932  0 
cdrom                  38560  1 sr_mod
sd_mod                 19984  5 
generic                 5124  0 
ata_piix               11012  8 
ahci                   17668  0 
libata                 78992  2 ata_piix,ahci
scsi_mod              139496  6 sbp2,sg,sr_mod,sd_mod,ahci,libata
thermal                13576  0 
processor              23360  2 acpi_cpufreq,thermal
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


Toshiba-Laptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:A0:D1:BC:CB:A6  
          inet addr:10.16.56.139  Bcast:10.16.56.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2564 (2.5 KiB)  TX bytes:2564 (2.5 KiB)


Toshiba-Laptop:~$ netstat -r

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.16.56.0      0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         10.16.56.1      0.0.0.0         UG    0      0        0 eth0


Toshiba-Laptop:~$ sudo mii-tool eth0 

eth0: negotiated 100baseTx-FD flow-control, link ok



Toshiba-Laptop:~$ ping -c 3 127.0.0.1

PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.041 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.041 ms

--- 127.0.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.039/0.040/0.041/0.005 ms


Toshiba-Laptop:~$ ping -c 3 10.16.56.1

PING 10.16.56.1 (10.16.56.1) 56(84) bytes of data.
From 10.16.56.139 icmp_seq=1 [COLOR="Red"]Destination Host Unreachable[/COLOR]
From 10.16.56.139 icmp_seq=2 [COLOR="Red"]Destination Host Unreachable[/COLOR]
From 10.16.56.139 icmp_seq=3 [COLOR="Red"]Destination Host Unreachable[/COLOR]

--- 10.16.56.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
, pipe 3




Any help would be greatly appreciated!!  Sorry for the long posting.

---

### Post by phitoo on 2006-08-04
> **electri said:**
> 
my Toshiba Tecra A4 laptop successfully obtains an IP address 
(via DHCP) and I can get out to the Internet just fine.


Toshiba-Laptop:~$ cat /etc/network/interfaces

auto lo
iface lo inet loopback

# auto eth0
# iface eth0 inet dhcp

auto eth0
iface eth0 inet static
address 10.16.56.139
netmask 255.255.255.0
# broadcast 10.16.56.255
gateway 10.16.56.1 

# auto eth1
# iface eth1 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp


I happen to have a Tecra A4 S313 and I think you've hit a problem that has been frustrating me from day one. Linux picks up the wireless first as eth0 and the Marvell chip sometimes as eth1 and sometimes as eth2. Don't ask why! :-( I still haven't figured out what is going on.

In you /etc/network/interfaces uncomment the lines for eth1 and add a couple of similar lines for eth2. Hopefully it'll work.

---

### Post by electri on 2006-08-04
> **phitoo said:**
> I happen to have a Tecra A4 S313 and I think you've hit a problem that has been frustrating me from day one. Linux picks up the wireless first as eth0 and the Marvell chip sometimes as eth1 and sometimes as eth2. Don't ask why! :-( I still haven't figured out what is going on.

In you /etc/network/interfaces uncomment the lines for eth1 and add a couple of similar lines for eth2. Hopefully it'll work.


I appreciate your suggestion, but it didn't seem to work.  

I tried adding the same static IP assignment to eth1 and 
eth2.  As you can see here, now eth0 and eth1 are both 
showing 10.16.56.139:

[FONT="Courier New"]Toshiba-Laptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:A0:D1:BC:CB:A6  
          inet addr:10.16.56.139  Bcast:10.16.56.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:E7:41:7F  
          inet addr:10.16.56.139  Bcast:10.16.56.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fee7:417f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x8000 Memory:b800b000-b800bfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3444 (3.3 KiB)  TX bytes:3444 (3.3 KiB)


Toshiba-Laptop:~$ netstat -r

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.16.56.0      *               255.255.255.0   U         0 0          0 eth0
10.16.56.0      *               255.255.255.0   U         0 0          0 eth1
default         10.16.56.1      0.0.0.0         UG        0 0          0 eth1
default         10.16.56.1      0.0.0.0         UG        0 0          0 eth0

. . . but unfortunately . . . 

Toshiba-Laptop:~$ ping -c 3 10.16.56.1
PING 10.16.56.1 (10.16.56.1) 56(84) bytes of data.
From 10.16.56.139 icmp_seq=1 [COLOR="Red"]Destination Host Unreachable[/COLOR]
From 10.16.56.139 icmp_seq=2 [COLOR="Red"]Destination Host Unreachable[/COLOR]
From 10.16.56.139 icmp_seq=3 [COLOR="Red"]Destination Host Unreachable[/COLOR]

--- 10.16.56.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
, pipe 3


[/FONT]

---

### Post by phitoo on 2006-08-04
> **electri said:**
> I appreciate your suggestion, but it didn't seem to work.

:-(

I guess it was not a slam-dunk after all.

Working. Reverting ASAP.

---

### Post by RedBoot on 2006-08-04
Help me out here, I think you're just trying to get the WIRED eth0 'Marvel' to work first, right? (Cuz I'm struggling with the wireless NIC thing myself right now!)

A few things to try:

Undo what you have in the second post. You have one IP address on two interfaces.

When you plug in the network cable between you NIC and the router (switch?) do you get the correct lights on both devices (should look just like they do when running Windows)?

Try pinging the actual IP address 10.16.56.139, not just the 127.0.0.1 (probably just superstition on my part.)

---

### Post by electri on 2006-08-05
> **RedBoot said:**
> Help me out here, I think you're just trying to get the WIRED eth0 'Marvel' to work first, right? 

Affirmative . . . just plain old wired Ethernet.

> **RedBoot said:**
> When you plug in the network cable between you NIC and the router (switch?) do you get the correct lights on both devices (should look just like they do when running Windows)?

Affirmative.

> **RedBoot said:**
> Try pinging the actual IP address 10.16.56.139, not just the 127.0.0.1 (probably just superstition on my part.)

I'm now working at home again where my D-Link DI-604 router is at IP address 172.16.0.1.  I set up a static IP of 172.16.0.149 for my (Toshiba Tecra A4) laptop - both in the router and in Ubuntu's /etc/network/interfaces file. But pinging still doesn't work right.

With the static IP of 172.16.0.149 and forwarding ports under Win-XP, I can run Azureus (p2p) and he gets a happy little green face (no NAT problems) and downloads my torrents.  I can also ping everything under the sun, such as 172.16.0.1, 67.166.7.1 (Comcast DNS server) etc. 

But back under Ubuntu, the only things I can ping are loopback and the static IP address (172.16.0.149).  Everything else gives me Destination Host Unreachable.

BTW, I chose Ubuntu Linux initially to avoid having to burn a bunch of huge ISOs.  But apparently unless one is lucky and the network config works right out of the box, one quickly is forced into becoming a voracious forum reader and a networking guru.

I burned the ISOs for Fedora Core 5 last night.  Just for kicks I'm going to see if Fedora has any better luck in auto-configuring my NIC.

Thanks for your assistance.

---

### Post by electri on 2006-08-05
For the record, my Toshiba laptop networking problem is apparently *NOT* caused by my Ubuntu configuration.

I did not take sufficient notice that I have a solid yellow indicator light on my NIC under Linux, but I get an intermittent yellow under Windows XP as network transmissions occur.

I just got done loading 5 CDs worth of Fedora Core 5.  It correctly displayed the MAC address of my wired NIC card (eth0), it gave me an opportunity to set static IP, gateway, DNS servers, etc.  But once I booted into Fedora I had the same exact problem I've been having under Ubuntu:

1) I can *ONLY* ping loopback and the hard IP (172.16.0.149)
2) Ping attempts to router, DNS servers etc. error-out
2) solid yrllow MIC indicator light

So, anybody who took the trouble to read my posts (Thank You!) and might have thought Ubuntu was at fault - you can stop thinking that now.

It's back to the salt mines for me . . .

---

### Post by Joeak on 2006-08-05
DHCP should be easier to try with than messing with multiple static IP entries which could be causing conflicts with each other.  With DCHP enabled on all the probable interface names, whichever one you plug into should come active.  

In /etc/network/interfaces try:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp

---

### Post by RedBoot on 2006-08-05
I've been down the Fedora and SuSE routes and it's not any easier than Ubuntu.

Of course, nothings easy when it just won't work. 

Hope there's some answers down in that salt mine.

I also suggest the [Wireless Troubleshooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") even though yours is not a wireless adapter. The commands they employ and the methodical, step by step process they use are excellent and you should find the point where the problem occurs before you get to the wireless commands.

---

### Post by electri on 2006-08-06
> **Joeak said:**
> DHCP should be easier to try with than messing with multiple static IP entries which could be causing conflicts with each other.  With DCHP enabled on all the probable interface names, whichever one you plug into should come active.  

In /etc/network/interfaces try:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp


Good news.  After a reinstall of Ubuntu (following an intermediate install of Fedora) DHCP is now **working!** and I have network connectivity (through my D-Link router and Comcast cable modem here at home).  

I have no idea how I managed to screw-up something so simple since the */etc/network/interfaces* DHCP setup you describe is basically the installation default (except for the commented items).  But obviously, I screwed it up somehow.  Duh.

Thanks to everybody who took the time to respond to my posts.

---

### Post by electri on 2006-08-06
> **electri said:**
> Good news.  After a reinstall of Ubuntu (Dapper Drake) DHCP is now **working!** and I have network connectivity (through my D-Link router and Comcast cable modem here at home).

Oops . . . spoke too soon.  

I powered-off my laptop for a few hours.  Upon reboot **DHCP is broken again**):

1. Yellow link light on NIC is pegged **ON**
2. ifconfig shows no IP address on eth1 (wired NIC)
2. Ping attempts to anything but loopback say "[COLOR="Red"]Network is Unreachable[/COLOR]"

_daemon.log_
- DHCPDISCOVER continuously sent on eth1
- [COLOR="Red"]No DHCPOFFERS received[/COLOR]
- [COLOR="Red"]No working leases in persistent database - sleeping[/COLOR].

I really hate to say anything nice about Microsoft, but at least DHCP works every single time I boot my laptop into Windows XP, both at home (router and Comcast cable modem) and at work (gateway and proxy server). 
 
Hmmm, maybe I should just do a complete reinstall every time I want to use Linux on the laptop [Yes, I'm joking . . . it's the frustration talking]

Back to the drawing board . . .

---

### Post by electri on 2006-08-06
.

---

### Post by Margueritte on 2006-08-07
Hi
Try something, I don't have any problems with networking right now but struggled initially to get it up and running.. this worked for me
add / remove - remove dhcp from system
set static ip address
then reinstall dhcp...

---

### Post by electri on 2006-08-07
> **Margueritte said:**
> Hi
Try something . . . add / remove - remove dhcp from system set static ip address then reinstall dhcp...

As a rank beginner with Ubuntu, I wouldn't have any idea how to go about removing/reinstalling DHCP.  I haven't even gotten around to figuring out what package management system Ubuntu uses.  Also, I tried static IP over and over for several days and was never able to get it to work properly.

I'm back at work this morning where there is a gateway/DHCP server.  When I first booted-up Ubuntu, DHCP worked, I got an IP address on eth1, and I could get out to the Internet.  However, a little while later (a) I lost my network connection (b) ifconfig showed my IP address had disappeared, and (c) all my DHCPDISCOVERS on eth1 are going unanswered again:

- DHCPDISCOVER on eth1 to 255.255.255.255 port *nn* interval *nn*
. . . . 
- [COLOR="Red"]No DHCPOFFERS received[/COLOR]
- [COLOR="Red"]No working leases in persistent database - sleeping[/COLOR]

Rebooting Ubuntu had no effect.  DHCP did not work.

---

