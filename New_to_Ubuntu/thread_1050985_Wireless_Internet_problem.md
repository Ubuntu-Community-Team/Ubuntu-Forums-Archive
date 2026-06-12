---
title: "Wireless Internet problem"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Raghu1990 on 2009-01-26
Hello, everyone, this is my first post here.
I have a PC with Ubuntu 7.10 (aka gutsy gibbon) loaded on it along with Windows XP. I'm having problems with my wireless adapter (DWA-100) which is plugged into an USB port. I searched the forums here extensively but I'm still stuck with this problem:

Problem: My adapter is recognized, but i am unable to connect to the internet.

```


vamsi@vamsi-desktop:~$ iwconfig
lo        no wireless extensions.



eth0      no wireless extensions.


wlan0     RT73 WLAN  ESSID:"" 
 
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s 
 
          RTS thr:off   Fragment thr:off

          Link Quality=75/100  Signal level:-60 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




```

also, 

```
vamsi@vamsi-desktop:~$  sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                          Internet Systems Consortium
 DHCP Client V3.0.5

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:21:91:86:9c:7b

Sending on   LPF/wlan0/00:21:91:86:9c:7b

Sending on   Socket/fallback

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12

No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

any help would be appreciated as i've been struggling with this for about a week already

---

### Post by Izek on 2009-01-26
Have you tried installing WICD instead?

[http://ubuntuforums.org/showthread.php?t=527488](http://ubuntuforums.org/showthread.php?t=527488)

---

### Post by Raghu1990 on 2009-01-26
the starter of that thread specifically mentions that my wireless must be working to continue installing WICD. This is a problem because my wireless is NOT working.

---

### Post by Izek on 2009-01-26
>> Delete Post <<

---

### Post by Raghu1990 on 2009-01-26
umm.. some help please??

---

