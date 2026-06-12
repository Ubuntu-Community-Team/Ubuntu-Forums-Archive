---
title: "sudo iwconfig essid &quot;*******&quot; returns iwconfig: unknown command &quot;*******&quot;"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by oh_hi95 on 2008-02-25
I'm trying to configure my Netgear wg111v3 to work in Ubuntu 7.10; I installed the driver with ndiswrapper successfully and am following kevdog's how to on manual network configuration.  However, when I input the line:

****@****-desktop:~$ sudo iwconfig essid "*******"

the computer returns with the line:

iwconfig: unknown command "*******"

any suggestions? any insight is appreciated

---

### Post by oh_hi95 on 2008-02-25
here's some more info about the wlan0 connection...

****@****-desktop:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"*******"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:FA:7D:E4   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by oh_hi95 on 2008-02-25
here's the command that I tried next, after looking at the help document for iwconfig

****@****-desktop:~$ sudo iwconfig interface essid "*******"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device interface ; No such device.

once again, all help is appreciated

---

### Post by mrsteveman1 on 2008-02-25
have to specify an interface by name

```
sudo iwconfig wlan0 essid blahblahblah
```

---

### Post by spd106 on 2008-02-25
You had it right in the previous post.

```
sudo iwconfig wlan0 essid *******
```

In your case <interface> = wlan0

---

### Post by oh_hi95 on 2008-02-25
wow, thanks, I didn't even think about that, must have gotten lost somewhere

alright, I've followed the "how to" to its conclusion but the device still won't connect

any ideas?

---

### Post by oh_hi95 on 2008-02-25
here's what the computer says when I input 

****@****-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1b:2f:d0:30:29
Sending on   LPF/wlan0/00:1b:2f:d0:30:29
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
SIOCSIFMTU: Invalid argument
bound to 192.168.0.14 -- renewal in 98179 seconds.

I hope that is of some help

---

### Post by oh_hi95 on 2008-02-25
I've got it working now. 

Thanks everybody.

---

### Post by stooshbunutu on 2008-04-10
> **oh_hi95 said:**
> I've got it working now. 

Thanks everybody.

You can mark your thread as solved via the thread options menu at the top

---

