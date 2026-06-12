---
title: "Connect a Wifi with WPA Key in LiveCD but cannot connect once installed."
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by jmtalarn on 2008-02-13
Hello to everybody,

I tested the Ubuntu 7.10 distribution with the Live-CD in my laptop with a wifi PCMCIA Card SMC8235w and I checked that all works fine, event it connect to my home network with WPA personal key.
But once system was installed I cannot connect to my network with the WPA key, however it can connect with another network without security.

What there is in the LiveCD version that not will be installed on my laptop?

In the LiveCD I don't configured anything, simply NetworkManager detected the network and when I clicked over the network detected a window asking me for the WPA key appeared.

However, once installed, detects my network home with less signal than with the LiveCD and when I click over the network detected, the popup window ask me only for a  WEP key, and no WPA keys can be selected in the key type combo list.

If I try to configure NetworkManger with the manual configuration, I can select the WPA Personal type key but then not connect.

I have the wpa_supplicant installed and the /etc/network/interfaces only with the lo interface configured, as NetworkManager requires to manage the interfaces.

Anyone can help me?? What I need to do to let my installed Ubuntu work like the LiveCD?

Thank yoU!

---

### Post by jmtalarn on 2008-02-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/59549&quot;]https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/59549](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/59549&quot;]https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/59549) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I find this,

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/59549]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/59549")

is very similar to mine :o.

---

### Post by wieman01 on 2008-02-13
For troubleshooting, you might want to start here:

[http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")

---

### Post by jmtalarn on 2008-02-13
Ok, I will try it.

But in the LiveCD I don't configured anything and it worked very well without any change in any file. What can be the reason of this?

---

### Post by wieman01 on 2008-02-13
> **jmtalarn said:**
> Ok, I will try it.

But in the LiveCD I don't configured anything and it worked very well without any change in any file. What can be the reason of this?
Updates. Once you have installed Ubuntu, updates overwrite the driver used on the LiveCD. It's a fairly common issue.

I hope Hardy will be much better in this respect.

---

### Post by jmtalarn on 2008-02-13
Ah! Oh! Pretty updates then...

And How I can "downgrade" the driver? How can I extract the driver from the CD and install it?

Many thanks wieman01! I posted this same post in the spanish Ubuntu forums and no body replies so fast, accurate and clear than you!

---

### Post by wieman01 on 2008-02-13
> **jmtalarn said:**
> Ah! Oh! Pretty updates then...

And How I can "downgrade" the driver? How can I extract the driver from the CD and install it?

Many thanks wieman01! I posted this same post in the spanish Ubuntu forums and no body replies so fast, accurate and clear than you!
No problem. :-)

Could you find out what sort of chipset your card uses? That would help. Unfortunately downgrading won't be possible once you have upgraded, but I could find a good tutorial for you if you tell me the name of the chipset (e.g. Ralink RT73).

---

### Post by staticvoid on 2008-02-13
you might try reseting the router itself, or going to 192.168.X.X to change some settings..

sv

---

### Post by jmtalarn on 2008-02-13
wieman01: 
 Is a PCMCIA EZ-Connect SMC2835W card based on the Chipset Prism Javelyn!
 The driver displayed when I do the lsmod is prism54.
 Thanks another time!

staticvoid:
 Is not router problem, there is another laptop (winxp) in the same network working fine. And this is the best and secure configuration that can network take due security.



Thanks all for your interest!

---

### Post by wieman01 on 2008-02-13
A couple of things... First of all this thread is a good starting point:

[http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")

To help us understand what's going on, please post the results of following commands:
> sudo iwlist scan
> sudo lshw -C network
> sudo cat /etc/network/interfaces

---

### Post by jmtalarn on 2008-02-13
Ok! I will do it this afternoon, now I'm at the office.

At this time all can I say is that in /etc/network/interfaces only there is defined the localhost interface:
> auto lo
iface lo inet loopback

Thanks! I will tell you tomorrow about the results of the commands!

---

### Post by wieman01 on 2008-02-13
> **jmtalarn said:**
> Ok! I will do it this afternoon, now I'm at the office.

At this time all can I say is that in /etc/network/interfaces only there is defined the localhost interface:

Thanks! I will tell you tomorrow about the results of the commands!
Now back to work, hush hush! ;-)

---

### Post by jmtalarn on 2008-02-13
Hello! another time here!

Ok, I runned the commands that you say an this are the results:

sudo iwlist scan (my network with WPA personal is the first one)
> eth1      Scan completed :
          Cell 01 - Address: 00:14:7F:8E:84:75
                    ESSID:"SpeedTouch9A848B"
                    Mode:Master
                    Encryption key:on
                    Frequency:2.412 GHz (Channel 1)
                    Quality:29/0  Signal level:-49 dBm  Noise level:-78 dBm
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:50:7F:35:5A:8A
                    ESSID:"Talleres Morest"
                    Mode:Master
                    Encryption key:on
                    Frequency:2.462 GHz (Channel 11)
                    Quality:251/0  Signal level:-83 dBm  Noise level:-78 dBm
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:19:15:4F:C7:16
                    ESSID:"WLAN_BF"
                    Mode:Master
                    Encryption key:on
                    Frequency:2.422 GHz (Channel 3)
                    Quality:9/0  Signal level:-69 dBm  Noise level:-78 dBm
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:60:B3:ED:00:80
                    ESSID:"WLAN_92"
                    Mode:Master
                    Encryption key:on
                    Frequency:2.422 GHz (Channel 3)
                    Quality:250/0  Signal level:-84 dBm  Noise level:-78 dBm
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

sudo lshw -C network
>   *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:55:cf:6e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:04:e2:b3:73:70
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=prism54 driverversion=1.2 latency=80 maxlatency=28 mingnt=10 module=prism54 multicast=yes wireless=IEEE 802.11b/g

and the content of /etc/network/interfaces is what I have said
> auto lo
iface lo inet loopback


What conclusions can we take with this?

---

### Post by wieman01 on 2008-02-13
Have you tried connecting to a WEP secured and unsecured network? Did it work? Try an unsecured one first (all encryption turned off).

If this does not do, we have to replace the current Linux driver with "ndiswrapper". I am trying to avoid it, but that might be the ultimate solution.

---

### Post by jmtalarn on 2008-02-13
Yes, I can  be connected with a unsecured Network.

In another hand.
I tried to do the following in the manual:

> sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo wpa_supplicant -w -D<****see footer below***> -i<interface> -c/etc/wpa_supplicant.conf -dd 
sudo ifconfig <interface> up
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

and I got the following

with the last step (sudo dhclient eth1):
> jmtalarn@jmtalarn-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 6807
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:04:e2:b3:73:70
Sending on   LPF/eth1/00:04:e2:b3:73:70
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8



And then in the wpa_supplicant console i get...
> RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=70
WEXT: Custom wireless event: 'Received a beacon from an unkown AP to 00:60:B3:ED:00:80  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:14:7f:8e:84:75 blacklist count incremented to 2
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 556 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:7f:8e:84:75 ssid='SpeedTouch9A848B' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - blacklisted
1: 00:60:b3:ed:00:80 ssid='WLAN_92' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:60:b3:57:78:34 ssid='WLAN_8C' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:7f:8e:84:75 ssid='SpeedTouch9A848B' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - blacklisted
1: 00:60:b3:ed:00:80 ssid='WLAN_92' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:60:b3:57:78:34 ssid='WLAN_8C' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:14:7f:8e:84:75 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:7f:8e:84:75 ssid='SpeedTouch9A848B' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:14:7f:8e:84:75 ssid='SpeedTouch9A848B'
Try to find non-WPA AP
Trying to associate with 00:14:7f:8e:84:75 (SSID='SpeedTouch9A848B' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=24
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=72
WEXT: Custom wireless event: 'Authenticate request (ex) to 00:14:7F:8E:84:75  : ACCEPTED  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=72
WEXT: Custom wireless event: 'Authenticate request (ex) to 00:14:7F:8E:84:75  : ACCEPTED  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:14:7f:8e:84:75 into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 556 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:7f:8e:84:75 ssid='SpeedTouch9A848B' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:14:7f:8e:84:75 ssid='SpeedTouch9A848B'
Try to find non-WPA AP
Trying to associate with 00:14:7f:8e:84:75 (SSID='SpeedTouch9A848B' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
ioctl[SIOCSIWMODE]: Input/output error
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=24
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=72
WEXT: Custom wireless event: 'Authenticate request (ex) to 00:14:7F:8E:84:75  : ACCEPTED  (00)'
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:14:7f:8e:84:75 blacklist count incremented to 2
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 385 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:7f:8e:84:75 ssid='SpeedTouch9A848B' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - blacklisted
1: 00:60:b3:ed:00:80 ssid='WLAN_92' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:7f:8e:84:75 ssid='SpeedTouch9A848B' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - blacklisted
1: 00:60:b3:ed:00:80 ssid='WLAN_92' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:14:7f:8e:84:75 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:7f:8e:84:75 ssid='SpeedTouch9A848B' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:14:7f:8e:84:75 ssid='SpeedTouch9A848B'
Try to find non-WPA AP
Trying to associate with 00:14:7f:8e:84:75 (SSID='SpeedTouch9A848B' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
ioctl[SIOCSIWMODE]: Input/output error
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=72
WEXT: Custom wireless event: 'Authenticate request (ex) to 00:14:7F:8E:84:75  : ACCEPTED  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=70
WEXT: Custom wireless event: 'Received a beacon from an unkown AP to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=24
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=70
WEXT: Custom wireless event: 'Received a beacon from an unkown AP to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:14:7f:8e:84:75 into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
Scan timeout - try to get results
Received 556 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:7f:8e:84:75 ssid='SpeedTouch9A848B' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:14:7f:8e:84:75 ssid='SpeedTouch9A848B'
Try to find non-WPA AP
Trying to associate with 00:14:7f:8e:84:75 (SSID='SpeedTouch9A848B' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
ioctl[SIOCSIWMODE]: Input/output error
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=24
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=70
WEXT: Custom wireless event: 'Received a beacon from an unkown AP to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=72
WEXT: Custom wireless event: 'Authenticate request (ex) to 00:14:7F:8E:84:75  : ACCEPTED  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=72
WEXT: Custom wireless event: 'Authenticate request (ex) to 00:14:7F:8E:84:75  : ACCEPTED  (00)'
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:14:7f:8e:84:75 blacklist count incremented to 2
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
Scan timeout - try to get results
Received 214 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:7f:8e:84:75 ssid='SpeedTouch9A848B' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - blacklisted
Try to find non-WPA AP
0: 00:14:7f:8e:84:75 ssid='SpeedTouch9A848B' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - blacklisted
No APs found - clear blacklist and try again
Removed BSSID 00:14:7f:8e:84:75 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:7f:8e:84:75 ssid='SpeedTouch9A848B' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:14:7f:8e:84:75 ssid='SpeedTouch9A848B'
Try to find non-WPA AP
Trying to associate with 00:14:7f:8e:84:75 (SSID='SpeedTouch9A848B' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
ioctl[SIOCSIWMODE]: Input/output error
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=70
WEXT: Custom wireless event: 'Received a beacon from an unkown AP to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=24
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=63
WEXT: Custom wireless event: 'Received a probe from client to 00:14:7F:8E:84:75  (00)'
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth1
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
ioctl[SIOCSIWAUTH]: Operation not supported

> jmtalarn@jmtalarn-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 6807
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:04:e2:b3:73:70
Sending on   LPF/eth1/00:04:e2:b3:73:70
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8


---

### Post by jmtalarn on 2008-02-13
In the previous step I run wpa_supplicant with parameter -Dwext.

---

### Post by wieman01 on 2008-02-14
> **jmtalarn said:**
> In the previous step I run wpa_supplicant with parameter "-Dwext" .
This is a Prism chipset so you try "-Dhostap" instead of "-Dwext". 
> hostap = Host AP driver (Intersil Prism2/2.5/3)
atmel = ATMEL AT76C5XXx (USB, PCMCIA)
wext = Linux wireless extensions (generic)
madwifi = Atheros
wired = wpa_supplicant wired Ethernet driver
If that still fails, let's try another tool called WICD:

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

Installation is very simple and it reportedly works for a great number of people.

If all that fails in the end, we have to revert to using 'ndiswrapper' which I am trying to avoid. :-)

---

### Post by jmtalarn on 2008-02-14
Hi! 
I found this post in UbuntuForums...

[http://ubuntuforums.org/showthread.php?t=30445]("http://ubuntuforums.org/showthread.php?t=30445")

Maybe the solution is to use ndiswrapper...

But my question is: The LiveCD is using ndiswrapper ?

In the HowTo references to a wlan interface, as in the LiveCD. In the LiveCD is defined a wlan interface and a wmaster interface, but the prism54 module is loaded too!

Anyone can confirm this?

---

### Post by wieman01 on 2008-02-14
It's an old thread so the information might be a bit outdated.

The LiveCD does not use 'ndiswrapper', it's the native Linux driver that kicks in. Second, the wifi interface is not the module, so the names differ. Don't worry about the interface name for the time being. Give 'ndiswrapper' a go and post here if you need my help.

---

### Post by jmtalarn on 2008-02-14
Is possible to overwrite the firmware existing on the system with the one in the LiveCD?

What I trying to say is: Booting the LiveCD, copying the firmware existing in the distribution and writting over the existing in the local file system.

It can be a solution? Or with the posterior updates it will be overwrited another time?

I will try this afternoon the -Dhostap parameter another time in wpa_supplicant command but I tried yesterday and didn't work. I will do step by step, taking time in all steps.

And with the supose that wcid doesn't work. What will be the way?

Aaargh!

---

### Post by jmtalarn on 2008-02-14
More Information relationed with the post #15...

When I run wpa_supplicant with less detail in messages I get a Line like 

> Authentication with 00:00:00:00:00:00 timed out

every time that it tries to associate to the network ( Trying to associate with 00:14:7f:8e:84:75 (SSID='SpeedTouch9A848B' freq=2412 MHz) )

---

### Post by wieman01 on 2008-02-14
If WICD does not work, we have to go for 'ndiswrapper'.

But your idea of pulling of copy of the driver/firmware from the LiveCD might actually work. I have never done that before but it's a possibility. You need to located the file, then pull a copy and overwrite the installed version of the driver. Sounds interesting...

---

### Post by jmtalarn on 2008-02-14
I get a doubt for myself proposal. 

Using a "correct" driver/firmware it will enable automatically the WPA encryption with the NetworkManager? And if it is true, why Ubuntu installs another version driver/firmware version than the used in the LiveCD?

Searching for the forums I find this about the gnome keyring:

[http://ubuntuforums.org/showthread.php?t=514028]("http://ubuntuforums.org/showthread.php?t=514028")

Do You think it have relation with that NetworkManager don't show the possibility of input a WPA key for the autodetected WPA network?

---

### Post by jmtalarn on 2008-02-14
Bad news...

My great Idea to overwrite the firmware didn't work...

Using the wpa_supplicant with hostap didn't work...
> jmtalarn@jmtalarn-laptop:~$ **sudo wpa_supplicant -w -Dhostap -ieth1 -c/etc/wpa_supplicant.conf -dd**
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'hostap' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=16):
     53 70 65 65 64 54 6f 75 63 68 39 41 38 34 38 42   SpeedTouch9A848B
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=10): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='SpeedTouch9A848B'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=19 enc_capa=0x7
  capabilities: key_mgmt 0xf enc 0x7
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:04:e2:b3:73:70
wpa_driver_hostap_set_wpa: enabled=1
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_countermeasures: enabled=0
wpa_driver_hostap_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Added interface eth1
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth1
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_hostap_set_wpa: enabled=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
wpa_driver_hostap_set_drop_unencrypted: enabled=0
wpa_driver_hostap_set_countermeasures: enabled=0
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6


> jmtalarn@jmtalarn-laptop:/etc$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:04:e2:b3:73:70
Sending on   LPF/eth1/00:04:e2:b3:73:70
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

My next step will be install wcid...

I'll tell you the results

---

### Post by wieman01 on 2008-02-14
And if all this does not help, you find competent help here:

[http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")

---

### Post by jmtalarn on 2008-02-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/59549](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/59549) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I found this related with my problem:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/59549]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/59549")

I installed wcid but after the reboot it didn't work. This weekend I will take more time in this, ( my girlfriend shouted for more time in her side! ;) , sure is problem with the services or the session startup.

---

### Post by jmtalarn on 2008-02-18
I desist!

I couldn't repair the wicd...

I reinstalled everything, and I will work with a wired connection....](*,)   :(

...I will try it later, maybe with Hardy Heron

---

### Post by wieman01 on 2008-02-18
So "ndiwrapper" is not option at all?

---

### Post by jmtalarn on 2008-02-21
Hi!

I did it!!!

I'm obstinate! 

Finally I copied all /lib/modules/2.6.22-14-generic/ from LiveCd to the installed one.

And after this Ubunt booted with a little more time but Now it detects the network and his security, it prompts me for the WPA personal, I introduce it and it connect!

Well! Was Hard!

Thanks wieman01 for all the support!!

---

### Post by wieman01 on 2008-02-21
Wow, you impress me. Really. :-) Thanks for sharing this information. But make sure your driver will not be overwritten by any updates. You can lock the version using Synaptic I reckon.

Well done!

---

