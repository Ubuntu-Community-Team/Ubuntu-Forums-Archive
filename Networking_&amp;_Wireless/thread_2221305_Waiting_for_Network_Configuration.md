---
title: "Waiting for Network Configuration"
date: 2014-05-01
forum: Networking &amp; Wireless
---

### Post by Daniel_Aurelio_Gal on 2014-05-01
Hi, I'm Daniel, an ex Debian user, switching to Ubuntu attracted by 5 years LTS support. I'm going to get "Waiting for Network Configuration" problem every time I'll try to boot with this NIC configurations:
```
 [I]
  $ cat /etc/network/interfaces[/I]
  *auto lo*
  *iface lo inet loopback*
  

  *auto wlan0*
  *iface wlan0 inet dhcp*
  *wpa-ssid "D-Link DSL-2750B"*
  *wpa-psk coolpassword*

```  

  After boot I do:
 ```
 [I]
  $ sudo ifdown wlan0[/I]
  *$ sudo ifup wlan0*

```  

  and my connection start.
  
  I want to know why network configuration doesn't work at boot. My configuration is:
  
[LIST]
[*]Ubuntu 14.04 Minimal 
[*]postgresql 
[*]samba (yet not configurated) 
[/LIST]
 
  Thanks a lot.

---

### Post by TheFu on 2014-05-01
I've never needed to add anything to the interfaces for DHCP wifi connections.  NetworkManager should handle that completely.

---

### Post by Daniel_Aurelio_Gal on 2014-05-01
> **TheFu said:**
> I've never needed to add anything to the interfaces for DHCP wifi connections.  NetworkManager should handle that completely.
Going without Gnome, is a Ubuntu Minimal install with simply window manager (dwm).

---

### Post by Daniel_Aurelio_Gal on 2014-05-11
I didn't find a really solution of the specific issue but I changed my configuration, maybe can be useful for someone later.
```

gale@acer:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface home inet dhcp
    wpa-ssid "D-Link DSL-2750B"
    wpa-psk *******
iface work inet dhcp
    wpa-ssid tlr-guest
    wpa-psk *******

```

I maked a simple python script:
```

gale@acer:~$ sudo touch /usr/local/bin/connect.py
gale@acer:~$ sudo chmod +x /usr/local/bin/connect.py
gale@acer:~$ sudo vi /usr/local/bin/connect.py 
#!/usr/bin/python
import subprocess
import os

essid_home = "D-Link DSL-2750B"
essid_work = "tlr-guest"

os.system("ifdown wlan0")
os.system("ifconfig wlan0 up")
output = subprocess.check_output("iwlist", "scan")
if essid_home in output:
        os.system("ifup wlan0=home")
elif essid_work in output:
        os.system("ifup wlan0=work")

```

Now I can start my connect script.
```

gale@acer:~$ sudo connect.py 
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/ec:55:f9:34:04:c2
Sending on   LPF/wlan0/ec:55:f9:34:04:c2
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67 (xid=0x580cda00)
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/ec:55:f9:34:04:c2
Sending on   LPF/wlan0/ec:55:f9:34:04:c2
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x73ae359a)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 (xid=0x73ae359a)
DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67 (xid=0x73ae359a)
DHCPOFFER of 192.168.1.5 from 192.168.1.1
DHCPACK of 192.168.1.5 from 192.168.1.1
bound to 192.168.1.5 -- renewal in 38057 seconds.

```

You can also add sudoers exception for no password sudo requirement:
```

gale@acer:~$ sudo visudo
[COLOR=#ff0000]...[/COLOR]
[COLOR=#ff0000]...
[COLOR=#ff0000]...[/COLOR][/COLOR]
gale ALL= NOPASSWD: /usr/local/bin/connect.py

```
and put that into ~/.xsession script:
```

gale@acer:~$ cat .xsession
exec sudo connect.py &
exec dwm

```

Of course python is required

---

