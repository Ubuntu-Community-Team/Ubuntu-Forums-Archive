---
title: "Help with /etc/network/interfaces"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by dierre on 2006-12-09
Hello!

I have just managed to have my usb wi-fi adapter! Yey!
I only need a little help to make it perfect...

I need to type the following commands to set up the network:

```

ifconfig rausb0 up
/sbin/iwpriv rausb0 set NetworkType=Infra
/sbin/iwpriv rausb0 set AuthMode=WPA2PSK
/sbin/iwpriv rausb0 set EncrypType=AES
/sbin/iwpriv rausb0 set SSID=homenet
/sbin/iwpriv rausb0 set WPAPSK=mysecret
dhclient rausb0
```

So I added a section to my /etc/network/interfaces like this:
```

iface rausb0 inet dhcp
post-up /sbin/iwpriv rausb0 set NetworkType=Infra
post-up /sbin/iwpriv rausb0 set AuthMode=WPA2PSK
post-up /sbin/iwpriv rausb0 set EncrypType=AES
post-up /sbin/iwpriv rausb0 set SSID=homenet
post-up /sbin/iwpriv rausb0 set WPAPSK=mysecret
```


but it doesn't seem to work (using ifup rausb0, of course)... what is wrong? Thank you!

---

### Post by TheGreatFuzzMan on 2006-12-09
This is my working configuration: 

auto ra0
iface ra0 inet dhcp
        wireless-essid myessid
        wireless-key myasciikey
        pre-up ifconfig ra0 up
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwconfig ra0 essid myessid
        pre-up iwpriv ra0 set WPAPSK="myasciikey"

I noticed your AuthMode=WPA2PSK. Is that on purpose? I use AutoMode=WPAPSK. There may be compatibility/support issues with WPA2?

Also, I typed all those commands in the terminal manually the very first time I connected. Goto terminal and type 'ifconfig rausb0 down'. Then, type those commands without the "pre-up". Then type 'ifconfig rausb0 up'. This step will insure the prior/incorrect settings from tools or the Networks control panel are cleared.

Just for completeness, I do not use network_manager or wpa_supplicant in my configuration. I only put a file 'wpasupplicant' in the '/etc/default/' directory. Type 'ENABLE=0' in that file, without the quotations.

---

### Post by dierre on 2006-12-09
Yes, WPA2PSK is on purpose, ad I decided to set up my network with WPA2 and AES. No, I don't use wpa_supplicant, either.

Inspired by your interfaces I decided to convert post-up's in pre-up's :-)
```

iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
pre-up /sbin/iwpriv rausb0 set NetworkType=Infra
pre-up /sbin/iwpriv rausb0 set AuthMode=WPA2PSK
pre-up /sbin/iwpriv rausb0 set EncrypType=AES
pre-up /sbin/iwpriv rausb0 set SSID=homenet
pre-up /sbin/iwpriv rausb0 set WPAPSK=unafrasesegretissima
pre-up ifconfig rausb0 up
```

This did NOT work. :-(

The funny thing is that if I launch the following script manually, then everything works perfectly:

```
ifconfig rausb0 up
/sbin/iwpriv rausb0 set NetworkType=Infra
/sbin/iwpriv rausb0 set AuthMode=WPA2PSK
/sbin/iwpriv rausb0 set EncrypType=AES
/sbin/iwpriv rausb0 set SSID=homenet
/sbin/iwpriv rausb0 set WPAPSK=unafrasesegretissima
ifconfig rausb0 up
dhclient rausb0
```

---

### Post by TheGreatFuzzMan on 2006-12-09
Do you have 'auto rausb0' at the top of that section? I don't think it would matter in your case, but it is definitely odd that only the script works. Obviously, your settings in the interface file are not being processed... ](*,)

---

### Post by dierre on 2006-12-09
No, I left out the auto rausb0 for now in order to troubleshoot... I was activating the interface manually with ifup rausb0

And another funny thing is that the settings *are* being processed... i tried adding some lines like "pre-up echo I'm doing this and that" and they do get displayed. :-/

---

### Post by TheGreatFuzzMan on 2006-12-10
You mentioned you don't use wpa_supplicant. Did you created the /etc/default/wpasupplicant file i mentioned? That may be a required step in our cases. Put 'ENABLE=0' in the file, without the quotations.

---

### Post by dierre on 2006-12-10
Yes, I tried to create /etc/default/wpasupplicant as you suggested (ENABLE=0) but the issue seems independent of whether that file exists or not.

I discovered another funny thing: my script works or not depending on how I launch it!  "./wifi.sh" --> NOT working  but  ". wifi.sh" --> WORKS!

```
root@bart:~# ifconfig rausb0 down

root@bart:~# 
root@bart:~# . wifi.sh 
There is already a pid file /var/run/dhclient.pid with pid 5889
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/rausb0/00:18:f8:2c:2e:c6
Sending on   LPF/rausb0/00:18:f8:2c:2e:c6
Sending on   Socket/fallback
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.100 -- renewal in 41726 seconds.
root@bart:~# 

root@bart:~# 
root@bart:~# 
root@bart:~# ifconfig rausb0 down


root@bart:~# 
root@bart:~# 
root@bart:~# ./wifi.sh 
There is already a pid file /var/run/dhclient.pid with pid 7026
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/rausb0/00:18:f8:2c:2e:c6
Sending on   LPF/rausb0/00:18:f8:2c:2e:c6
Sending on   Socket/fallback
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 13

[interrupted]

root@bart:~# 
root@bart:~# ifconfig rausb0 down

root@bart:~# 
root@bart:~# . wifi.sh 
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/rausb0/00:18:f8:2c:2e:c6
Sending on   LPF/rausb0/00:18:f8:2c:2e:c6
Sending on   Socket/fallback
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.100 -- renewal in 35554 seconds.
root@bart:~#
```


And here is the script:
```
root@bart:~# cat wifi.sh 
#!/bin/bash
ifconfig rausb0 up
/sbin/iwpriv rausb0 set NetworkType=Infra
/sbin/iwpriv rausb0 set AuthMode=WPA2PSK
/sbin/iwpriv rausb0 set EncrypType=AES
/sbin/iwpriv rausb0 set SSID=homenet
/sbin/iwpriv rausb0 set WPAPSK=unafrasesegretissima
ifconfig rausb0 up
dhclient rausb0
root@bart:~# 

```

I really don't understand what is going on.... :-(

---

### Post by FrodoB on 2006-12-10
It looks to me like this post addresses the issues:

[http://ubuntuforums.org/showthread.php?t=202834&highlight=WPA-PSK+Wieman01](http://ubuntuforums.org/showthread.php?t=202834&highlight=WPA-PSK+Wieman01)

---

### Post by dierre on 2006-12-10
Hmmm... I don't know how much that post addresses my issue... I'm using ralink's drivers, not ndiswrapper. I managed to have the wifi running, I simply can't configure /etc/network/interfaces so that ifup/ifdown do the work...
Thank you for pointing me at that thread, though.

---

### Post by dierre on 2006-12-10
Ok, so I managed to solve it. I noticed that adding some sleep the script worked smoothly...

Here is the relevant section from my /etc/netowrk/interfaces:

```

auto rausb0
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
pre-up sleep .1
pre-up /sbin/iwpriv rausb0 set NetworkType=Infra
pre-up sleep .1
pre-up /sbin/iwpriv rausb0 set AuthMode=WPA2PSK
pre-up sleep .1
pre-up /sbin/iwpriv rausb0 set EncrypType=AES
pre-up sleep .1
pre-up /sbin/iwpriv rausb0 set SSID=homenet
pre-up sleep .1
pre-up /sbin/iwpriv rausb0 set WPAPSK=unafrasesegretissima
pre-up sleep .1
```

With this configuration works perfectly, even hibernate is supported :-)

Is this necessity for sleep a bug or a feature? :-)  I was thinking of filing a bug report, but against which package could I do that?

Thank you for your help!

---

