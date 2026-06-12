---
title: "Wifi connects but no internet"
date: 2016-08-20
forum: Networking &amp; Wireless
---

### Post by Arminius on 2016-08-20
I've seen similar postings of this problem but none of the solutions seem to work for me.

Previous threads asked for this information. 

```
user@Computer:~$ ifconfig -a
enp2s0    Link encap:Ethernet  HWaddr (1st MAC Address)  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

enp5s2    Link encap:Ethernet  HWaddr (2nd MAC Address) 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:1st IP I think  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:184704 (184.7 KB)  TX bytes:184704 (184.7 KB)

wlx0015af9cfc82 Link encap:Ethernet  HWaddr (3rd MAC Address)  
          inet addr:2nd IP I think  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: 3rd IP I think Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6305 (6.3 KB)

user@Computer:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
Linux Computer 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
user@Computer:~$ ispci -nnk | grep -iA2 net
No command 'ispci' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
ispci: command not found
user@Computer:~$ iwconfig
enp2s0    no wireless extensions.

lo        no wireless extensions.

enp5s2    no wireless extensions.

wlx0015af9cfc82  IEEE 802.11bgn  ESSID:"MyESSID"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: (4th MAC Address)  
          Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
user@Computer:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

### Post by Keith_Helms on 2016-08-21
What is > inet addr:2nd IP I think  Did you edit the output from the command after pasting it?

---

### Post by wildmanne39 on 2016-08-21
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Arminius on 2016-08-21
> **Keith_Helms said:**
> What is   Did you edit the output from the command after pasting it?

Yes, figured it was bad security to post to much personal information like Mac/IP address.
Next time I'll just change some numbers around.

---

### Post by Keith_Helms on 2016-08-22
Mode Ad-Hoc doesn't look right.  If you're connecting to a router, it should be mode managed.  Click on the network manager applet, select edit connections, select the entry under wifi for your network, and click edit.  On the wifi tab for that connection, the mode should be set to client and on the IPv4 Settings tab Method should be set to Automatic (DHCP).  If those options are not set that way, change them and then disconnect and reconnect from the network.

---

### Post by Arminius on 2016-08-22
> **Keith_Helms said:**
> Mode Ad-Hoc doesn't look right.  If you're connecting to a router, it should be mode managed.  Click on the network manager applet, select edit connections, select the entry under wifi for your network, and click edit.  On the wifi tab for that connection, the mode should be set to client and on the IPv4 Settings tab Method should be set to Automatic (DHCP).  If those options are not set that way, change them and then disconnect and reconnect from the network.

Tried that, doesn't even connect at all.
Sucks that Ubuntu doesn't display the current WIFI in range.

Anyway settings under WiFi tab are 
SSID: My SSID
Mode: Client
BSSID:
Device: (Only one is available and I've added it to my routers white list.
Cloned MAC address:
MTU: automatic

Wifi security tab
Security: WPA & WPA2 personal
Password: Definitely the right password.

IPv4 Settings tab 
Method: Automatic  (DHCP)
Addresses: Blank
Additional DNS servers:
Additional search domains:
DHCP client ID:
Require IPv4 addressing not ticked.

IPv6 tap
Method: Ignore
Everything else is blank.

---

### Post by jeremy31 on 2016-08-22
Please post results for ```
ls /etc/NetworkManager/system-connections
```

---

### Post by Arminius on 2016-08-22
> **jeremy31 said:**
> Please post results for ```
ls /etc/NetworkManager/system-connections
```

Wi-Fi connection 1     Wi-Fi connection 1-5eea9b52-6F58-48c8-b308-3bede7d05f73

---

### Post by Keith_Helms on 2016-08-23
> **Arminius said:**
> Tried that, doesn't even connect at all.
Sucks that Ubuntu doesn't display the current WIFI in range.


When working properly, Ubuntu DOES display all the current Wifi networks in range.

When you click on the network manager icon, you don't see any networks listed under Wi-Fi Networks?

---

### Post by jeremy31 on 2016-08-23
It is the ad-hoc causing the issue, do ```
sudo iwconfig wlx0015af9cfc82 mode managed
```
And wait 10-30 seconds, then see if ```
iwlist scan
``` shows any wifi access points

---

