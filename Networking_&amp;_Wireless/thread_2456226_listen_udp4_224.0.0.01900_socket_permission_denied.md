---
title: "listen udp4 224.0.0.0:1900: socket: permission denied"
date: 2021-01-07
forum: Networking &amp; Wireless
---

### Post by Raymond Day on 2021-01-07
Want to get a old RIO music player working again. It will work with Logitech Media Server.

There is a install for slimrio.

[It is saved on the "Wayback Machine"]("https://web.archive.org/web/20110810013823/http://empeg.org.uk/slimrio/index.html")

Long ago I had it working when I installed a DHCP server on the server Logitech Media Server is on. But my router is doing the DHCP addresses now.

[I think the ssdp.c program]("https://web.archive.org/web/20110810014202/http://empeg.org.uk/slimrio/source/ssdp.c") need to have the RIO see the server and install the OS on it from the server.

All I changed in the ssdp.c file is the IP of the "char *server="194.168.151.150";" to my servers IP address.

Then when I type **ssdp** it comes back with this:

**2021/01/07 06:33:21 listen udp4 224.0.0.0:1900: socket: permission denied**

My guess is that Plex server is using the UDP port not sure.

It be nice to have this slimRio working again with a server and the music have on Logitech Media Server.

-Raymond Day

---

### Post by TheFu on 2021-01-07
To see which programs are listening, use something like this:
```
# Open ports with listeners, not localhost
ss -lntu|egrep -v 127
netstat -tunl|grep LISTEN|grep -v 127
netstat -tulpn |grep LISTEN|grep -v 127
```

Those examples are for TCP and UDP, so you may want to remove the TCP options.

---

### Post by Raymond Day on 2021-01-07
There is a long list of numbers with them 3 commands but none are port 21075 that the ssdp.c says it listen for.

Them 3 commands ending up at 112 lines.

-Raymond Day

---

