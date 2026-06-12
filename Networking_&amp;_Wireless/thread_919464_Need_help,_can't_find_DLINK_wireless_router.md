---
title: "Need help, can't find DLINK wireless router"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by wangrui on 2008-09-14
Hi everyone,

I have a problem which I really can't solve by myself. Can anyone help me out?

I bought a DLINK DI-524M wireless router. I can connect to the router from Windows XP without any problem. But from ubuntu, no matter how I try. I can't find the router. I can see a lot of other routers from

        sudo iwlist scan

And I can connect to other routers. But just can't see the router I bought.
Here is the output of iwconfig
```
ath0      IEEE 802.11g  ESSID:"WRNET"  Nickname:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:1023  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
The output of lshw -class net
```
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wifi0
       version: 01
       serial: 00:15:af:a2:29:f8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

```
sudo iwlist scan
```
ath0      Scan completed :
          Cell 01 - Address: 00:14:78:E0:C4:F8
                    ESSID:"TP-LINK"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f01010008ff7f
          Cell 02 - Address: 00:19:E0:C9:EF:F0
                    ESSID:"TP-LINK"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f01010008ff7f
          Cell 03 - Address: 00:1D:0F:2C:B4:A8
                    ESSID:"TP-LINK"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f01010008ff7f

```
sudo iwlist ap
```
ath0      Peers/Access-Points in range:
    00:14:78:E0:C4:F8 : Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
    00:19:E0:C9:EF:F0 : Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm
    00:1D:0F:2C:B4:A8 : Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm

```
There should be no problem of the wireless driver. Because it can connect to other routers, even with LEAP encryption. And there should be no problem of the router, because I can connect to it from Windows XP. But why can't this rounter be found under ubuntu. There are a lot of hardware settings in the router. But I don't know anyone of them. Can anybody help me out?

I found a lot of articles on the web. But all of them assume the router can be seen from iwlist. But my problem is that I can't see the router from iwlist. And there should be no hardware problem. The same router and wireless card can work perfectly in Windows. And the same wireless card can connect to other routers in ubuntu. What could the problem be? What should I do? Thanks very much!

---

### Post by prshah on 2008-09-14
> **wangrui said:**
> 
Here is the output of iwconfig
```
ath0      IEEE 802.11g  ESSID:"WRNET"  Nickname:""

```
sudo iwlist scan
```
ath0      Scan completed :
          Cell 01 - Address: 00:14:78:E0:C4:F8
                    ESSID:"TP-LINK"
          Cell 02 - Address: 00:19:E0:C9:EF:F0
                    ESSID:"TP-LINK"
          Cell 03 - Address: 00:1D:0F:2C:B4:A8
                    ESSID:"TP-LINK"

```


Can you please post the SSID and MAC address of the dlink router (see from Win)? 

Why do all the cells have the _same_ essid (but different mac ids?). Have you "sanitized" the output or is that actually what your network card sees?

---

### Post by wangrui on 2008-09-14
> **prshah said:**
> Can you please post the SSID and MAC address of the dlink router (see from Win)? 

Why do all the cells have the _same_ essid (but different mac ids?). Have you "sanitized" the output or is that actually what your network card sees?

Thank you for helping me out.

There is a router admin page at 192.168.0.1. In the status page, it says

```

 &#38887;&#20307;&#29256;&#26412;(Firm version) : v1.02CN ,  0day:0h:0m:43s
--------------------------------------------
LAN &#31471;
MAC &#22320;&#22336;(Address): 	 00:1e:58:86:36:40
IP &#22320;&#22336;(Address): 	 192.168.0.1
&#23376;&#32593;&#25513;&#30721;: 	 255.255.255.0
DHCP &#26381;&#21153;&#22120;: 	  Enabled
--------------------------------------------
WAN &#31471;
MAC &#22320;&#22336;(Address): 	 00:15:af:a2:29:f8
&#32852;&#26426;&#29366;&#24577;(Status): 	 Getting IP from DHCP server...  
IP &#22320;&#22336;(Address): 	 0.0.0.0
&#23376;&#32593;&#25513;&#30721;: 	 0.0.0.0
&#32593;&#20851;(Gateway): 	 0.0.0.0
DNS &#26381;&#21153;&#22120;: 	 
--------------------------------------------
&#26080;&#32447;802.11g
SSID : 	WRLINK
&#20449;&#36947;(Channel): 	6
&#21152;&#23494;&#26041;&#24335;(Encryption): 	WPA2 Mixed(AP), Disabled(WDS)

```

In the wireless advance settings, it said
> 
&#26080;&#32447;&#39640;&#32423;&#35774;&#32622;(wireless advance settings)
TX&#36895;&#29575;: 	        Automatic
&#22825;&#32447;&#21457;&#23556;&#21151;&#29575;: 	10%
&#20449;&#26631;&#38388;&#38548;: 	100(&#27627;&#31186;ms, &#33539;&#22260;:20~1000, &#40664;&#35748;:100)
RTS &#38400;&#20540;: 	2346(&#33539;&#22260;range: 256~2346, &#40664;&#35748;:2346)
&#20998;&#27573;&#38400;&#20540;: 	2346(&#33539;&#22260;range: 256~2346, &#40664;&#35748;:2346, &#21482;&#33021;&#20026;&#20598;&#25968;)
DTIM &#26102;&#38388;: 	1(&#33539;&#22260;range: 1~255, &#40664;&#35748;:1)
&#21069;&#23548;&#30721;&#31867;&#22411;: 	&#30701;&#21069;&#23548; (.)&#38271;&#21069;&#23548; 

I kind hope some settings in this page can make it work. But I don't understand any of them. And I don't know how to translate them to English. Sorry about that.

Sometimes I can see different routes, mostly 5 from my apartment. But now there are only three TP-LINKs. I guess it's because three of my neighbours are using TP-LINK. Their signals are very weak. I can't even see so many routers from Windows. But in ubuntu I see a lot more routers except mine. Is it because the signal is too strong?

---

### Post by wangrui on 2008-09-14
Hi,

I booted to Windows XP. I can see five access points in Windows
```

WRLINK 100%
NETGEAR 20%
company 0%
TP-LINK 0%
super_man 0%

```
When I scan again, only three left.

When I connected to the router, I found the following information from the network status page
```

MAC	00-15-af-a2-29-f8
IP	192.168.0.102
netmask	255.255.255.0
gateway	192.168.0.1
DHCP	192.168.0.1
DNS	192.168.0.1

```

And in the network hardware setting tab. I found the following information
```

Atheros AR5007EG Wireless Network Adapter - Advance Setting
802.11b Preamble		Long and Short
Map Register			256
Network Address			Not exist
Power Save Mode			Normal
Scan Valid Interval		60

```

When I back to ubuntu, there are two access points left,
```

wangrui@wreeepc:~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:B0:0C:01:10:74
                    ESSID:"IPCOM"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=1/70  Signal level=-94 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:21:27:36:95:26
                    ESSID:"super_man"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f01010008ff7f


```

---

### Post by wangrui on 2008-09-14
And here is the route's wireless basic setting
```

&#28608;&#27963;&#26080;&#32447;(Active Wireless)  	: Yes
&#26080;&#32447;&#32593;&#32476;&#21517;(ESSID) 		: WRLINK(&#21035;&#21517;&#26159;SSID)
&#26080;&#32447;&#20449;&#36947;(Channel) 		: 6
&#33258;&#21160;&#25195;&#25551;&#20449;&#36947;(Auto Scan Channel) 	: No 	
802.11g&#26041;&#24335;(Use 802.11g) 	: Yes
WMM 				: Yes 	
&#28608;&#27963;&#38544;&#34255;&#26080;&#32447;(Hide wireless)	: No  (&#21035;&#21517;&#26159;SSID&#24191;&#25773;) 

```

---

