---
title: "Problems with the WPC54GX on old laptop..."
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by shearn89 on 2007-06-19
Hi all - I'm having some problems with the Linksys WPC54GX on an old laptop (see sig.). I'm running Dapper, and have succesfully installed the drivers using ndiswrapper, however, whenever I try and wun wpa_supplicant (i'm using WPA2 Personal security on the AP), it freezes just as it appears to connect....

Any help would be greatly appreciated.

Here is the output of iwconfig and ifconfig:
```

iwconfig:
wlan0     Auto  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:108 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig:
eth0      Link encap:Ethernet  HWaddr 08:00:46:1D:17:A0  
          inet addr:192.168.3.135  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::a00:46ff:fe1d:17a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1724801 (1.6 MiB)  TX bytes:3798 (3.7 KiB)
          Interrupt:10 Base address:0x6800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:672 (672.0 b)  TX bytes:672 (672.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:13:10:51:E7:D8  
          inet6 addr: fe80::213:10ff:fe51:e7d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1588 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:126958 (123.9 KiB)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:36000000-36080000 

```

I know the card is working, because the power light flashes a lot (though it's not constant).

Here is my wpa_supplicant.conf file:
```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

ap_scan=2

network={
        ssid="GBS_Net"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
#	pairwise=CCMP TKIP
#	group=CCMP TKIP       		
	psk=[REMOVED]
  }

```

The AP's essid is hidden. When I run wpa_supplicant without ap_scan=2, the AP is listed, but with no ESSID (i can tell its mine due to the MAC Address), and it won't connect. 

Running 
```

sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper -dd

```

Gives a stream of output, then the laptop freezes. The Power light goes out on the card, but the Link light is constant.

I'll try and get the output of the command above.

EDIT: tried "wpa_supplicant.... >> wpaout", but it crashes before it writes the output, so here it is (most of it) manually. It skips past the beginning, because it scrolls up before i can read it, and freezes before i can go back and look.

```

EAPOL: External notification - EAP fail=o
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8c07 len=34
AssocReq IE wireless event - hexdump(len=26) <long string of numbers in pairs>
Wireless event: cmd=0x8c07 len=34
AssocReq IE wireless event - hexdump(len=26) <same long string of numbers in pairs>
Wireless event: cmd=0x8b15 len=20
Wireless event: Wireless event: new AP: <my ap's mac address>
Association info event
req_ies - hexdump(len=26): <same long string of numbers in pairs>
resp_ies - hexdump(len=26): <same long string of numbers in pairs>
WPA: set own WPA/RSN IE - hexdump(len=26): <same long string of numbers in pairs>
State: ASSOCIATING -> ASSOCIATED
Associated to a new BSS: BSSID=<my ap's mac address>
No keys have been configure - skip key clearing
Network configuration found for the current AP
WPA: Using WPA IE from AssocReq to set cipher suites
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY-MGMT WPA-PSK
WPA set own WPA IE default - hexdump(len=26): <same long string of numbers in pairs>
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Associated with <my ap's mac address>
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
RX EAPOL from <my ap's mac address>
RX EAPOL - hexdump(len=58): <HUGE string of numbers in pairs>
Setting authentication timeout: 10 sec 0 usec
WPA: EAPOL frame too short to be a WPA EAPOL-Key (len 58, expecting at least 99)

```

And then it freezes...

---

### Post by shearn89 on 2007-06-20
bump... (sorry)

---

