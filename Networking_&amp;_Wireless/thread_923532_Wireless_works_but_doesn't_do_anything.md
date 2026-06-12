---
title: "Wireless works but doesn't do anything?"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by L815 on 2008-09-18
I'm using Kubuntu Intrepid alpha 5. The wireless card is detected and detects points, but doesn't connect or do anything.

It works perfectly in Ubuntu Intrepid alpha 5. 
I can't manually set it because I don't know how to do it on an encrypted connection.

Anyone have any ideas on what I can do to get it to connect?

PS: I have updated everything since yesterday.

---

### Post by vikram on 2008-09-18
Please try Knetworkmanager

sudo aptitude install knetworkmanager network-manager wpasupplicant 

This will help you set up encrpted network via a GUI without manual configuration

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu](https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu)

---

### Post by L815 on 2008-09-19
Knetworkmanager is what is installed by default, and is culprit of the issue.

---

### Post by Crafty Kisses on 2008-09-19
Post the results of:
```
lshw -C network
```
And:
```
iwconfig
```

---

### Post by Adhémar on 2008-09-19
Hello,

I have the same problem. The results of the commands are:

```
adhemar@vaio:~$ sudo lshw -C network
[sudo] password for adhemar:
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:49:e1:92
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
```
I just hid the irrelevant ethernet section.

and:
```
adhemar@vaio:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"name-of-a-network"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:BD:65:41:B4
          Bit Rate=54 Mb/s   Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality=72/100  Signal level:-62 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Note that I am not connected with wlan0, and that the connection doesn't work. If I add the interface to /etc/network/interfaces, and try to ifup it manually, I just get some dhcp timeout.

Thks in advance,

Adhémar

---

### Post by Adhémar on 2008-09-19
Well, sorry for the double post, but I have more informations... Here is what I get when trying to bring the wireless up with ifup:

```
root@vaio:~# cat /etc/network/interfaces 
auto lo                                  
iface lo inet loopback                   

iface wlan0 inet dhcp
```

```
root@vaio:~# iwlist wlan0 scan
wlan0     Scan completed :    
                         
[...]
          Cell 16 - Address: 00:1E:BD:65:39:C4                                
                    ESSID:"UCLouvain-prive"                                   
                    Mode:Master                                               
                    Channel:11                                                
                    Frequency:2.462 GHz (Channel 11)                          
                    Quality=62/100  Signal level:-70 dBm  Noise level=-127 dBm
                    Encryption key:off                                        
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s        
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s     
                              48 Mb/s; 54 Mb/s                                
                    Extra:tsf=00000414641fa18c                                
                    Extra: Last beacon: 1572ms ago                            

[...]
```

```
root@vaio:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"UCLouvain-prive"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:BD:65:41:B4
          Bit Rate=54 Mb/s   Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Encryption key:off
          Power Management:off
          Link Quality=79/100  Signal level:-55 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
root@vaio:~# sudo ifdown wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:19:d2:49:e1:92
Sending on   LPF/wlan0/00:19:d2:49:e1:92
Sending on   Socket/fallback
root@vaio:~# sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:19:d2:49:e1:92
Sending on   LPF/wlan0/00:19:d2:49:e1:92
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/network/run/ifstate: No such file or directory
[: 164: 0: unexpected operator
```

---

### Post by vikram on 2008-09-19
look at the output of the command 
dmesg

and 

iwevent (while connecting)

it may provide some more info 

Also if wlan0 is defined in  /etc/network/interfaces Knetworkmanager will NOT configure it. you can either choose the manual configuration or Knetworkmanager

---

### Post by Adhémar on 2008-09-19
Hello,

> **vikram said:**
> Also if wlan0 is defined in  /etc/network/interfaces Knetworkmanager will NOT configure it. you can either choose the manual configuration or Knetworkmanager
Yes, I know. But my point is that the problem is not knetworkmanager, but something else.

For the output of dmesg, I can't post everything, because it exceed the forum upload limit, but the important part seems to be:
```
[23809.719885] wlan0: deauthenticated
[23810.716421] wlan0: authenticate with AP 00:1e:bd:64:5e:d4
[23810.717826] wlan0: authenticated
[23810.717838] wlan0: associate with AP 00:1e:bd:64:5e:d4
[23810.720312] wlan0: RX ReassocResp from 00:1e:bd:64:5e:d4 (capab=0x421 status=0 aid=1)
[23810.720321] wlan0: associated
[23810.721350] wlan0: disassociating by local choice (reason=3)

```

With iwevent, I get:

```
root@vaio:~# iwevent
Waiting for Wireless Events from interfaces...
17:13:37.551152   wlan0    Custom driver event:ASSOCINFO(ReqIE65010802040b160c12182432043048606c RespIE)
17:13:37.551280   wlan0    New Access Point/Cell address:00:1E:BD:64:5E:D4
17:13:37.551311   wlan0    New Access Point/Cell address:Not-Associated
17:13:54.029073   wlan0    Scan request completed
17:14:54.031287   wlan0    Scan request completed
```

But I think that an important point is that the interface wmaster0 is not found, as 'wmaster0: unknown hardware address type 801' says. I don't know what is this wmaster0...

Thks

A.

edit: I just noticed that the frequency in iwconfig and iwlist don't match. I don't have time to check it right now.
edit2: I checked it. It was not the real problem. I am still unable to connect to my wireless network.

---

### Post by seeker5528 on 2008-09-19
> **Adhémar said:**
> Hello,


Yes, I know. But my point is that the problem is not knetworkmanager, but something else.

For the output of dmesg, I can't post everything, because it exceed the forum upload limit, but the important part seems to be:
```
[23809.719885] wlan0: deauthenticated
[23810.716421] wlan0: authenticate with AP 00:1e:bd:64:5e:d4
[23810.717826] wlan0: authenticated
[23810.717838] wlan0: associate with AP 00:1e:bd:64:5e:d4
[23810.720312] wlan0: RX ReassocResp from 00:1e:bd:64:5e:d4 (capab=0x421 status=0 aid=1)
[23810.720321] wlan0: associated
[23810.721350] wlan0: disassociating by local choice (reason=3)

```



I got something similar to that in Intrepid while network manager is installed, purged all the network manager stuff and my wireless works.

> **L815 said:**
> Anyone have any ideas on what I can do to get it to connect?

At the command prompt type:

sudo kate /etc/network/interfaces

: if you prefer some other editor than kate, use that.

I posted the configurations I use here [LINK](http://ubuntuforums.org/showpost.php?p=5817554&postcount=32)

For the dns lines to work you need resolvconf installed.
For dhcp use something like:

```

iface wlan0 inet dhcp
wireless-essid [your ssid]
wireless-key [your WEP key]

```

or if I've done my research correctly for WPA:

```

iface wlan0 inet dhcp
wpa-ssid [your ssid]
wpa-psk  [text passphrase or 64 character hex key]

```

To have it enabled at boot, add an additional auto line if one is not already present for the interface in question:

auto wlan0

: or add the interface to an existing line:

auto eth0 wlan0

: to stop/start it with out rebooting type:

sudo ifdown wlan0
sudo ifup wlan0

Later, Seeker

---

