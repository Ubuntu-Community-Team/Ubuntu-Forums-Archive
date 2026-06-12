---
title: "nmap wierdness"
date: 2015-01-08
forum: Networking &amp; Wireless
---

### Post by pdcooper on 2015-01-08
i use a bash script to back up a (windows) computer . 
to see if the target is up/down I do 
```
MACHINENAME='Jane-PC'
.....
MACHINE=$(nmap -sL 192.168.1.0/24 | grep $MACHINENAME  | sed 's/[()]/ /g' | awk '{print $6}')
```
....
then i smbmount the stuff to back up 
mount -t cifs //$MACHINE/ToBackup     ....... etc etc 
and it has been working, identifying the target as 192.168.1.65

but recently the output is this 
 nmap -sL 192.168.1.0/24 | grep 'Jane-PC'
Nmap scan report for Jane-PC.home (192.168.1.65)
Nmap scan report for Jane-PC.home (192.168.1.74)

```
ping -c2 192.168.1.65
PING 192.168.1.65 (192.168.1.65) 56(84) bytes of data.
64 bytes from 192.168.1.65: icmp_seq=1 ttl=128 time=15.7 ms
64 bytes from 192.168.1.65: icmp_seq=2 ttl=128 time=4.46 ms


nmap -O -v  192.168.1.74
Starting Nmap 6.40 ( http://nmap.org ) at 2015-01-08 22:16 GMT
Initiating ARP Ping Scan at 22:16
Scanning 192.168.1.74 [1 port]
Completed ARP Ping Scan at 22:16, 0.49s elapsed (1 total hosts)
Nmap scan report for 192.168.1.74 [host down]
Read data files from: /usr/bin/../share/nmap
Note: Host seems down. If it is really up, but blocking our ping probes, try -Pn
Nmap done: 1 IP address (0 hosts up) scanned in 2.50 seconds
           Raw packets sent: 2 (56B) | Rcvd: 0 (0B)

```

the only thing I can think of is when the machine was temporarily connected with a cable ( it isnt at the moment) 

does nmap cache data ? 
if so , how do i clear it ?

---

### Post by bashiergui on 2015-01-08
No nmap does not cache results. Did you try what the results suggested- use -Pn? Do you have a firewall that's blocking pings?

---

### Post by pdcooper on 2015-01-09
no firewall - this is all within my LAN 

this is the output of the network scan 
# nmap -sL 192.168.1.0/24  | grep 'Jane-PC'
Nmap scan report for Jane-PC.home (192.168.1.65)
Nmap scan report for Jane-PC.home (192.168.1.74)
root@acer-AOA110:/usr/local/bin# 


192.168.1.65 is the machine that is up . Ive no idea what 192.168.1.74 is or where nmap is getting it from 

this is the Windows 7 machine I want 
> # nmap -O -v  -sV -Pn 192.168.1.65

Starting Nmap 6.40 ( [http://nmap.org](http://nmap.org) ) at 2015-01-09 20:09 GMT
NSE: Loaded 23 scripts for scanning.
Initiating ARP Ping Scan at 20:09
Scanning 192.168.1.65 [1 port]
Completed ARP Ping Scan at 20:09, 0.27s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 20:09
Completed Parallel DNS resolution of 1 host. at 20:09, 0.02s elapsed
Initiating SYN Stealth Scan at 20:09
Scanning Jane-PC.home (192.168.1.65) [1000 ports]
Discovered open port 135/tcp on 192.168.1.65
Discovered open port 80/tcp on 192.168.1.65
Discovered open port 554/tcp on 192.168.1.65
Discovered open port 443/tcp on 192.168.1.65
Discovered open port 139/tcp on 192.168.1.65
Discovered open port 445/tcp on 192.168.1.65
Discovered open port 5357/tcp on 192.168.1.65
Discovered open port 2869/tcp on 192.168.1.65
Increasing send delay for 192.168.1.65 from 0 to 5 due to 11 out of 27 dropped probes since last increase.
Discovered open port 10243/tcp on 192.168.1.65
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at [http://www.insecure.org/cgi-bin/servicefp-submit.cgi](http://www.insecure.org/cgi-bin/servicefp-submit.cgi) :
SF-Port80-TCP:V=6.40%I=7%D=1/9%Time=54B035AA%P=i686-pc-linux-gnu%r(GetRequ
SF:est,1A,"HTTP/1\.0\x20404\x20Not\x20Found\r\n\r\n")%r(HTTPOptions,53,"\x
SF:13_\xcdY\xf1\x1e\xc4\x85\x1a\x20g\xba\xe7\x0f\x88\x9c\rpm\xb6\xb7\xde\x
SF:bb>\xeb\xe1\x11\xde\xac\xbf\n\xf7\xb5Xt\xae\xec\x07\xde\x03G\xd4P\0\xac
SF:\xfd\x83Fl\xed:\xe38I\xe6\x9f\xc4eR\x1b\x10A~W\x1c\xddjS\xe89\x16\x0ftU
SF:\x82\x8b\xc01\xae\xc7\xcc\xcd\x9a")%r(RTSPRequest,4C,"%\xc6\xba\x05\?9\
SF:xc0\x14\x83H'\xe7\xacc\xdb\]&\xf0\x96\xd7\x168k\x9c\xfe\+\xa1\*\xdcS\x0
SF:4N\xa0R\xc0,\xd1\x96\xd6sSE'\xdb\xd3\n\xbe\xbc&\xdf\x04\xa5\x92\[P\x81\
SF:xbe\x97\\\x1d\xaa\x93\(yVO\xb4\x95\xc2\xcb\0q\xee\x07\x0c\r")%r(FourOhF
SF:ourRequest,1A,"HTTP/1\.0\x20404\x20Not\x20Found\r\n\r\n")%r(RPCCheck,3F
SF:,"x\xf0p\xa6C\xc7Bf\xa1\xf0\xb2\xa2\xf0\xa2KY0%\xd7\xb8\xf1\xe7}\x05\xc
SF:c/\xfc\xc7\x95e\x13m\x1a\xa5\x07\x87\x85\*J\xf9\xd4<v\x1d\xe5\x8c\xa3\x
SF:d1\t\xa6_\x84%\x12\xdb\xd0\x01>\x17\xdc\x9d\*\x13")%r(DNSVersionBindReq
SF:,67,"\x87\xea\xf5\xd9\x9e\.t\xaa\x9a\xf1\xa5\xa3\xf99`\x18\xca\xaa\xb5\
SF:xf4sH\xa3\x92\xc2\x89jyy\xcc\x11\xfc\x06K\xb1\x1f\xe6\t\xbe\x10\xd3\x98
SF:\xbf\xde\|I\xbe\x1b\xe6\x9f\xc4eR\x1b\x10A~W\x1c\xddjS\xe89\x16\x0ftU\x
SF:82\x8b\xc01\xae\xc7\xcc\xcd\x9a\xc3\x98\)F\x7f\$E\xb2\xfbp!\xde7\|\xbd\
SF:xca3H\x19v\xef\xd45\xe2k\x20")%r(DNSStatusRequest,42,"o\xbf\xeb\x10v\xf
SF:9\xe4\x85\xfb\xe9N0<\xef_\?\xdc\xae\xd0\xb0x\x99\xaf\x9d\xc0l\x16\x85\x
SF:b3K\xec\x7f\x9eK\x87\xcc\xf3\xa7\x89\xf4\xfd\x1b\)\x9a{\xf3\x82`\xfe\xd
SF:7\x9c\]\xea\xd3h\xb9\x96\x8f\xf4\xd5\x02\x0b@\xb1\.G")%r(SSLSessionReq,
SF:46,"l\xc9\tH\xc0MRk\xea\xd6\x0b\x97B\x0f-\x83T\xe8\x11\xbd\xf3\(\x0f>\x
SF:b2\xc0\xc4;6AY\x158U\x01s\xaf\x191i\xad\)\xaaF\x0c\xd7\xed\(`QN\xe7l\xe
SF:d:\xe38I\xe6\x9f\xc4e\xf27\xdd\xd0\x17\x1f\x90\x8c")%r(Kerberos,4A,"\xd
SF:9\x05\x9d\t\xfd\xe3C\x001_c\xa8\xe8B\xcd\xd1\x891\xb4\xad\x1e!\x92\|m\x
SF:cc\xe0\x84\x84\x8f\+\xaa\xed\xce\x19\x8a\xbc\xc0df\x9dt\x1e\xad\x99y\xb
SF:3\xc0\(yVO\xb4\x95\xc2\xcb\0q\xee\x07\x0c\r\xda\x03\xd8i\xd2t\xeerBx\)U
SF:")%r(SMBProgNeg,61,"\x97\x18h!eCK\xfa\x8e\xe2\x1cc\x9bR\x06\x0bx\xfc\x2
SF:0:\xbb\x1f\x938\xf3\xf5x/,\xb5\xd9_\x85FM\xd2\xad\r\t\x18\xb5\x9f4%\x20
SF:Cl\xf5\xc8\x99\xf6oT\xb5b\xeb\xa0\x91\x8e'\xac-z#x\x89&\xdf\x04\xa5\x92
SF:\[P\x81\xbe\x97\\\x1d\xaa\x93\(yVO\xb4\x95\xc2\xcb\0q\xee\x07\x0c\r\xda
SF:\x03\xd8");
MAC Address: E0:CA:94:BB:FF:66 (Askey Computer)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: phone|general purpose
Running: Microsoft Windows Phone|Vista|2008|7
OS CPE: cpe:/o:microsoft:windows cpe:/o:microsoft:windows_vista::- cpe:/o:microsoft:windows_vista::sp1 cpe:/o:microsoft:windows_server_2008::sp1 cpe:/o:microsoft:windows_7
OS details: Microsoft Windows Phone 7.5, Microsoft Windows Vista SP0 or SP1, Windows Server 2008 SP1, or Windows 7, Microsoft Windows Vista SP2, Windows 7 SP1, or Windows Server 2008
Uptime guess: 7.960 days (since Thu Jan  1 21:10:11 2015)
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=265 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows



this is the IP address nmap is reporting that isnt attached to anything 

> # nmap -O -v  -sV -Pn 192.168.1.74

Starting Nmap 6.40 ( [http://nmap.org](http://nmap.org) ) at 2015-01-09 20:09 GMT
NSE: Loaded 23 scripts for scanning.
Initiating ARP Ping Scan at 20:09
Scanning 192.168.1.74 [1 port]
Completed ARP Ping Scan at 20:09, 0.49s elapsed (1 total hosts)
Nmap scan report for 192.168.1.74 [host down]
Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (0 hosts up) scanned in 2.72 seconds
           Raw packets sent: 2 (56B) | Rcvd: 0 (0B)

---

### Post by bashiergui on 2015-01-10
> [FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]192.168.1.65 is the machine that is up . Ive no idea what 192.168.1.74 is or where nmap is getting it from[/FONT]they both have the same hostname. You said that the Windows machine was plugged in via ethernet briefly. The .65 address is probably Windows' wireless IP, and the .74 address is Windows' ethernet address.  that would be easy to confirm by running ipconfig on the Windows computer, you'll probably see both interfaces.

---

### Post by pdcooper on 2015-01-21
it isnt connected with the ethernet, just wireless.  And i want nmap *NOT* to find the .74 address 


```
Microsoft Windows [Version 6.1.7601] 
Copyright (c) 2009 Microsoft Corporation.  All rights reserved. 

C:\Users\Jane>ipconfig 

Windows IP Configuration 


Wireless LAN adapter Wireless Network Connection 2: 

   Connection-specific DNS Suffix  . : 
   Link-local IPv6 Address . . . . . : fe80::8c10:e06b:c06:d297%17 
   IPv4 Address. . . . . . . . . . . : 192.168.173.1 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0 
   Default Gateway . . . . . . . . . : 

Ethernet adapter Bluetooth Network Connection: 

   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : 

Wireless LAN adapter Wireless Network Connection: 

   Connection-specific DNS Suffix  . : home 
   Link-local IPv6 Address . . . . . : fe80::49ed:fad2:34fe:a465%12 
   IPv4 Address. . . . . . . . . . . : 192.168.1.65 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0 
   Default Gateway . . . . . . . . . : 192.168.1.254 

Ethernet adapter Local Area Connection: 

   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : home 

Tunnel adapter isatap.home: 

   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : home 

Tunnel adapter isatap.{422D638F-AD2C-4EB9-9E8D-427AC1EAFD2F}: 

   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : 

Tunnel adapter Local Area Connection* 13: 

   Connection-specific DNS Suffix  . : 
   IPv6 Address. . . . . . . . . . . : 2001:0:9d38:6ab8:c56:afd:a971:9720 
   Link-local IPv6 Address . . . . . : fe80::c56:afd:a971:9720%19 
   Default Gateway . . . . . . . . . : :: 

Tunnel adapter isatap.{E5B6DB4D-DC81-44E5-9BC7-996B5B070812}: 

   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : 

C:\Users\Jane> 


```

---

