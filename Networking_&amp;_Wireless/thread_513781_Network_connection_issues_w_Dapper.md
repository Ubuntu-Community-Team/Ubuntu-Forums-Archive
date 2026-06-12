---
title: "Network connection issues w/ Dapper"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by jones28s on 2007-07-30
OK.  I've been through many of the forums already, and haven't found a solution.  I cannot seem to get my connection working properly.

I am running Ubuntu 6.06 LTS Server (Dapper).  I installed the LAMP version a few months back.  Initially, it connected to the internet fine, but started having problems, so I put it aside.  I'm now trying to get it connected.

I am connecting to my network.  Pings to my gateway return about 40% of the time consistently (60% packet loss), and the one's I'm getting back are very slow.  I seem to be getting DNS resolution (also slow, but it is working).  There is no difference in connectivity whether it is configured with Static IP or DHCP from my Netgear router.  I am hardwired to router.  All other PCs connected through router are working and connecting fine.

Cannot connect to anything successfully on the internet through Firefox, nor any other application.  I was able to ftp from terminal window to my local web server, but not from browser.

I have disabled the IPV6 connection, and have incrementally lowered the MTU settings from 1500 to 1100, with no real change in response.  Ifconfig settings are below:

patrick@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8B:FE:E2:68
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:278 errors:339 dropped:0 overruns:0 frame:339
          TX packets:258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:29341 (28.6 KiB)  TX bytes:27574 (26.9 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

Any ideas??  I'm at a loss.:confused:

---

### Post by PaulFr on 2007-07-30
The high frame errors you are getting point to some hardware misconfiguration or problem. It may also point to congestion on your network, but since other PCs work fine, this is unlikely. Since you are directly connected to your router, I presume there are three parts on your link - the network card in your system, the cable connecting it to the router, and the router port. I would suggest the following checks:

1. Check if there is any mismatch in speed between what your card can do and what the router expects on the port (for example, if the port expects a 100 Mbps connection only, and your card is 10 Mbps only). This is unlikely, since most ports and cards now are auto-sensing, but you should check the docs just to be sure.
2. Then check the cable - this is the prime suspect. Swap it out with a working cable and test.
3. Then the router port.
4. Finally, remove the network card and put in a known good one from your working PCs.

Hope this helps.

---

### Post by jones28s on 2007-07-31
Thank you Paul!  It turns out it was my network cable.  That's what I get for ignoring the KISS rule (keep it simple, stupid!)

Thanks again.  You've been a great help:KS

---

