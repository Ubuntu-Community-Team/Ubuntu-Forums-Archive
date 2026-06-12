---
title: "Ubuntu 16.04 Server causes entire LAN to flap intermittently when connected."
date: 2020-02-11
forum: Networking &amp; Wireless
---

### Post by mikeaw2010 on 2020-02-11
Machine: Dell Precision T5600 Server
OS: Ubuntu 16.04 Server
Programs running: Eve-ng, Apache web server on port 591 instead of 80

I've ruled out the following:

-- No conflicting IP's on the (3 device) LAN.
-- Tried on three different routers (2 different Arris, 1 Netgear).
-- Tried on two different ISP's (AT&T Fiber and Suddenlink Cable).
-- Tried on the DMZ and also behind the firewall, same results.
-- Tried on two different NIC's, one onboard and the other a NIC card.
-- Disabling ipv6 on both the modem/router and the server has no effect.
-- Assigning statics also has no effect.

Whenever the server is connected and powered on, the entire LAN, wireless devices, everything (including the server) will go through a sudden packet loss burst. I activated wireshark on my desktop but am not picking up anything peculiar during these outages. During these outages, when you monitor the interface such as a ```
ifconfig pnet0
``` command, you can literally watch the TX rate climb to tens to HUNDREDS of GIGABYTES, in just a matter of literal seconds before it stops and just like that all network connectivity is restored...several minutes later the same thing happens. I then tried to perform a nethogs but when the Tx rate spikes and network connectivity is lost, nethogs is unable to record and spams the console with ```
cannot open xyz folder
``` where xyz varies and differs between each message, After the Tx surge, nethogs comes back with several listings to IP 203.107.36.142 which was not present beforehand, but does not list what port or protocol is open or being used to associate with it.

Now here is what is weirder. The issue is only replicable if the server is connected to a router or modem. I connected it directly to my PC (auto-sensing / auto-negotiation - no crossover needed) and configured a static to access the server on my PC but the connection remains stable and no flapping, bursts are experienced. When performing wireshark everything looks normal...

Any idea as to what is going on?

---

### Post by EuclideanCoffee on 2020-02-12
Has this always been an issue or something that happened suddenly? If the latter, I would suspect malware. The malware may be attached to the service you are running, the machine, or the network. If you reformat, you may still have a problem, especially if your router is compromised. Have you checked your router to see if your computer is sending a lot of data from the PC providing the weird IP logs?

---

### Post by mikeaw2010 on 2020-02-13
Hi, this only started happening after I attached the server to the network a few weeks ago. With my home PC only connected only, I dont have an issue. The server has never worked on my network.

These are the modem / gateway logs when the issue occurs:

```

2020-02-13 00:11:41.00 [UNPRIV TCP packet: ]TCP Packet - Source:185.175.93.17,49554 Destination:47.221.X.X,31651
2020-02-13 00:11:47.00 [UNPRIV TCP packet: ]TCP Packet - Source:185.175.93.17,49554 Destination:47.221.X.X,31960
2020-02-13 00:12:04.00 [UNPRIV TCP packet: ]TCP Packet - Source:92.118.37.70,48512 Destination:47.221.X.X,3389
2020-02-13 00:12:13.00 [PRIV TCP packet: ]TCP Packet - Source:159.203.42.130,59515 Destination:47.221.X.X,23
2020-02-13 00:12:19.00 [UNPRIV TCP packet: ]TCP Packet - Source:93.174.95.41,47842 Destination:47.221.X.X.,55222
2020-02-13 00:12:23.00 [UNPRIV TCP packet: ]TCP Packet - Source:185.176.27.254,49388 Destination:47.221.X.X,27918
2020-02-13 00:13:06.00 [UNPRIV TCP packet: ]TCP Packet - Source:193.32.163.74,52337 Destination:47.221.X.X,52401

```

---

### Post by mikeaw2010 on 2020-02-13
Noticing something else - this is occuring whenever I experience packet loss, but disapears as soon as network connectivity restores:

```

root@eve-ng:~# netstat -lnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 0.0.0.0:55246           0.0.0.0:*                           2277/gnome-power-ma
udp        0      0 0.0.0.0:34924           0.0.0.0:*                           2277/gnome-power-ma
raw        0 103680 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0 101376 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0 105984 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0 108288 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0  69120 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0  96768 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0  92160 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0  66816 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0  92160 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0 103680 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0 103680 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0  78336 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0 101376 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0 101376 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0  96768 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0  89856 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0  82944 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0  85248 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0  92160 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0 124416 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0  92160 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0 110592 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0  92160 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1
raw        0 108288 0.0.0.0:255             0.0.0.0:*               7           1771/sleep 1

```

Edit: I killed the PID's when they appeared (note that they are only present during the network outage) and after I did, network connectivity was instantly restored, however; soon after I lost connectivity again and this time found this:

```

root@eve-ng:~# netstat -lnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 0.0.0.0:54814           0.0.0.0:*                           19377/systemd-udevd
udp        0      0 0.0.0.0:56434           0.0.0.0:*                           19377/systemd-udevd
raw        0  82944 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0  96768 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0 110592 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0  96768 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0  80640 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0  62208 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0  92160 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0  96768 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0 103680 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0 108288 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0  57600 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0  89856 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0 108288 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0 145152 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0 129024 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0  82944 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0  55296 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0  78336 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0 101376 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0  66816 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0 188928 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0 101376 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0  82944 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"
raw        0 101376 0.0.0.0:255             0.0.0.0:*               7           19189/echo "find"

```

---

### Post by wildmanne39 on 2020-02-13
Hello mikeaw2010, when you find you have more information to add right after you posted instead of creating a duplicate post with more information just edit your post to include the extra information please.

Thanks

---

