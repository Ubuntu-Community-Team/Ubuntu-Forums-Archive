---
title: "NTP Setup for Local LAN (No internet)"
date: 2019-08-20
forum: Networking &amp; Wireless
---

### Post by catman2 on 2019-08-20
I want to setup NTP in an isolated local network with many PCs

The network looks like this. There is no gateway.
 192.68.0.1 MainServer
 192.68.0.2 - 192.68.0.255 Other servers and client PCs

I am confused with all the ntp options in the config file. What options are really needed to get all offline PCs on the network tightly together?


Can someone please comment of the setups of /etc/ntp.conf files for server and clients? 

Is this a good setup? If not what should be added and why?
  Main server (IP 192.168.0.1) /etc/ntp.conf:
    ```

driftfile /var/lib/ntp/ntp.drift
server 127.127.1.0 iburst 
fudge 127.127.1.0 stratum 2

```
 
All others /etc/ntp.conf:
> 
driftfile /var/lib/ntp/ntp.drift
    server 192.168.0.1 iburst 
    fudge 127.127.1.0 stratum 3

---

### Post by SeijiSensei on 2019-08-21
How are you going to insure that the server has the correct time if it cannot synchronize with Internet time servers? There are methods to [interface ntpd with external clocks]("https://www.eecis.udel.edu/~mills/ntp/html/extern.html").

Can the server see the Internet, or is it physically disconnected? If it can see the Internet, you can use IP tables rules to limit it to connections on the NTP port, 123 tcp/udp.

I think the configuration files are fine, but the way to make sure is to set up the server and a single client for testing.  Manually reset the clock on the client so it's off by five minutes or so, then force it to get the correct time from the server.

You could use ntpdate on the clients rather than another implementation of ntpd.

---

