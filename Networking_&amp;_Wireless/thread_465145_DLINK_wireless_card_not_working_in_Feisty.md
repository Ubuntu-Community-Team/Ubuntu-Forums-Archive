---
title: "DLINK wireless card not working in Feisty"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by mail480697 on 2007-06-05
I've got a new DLINK wireless PCI card that I'm trying to get going.  So far, no luck.  Basically, it looks like its working but never gets an IP address.  I need help.  Here are some details:

$ ethtool -i wlan0
driver: ndiswrapper
version: 1.38
firmware-version: D-Link,03/22/2005,4.0.0.1414
bus-info: 0000:01:0e.0

$ iwlist wlan0 scanning
wlan0 Scan completed :
Cell 01 - Address: 00:18:39:C2:CC:69
ESSID:"Voltaplein2"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.437 GHz (Channel 6)
Quality:100/100 Signal level:-29 dBm Noise level:-96 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Extra:bcn_int=100
Extra:atim=0
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK

$ sudo lshw -class network
*-network:0
description: Wireless interface
product: AR5212 802.11abg NIC
vendor: Atheros Communications, Inc.
physical id: e
bus info: pci@01:0e.0
logical name: wlan0
version: 01
serial: 00:15:e9:a8:9d:d3
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=D-Link,03/22/2005,4.0.0.1414 latency=128 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11b
resources: iomemory:febf0000-febfffff irq:19

$ sudo iwconfig wlan0
wlan0 IEEE 802.11b ESSID:"Voltaplein2"
Mode:Managed Frequency:2.437 GHz Access Point: Not-Associated
Bit Rate=108 Mb/s
Encryption key:3130-3938-4E52-4164-616D Security mode:restricted
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Notice that iwlist reports a strong signal, but iwconfig reports none at all! When I try to bring this interface up, I get:

$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:15:e9:a8:9d:d3
Sending on LPF/wlan0/00:15:e9:a8:9d:d3
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
$

It never hears back from the router, never gets an IP address

my syslog shows this:

Jun 1 22:31:49 localhost avahi-autoipd(wlan0)[3256]: Found user 'avahi-autoipd' (UID 111) and group 'avahi-autoipd' (GID 111).
Jun 1 22:31:49 localhost avahi-autoipd(wlan0)[3256]: Successfully called chroot().
Jun 1 22:31:49 localhost avahi-autoipd(wlan0)[3256]: Successfully dropped root privileges.
Jun 1 22:31:49 localhost avahi-autoipd(wlan0)[3256]: fopen() failed: Permission denied
Jun 1 22:31:49 localhost avahi-autoipd(wlan0)[3256]: Starting with address 169.254.10.115
Jun 1 22:31:54 localhost avahi-autoipd(wlan0)[3256]: Callout BIND, address 169.254.10.115 on interface wlan0
Jun 1 22:31:54 localhost avahi-daemon[4699]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.10.115.
Jun 1 22:31:54 localhost avahi-daemon[4699]: New relevant interface wlan0.IPv4 for mDNS.
Jun 1 22:31:54 localhost avahi-daemon[4699]: Registering new address record for 169.254.10.115 on wlan0.IPv4.
Jun 1 22:31:58 localhost avahi-autoipd(wlan0)[3256]: Successfully claimed IP address 169.254.10.115
Jun 1 22:31:58 localhost avahi-autoipd(wlan0)[3256]: fopen() failed: Permission denied


I'd sure appreciate help getting this baby going.

TIA

---

### Post by tturrisi on 2007-06-05
get rid of ndiswrapper & use the linux madwifi drivers for your atheros chip card!
madwifi is in linux-restricted-modules packages

---

### Post by mail480697 on 2007-06-06
I started with the madwifi drivers, which didn't work, and went to ndiswrapper as suggested by other postings in this forum.

Bottom line: Neither the madwifi drivers nor the ndswrapper driver work with this card.

What should I do?

---

### Post by moron on 2007-06-06
Are you absolutely sure that the Madwifi drivers did not work at all?  On my own box which has a PCI D-Link card with the same chipset I have intermittent issues with this card but can connect if I keep trying with ye olde "sudo /etc/init.d/networking restart".  From a fresh boot it takes anywhere from 2 to 4 or more tries but eventually it will connect (though it loses connection at random points).

I'd try sticking with the madwifi drivers if you since they are actively updated where as you are basically on your own with a mystery Windows binary and ndiswrapper.

Cheers

---

### Post by mail480697 on 2007-06-07
OK -- back to madwifi drivers.  Things are not getting better!

First off, the signal quality is lower:

$ iwlist scanning

ath0      Scan completed :

          Cell 01 - Address: 00:18:39:C2:CC:69
                    ESSID:"Voltaplein2"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/94  Signal level=-37 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  

Also:

$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"Voltaplein2"  Nickname:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/94  Signal level=-34 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Next, bring the if up fails as before:

$ sudo ifup ath0
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:15:e9:a8:9d:d3
Sending on   LPF/ath0/00:15:e9:a8:9d:d3
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
jerryb@LindsayBritton:~$ 


What is one to do?  Neither the ndiswrapper nor the madwifi drivers work!

---

### Post by tturrisi on 2007-06-07
signal quality is just fine!
different drivers use different equations to show signal quality, the bottom line is "can you connect".

If your wlan is Open and uses no encryption, then get rid of network-manager buggy app and put this in you /etc/network/interfaces file:
```
# Home
iface ath0 inet dhcp
wireless-essid YOUR-ESSID-NAME-HERE
# wireless-key WEP-KEY_HERE  # if use WEP put in key & remove the comment at beginning of line
auth ath0
```

---

### Post by mail480697 on 2007-06-07
Yeah, I already did that. Here's the file:

$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


# The primary network interface
iface eth0 inet dhcp

auto ath0

iface ath0 inet dhcp
wireless-essid myessid
wireless-key s:mypassword

---

### Post by tturrisi on 2007-06-08
Try using net-admin to associate with the ap. or do:
iwconfig ath0 key XXXXXXXXXX
[http://madwifi.org/wiki/UserDocs/SimpleWEPClient](http://madwifi.org/wiki/UserDocs/SimpleWEPClient)
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

---

### Post by mail480697 on 2007-06-08
OK -- I tried those things without much success.  First I got the AP MAC address via arp -a (I have a second machine up)

$ arp -a
? (192.168.1.100) at 00:50:DA:80:E2:89 [ether] on eth0
? (192.168.1.1) at 00:18:39:C2:CC:67 [ether] on eth0

the router is the second IP.

Then I specified all parameters on the iwconfig command:

$ sudo iwconfig ath0 essid "myessid" key s:mykey ap 00:18:39:C2:CC:67
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"myessid"  Nickname:""
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:18:39:C2:CC:67   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/94  Signal level=-40 dBm  Noise level=-95 dBm
          Rx invalid nwid:476  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Then I tried to get an address via dhcp:

$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 18224
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:15:e9:a8:9d:d3
Sending on   LPF/ath0/00:15:e9:a8:9d:d3
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
$ 

As you can see, consistent failure!

The tail of the syslog reveals:

Jun  8 11:17:48 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
Jun  8 11:17:56 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
Jun  8 11:18:09 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
Jun  8 11:18:10 localhost dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jun  8 11:18:10 localhost dhclient: send_packet: No such device
Jun  8 11:18:16 localhost dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Jun  8 11:18:16 localhost dhclient: send_packet: No such device
Jun  8 11:18:19 localhost dhclient: No DHCPOFFERS received.
Jun  8 11:18:19 localhost dhclient: No working leases in persistent database - sleeping.
Jun  8 11:18:26 localhost dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Jun  8 11:18:26 localhost dhclient: send_packet: No such device
Jun  8 11:18:35 localhost dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jun  8 11:18:35 localhost dhclient: send_packet: No such device
Jun  8 11:18:41 localhost dhclient: No DHCPOFFERS received.
Jun  8 11:18:41 localhost dhclient: No working leases in persistent database - sleeping.
Jun  8 11:19:58 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
Jun  8 11:20:06 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 21
Jun  8 11:20:27 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 2
Jun  8 11:20:29 localhost dhclient: No DHCPOFFERS received.
Jun  8 11:20:29 localhost dhclient: No working leases in persistent database - sleeping.

The "no such device" message is new, pobably as a result of specifying the AP MAC address, though I'm not sure.

I sure wish this was easier!

---

### Post by tturrisi on 2007-06-08
try using a hypen inbetween every 4 wep characters: 1234-1234-12
Is the ap setup to use a hex key (open) or a passkey (shared)?
Try setting up the ap with no security at first, then see if can connect.
Then setup as "open" with wep.
Then try closed w/ wep & passphrase.

Have you tried net-admin?  system > networking?

---

### Post by mail480697 on 2007-06-08
The security on the router is WPA2, not WEP.  The passkey is ASCII, hence the "key s:mykey" option.

I configured the router to require the passkey, since I want to restrict access in my neighborhood.  Really don't want to use WEP either. 

FWIW my other wireless device (MacBook) connects first time, every time using the same ESSID and passkey.

I tried messing with the net-admin app, but got no further than this. Actually the CLI has told me more about what's going on (or not,as in this case!)

Are you suggesting that I disable the passkey just to see if I can get it going without?  If I succeed, though, it will mean that the wireless support in MADWIFI is broken in this regard, which may help me file a bug report, but won't get it working.

---

### Post by moron on 2007-06-08
Your signal strength is almost too good if what is being reported is correct.  If memory serves 70 is the maximum you can get (the value you see is *not* a fraction).  It can actually cause a problem if your signal strength is too high as it can confuse the card so if you are right next to the router, move further away.  Something in the range of 40 is considered a reasonably strong signal.  

Are you using WPA or WPA2?  WPA2 may not be supported by the MadWifi drivers (according the sticky in this section, check the madwifi.org website to be sure on that front).  Try switching to WPA (TKIP) in your router and see if that solves the problem.  I can confirm that this does work with my Atheros based card.

Also, your listed "/etc/network/interfaces" file seems to be missing needed arguments.  Refer to the  sticky for everything you need in there:

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

Cheers

---

### Post by tturrisi on 2007-06-08
> **mail480697 said:**
> The security on the router is WPA2, not WEP.  The passkey is ASCII, hence the "key s:mykey" option.
That explains your issu.
You cannot nativiely connect to a WPA secured wlan, you must install wpasupplicant.
[http://www.translever.com/howto/wifi/madwifi-wpa_supplicant_RSN_howto/madwifi-wpa_supplicant_RSN_howto.html](http://www.translever.com/howto/wifi/madwifi-wpa_supplicant_RSN_howto/madwifi-wpa_supplicant_RSN_howto.html)
or
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by iClouseau88 on 2007-06-08
What's the model number of this card?  Secondly, does it work in Windows XP?

I suspect that this is DLink WDA-2320 PCI Wireless Card which I have not been able to get it work with DI-624C wireless router in my bro-in-law's XP machine.  Full signal strength but still no Internet.  I use the latest 1.02 firmware from DLink then Atheros 4.2.2.33 firmware (lizzi555 in dslreports.com), and WPA PSK/TKIP encryption but still no go.  You may have to try no encryption first.  I may also have to try resetting the computer first.

---

### Post by daschmidty on 2007-06-08
If it is a dlink 5xx series pci card..they do not claim to support WPA encryption. My new G510 and i know the G550 only list support for 64/128 bit WEP.

---

### Post by mail200752 on 2007-06-09
Thanks all for  your input.  To summarize:

wpasupplicant is installed. I looked over the linksk, especially 

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

but they seem to be deprecated by feisty.  e.g. the keywords "wpa-xxx" are superseded by "wireless-xxx"  

The card is a dlink g520. the doc says that it supports wpa

The signal strength is so good because the card is less than three feet from the router!  (I won't move it to its destination until it works properly)

Anything else I should try to debug this or get it working?

---

### Post by tturrisi on 2007-06-09
try this:

/etc/network/interfaces
```
auto ath0
iface ath0 inet dhcp
# For linux >= 2.6.14 and recent madwifi (>=r1500) use 'wext', otherwise use 'wpa-driver madwifi'
wpa-driver wext
wpa-ssid MyNet
wpa-psk 000102030405060708090a0b0c0d0e0f101112131415161718191a1b1c1d1e1f
```

[http://madwifi.org/wiki/UserDocs/Distro/Debian/ConfiguringtheMadWifidevice](http://madwifi.org/wiki/UserDocs/Distro/Debian/ConfiguringtheMadWifidevice)

---

### Post by mail480697 on 2007-06-09
Adding the wpa- options did the trick!

Wow!  I can't believe that this was so hard!!  I really thought that the wireless improvements in Feisty would have done the trick.  A little disappointing, I must say,

Still, thanks to one and all for your help!

---

### Post by tturrisi on 2007-06-09
> **mail480697 said:**
> Adding the wpa- options did the trick!

Wow!  I can't believe that this was so hard!!  I really thought that the wireless improvements in Feisty would have done the trick.  A little disappointing, I must say,

Still, thanks to one and all for your help!

Glad you got it working!
FYI, apparantly wifi in Ubuntu has improved a lot.  Just last year I was running Dapper & wifi was a royal pita.  I run Debian now so cannot compare Ubuntu wifi improvements.  The newest "improvements" in Feisty are the automatic detection & inclusion of restricted-packages, which madwifi is a part of, as well as network-manager connection applet (buggy afaic).  Debian & linux overall desperately needs something comparale to windows wireless zero config.  The best so far is a package called WICD  (a name I came up with but not developed by me):   [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

