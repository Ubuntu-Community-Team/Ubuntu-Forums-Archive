---
title: "Ubuntu 8.10, ICS, and Xbox 360 conn woes ..."
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by xen-uno on 2008-11-16
Trying to get ICS (Internet Connection Sharing aka masquerade) working for Xbox Live (and any other comp hooked to the switch). DHCP-server is installed.

Wired topology is eth1 > internet (cable modem), eth0 > SMC switch (local lan) > Xbox.

I have consulted ...
[http://ubuntuforums.org/showthread.php?p=6060607#post6060607](http://ubuntuforums.org/showthread.php?p=6060607#post6060607) (primarily)
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

... and fixed the 8.10 NM (aka Network Configuration) bug via
[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)
... used the 2nd dialog based HowTo. Disabled auto eth0 and created new ("eth0 corrected") with IP: 192.168.0.1, Netmask: 255.255.255.0, Gateway: 192.168.0.0, and DNS: 192.168.0.0.

**ifconfig** returns:
```
jan@PlanetX:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:02:56:41  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe02:5641/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82348 (82.3 KB)  TX bytes:5244 (5.2 KB)
          Memory:e3300000-e3320000 

eth1      Link encap:Ethernet  HWaddr 00:50:ba:10:5f:70  
          inet addr:12.202.5.100  Bcast:12.202.7.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:33429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3507852 (3.5 MB)  TX bytes:379964 (379.9 KB)
          Interrupt:22 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13320 (13.3 KB)  TX bytes:13320 (13.3 KB)
```

**sudo sysctl net.ipv4.ip_forward** returns 1 as it should

Edited **dhcpd.conf**:
```
ddns-update-style none;

   # option definitions common to all supported networks...
option domain-name "PlanetX";
   #option domain-name "example.org";
option domain-name-servers 12.207.234.29, 12.207.235.32;
   #option domain-name-servers ns1.example.org, ns2.example.org;

   #added by SAJ
option routers 192.168.0.1;

default-lease-time 42300;
max-lease-time 84600;
   #default-lease-time 600;
   #max-lease-time 7200;

   # If this DHCP server is the official DHCP server for the local
   # network, the authoritative directive should be uncommented.
authoritative;
   #authoritative;

   # Use this to send dhcp log messages to a different log file (you also
   # have to hack syslog.conf to complete the redirection).
log-facility local7;

#added by SAJ
subnet 192.168.0.0 netmask 255.255.255.0 { 
   range 192.168.0.100 192.168.0.200;
}
```

Added following lines to **/etc/rc.local**
```
#added by SAJ
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth1 -j MASQUERADE

exit 0
```


**sudo gedit /etc/default/dhcp3-server** contents:

```
INTERFACES="eth0"
   #INTERFACES=""
```

^^^ I wonder if this should say INTERFACES="eth0 corrected" since I disabled the default and created new via Network Manager?

-   -   -   -   -   -   -   -   -   -

ICS works great when desktop is running XP x64. Xbox returns these values:
IP: 192.168.0.207
Subnet: 255.255.255.0
Gateway: 192.168.0.1
DNS Pri: 192.168.0.1
DNS Sec: 0.0.0.0

XP returns the following:
```
C:\Documents and Settings\jan>ipconfig /all

Windows IP Configuration
Host Name . . . . . . . . . . . . : Planet64x
Primary Dns Suffix  . . . . . . . :
Node Type . . . . . . . . . . . . : Unknown
IP Routing Enabled. . . . . . . . : Yes
WINS Proxy Enabled. . . . . . . . : No


Ethernet adapter NIC to Internet: (known as eth1 to Ubuntu)

Connection-specific DNS Suffix  . :
Description . . . . . . . . . . . : D-Link DFE-538TX 10/100 Adapter
Physical Address. . . . . . . . . : 00-50-BA-10-5F-70
DHCP Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IP Address. . . . . . . . . . . . : 12.208.168.236
Subnet Mask . . . . . . . . . . . : 255.255.248.0
Default Gateway . . . . . . . . . : 12.208.168.1
DHCP Server . . . . . . . . . . . : 12.207.234.13
DNS Servers . . . . . . . . . . . : 12.207.234.29
                                    12.207.235.32
Lease Obtained. . . . . . . . . . : Saturday, November 15, 2008 11:37:35 AM
Lease Expires . . . . . . . . . . : Monday, November 17, 2008 7:58:47 PM


Ethernet adapter NIC to Switch: (known as eth0 to Ubuntu)

Connection-specific DNS Suffix  . :
Description . . . . . . . . . . . : Intel(R) 82566DC-2 Gigabit Network
Connection
Physical Address. . . . . . . . . : 00-1C-C0-02-56-41
DHCP Enabled. . . . . . . . . . . : No
IP Address. . . . . . . . . . . . : 192.168.0.1
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . :
```

Any ideas?

---

### Post by xen-uno on 2008-11-19
[img]http://home.mchsi.com/~xen-uno/Bump100x100.gif[/img]

---

### Post by superprash2003 on 2008-11-19
nice bump pic :) .. Well you could try using firestarter( sudo apt-get install firestarter) , it has an ICS feature.. easy to setup with DHCP server..

---

### Post by xen-uno on 2008-11-20
Ja ... gotta love those road signs. I've heard FireStarter mentioned before. I don't need a firewall (disableable I hope) but I do need the ICS. I'll give it a shot (I'll try putting in "eth0 corrected first in dhcp3-server first, cuz as far as I can tell, everything else is right).

Thanks!

---

### Post by xen-uno on 2008-11-26
OK ... FireStarter did the trick as far as ICS is concerned but is blocking ports when using DC++. I really don't want a firewall in the first place. If FS configured the normal Ubuntu network files related to ICS, then it should be safe to remove without loosing ICS connectivity. Anyone know for certain? I'd like to skip a round robin of installs/uninstalls.

---

