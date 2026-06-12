---
title: "Trying to connect to my unsecured wireless network, not getting an IP address."
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by Royle on 2006-09-13
Ubuntu 6.06 recognizes my wireless card.  To configure it, I went to the properties of it, filled in my SSID, and set it to DHCP and enabled it.  It is not given an IP and I can not connect to the internet.  Is there something I'm doing wrong?  Any help is greatly appreciated.

---

### Post by trubblemaker on 2006-09-14
can you give me the content of :
```
 iwconfig 
ifconfig 
iwlist scan 
```
it will help with debugging thanks

---

### Post by Royle on 2006-09-14
```
mike@basement:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0D:87:13:FD:06
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:12:0E:01:D0:0D
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x4000

mike@basement:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"Royle"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=49/100  Signal level=29/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

mike@basement:~$ iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
mike@basement:~$ iwlist wlan0 ap
wlan0     No Peers/Access-Point in range

mike@basement:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results
eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


```

---

### Post by trubblemaker on 2006-09-14
ok good news it's recognizing your card, bad news it's not associating to an ip address.

Did you just upgrade to dapper?  

Does the network GUi freeze at all on you?

what's the output of 
```
 lspci | grep controller 
```

when you get your essid listed when you type 
```
 iwconfig 
```
I think your is royal, and it says that the access point isn't associated try typing
```
 iwconfig wlan0 ap any 
iwconfig 
sudo dhclient wlan0
ifconfig 
```
then test if the internet works. I'll need the output if it doesn't work.

---

### Post by NetworkGuy on 2006-09-14
What make/model/chipset is the wireless card?

---

### Post by Royle on 2006-09-14
This is a clean install of dapper.  The network GUI doesn't freeze, but after I configure the wireless part, a dialog box comes up saying activating wlan0, and that stays for about 30 seconds to a minute.  I tried your suggestions and the wireless card was still not given an IP.  Here is the output of everything.  To get iwconfig wlan0 ap any to work I had to put sudo in front of it.
```


mike@basement:~$  lspci | grep controller
0000:00:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:00:09.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
0000:00:0a.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
0000:00:0b.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
0000:00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
mike@basement:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"Royle"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=46/100  Signal level=25/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

mike@basement:~$ iwconfig wlan0 ap any
Error for wireless request "Set AP Address" (8B14) :
    SET failed on device wlan0 ; Operation not permitted.
mike@basement:~$ sudo iwconfig wlan0 ap any
mike@basement:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"Royle"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=47/100  Signal level=26/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

mike@basement:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:12:0e:01:d0:0d
Sending on   LPF/wlan0/00:12:0e:01:d0:0d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
mike@basement:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0D:87:13:FD:06
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:87ff:fe13:fd06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2877161 (2.7 MiB)  TX bytes:320093 (312.5 KiB)
          Interrupt:11 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:12:0E:01:D0:0D
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x4000
```

Thanks for your continued support.

---

### Post by Royle on 2006-09-14
My wireless card is the Airlink AWLH3025 Wireless G PCI card seen here [http://www.airlinkplus.com/wireless/awlh3025.htm](http://www.airlinkplus.com/wireless/awlh3025.htm) .
It uses the ACX111 chipset.

---

### Post by trubblemaker on 2006-09-14
ok so looking over everything I see when you do iwlist scan, nothing is listed, do you have encyption on your wireless network? can you move the computer until you get a listing from 
```
 iwlist scan 
```
if you can't see the network you won't be able to connect to it.

---

### Post by Royle on 2006-09-14
There is no protection on my wireless network, also my computer is about 5 feet from the wireless router right now, as it's connected to it by wire right now, so I can't see location being a reason for it not picking up the network.

---

### Post by trubblemaker on 2006-09-14
have you ever connected to that network? can other computers connect?

---

### Post by trubblemaker on 2006-09-14
try messign around with the wireless settings on your router

---

### Post by Royle on 2006-09-14
Yep, that same computer has connected to the wireless network when windows was installed on it, and my PSP connects to it.

---

### Post by trubblemaker on 2006-09-14
so that's really not cool. if you can't see the network on iwlist scan, then your can't connect. any ineresting messages related in dmesg?

---

### Post by NetworkGuy on 2006-09-14
Use this howto to get your ACX111 working.  There is a known firmware issue with the kernel and the ACX111 chipset.

[http://www.ubuntuforums.org/showthread.php?t=233565](http://www.ubuntuforums.org/showthread.php?t=233565)

Don't worry that it says it's for a Linksys card, this howto will work for any ACX111 chipset card.  I have the same chipset and had the same problems.  This got me up and running in a couple of minutes.

---

