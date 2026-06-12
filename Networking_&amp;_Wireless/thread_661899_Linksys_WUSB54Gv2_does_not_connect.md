---
title: "Linksys WUSB54Gv2 does not connect"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by strykrforce on 2008-01-08
I recently acquired an old PC that I put Xubuntu on along with a Linksys WUSB54Gv2 USB wireless adapter. I've installed ndiswrapper 1.50 and the "ndiswrapper -l" shows that the drivers are installed and the device is detected. The problem is that it won't connect to any wireless networks through both the built in network utility and the command line. I've been working on it for a week, and its become somewhat of an obsession (don't know if that's a good or bad thing). "iwconfig" keeps showing that it isn't associated with any access point and the ESSID is "off/any"

Please help, its driving me nuts...

---

### Post by rustybronco on 2008-01-08
could you post the output of lsusb?

---

### Post by strykrforce on 2008-01-08
Bus 001 Device 003: ID 13b1:000a Linksys
Bus 001 Device 001: ID 0000:0000

---

### Post by rustybronco on 2008-01-08
I don't know if it will help much, see if you can glean anything from this thread. 
[http://ubuntuforums.org/showthread.php?t=87991](http://ubuntuforums.org/showthread.php?t=87991)

---

### Post by Hightide on 2008-01-08
You may find this thread useful!

[http://ubuntuforums.org/showthread.php?t=588045&highlight=linksys](http://ubuntuforums.org/showthread.php?t=588045&highlight=linksys)

---

### Post by strykrforce on 2008-01-08
> **Hightide said:**
> You may find this thread useful!

[http://ubuntuforums.org/showthread.php?t=588045&highlight=linksys](http://ubuntuforums.org/showthread.php?t=588045&highlight=linksys)

That's for version4... I think it has a different chipset than the first two.

---

### Post by strykrforce on 2008-01-08
I can see the adapter in the network manager and it lets me change settings like roaming mode, whether to use DHCP and put passwords, but it doesn't connect to anything.

---

### Post by rustybronco on 2008-01-08
[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)
and
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

may help, also prism54.org
if you live in the states and get ticked at it i'll swap a v4 with you ( I would like to mess with a v2)

---

### Post by lahook on 2008-01-08
I have 2 machines with these cards working. one has gutsy the other has hardy alpha2.
I basically followed this post         [http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54](http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54)

i installed      cpp gcc build-essential linux-headers-$(uname -r)
                   ndisgtk    
                   ndiswrapper 1.51 (with other release's it would lock up or drop for me)
added the windows driver WUSB54Gv2.inf and the WUSBGXP.sys to the ndiswrapper folder
i think it's /etc/ndiswrapper (not with my machines @ work on windows)
set my router for wpa personal and mac filtering

forgot sudo modprobe ndiswrapper
sudo ndiswrapper -m

can you connect without any security?

---

### Post by strykrforce on 2008-01-08
Yeah, I followed that post also.

I installed cpp, gcc, build-essential, and the linux-headers that came on the Xubuntu 7.10 disk.
I didn't install ndisgtk because I figured it was just a gui.
ndiswrapper automatically copied the inf and sys file over to /etc/ndiswrapper/wusb54gv2.
My router is set on wep with no MAC filtering.

I can't connect even without security to a neighboring Linksys router.

EDIT -- Actually, it turns out that I AM using ndiswrapper 1.51.

---

### Post by strykrforce on 2008-01-08
Sorry man, I'm borrowing this from a friend while at college...

---

### Post by rustybronco on 2008-01-08
I'm **Not** me too-ing, ndiswrapper+ the drivers for your card is all I can find to work with this card, but the kernel has support for prism chipsets wlan-ng iirc.

---

### Post by rustybronco on 2008-01-08
can you drop wep from the router for a moment and try to connect, or try 64 bit wep?
***oops*** is the security off in the router? ( guess I should have re-read the thread first)

---

### Post by lahook on 2008-01-08
what linksys router do you have?
when using a wrk54g i could only connect without security.
with a wrt54gc and wrt54gsv7 i'm able to connect with wpa personal with tpik
if i get dropped most of the time i need to reboot to reconnect. (only been dropped on the gutsy machine)
i'm lost at why this isn't working for you. it sounds like we used pretty much the same set up.

when you installed the ndiswrapper you did the (make     sudo make install )?

---

### Post by strykrforce on 2008-01-08
Sorry, I don't know the exact model, but Windows tells me that it is a WRT54G when I connect to it. It's in someone else's apartment.

Yes, I did "sudo make" then "sudo make install"

EDIT -- My router is a D-link Dl-524 rev. D with the newest firmware.

---

### Post by lahook on 2008-01-08
what do you get with "sudo lshw -C network" ?
i get this:  *-network               
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       serial: 00:0f:66:14:53:40
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wusb54gv2 driverversion=1.51+Linksys,03/30/2004, 3.00.12 ip=192.168.0.103 link=yes multicast=yes wireless=IEEE 802.11g
here's my " cat /etc/network/interfaces"
auto lo
iface lo inet loopback 

my " iwconfig"
lo        no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"xxxxxxxx"  (my network name)
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx:xx:xx:xx:xx:xx  (mac address) 
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2432 B   Fragment thr:2432 B   
          Power Management:off
          Link Quality:96/100  Signal level:-34 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

do you get anything similar to these?
if you want to know what files are in  some of my folders let me know.
i hope this helps you

---

### Post by strykrforce on 2008-01-08
Results of "sudo lshw -C network":

*-network
description: wireless interface
physical id: 1
logical name: wlan0
serial: 00:12:17:92:73:68
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+wusb54gv2 driverversion=1.51+Linksys,03/30/2004, 3.00.12 link=no multicast=yes wireless=IEEE802.11g

Results of "iwconfig"

lo no wireless extensions

wlan0  IEEE 802.11g  ESSID:off/any
Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
Bit Rate:2Mb/s   Tx-Power:32 dBm
RTS thr:2432 B   Fragment thr:2432 B
Power Management:off
Link Quality:0  Signal level:0 Noise level:0
RX invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0  Missed beacon:0

Result of "cat /etc/network/interfaces"

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-mode Managed
wireless-essid xxxxx <- network name
wireless-key s:xxxxx <- password
wireless-channel 6
auto wlan0

What files do you have in your "/etc/ndiswrapper/wusb54gv2"?
Also, whenever I do "sudo ifup wlan0" or "sudo dhclient wlan0" no DHCPOFFERS are received.

---

### Post by lahook on 2008-01-08
try commenting out the added lines in your /etc/network/interfaces.conf  (#)

my /etc/ndiswrapper/wusb54gv2 contains 3 files
13B1:000A.F.conf     wusb54gv2.inf  and  wusbgxp.sys

the 13B1:000A.F.conf contains
:sys_files|wusbgxp.sys 
NdisVersion|0x50001
Environment|1
class_guid|4d36e972-e325-11ce-bfc1-08002be10318
mac_address|XX:XX:XX:XX:XX:XX
driver_version|Linksys,03/30/2004, 3.00.12.0
BusType|15
SlotNumber|01

BusType|0
CardType|USB
ConfigProfile|256
DeviceID|USB\Vid_13b1&Pid_000a
FWFileName|PRISMA02.arm
HelpText|The Linksys Wireless-G USB Network Adapter provides wireless local area networking.
NitroMode|1
PlatformID|14480
PpeCompressEnable|1
PpeConcatEnable|1
PpePdlpEnable|1
PpePiggyBackEnable|1
PRISMIOC|1
PSMode|1
Service|PRISM_A02
SilentInstall|1
SSID|PRISM-SSID
UsbVariant|14471
VendorDesc|Linksys Wireless-G USB Network Adapter

---

### Post by strykrforce on 2008-01-09
YES! Thank you, you have save my sanity ///_^

Removing the extra lines in /etc/network/interfaces allows me to connect to the routers. I guess that users shouldn't touch the built in network manager at all.

---

