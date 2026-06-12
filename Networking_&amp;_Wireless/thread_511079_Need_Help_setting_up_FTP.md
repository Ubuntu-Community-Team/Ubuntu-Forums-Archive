---
title: "Need Help setting up FTP"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by BGI on 2007-07-27
Hello all,

I am new to Linux but have a background in web programming and have a decent understanding of networking. I have recently setup an archive server for the business I work for. The 2 requirements of this server are access to the network internally via shared files and ftp access so we can access our archive files on the road and at home. I am using Proftpd and the problem I am having is. I can access my files internally via local neighborhood perfectly and access the ftp via internal ip address 192.168.1.133 but cannot access the ftp with an external ip. The machine is currently set as DHCP and I have been able to access the ftp via ext ip if i set the ip as a static ip but then an unable to access files internally. I can install a second network card if need be where one is set DHCP and one is set with static IP. What I was wondering was what is the best way to set this up. I have tried to use webmin to create some rules so that I am able to route my internal ip to the external ip but have had no luck. Any suggestions or help would b much appreciated.

---

### Post by dmizer on 2007-07-30
okay ... here's a little nugget i learned about a week ago.

if you're using a router, you can't access your ftp server by using your wan ip address.

iow:
you will be able to access your server at 192.168.1.133, but if you are on your local network, you will not be able to access your own ftp server via your external ip.  very few routers have wan address rerouting capability because it's generally not needed.

i suspect that if you attempt to connect to your ftp server from another location, that it will work just as expected.

if it does not work from a remote location:
1) make sure that port forwarding is set up correctly on your router.
2) take a look at the third link in my sig.

---

### Post by BGI on 2007-07-30
Thank you for the response. It was somewhat helpful but when Masquerading my address I get thi error

IPv6 getaddrinfo 'comp32' error : No address is associated with the hostname comp32 - 127.0.1.1:21  masquerading as 70.93.53.134

I can still connect internally but not externally. I really dont want to have to backup all my info and format to a crappy windows based machine just so I can setup a working FTP so anyone that could help me it would be much appreciates

---

### Post by Malh on 2007-07-30
> **BGI said:**
> Thank you for the response. It was somewhat helpful but when Masquerading my address I get thi error

IPv6 getaddrinfo 'comp32' error : No address is associated with the hostname comp32 - 127.0.1.1:21  masquerading as 70.93.53.134

I can still connect internally but not externally. I really dont want to have to backup all my info and format to a crappy windows based machine just so I can setup a working FTP so anyone that could help me it would be much appreciates

the IPv6 error isn't causing you to be unable to connect externally, you need a static IP to connect externally.  contact your ISP and ask for a static ip.  i had to connect my ftp server directly to the cable modem to get it working externally as it had to have a static ip address

---

### Post by BGI on 2007-07-30
I have set it up with a static IP and yes it does work that way but then I cannot use it within our internal network via file sharing. The computer is used for a dump for photo files that can be 3gig of files so i need for it to work via file sharing as well. I am thinking of trying a second NIC card so that one can be connected internally and one can be connected externally I just hope it will recognize both and work

---

### Post by mwacky on 2007-09-04
Heard of Dynamic DNS, I can easy connect to an ftp server on a windows xp pro box through dynamic ip provider.  Just need to set connection static internally...  I'm having problems on my linux box and getting wireless to stay static, see this [thread]("http://ubuntuforums.org/showthread.php?t=543172").

---

