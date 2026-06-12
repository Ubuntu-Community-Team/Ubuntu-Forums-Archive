---
title: "Ubuntu 7.10 2 nic 2 routers"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by sonicsqwirl on 2008-04-10
First i apologize, I'm pretty new to both Networking and Linux.  So, i'll try to be as detailed in my description of my problem as possible,

Second, I thank whoever is willing to help in advance!

My setup looks like this...  I have a cable modem hooked up to the WAN port on the first router (linksys wrt54gs wireless).  This router is default setup (DHCP Enabled etc...).  I have my first nic (eth0) hooked up to the 4th LAN port and set with a static IP address.  I get internet and etc just fine.  I read a post on setting up LTSP for 2 nics and did that setup for the second nic (eth1).  I purchased another wireless router (linksys wrt54g) to use as the "switch" because i want to eventually use the ThinClients over the wireless, but for now i'm cabling into it.  I can't for the life of me get the second router to play nice with the eth1 nic.  I am using a crossover cable, from eth1 to WAN on the second router, doesn't work... tried crossover to the 4th LAN spot... still doesn't work.  I've verified that m dhcp3 server is running.  I'll post my nics and DHCP configuration...

ifconfig...
```

eth0      Link encap:Ethernet  HWaddr 00:1D:60:54:B3:64  
          inet addr:192.168.1.199  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5669106 (5.4 MB)  TX bytes:719218 (702.3 KB)
          Interrupt:20 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:1D:60:54:C4:9F  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11047 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:850739 (830.7 KB)  TX bytes:1041402 (1016.9 KB)
          Interrupt:23 Base address:0x4000 
```

dhcpd.conf
```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.2.0 netmask 255.255.255.0 {
    range 192.168.2.20 192.168.2.250;
    option domain-name "*";
    option domain-name-servers 192.168.2.1;
    option broadcast-address 192.168.2.255;
    option routers 192.168.2.1;
#    next-server 192.168.2.254;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
```

---

### Post by SpaceTeddy on 2008-04-10
have you enabled to dhcp-server to listen on eth1 ? is has to be specified in /etc/default/dhcp3-server. Have you disabled the DHCP-server on the second router device ? with two DHCP-server on one network you can get very strange results... 

also, you should use a normal patch cable and NOT use the WAN port of the WRTGS. Use one of the LAN ports instead. 

Also, what does your syslog say /var/log/syslog when you start/stop the dhcp-server and when your clients are trying to pull leases from it...

or am i misunderstanding your problem ? if so, i am sorry... :)

---

