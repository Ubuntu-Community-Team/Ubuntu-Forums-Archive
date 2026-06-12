---
title: "Wireless card configured but won't connect"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by maspiotis on 2007-02-18
I have a D-link dwl 650 wireless card, which Edgy seems to have recognized and it is configured.  From the terminal I can get a list of nearby signals and it shows the modem working.  But when I go to firefox I can't get any websites to come up.  Any help would be greatly appreciated.

Thanks
Michael Aspiotis

---

### Post by maspiotis on 2007-02-18
This is what the puter is telling me about my connection: it really does not mean too much to me:

maspiotis@maspiotis-laptop:~$ sudo ifup wlan0
Password:
ifup: interface wlan0 already configured
maspiotis@maspiotis-laptop:~$ ip link
1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 08:00:46:48:15:5b brd ff:ff:ff:ff:ff:ff
3: sit0: <NOARP> mtu 1480 qdisc noop 
    link/sit 0.0.0.0 brd 0.0.0.0
4: wlan0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:0d:88:65:3a:ce brd ff:ff:ff:ff:ff:ff
maspiotis@maspiotis-laptop:~$ ip neigh
192.168.1.1 dev eth0 lladdr 00:18:39:df:e9:43 REACHABLE
maspiotis@maspiotis-laptop:~$

---

### Post by Reedbeta on 2007-02-18
maspiotis,

Try doing 'sudo ifdown wlan0' followed by 'sudo ifup wlan0', i.e. disable and re-enable the interface.  If that doesn't help, do a 'netstat -nr' and post the results here - the routing table might be set up incorrectly.

---

### Post by maspiotis on 2007-02-19
Thanks for your help
Okay here is what I got:

maspiotis@maspiotis-laptop:~$ sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0d:88:65:3a:ce
Sending on   LPF/wlan0/00:0d:88:65:3a:ce
Sending on   Socket/fallback
maspiotis@maspiotis-laptop:~$ sudo ifup wlan0
ifup: interface wlan0 already configured
maspiotis@maspiotis-laptop:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
maspiotis@maspiotis-laptop:~$

---

### Post by gradedcheese on 2007-02-19
Sounds like no one answered the DHCP request.  Does scanning work?  Can you associate?

scanning:
```

sudo iwlist wlan0 scan

```

any results?

to associate:
```

sudo iwconfig wlan0 essid put_desired_SSID_here

```

if that worked, now ask for an IP address:

```

sudo killall dhclient
sudo dhclient wlan0

```

did it say something about being bound to some IP address?  If so, now try the internet...

---

### Post by maspiotis on 2007-02-20
Here is what I get:


maspiotis@maspiotis-laptop:~$ sudo iwconfig wlan0 essid linksys_SES_51978
Password:
maspiotis@maspiotis-laptop:~$ sudo killall dhclient
dhclient: no process killed
maspiotis@maspiotis-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0d:88:65:3a:ce
Sending on   LPF/wlan0/00:0d:88:65:3a:ce
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
maspiotis@maspiotis-laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:03:93:EE:C5:48
                    ESSID:"RMG EXTREME"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:175  Signal level:0  Noise level:50
                    Extra: Last beacon: 582ms ago
          Cell 02 - Address: 00:18:39:DF:E9:45
                    ESSID:"linksys_SES_51978"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:140  Signal level:0  Noise level:30
                    Extra: Last beacon: 276ms ago
          Cell 03 - Address: 00:12:17:2B:C0:4C
                    ESSID:"alexatony"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:141  Signal level:0  Noise level:30
                    Extra: Last beacon: 426ms ago
          Cell 04 - Address: 00:13:10:D0:59:3C
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:153  Signal level:0  Noise level:55
                    Extra: Last beacon: 171ms ago
          Cell 05 - Address: 00:11:50:31:A0:F1
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:144  Signal level:0  Noise level:32
                    Extra: Last beacon: 191ms ago

maspiotis@maspiotis-laptop:~$

---

### Post by Tichondrius on 2007-02-20
Don't you have WEP security in your WLAN ?

If so, you need to enter the key to be able to connect:

sudo iwconfig wlan0 key open 123456789A
sudo iwconfig wlan0 essid MyWifi

To check if you are connected, type 

iwconfig wlan0

and it should say you are associated with thhe access point.
If that didnt work, try again but use "restricted" instead of "open" in the first command above.

---

### Post by maspiotis on 2007-02-20
maspiotis@maspiotis-laptop:~$ iwconfig wlan0
wlan0     802.11b linked  ESSID:"linksys_SES_51978"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:DF:E9:45   
          Bit Rate=11 Mb/s   Sensitivity=80/85  
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:97/100  Signal level:-38 dBm  Noise level:-253 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It seems to me from this output that my wireless card is working and it is associated with my essid, but when I disconnect my ethernet cable and try to pull up a website I get nothing.

---

### Post by gradedcheese on 2007-02-20
Associating is the first step.  Now you need an IP address.  As a test, try:

sudo ifconfig wlan0 up
sudo dhclient wlan0

(that assumes you want to use DHCP, which is probably want you want).  This was all in my original post, above.

---

### Post by maspiotis on 2007-02-20
First, thanks for taking the time to help out.  Second here is the out put:


maspiotis@maspiotis-laptop:~$ sudo ifconfig wlan0 up
Password:
maspiotis@maspiotis-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 25519
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0d:88:65:3a:ce
Sending on   LPF/wlan0/00:0d:88:65:3a:ce
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
maspiotis@maspiotis-laptop:~$

---

### Post by gradedcheese on 2007-02-20
Ok.  This means that you did associate to your WiFi access point, but it's not handing out an IP address to you.  Just to be sure: this is the same access point that works normally for other PCs?  It does have DHCP turned on and that's what the other PCs use?

---

### Post by almax00 on 2007-02-20
is MAC address filtering acitve on the router ? use the wired connection to open the web admin page for the router and turn MAC filtering off. the wireless may be associating with the router but being blocked because the MAC is not known to the router. you should be able to manually enter the MAC for your wireless card via the admin page. you should turn MAC filtering back on once you can connect wireless as it is a security measure to block unknown MACs. 

if you already know this - please forgive the post.

---

### Post by Tichondrius on 2007-02-20
I agree with previous posters that it looks like your wireless link to the access point is active. But you don't get a response to DHCP request either because your wireless router doesn't have DHCP server turned on, or maybe because you have MAC filtering turned on and didnt add the MAC of your wireless card to the list.

It's usually a good idea to use DHCP, but if you prefer not to use it, you can set the address statically in the networking properties dialog box.

---

