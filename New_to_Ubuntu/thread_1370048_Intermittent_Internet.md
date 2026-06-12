---
title: "Intermittent Internet"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-01-01
I'm having really annoying problems with my internet constantly dropping out. I have wireless and the network manager says it's connected with good signal but when you want to load a site or click on links it often takes ages. Sometimes it says server not found and just hangs. Even tho it looks like I'm connected to the internet I'm not, I can't go anywhere. Anyone have an idea what this could be?

I now have no internet at all. I have obviously totally messed up the settings and don't know what they should be. I need someone who really knows about Networks to help me ..please ? I have posted terminal out put suggested in other peoples posts on the last page of this thread or post whatever :D Thanks.

---

### Post by drakkoss on 2010-01-01
OK .. the NIC (Network Interface Card, or chip) should be at least 5 years old.The NIC is connected between your computer and the network box provided to you by your cable company.Bye !!

---

### Post by Paqman on 2010-01-01
> **ThePinkWitch said:**
> Anyone have an idea what this could be?

The problem could be your ISP. Have you got another machine you can check on? Have you rebooted your router yet?

---

### Post by ThePinkWitch on 2010-01-01
> **Paqman said:**
> The problem could be your ISP. Have you got another machine you can check on? Have you rebooted your router yet?

I just booted up the other computer and the internet was working fine. I got back on this one and it's really fast, so not sure whats going on. The other one has windows on it and seems to always work ok. I'm not sure if it's my ubuntu settings or a problem with my ISP. Lightening fast one minute and comatose the next. I was impressed how easily I got my wireless connection to work with Ubuntu compared with all the dramas I had a year ago when I wanted to try Ubuntu. Just worked right away this time. I just need to solve this and a couple of small other probs and I will be extremely happy :) Thankyou for your replies.

---

### Post by Paqman on 2010-01-02
> **ThePinkWitch said:**
> Lightening fast one minute and comatose the next.

Is it slow to initially find a site? It could be a DNS problem. Can you temporarily [switch your Domain Name Servers in your router]("https://store.opendns.com/setup/device/router/") to:
208.67.222.222
208.67.220.220 

...(which is OpenDNS) and see if you get any improvement?

---

### Post by ThePinkWitch on 2010-01-03
Thanks for your reply..I can't get internet at all now. I got tired of the net not working and decided after losing network manger that I would just reinstall Ubuntu because my internet worked just fine to begin with. I accidently deleted the partition with winxp on it so spent the last few days reinstalling windows and Ubuntu. Trouble is no matter what I do I can't get my damn internet working at all now. Once it said it was connected but firefox wouldn't connect and update manager couldn't download anything. I'm about to reinstall again and see if that helps because I have deleted and tried to set up numerous connections now. Help?

---

### Post by ThePinkWitch on 2010-01-03
> **Paqman said:**
> Is it slow to initially find a site? It could be a DNS problem. Can you temporarily [switch your Domain Name Servers in your router]("https://store.opendns.com/setup/device/router/") to:
208.67.222.222
208.67.220.220 

...(which is OpenDNS) and see if you get any improvement?

 Re: Intermittent Internet
Thanks for your reply..I can't get internet at all now. I got tired of the net not working and decided after losing network manger that I would just reinstall Ubuntu because my internet worked just fine to begin with. I accidently deleted the partition with winxp on it so spent the last few days reinstalling windows and Ubuntu. Trouble is no matter what I do I can't get my damn internet working at all now. Once it said it was connected but firefox wouldn't connect and update manager couldn't download anything. I'm about to reinstall again and see if that helps because I have deleted and tried to set up numerous connections now. Help?

---

### Post by ThePinkWitch on 2010-01-04
I finally got the internet working again..now to see if it's still dropping out.

---

### Post by mkoehler on 2010-01-04
Sounds good, let us know.  If it is a DNS renewal issue, then you should still be able to access websites via the IP address (not that this is preferable, but it will allow us to discern if it is a DNS issue or not).  Here's a few IPs that you can test:

Ubuntu: 91.189.94.156
Google: 64.233.169.106
Yahoo: 209.191.93.53

---

### Post by ThePinkWitch on 2010-01-04
> **mkoehler said:**
> Sounds good, let us know.  If it is a DNS renewal issue, then you should still be able to access websites via the IP address (not that this is preferable, but it will allow us to discern if it is a DNS issue or not).  Here's a few IPs that you can test:

Ubuntu: 91.189.94.156
Google: 64.233.169.106
Yahoo: 209.191.93.53

Thankyou for helping me with this, it's driving me nuts. I can connect ok or I should say Network manager says it's connected,  but it's still dropping out and for long periods of time. how can I use those Ip to test it. Sorry I'm a bit hopeless with this stuff. I'm not sure if it's my IP or maybe someone is using my wireless or something because I've been getting really slow speeds for a few weeks now. I've maybe configured the connection wrong.  :confused:

---

### Post by Methuselah on 2010-01-04
How far are you from where your wifi access point is located?
Are you moving about?

---

### Post by AgentZ86 on 2010-01-04
If it's working good on a separate windows computer, and not on ubuntu then what is the difference in your network card ?

When you connect with windows are you connecting wirelessly ? or wired ?

What is your wireless network card make/model ?

I had a similar problem with netgear wireless usb stick / driver on ubuntu, 

The very same computer could boot to windows and worked great, but on ubuntu it also worked great sometimes and would loose internet sometimes.

The wireless network meter said that my connection strength was low on ubuntu but it said it was very high on windows.

So I noticed a difference right away.

I suspect compatibility issue but of course it can be other things I wish I could help.

Can you try the wireless card/ from the working windows computer and put in your ubuntu system to see if there is any noticeable difference ?

Also did you happen to notice if the drop out may occur mostly when both computers are on the wireless network at the same time or does it make any difference if only the unbuntu computer is on by itself ?

I hope this helps

---

### Post by Prisma on 2010-01-04
Hi guys, happy new year :)

I am also having random connection problems. I am using Ubuntu 9.04 64bits. I have a D-Link wireless router and a D-Link USB stick. 
My wife has Ubuntu 9.04 32 bits version in her laptop with an Atheros internal wireless chip and her wireless signal never drops. 

I used to have the 32 bits version installed in the same PC and I never had this problem. When I installed the 64 bit version few months ago I got this weird random drop of connection. I think its a bug in the 64bits version. :(

---

### Post by Dracona on 2010-01-04
> **ThePinkWitch said:**
> I'm having really annoying problems with my internet constantly dropping out. I have wireless and the network manager says it's connected with good signal but when you want to load a site or click on links it often takes ages. Sometimes it says server not found and just hangs. Even tho it looks like I'm connected to the internet I'm not, I can't go anywhere. Anyone have an idea what this could be?


I have had similar problems, but it was related with my wireless router ( linksys ) just curious if you are using a linksys router.  if not plz disregared this post.

Thanks 
Dracona

---

### Post by ThePinkWitch on 2010-01-05
> **Methuselah said:**
> How far are you from where your wifi access point is located?
Are you moving about?

I'm only about 15' from the wireless modem and I have excellent signal strength.

---

### Post by ThePinkWitch on 2010-01-05
> **AgentZ86 said:**
> If it's working good on a separate windows computer, and not on ubuntu then what is the difference in your network card ?

When you connect with windows are you connecting wirelessly ? or wired ?

What is your wireless network card make/model ?

I had a similar problem with netgear wireless usb stick / driver on ubuntu, 

The very same computer could boot to windows and worked great, but on ubuntu it also worked great sometimes and would loose internet sometimes.

The wireless network meter said that my connection strength was low on ubuntu but it said it was very high on windows.

So I noticed a difference right away.

I suspect compatibility issue but of course it can be other things I wish I could help.

Can you try the wireless card/ from the working windows computer and put in your ubuntu system to see if there is any noticeable difference ?

Also did you happen to notice if the drop out may occur mostly when both computers are on the wireless network at the same time or does it make any difference if only the unbuntu computer is on by itself ?

I hope this helps

Thankyou everyone for dropping by to help.

I dual boot on this computer and it's definitely heaps better on Windows. I have a netgear WG111v2 usb dongle, the modem is a SpeedStream 2936 Wifi. The drop outs occur wether the other computer is on or not. Its actually better on the other computer as well. I have issues with both but much worse on Ubuntu. I have actually emailed my ISP and am waiting for them to ring me. I connect wirelessy. I'm just thinking I installed and deleted the connection so many times I may have done something weird to the settings. I wasn't sure of a couple of the settings. I really hope to sort this out so I can use Ubuntu again. Thanks :)

---

### Post by ThePinkWitch on 2010-01-06
Any more ideas..If I can't get the internet to work Ubuntu is useless to me :( I now have the netmanager saying I'm connected with 100% signal strength but can't go anywhere.
ayte@kaytesRocket:~$ sudo dhclient wlan0
[sudo] password for kayte: 
There is already a pid file /var/run/dhclient.pid with pid 1927
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:18:4d:19:cb:b1
Sending on   LPF/wlan0/00:18:4d:19:cb:b1
Sending on   Socket/fallback
DHCPREQUEST of 10.0.0.2 on wlan0 to 255.255.255.255 port 67
DHCPACK of 10.0.0.2 from 10.0.0.138
bound to 10.0.0.2 -- renewal in 884728642 seconds.
kayte@kaytesRocket:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
01:00.1 Display controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
kayte@kaytesRocket:~$ lsusb
Bus 001 Device 007: ID 090c:1000 Feiya Technology Corp. Flash Drive
Bus 001 Device 005: ID 0846:6a00 NetGear, Inc. WG111v2 54 Mbps Wireless [RealTek RTL8187L]
Bus 001 Device 002: ID 04b8:0847 Seiko Epson Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
kayte@kaytesRocket:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
arc4                    1660  2 
ecb                     2524  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
x_tables               16544  1 ip_tables
snd_seq_oss            28576  0 
ppdev                   6688  0 
usblp                  12636  0 
rtl8187                50624  0 
mac80211              181076  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
cfg80211               93052  2 rtl8187,mac80211
led_class               4096  1 rtl8187
parport_pc             31940  1 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
usb_storage            52576  1 
sis900                 19932  0 
mii                     5212  1 sis900
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
sis_agp                 6972  1 
agpgart                34988  3 ttm,drm,sis_agp
kayte@kaytesRocket:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
arc4                    1660  2 
ecb                     2524  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
x_tables               16544  1 ip_tables
snd_seq_oss            28576  0 
ppdev                   6688  0 
usblp                  12636  0 
rtl8187                50624  0 
mac80211              181076  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
cfg80211               93052  2 rtl8187,mac80211
led_class               4096  1 rtl8187
parport_pc             31940  1 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
usb_storage            52576  1 
sis900                 19932  0 
mii                     5212  1 sis900
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
sis_agp                 6972  1 
agpgart                34988  3 ttm,drm,sis_agp
kayte@kaytesRocket:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
arc4                    1660  2 
ecb                     2524  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
x_tables               16544  1 ip_tables
snd_seq_oss            28576  0 
ppdev                   6688  0 
usblp                  12636  0 
rtl8187                50624  0 
mac80211              181076  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
cfg80211               93052  2 rtl8187,mac80211
led_class               4096  1 rtl8187
parport_pc             31940  1 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
usb_storage            52576  1 
sis900                 19932  0 
mii                     5212  1 sis900
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
sis_agp                 6972  1 
agpgart                34988  3 ttm,drm,sis_agp
kayte@kaytesRocket:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
arc4                    1660  2 
ecb                     2524  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
x_tables               16544  1 ip_tables
snd_seq_oss            28576  0 
ppdev                   6688  0 
usblp                  12636  0 
rtl8187                50624  0 
mac80211              181076  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
cfg80211               93052  2 rtl8187,mac80211
led_class               4096  1 rtl8187
parport_pc             31940  1 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
usb_storage            52576  1 
sis900                 19932  0 
mii                     5212  1 sis900
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
sis_agp                 6972  1 
agpgart                34988  3 ttm,drm,sis_agp
kayte@kaytesRocket:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:2a:dc:76:3a  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:91 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9549 (9.5 KB)  TX bytes:9549 (9.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:4d:19:cb:b1  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:4dff:fe19:cbb1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:141674 (141.6 KB)  TX bytes:62879 (62.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-4D-19-CB-B1-31-39-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

kayte@kaytesRocket:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SpeedStream2936"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:13:A3:F0:80:41   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kayte@kaytesRocket:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:A3:F0:80:41
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"SpeedStream2936"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 11248ms ago
                    IE: Unknown: 000F537065656453747265616D32393336
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C

---

### Post by ThePinkWitch on 2010-01-06
Noone any ideas???

---

