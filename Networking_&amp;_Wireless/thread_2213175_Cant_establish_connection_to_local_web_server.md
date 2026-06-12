---
title: "Cant establish connection to local web server"
date: 2014-03-25
forum: Networking &amp; Wireless
---

### Post by aryzing on 2014-03-25
Hi all,
I am unable to connect to a webserver on the local network. After trying to solve the issue for several days, as well as posting to [Ask Ubuntu]("http://askubuntu.com/questions/437563/unable-to-load-page-using-express-from-local-machine") and [Stackoverflow]("http://stackoverflow.com/questions/22566669/cant-connect-to-express-app-over-lan") and receiving no replies, I am still unable to establish connection to the webserver. 

It is a simple webserver created with Express and Node.js with a single index.html page. I can access it from the machine I am developing it on, both on localhost:3000 and 192.x.x.x:3000. However, other machines on the same network cannot access it with the 192.x.x.x:3000 address. Now, what truly confuses me is that I have enabled port forwarding on my router, and I can access the webserver from a machine in another network at [http://external.ip.address:3000](http://external.ip.address:3000)!! What is going on? Any suggestions?

Any help much appreciated!

---

### Post by steeldriver on 2014-03-25
Can you communicate between the LAN machines in other respects (ping? ssh?)

---

### Post by aryzing on 2014-03-25
No, i tried pinging from a windows machine, and it said the host is not accessible. Should I be changing some settings in ubuntu?

(thanks for replying!)

---

### Post by Iowan on 2014-03-25
> **aryzing said:**
> No, i tried pinging from a windows machine, and it said the host is not accessible. 
Pinging by local IP address (192.168.X.X) or by name?

---

### Post by aryzing on 2014-03-25
by ip address
Webserver located at 192.168.1.37
Pinging from pc at 192.168.1.38

on 192.168.1.38:
```

$ ping 192.168.1.37
PING 192.168.1.37 (192.168.1.37) 56(84) bytes of data.
From 192.168.1.38 icmp_seq=1 Destination Host Unreachable
From 192.168.1.38 icmp_seq=2 Destination Host Unreachable
From 192.168.1.38 icmp_seq=3 Destination Host Unreachable
etc...

```

thx for quick reply!

---

### Post by Iowan on 2014-03-25
Curious... Can the server ping elsewhere (can it ping 192.168.1.38)?
Is there a firewall on the server?

---

### Post by aryzing on 2014-03-25
Yes, the webserver (37) can succesfully ping the other pc (38)

on the webserver (192.168.1.37):
```
~$ ping 192.168.1.38
PING 192.168.1.38 (192.168.1.38) 56(84) bytes of data.
64 bytes from 192.168.1.38: icmp_req=1 ttl=64 time=45.1 ms
64 bytes from 192.168.1.38: icmp_req=2 ttl=64 time=2.47 ms
64 bytes from 192.168.1.38: icmp_req=3 ttl=64 time=2.03 ms
```

Regarding the firewall, as far as I know, it is whatever a standard ubuntu 12.04 LTS install has (on both machines).
thx!

---

### Post by aryzing on 2014-03-25
OK, so what i finally decided to do was to install Node.js and Express on the other pc (192.168.1.38). As a result, the strangest thing happened:

1. All devices on the network can access the new web server on the pc (38:3000).
2. The pc can now access the webserver (37:3000). Note that previously the pc *could not* access the webserver.
3. The pc can now also ping the webserver, which it previously could not.
4. All other devices still can not access the webserver (37:3000).

Basically, installing Node and Express on the pc (38) gave it and only it access to the webserver (37), all other devices still cannot access it. This is very strange. I shall pursue this no further. When I have time ill simply do a clean install of ubuntu on the webserver and take it from there. Hopefully this will solve everything.

Any final comments?

Thanks for all the help!

---

