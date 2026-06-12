---
title: "Complicated and unsure what to do"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by thrownintothis on 2007-12-27
I got thrown into this and have no idea what to do. I just inherited providing internet access to an apartment building full of college students. In the apartment building, there are 8 floors. Only floors 2 through 8 have internet access, 1st floor only the managers office has internet access and it gets a static IP.



Floors 2 through 8, every apartment has a wired LAN connection, and there are 3 wireless AP’s on each floor (Mikrotik 2.4GHz) 

The server is on the 5th floor, there are switches located on every floor, north end of the building and south end.

Each AP has a static IP on it presently, basically for remote monitoring and remote access. Each AP has DHCP running on it as well and have 192.168.x.x IP’s on them. The server (running ubuntu) has dhcp3 running on it with 1 full class c block setup on it. IP tables are also running on the server and things are setup that you can only sh into the server from specified IP’s or you have to be sitting at the server itself. Each tenant of the apartment complex should be able to access the internet via a wired connection in their apartment or via one of the wireless AP’s



I just had 2 cable services installed at the location, 8 megs each, in order to replace a 10 meg wireless link that was serving the building. I do know that, although each of the cable services installed have 5 static IP’s assigned to them, the SMC router/cable modems do DHCP as well and assign 10.x.x.x IP’s to each user. On one service, I plan to assign 1 static to the server, and 1 to the managers office. I plan to add another NIC to the server (giving me a total of 2 NIC’s) and assign a second static IP to that NIC. 



I believe I need to shutdown the DHCP3 service currently running on the server, then change the IP tables to allow access using IP’s from the cable company. I’m really new to the linux/ubuntu OS and need some guidance.

I have been talking via email with one person who said..
You are stuck. You can't do that and bond/load balance those connections.

You have to (this will look ok in a fixed font):

   Comcast1          Comcast2
     \                /
      \              /    Public IPs - (DHCP'd or not)
       \            /
   [ Linux boxen upstream nic              ]
   [ iptables, squid, dansguardian, DHCPD, Load Balancing Routes  ]
   [ Linux box downstream nic              ]
          |
          |
          |
     [switch/hubs]

     /       \         \            \

WiFiAP1    WiFiAP2   Dorm Room    Dorm Room


---------------------------

This is a lot more than any sane person wants to do on a system from remote. Too many variables.

I need some help. I really don't know what to do, where to start or anything else but I have to have this fixed before Jan4.

---

### Post by PriceChild on 2007-12-27
*moved and approved*

---

