---
title: "ntp client configuration"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by derek71 on 2010-04-15
I have set-up ntp client on my Ubuntu 8.04 server and pointed it to my PC which runs the NTP server.  I have basic connectivity to the server, though I wondered what would a good configuration for a network with one time server?  Should I run a cron job to periodically reset the system and hardware clock on the clients?

---

### Post by nixclusive on 2010-04-15
A cron job to synchronize time from your ntp server is a good idea.

---

### Post by srs5694 on 2010-04-15
I'd suggest running the full NTP server on the client, but point it at your network's main NTP server. Although a periodic update via a cron job will work, it could result in periodic shifts in time, which could be disruptive if you happen to be running any time-sensitive programs. That said, these time shifts are likely to be very small, so you might not notice them; but if you happen to be running any sensitive program, it could have effects that would seem like hard-to-diagnose bugs. The full NTP server, OTOH, slews the clock so that there aren't any sudden jumps in the time (except possibly when the NTP server first starts, depending on how the startup script does it).

---

### Post by derek71 on 2010-04-15
So I would run ntp client and server on the Ubuntu server machine, point the ntp client to the server via the loopback address and then point the ntp server to the network time server?

Would this be hard to configure and test?  The ntp client I setup first was fairly straightforward, though this setup would add an extra layer between the time server (windows xp box for now) and the client machines.

---

### Post by srs5694 on 2010-04-15
Not quite. The ntpd program (which is what actually runs) is both a client *and* a server, so there's no need to point it at itself. Just point it at whatever upstream server(s) you want to use, via entries in its /etc/ntp.conf file:

```

server 0.pool.ntp.org
server time.example.com
server tempus.fugit.example.net

```

You'd configure one computer on your network (presumably one that's always or almost always available) to point to one or more outside time servers, as above (the example.com and example.net servers are fictitious). You'd then replace this line or these lines with one that points to your own main NTP server on all other computers, but otherwise configure them identically.

---

### Post by derek71 on 2010-04-20
I have ntp installed and confirmed that it is running.  I pointed ntp to a local windows machine which in turn can reach the internet time server.  I have run into problems with high levels of jitter and offset when i check with: sudo ntpq --numeric --peers.  I noticed that for my local windows time server, there is no "*" or "+" next to the address even though: sudo ntpdate -q -d  does not indicate any errors in reaching the windows machine.  I tried adding iburst to the server definition line though I have not seen any effect.  The command does see the offset in the time compared to the windows box though it does not correct itself at least over a period of an hour or so.  What changes should I try in my ntp.conf?

---

### Post by derek71 on 2010-04-26
In my attempt to find the source of the problem with my ntp server drifting from my PC (which runs my local time server for my network), I opened my ubuntu server to the internet and added time.nist.gov to the list of servers in ntp.conf.

After a few minutes, NTP synchronized to the nist site, and the accessable flag shows next to server line.

It looks like the problem with my NTP setup may be my network or the time server running on the pc.

What would govern ntp access to a local server, other than port 123?

---

