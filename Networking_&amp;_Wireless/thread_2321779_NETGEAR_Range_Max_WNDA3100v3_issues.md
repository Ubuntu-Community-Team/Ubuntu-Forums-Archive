---
title: "NETGEAR Range Max WNDA3100v3 issues"
date: 2016-04-24
forum: Networking &amp; Wireless
---

### Post by haak2 on 2016-04-24
I'm new to Ubuntu but I was wondeing if anyone could help me out. I just installed Ubuntu 16.04 but I'm having trouble figuring out how to install ndiswrapper and the other crap, especially since the desktop doesn't have a wired connection. 

The guide I'm trying to use is this one:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing_packages_with_internet_access_on_another_computer](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing_packages_with_internet_access_on_another_computer)

Supposedly they can be installed from the same DVD I used to install Ubuntu but when I pop the DVD in nothing happens except it giving me the option to view file contents.

On the other part, I downloaded all the packages onto my phone, then transfered those packages to my ubuntu desktop but when I try to unpack it through a terminal, it can't find the file in the directory. 

I can double-click the packages and it gives me the option to install but when I click the install button nothing happens.

I'm pretty much at my wits end here so any help would be appreciated. Thanks.

---

### Post by Bucky Ball on 2016-04-24
Welcome. Please open a terminal and post the output of this:

```
sudo lshw -C network
```

Put it between code tags. See the green link in my signature for how. You may not need ndiswrapper and it is definitely best avoided. Last resort.

If you actually tell us what problems you are having with your wireless we might be able to give you more help getting it working.

If you can plug an ethernet cable in and update you may find your wireless starts working with a reboot or prior to without you doing anything. With no details about you hardware and situation, hard to know.

(PS: I would stop trying to install things when you're not exactly sure of the consequences before you find yourself reinstalling the OS! :))

---

### Post by haak2 on 2016-04-26
Here's what I got:
```

*-network                      
description:  Ethernet  interface        
product:  191 Gigabit  Ethernet  Adapter      
vendor:  Silicon Integrated  Systems  [SiS]       
physical  id:  4        
bus  info:  pci@0000:00:04.0        
logical  name:  enp0s4        
version:  02        
serial:  00:1c:25:89:8d:83        
size:  10Mbit/s        
capacity:  100Mbit/s        
width:  32 bits        
clock:  33MHz        
capabilities:  pm  bus_master cap_list  ethernet  physical  tp mii  10bt  10bt-fd 100bt  100bt-fd 
autonegotiation        
configuration:  autonegotiation=on broadcast=yes  driver=sis190 driverversion=1.4 duplex=half 
latency=0 link=no multicast=yes  port=MII speed=10Mbit/s        
resources:  irq:19  memory:fdffc000-fdffc07f ioport:fe00(size=128)
```

Just some background information first off:
1. Acer Aspire M1610
2. DRR2 2GB Ram
3. Dual boot with Windows Vista
4. Hard Drive partitioning: 150GB for Vista. 90GB for Ubuntu
5. Graphics card: GeForce 8400
6. Wireless Dongle: NETGEAR Range Max WNDA3100v3 N-600 Wireless Dual Band USB 2.0 Adapter

Basically, I'm trying to install my Netgear dongle so I can connect to the internet. Unfortunately, the router stuck all the way at the other side of the house and can't be moved so a wired connection would require me to move the entire computer and I'd like to leave that as an absolute last resort.

---

### Post by Bucky Ball on 2016-04-26
Was the USB wireless dongle plugged in when you ran that command? No sign of it.

---

### Post by haak2 on 2016-04-26
It was indeed since it's plugged in at the back at all times. I've taken it out and put it back in a couple of times but that hasn't changed the code given above.

---

### Post by Bucky Ball on 2016-04-26
Shot in the dark: try a different USB socket and run that command again, please.

---

### Post by kurt18947 on 2016-04-26
> 
6. Wireless Dongle: NETGEAR Range Max WNDA3100v3 N-600 Wireless Dual Band USB 2.0 Adapter


I think if one were to select the most difficult wifi device to get working in linux, Netgear's WNDA3100 Vx would be near the top of the list. I'm not sure about WNDA3100v3 but WNDA3100v2 would only be recognized using NDISwrapper and NDISwrapper is far from a simple 100% guaranteed-to-work solution.  The simplest solution would be to purchase a device known to work out of the box. All my portables have Intel wifi (works out of the box) and desktops are wired. I'm not up to speed on the latest & greatest but TrendNet TEW-649 still works. I see it's discontinued on TrendNet's site but it's still readily available on ebay among other sources. I'm sure there are newer maybe better devices available but I have no experience with them.


Edit:  I checked wikidevi for WNDA3100v3's chip set. There is a linux driver available for it but it's not included in mainstream distros yet. I'd have more confidence downloading the driver source and compiling it than trying to get NDISwrapper to work.  It still might not be that simple for the inexperienced.  Here's the chipset info:

[https://wikidevi.com/wiki/Netgear_WNDA3100v3](https://wikidevi.com/wiki/Netgear_WNDA3100v3)

Here's a source for hardware that works in linux without playing & praying:

 [https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux](https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux)

---

### Post by haak2 on 2016-04-28
> **Bucky Ball said:**
> Shot in the dark: try a different USB socket and run that command again, please.

Tried them all. Same result. XP

> **kurt18947 said:**
> I think if one were to select the most difficult wifi device to get working in linux, Netgear's WNDA3100 Vx would be near the top of the list. I'm not sure about WNDA3100v3 but WNDA3100v2 would only be recognized using NDISwrapper and NDISwrapper is far from a simple 100% guaranteed-to-work solution.  The simplest solution would be to purchase a device known to work out of the box. All my portables have Intel wifi (works out of the box) and desktops are wired. I'm not up to speed on the latest & greatest but TrendNet TEW-649 still works. I see it's discontinued on TrendNet's site but it's still readily available on ebay among other sources. I'm sure there are newer maybe better devices available but I have no experience with them.

Well you see the main reason I decided to install Ubuntu is that I'm currently testing it on my old computer. I'll be building a new budget PC soon but since a legit Windows will cost me £100+ I was hoping to see if I can survive without it. So if it comes to the point that I'd have to buy a new wifi adapter, I'd rather try my luck on one of those dodgy looking cheap Windows OEMs that are always floating around...

> 
Edit:  I checked wikidevi for WNDA3100v3's chip set. There is a linux driver available for it but it's not included in mainstream distros yet. I'd have more confidence downloading the driver source and compiling it than trying to get NDISwrapper to work.  It still might not be that simple for the inexperienced.  Here's the chipset info:

[https://wikidevi.com/wiki/Netgear_WNDA3100v3](https://wikidevi.com/wiki/Netgear_WNDA3100v3)

Hey, if it's free I'm willing to try. XP

Any idea how I download that? The guides in those links tell me that I need to connect my ubuntu machine with a wired connection but I can't do that. Is there anyway to, say, download that driver as a package onto my phone that I can then transfer onto my ubuntu and install?

[EDIT]

I downloaded the files containing the original code given here:
[https://github.com/jurobystricky/Netgear-A6210/blob/master/README.md](https://github.com/jurobystricky/Netgear-A6210/blob/master/README.md)

I don't know what to do after that.

---

### Post by Bucky Ball on 2016-04-28
Why bother? A cheap wifi dongle that will work 'out of the box' will probably cost you about 5 pound.

---

### Post by haak2 on 2016-04-28
Because I don't want to feel like I wasted £25. :p

In all honesty, I am open to the idea of buying another device as long as it's roughly £5-£10 but I would like some recommendations (Dual band prefferably). I've seen some on Amazon (like [this one]("https://www.amazon.co.uk/gp/aw/d/B01B7I19MQ/ref=mp_s_a_1_3?qid=1461871269&sr=8-3&pi=SY200_QL40&keywords=wifi+adapter+dual+linux&dpPl=1&dpID=31Pk9EZtqiL&ref=plSrch")) but then I see comments below that say it doesn't actually work with linux like it says it does so I'm very wary at the moment.

But I also don't mind trying to compile that driver. I mean it&#8217;s gotta be worth a try right?

---

### Post by haak2 on 2016-04-29
[UPDATE]

Okay, sorry for the ugly double posting but there's been a bit of change of situation here. Apparently I did have a way of connecting ubuntu to the Internet that had been staring in face the entire time: my phone. XP

So now I'm connected to the internet but it's a bit inconvenient to use my phone all the time so I would still like to compile that driver. Unfortunately I'm stuck on the very first line on the instructions. Doing a "git clone" command seems to return this error.
```
:~$ git clone https://github.com/jurobystricky/Netgear-A6210
The program 'git' is currently not installed. You can install it by typing:
sudo apt install git
```

Any ideas on what I'm doing wrong?

---

### Post by Bucky Ball on 2016-04-29
Yes. You do exactly what it tells you to do in the message you posted.

> The program 'git' is currently not installed. You can install it by typing: sudo apt install git


```
 sudo apt install git
```

... and try again. If you read the output after you run a command you might save yourself some time. ;)

---

### Post by haak2 on 2016-04-29
#-o

Wow. For some reason I put in* "sudo apt install git clone https://github.com/jurobystricky/Netgear-A6210"*  thinking that's what I had to do. Naturally, it didn't work so I just  assumed the suggestion was wrong. XP

So I followed the instructions and, sure enough, I now have a functional  Netgear WNDA3100v3 connecting me to my router. Took me about three  tries to get it connected because for some reason it kept dropping  connection after I typed the password in. I unplugged it and plugged it  back again and used that network restart code in the guide. Don't know  which one of two got it to work (or if it was a combination of both) but  it works and now I'm one happy user.

Can't say its reliability has been tested much but if it does start  playing up, I guess that'll be another issue. But for now consider this  problem SOLVED. :cool:

Thanks for all the help Kurt and Bucky.

[EDIT]

Tried three reboots. The first time it didn't stay connected but it did on the second and third tries.

---

### Post by Bucky Ball on 2016-04-29
No problem, excellent news and thanks for marking as solved. This is going to help others as this card is known to be extremely problematic in Ubuntu. 

Enjoy the ride. :)

PS: Does wireless still work OK after a system reboot? I'm guessing so.

---

### Post by kurt18947 on 2016-05-01
> **Bucky Ball said:**
> No problem, excellent news and thanks for marking as solved. This is going to help others as this card is known to be extremely problematic in Ubuntu. 

Enjoy the ride. :)

PS: Does wireless still work OK after a system reboot? I'm guessing so.

I believe WNDA3100 **V2** is the problem child. WNDA3100 V1 had a native linux solution, WNDA3100 V2 did not. V3 has a native linux solution. V4 look out! :P

---

### Post by haak2 on 2016-06-23
[B]Update

[/B]Hi guys. Not sure if I'm supposed to create a new thread for this or not but I'm having issues with my Netgear dongle again and was wondering if I could get some help again. So I've recently built a new computer and installed Ubuntu 16.04 onto it. I followed[ the same instructions]("https://github.com/jurobystricky/Netgear-A6210") to get the linux driver for my Netgear dongle and it does work but for some reason it never works after rebooting. I always have to restart the Network Manager using a terminal command, and that always gets it working again but it's just such a pain doing that every time I start my new computer. It's weird because on my old computer it worked perfectly. I never had to restart Network Manager and it would always work after rebooting but for some reason on my new computer it won't.  Here's some wireless info if it's any use.

[EDIT]

Never mind. It's working perfectly now after I did a clean reinstall of Ubuntu.

```

########## wireless info START ##########

Report from: 23 Jun 2016 18:34 BST +0100

Booted last: 23 Jun 2016 00:00 BST +0100

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Biostar Microtech Int'l Corp RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1565:2400]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0846:9014 NetGear, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              565248  1 mt7662u_sta

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::53e3:ca8f:10de:7f62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7681 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13379957 (13.3 MB)  TX bytes:924080 (924.0 KB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlan0     Ralink STA  ESSID:"VM4757813"  Nickname:"mt7632u_sta"
          Mode:Managed  Frequency=2.462 GHz  Access Point: <MAC 'VM4757813' [AC3]>   
          Bit Rate=104 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-56 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1823     1  0 18:21 ?        00:00:04 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         MediaTek Inc.
GENERAL.PRODUCT:                        WNDA3100v3
GENERAL.DRIVER:                         usb
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     VM4757813
GENERAL.CON-UUID:                       35ab3c45-512e-422f-9681-f461d28b8cf7
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     104 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   35ab3c45-512e-422f-9681-f461d28b8cf7 | VM4757813
IP4.ADDRESS[1]:                         192.168.0.15/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             194.168.4.100
IP4.DNS[2]:                             194.168.8.100
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = hamza-H81MDV3
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.0.1
DHCP4.OPTION[11]:                       expiry = 1466789343
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.0.15
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       routers = 192.168.0.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       domain_name_servers = 194.168.4.100 194.168.8.100
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::53e3:ca8f:10de:7f62/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8168g-2_0.0.1 02/06/13
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
VM4757813  <MAC 'VM4757813' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  63      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
Speeds     <MAC 'Speeds' [AC1]>  Infra  2     2417 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1       no        
VM2154007  <MAC 'VM2154007' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/VM4757813]] (600 root)
[connection] id=VM4757813 | type=wifi | permissions=user:hamza:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=VM4757813
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country GB: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Speeds' [AC1]>
                    Protocol:802.11b/g/n
                    ESSID:"Speeds"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality=29/100  Signal level=-78 dBm  Noise level=-79 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'VM2154007' [AC2]>
                    Protocol:802.11g/n
                    ESSID:"VM2154007"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/100  Signal level=-79 dBm  Noise level=-80 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'VM4757813' [AC3]>
                    Protocol:802.11g/n
                    ESSID:"VM4757813"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=91/100  Signal level=-54 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  476.405511]  [<ffffffffc0656827>] rt28xx_open+0xc7/0x150 [mt7662u_sta]
[  476.405551]  [<ffffffffc06569d0>] ? rt28xx_ioctl+0x80/0x80 [mt7662u_sta]

########## wireless info END ###########


```

---

### Post by soft-kristal on 2016-09-02
I ordered a wireless adapter from Think Penguin a few days ago and tested it today. It's fully plug and play without any fuss at all. According to Canonical, any firmware/driver will be upgraded with other updates.

---

### Post by kurt18947 on 2016-09-05
> **soft-kristal said:**
> I ordered a wireless adapter from Think Penguin a few days ago and tested it today. It's fully plug and play without any fuss at all. According to Canonical, any firmware/driver will be upgraded with other updates.

The simplest solution by far if not the least expensive. One nice thing about hardware support in Linux is that once it's there, support is not discontinued on a whim. The same is not true of hardware that require manufacturer supplied binaries. Those can be broken by a kernel upgrade. So yes, some research prior to purchasing devices to be used on *buntu machines can pay a nice dividend in reduced aggravation.

---

