---
title: "How to open port 8000?"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by finita on 2007-05-23
Hi,

I have a server and by default port 8000 is closed.
When I check nmap -p 8000-8001 xxx.xxx.xxx.xxx
it is showing all ports which i requested are closed.

I want to broadcast stream from one of these ports, but having troubles.

I need to open the ports asap.

Thanks

---

### Post by reacocard on 2007-05-23
> **finita said:**
> Hi,

I have a server and by default port 8000 is closed.
When I check nmap -p 8000-8001 xxx.xxx.xxx.xxx
it is showing all ports which i requested are closed.

I want to broadcast stream from one of these ports, but having troubles.

I need to open the ports asap.

Thanks

You have to start a server on that port.

---

### Post by finita on 2007-05-23
Hi,

I'm starting shoutcast ./sc_serv

giving log below:

<05/23/07@15:42:13> [SHOUTcast] DNAS/Linux v1.9.7 (Jun 23 2006) starting up...
<05/23/07@15:42:13> [main] pid: 16610
<05/23/07@15:42:13> [main] loaded config from sc_serv.conf
<05/23/07@15:42:13> [main] initializing (usermax:32 portbase:8000)...
<05/23/07@15:42:13> [main] No ban file found (sc_serv.ban)
<05/23/07@15:42:13> [main] No rip file found (sc_serv.rip)
<05/23/07@15:42:13> [main] opening source socket
<05/23/07@15:42:13> [main] source thread starting
<05/23/07@15:42:13> [main] opening client socket
<05/23/07@15:42:13> [main] Client Stream thread [0] starting
<05/23/07@15:42:13> [main] client main thread starting
<05/23/07@15:42:13> [source] listening for connection on port 8001
<05/23/07@15:42:49> [sleeping] 0 listeners (0 unique)

Then opening Winamp and writing all necessary values correct.
After pressing connect giving error below:

<05/23/07@15:45:19> [source] invalid password from ***** xxx.xxx.xxx.xxx
<05/23/07@15:45:51> [sleeping] 0 listeners (0 unique)

And Connection aborting.

What the problem can be? I can not solve it.

---

### Post by finita on 2007-05-23
By the way, password is correct

---

### Post by reacocard on 2007-05-23
hmmm, can you please do 'nmap localhost' from the server?

---

