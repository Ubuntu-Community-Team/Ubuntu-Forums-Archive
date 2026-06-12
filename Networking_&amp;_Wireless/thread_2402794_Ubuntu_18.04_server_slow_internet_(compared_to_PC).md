---
title: "Ubuntu 18.04 server slow internet (compared to PC)"
date: 2018-10-04
forum: Networking &amp; Wireless
---

### Post by livium2000 on 2018-10-04
Hello. I have a DIY NAS at home with the following configuration:
[COLOR=#000000][FONT=Verdana]MB: Asrock H110M-ITX/ac[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]CPU: Intel i5 7600 T[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]SSD 120 GB [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]8 GB RAM
Ubuntu 18.04 server
I use it mostly for PLEX, Transmission, File backup, owncloud
[/FONT][/COLOR]Today I discovered that my internet on the server is slower then my PC running windows.
So I compared the result from server and PC by doing 2 tests: 
1. speedtest-cli
2 [COLOR=#000000][FONT=monaco]wget --output-document=/dev/null [http://speedtest.wdc01.softlayer.com/downloads/test500.zip](http://speedtest.wdc01.softlayer.com/downloads/test500.zip)

[/FONT][/COLOR]1. ```
Retrieving speedtest.net configuration...Testing from RCS & RDS (5.13.51.149)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by RCS&RDS (Iasi) [84.03 km]: 5.034 ms
Testing download speed................................................................................
Download: 566.66 Mbit/s
Testing upload speed................................................................................................
Upload: 86.98 Mbit/s

```
 On my PC (win 10) :
[COLOR=#000000][FONT=Verdana]Download 743 Mb/s, Upload 318 Mb/s

[/FONT][/COLOR]2.
Linux 
```
[COLOR=#000000][FONT=monaco]/dev/null           100%[===================>] 500.00M  1.47MB/s    in 5m 52s[/FONT][/COLOR]
```
Windows 15 MB/S

The server and the PC are both connected to my TPlink Archer C7 router using ethernet cable.
The server has intergrated network adapter ( gigabyte intel)
What could be the problem? Thanx

---

### Post by livium2000 on 2018-10-05
Today I found out that I have lost packages in my NIC.
```
ifconfig  enp0s31f6 | grep errors
RX errors 0  dropped 4809  overruns 0  frame 0
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

15 seconds later


```
ifconfig  enp0s31f6 | grep errors
        RX errors 0  dropped 4825  overruns 0  frame 0
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0] 
```

16 packages lost in 15 seconds. Why is that? Wrong driver maybe?

---

