---
title: "Outbound Port 80 connecting not working"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by DrHogie on 2007-04-03
I recently setup a Ubuntu Server 6.10.  When I was installing other software packages, I noticed that apt-get wouldn't connect to anything.  I found a thread that suggested changing the URIs in the apt-get configuration from http:// to ftp:// -- this fixed the apt-get problem.

However, later on I tried to get a file via wget.  The connection timed out.  I apt-get'd curl and tried using it.  It also timed out.  Curious, I fired up telnet.  I tried connecting to port 110 of a real-world server.  I got an instant response from said server.  So outbound connections are working.  Next, I tried connecting to that server's port 80.  The outside server's port 80 is working -- I verified this on a PC on the same network.  However, I got no response from port 80 from that either (yes, I typed in a dummy GET response so the server would respond).

I have disabled IPv6 on the machine and still no dice.  Does anyone have any suggestions?

Thanks in advance,
DrHogie

---

### Post by az on 2007-04-03
> **DrHogie said:**
> Next, I tried connecting to that server's port 80.  The outside server's port 80 is working -- I verified this on a PC on the same network.  However, I got no response from port 80 from that either 

Are you using residential broadband?  Many ISPs block port 80.

---

### Post by DrHogie on 2007-04-03
It is a commercial cable modem connection that we're using.  But, lemme try to draw this out with my l33t ASCII skillz.


Ubuntu Server <---------------||||-------------------> .com server on Internet
   |                                LAN firewall
   |
   |
   |
Laptop PC


I can connect from Laptop PC to Ubuntu Server on Port 80.
I can connect from Laptop PC to .com server on Internet port 80 (So the firewall is letting the connection through).
I cannot connect from Ubuntu Server on Port 80 to .com server on Internet.
I cannot connect from Ubuntu Server on Port 80 to Laptop PC.

So I don't think the ISP is blocking outgoing port 80, and I don't think the firewall in place is blocking port 80 either.   Any thoughts?

---

### Post by dbott67 on 2007-04-03
Many folks have had issues with IPv6 and with DNS resolution.  ***Before you change any of your DNS servers***, can you confirm whether or not you can ping by fully qualified domain name from the terminal.

Can you post the output of the following commands:
```
dbott@thedrake:~$ [COLOR=Red]**ping www.google.com**[/COLOR]
PING www.l.google.com (64.233.161.104) 56(84) bytes of data.
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=1 ttl=234 time=43.8 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=2 ttl=234 time=43.7 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=3 ttl=234 time=45.1 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=4 ttl=234 time=43.8 ms

--- www.l.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3012ms
rtt min/avg/max/mdev = 43.787/44.161/45.115/0.590 ms

dbott@thedrake:~$ [COLOR=Red]**ping www.cbs.com**[/COLOR]
PING a916.g.akamai.net (209.123.81.94) 56(84) bytes of data.
64 bytes from 209.123.81.94: icmp_seq=1 ttl=60 time=15.4 ms
64 bytes from 209.123.81.94: icmp_seq=2 ttl=60 time=15.5 ms
64 bytes from 209.123.81.94: icmp_seq=3 ttl=60 time=15.2 ms
64 bytes from 209.123.81.94: icmp_seq=4 ttl=60 time=15.7 ms
64 bytes from 209.123.81.94: icmp_seq=5 ttl=60 time=17.5 ms

--- a916.g.akamai.net ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4022ms
rtt min/avg/max/mdev = 15.229/15.905/17.566/0.845 ms

dbott@thedrake:~$ [COLOR=Red]**ping www.yahoo.com**[/COLOR]
PING www.yahoo-ht3.akadns.net (69.147.114.210) 56(84) bytes of data.
64 bytes from f1.www.vip.re3.yahoo.com (69.147.114.210): icmp_seq=1 ttl=47 time=40.7 ms
64 bytes from f1.www.vip.re3.yahoo.com (69.147.114.210): icmp_seq=2 ttl=47 time=38.2 ms
64 bytes from f1.www.vip.re3.yahoo.com (69.147.114.210): icmp_seq=3 ttl=47 time=38.5 ms
64 bytes from f1.www.vip.re3.yahoo.com (69.147.114.210): icmp_seq=4 ttl=47 time=38.7 ms
64 bytes from f1.www.vip.re3.yahoo.com (69.147.114.210): icmp_seq=5 ttl=47 time=41.4 ms

--- www.yahoo-ht3.akadns.net ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4020ms
rtt min/avg/max/mdev = 38.283/39.546/41.473/1.294 ms

```If you do not get replies, you may be suffering from name resolution issues.  You may want to try 2 things:

1. Blacklist ipv6 (as you have already done)
2. Change default DNS servers to OpenDNS servers.

Both steps are outlined in this thread (post #3 and #5):

[http://www.ubuntuforums.org/showthread.php?t=323747 ]("http://www.ubuntuforums.org/showthread.php?t=323747")

-Dave

---

### Post by DrHogie on 2007-04-04
I'm using an internal DNS server that's pointing out to my ISPs DNS server.  But I don't think that's the problem . . .

If I ping to [www.google.com](www.google.com) and [www.yahoo.com](www.yahoo.com), I can get responses from those sites with 100% accuracy.  If I ping the test site in question (mfjenterprises.com), I can get a response.  If I telnet to port 110 of the test site in question, I get an instant response.  If I telnet to port 80 of the test site in question, the connection times out.  But if I telnet to port 80 of the test site in question from my laptop, I get an instant response.

I'm by far not a Linux expert, but I've been setting up LAMP servers for web development/web serving for years -- this is the first time I've ever run into this problem.  Any other thoughts?  Because I'm throughly stumped.

---

