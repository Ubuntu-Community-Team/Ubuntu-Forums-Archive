---
title: "Port forwarding unsuccessful on ubuntu 18.04"
date: 2020-09-30
forum: Networking &amp; Wireless
---

### Post by bigbluewind on 2020-09-30
[COLOR=#1A1A1B][FONT=&amp]Hi,[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I have tried to open a port on ubuntu 18.04 desktop version.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I have managed to point the internal ip address ([192.168.1.xxx]("https://192.168.1.xxx/")) to my pc MAC in the DHCP and add up a profile of port (internal ip mapped to port) that needs to be opened up in PortForwarding page in router.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]In ubuntu, I have run the command sudo ufw allow portnumber/tcp and check the ufw status which is active and port is working.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]After completing all the above, I got "post is closed" once checking with [yougetsignal.com]("https://yougetsignal.com/") and "times out" with [canyouseeme.com]("https://canyouseeme.com/").[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]If there anything I have done wrong? Thanks for the help.[/FONT][/COLOR]

---

### Post by scorp123 on 2020-09-30
> **bigbluewind said:**
> After completing all the above, I got "post is closed" once checking with [yougetsignal.com]("https://yougetsignal.com/") and "times out" with [canyouseeme.com]("https://canyouseeme.com/") 

Is the service that's supposed to answer on that port even running?
Can you post the output of this command please:
```
sudo lsof -n -i -P
```

---

### Post by HermanAB on 2020-10-01
Note that a Berkeley Port is a number in the header of a datagram.  The Port number is used to route the datagram to/from a server.

A Port is considered Closed when:
a. The server is not listening, or not even running at all.
b. The network packet filter drops the datagram on the floor, so it cannot get to the server.

So, first make sure that your server is actually running and working properly, before playing with the packet filter.

---

### Post by slickymaster on 2020-10-01
Thread moved to **Networking & Wireless** for a better fit

---

