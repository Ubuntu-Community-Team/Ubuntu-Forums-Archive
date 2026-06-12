---
title: "Dhclient not working"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by Dracorius on 2006-12-18
hey everybody.
I'm relatively new to Linux. I had tried it before but i never got my wireless connection to work decently. Nevertheless i thought I'd give it another go. I'm running Ubuntu 6.10 amd64 on a intel core 2 duo 6600, 1024mB ram and a dwl-g122 wireless usb stick (rt2500 chipset)

By scouting many forums and tutorials, i put together the following connection script:

```
sudo iwpriv rausb0 enc 3
sudo sleep 1
sudo iwpriv rausb0 auth 3
sudo iwconfig rausb0 mode managed
sudo iwconfig rausb0 essid DeGreef
sudo iwpriv rausb0 wpapsk mypasskey
sudo iwconfig rausb0 essid DeGreef
sudo sleep 1
sudo ifconfig rausb0 up
sudo ifconfig rausb0 192.168.0.101 
sleep 10
sudo iwpriv rausb0 enc 3
sleep 1
sudo iwpriv rausb0 auth 3
sudo iwconfig rausb0 essid DeGreef
sudo dhclient rausb0

```

this seems to work (since I'm posting this from Ubuntu). However, dhclient only assigns an ip because i once recieved one after a couple of tries without the encryption. Now it's just checking that key to see if its still good.
Here is some of the output:

```
dracorius@dracorius-desktop:~$ sudo dhclient rausb0
Password:
There is already a pid file /var/run/dhclient.pid with pid 4815
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/rausb0/00:11:95:cf:ff:0b
Sending on   LPF/rausb0/00:11:95:cf:ff:0b
Sending on   Socket/fallback
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
Trying recorded lease 192.168.0.101
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 13.901/13.901/13.901/0.000 ms
bound: renewal in 231987 seconds.
dracorius@dracorius-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:"DeGreef"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:13:46:17:41:26   
          Bit Rate=48 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/70  Signal level:-64 dBm  Noise level:-208 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

dracorius@dracorius-desktop:~$ sudo iwlist rausb0 scan
rausb0    Scan completed :
          Cell 01 - Address: 00:13:46:17:41:26
                    Mode:Managed
                    ESSID:"DeGreef"
                    Encryption key:on
                    Channel:11

dracorius@dracorius-desktop:~$ 
```

There are some wierd things in there, like "Link Quality=0/70", and "Encryption key: off"
The latter i assume is normal because i didn't set a key in iwconfig, but in iwpriv. The first is rather strange though.

Has anyone got some advice as to what i'm doing worng, of why the dhcient cant obtain an ip?

Greetz :-D 
Arnout

PS: i just noticed this in the log of my router (don't mind the time/date, i didn't configure it...):
this is a successfull dhcp request from winXp:
Nov/02/2006 03:11:31 	DHCP lease IP 192.168.0.101 to pcarnout			00-11-95-cf-ff-0b
Nov/02/2006 03:11:30 	Authentication success			00-11-95-cf-ff-0b
Nov/02/2006 03:11:29 	Wireless PC connected			00-11-95-cf-ff-0b

this is a dhcp request from Ubuntu:
Nov/02/2006 02:34:19 	DHCP Request			87.244.188.59

why does is that last thing a weird ip i've never seen instaid of my mac adress?

---

### Post by MyTer on 2006-12-25
I have had similar problems, but I found this link

[https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_%28Rev_B%29](https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_%28Rev_B%29)

Happy Ubuntu(ing)

---

### Post by Floppyjoe on 2006-12-25
Doesn't this line in your script give you a static ip?  :
> sudo ifconfig rausb0 192.168.0.101

---

