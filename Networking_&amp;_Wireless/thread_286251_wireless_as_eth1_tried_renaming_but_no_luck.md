---
title: "wireless as eth1? tried renaming but no luck"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by Pathfinder_ on 2006-10-27
hi, i just did a fresh install of edgy and the first thing I noticed that my wireless doesn't work. i didn't try ndiswrapper because it worked under dapper before. I searched the forum and found that by renaming the interface to wlan0 it might work but unfortunately it didn't. 

```
andrew@andrew-desktop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:0e:11:af:b5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11g zd1211
```
lokking at this i think it recognizes the usb adapter as wired not wireless.

here's the output when i restart the network
```
Listening on LPF/wlan0/00:12:0e:11:af:b5
Sending on   LPF/wlan0/00:12:0e:11:af:b5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

and here's what iwconfig says
```
andrew@andrew-desktop:~$ sudo iwconfig
lo        no wireless extensions.

wlan0     802.11g zd1211  ESSID:"linksys"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Encryption key:off
          Link Quality=85/100  Signal level=83/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions
```

btw, i disabled ethernet in BIOS so thats why in the above output itdoesn't show eth0. 

Is there anyway to fix this?

---

### Post by Pathfinder_ on 2006-10-27
well i renamed it back to eth1 and after a reboot for some strange reason it sees the different networks around me. however i'm still unable to connect.

EDIT
well i managed to install network-manager. the problem is that 1) it does not connect on start up. 2) it connects after a few tries not on the fist.

EDIT 2
Fixed it. what i did is remove the old driver and install a newer one.

---

