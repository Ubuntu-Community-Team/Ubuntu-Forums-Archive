---
title: "NTP does not work correctly"
date: 2013-09-19
forum: Networking &amp; Wireless
---

### Post by gianfranco3 on 2013-09-19
I set up a LAN composed by 3 computers with Ubuntu OS.
The first PC has a network interface card and the following IP address 192.168.100.3 and subnet mask 255.255.255.0 gateway 192.168.100.200
The second PC has two network interface cards and the following IP address 192.168.100.200 and subnet mask 255.255.255.0 gateway 192.168.100.200 and IP address 192.168.1.300 and subnet mask 255.255.255.0 gateway 192.168.1.300
The third PC has a network interface card and the following IP address 192.168.1.4 and subnet mask 255.255.255.0 gateway 192.168.1.300

I'm trying to synchronize the third PC with the first one. In order to reach this goal I set-up a ntp server in the first PC and this is the ntp.conf

```
# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help


driftfile /var/lib/ntp/ntp.drift




# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/


statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# Specify one or more NTP servers.


# Use servers from the NTP Pool Project. Approved by Ubuntu Technical Board
# on 2011-02-08 (LP: #104525). See http://www.pool.ntp.org/join.html for
# more information.
server 0.ubuntu.pool.ntp.org
server 1.ubuntu.pool.ntp.org
server 2.ubuntu.pool.ntp.org
server 3.ubuntu.pool.ntp.org


# Use Ubuntu's ntp server as a fallback.
server ntp.ubuntu.com


# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details.  The web page <http://support.ntp.org/bin/view/Support/AccessRestrictions>
# might also be helpful.
#
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.


# By default, exchange time with everybody, but don't allow configuration.
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery


# Local users may interrogate the ntp server more closely.
restrict 192.168.100.0 mask 255.255.255.0 nomodify notrap
restrict 192.168.100.200 mask 255.255.255.255 nomodify notrap
restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap
restrict 192.168.1.4 mask 255.255.255.255 nomodify notrap
restrict ::1


# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
#restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap




# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
broadcast 192.168.100.255
boradcast 192.168.1.255
#broadcast 192.168.1.255


# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient

```
and I started the NTP server digiting the command 

```
/etc/init.d/ntp start
```

I tried to update the OS time of the third PC by using the following command
```
ntpdate 192.168.100.3
```

but I had the following answer 

```
No server suitable for the synchronization found.
```

I tried with the same command on the second PC having the same result.

Someone can help me?

Gianfranco

---

### Post by Lars Noodén on 2013-09-19
The third one looks to be on a different subnet from the first.  Can you even ping them from each other?

---

### Post by gianfranco3 on 2013-09-19
> **Lars Noodén said:**
> The third one looks to be on a different subnet from the first.  Can you even ping them from each other?
Yes, they are on different subnet, but I can ping them from each other, because I have enabled the forwarding in the second PC.

Gianfranco

---

### Post by gianfranco3 on 2013-09-23
Can anyone help me?

---

### Post by Lars Noodén on 2013-09-23
Is that error occuring with ntpdate?  We should try to find a way to get a more verbose error message.  What about trying ntpd?

```

sudo service ntp stop
sudo ntpd -q -l /tmp/foo

```

That should attempt to set the time just once and then quit, but log to /tmp/foo.  Look there for messages.  I'm still thinking that you might have networking issues.

---

### Post by gianfranco3 on 2013-09-24
> **Lars Noodén said:**
> Is that error occuring with ntpdate?  We should try to find a way to get a more verbose error message.  What about trying ntpd?

```

sudo service ntp stop
sudo ntpd -q -l /tmp/foo

```

That should attempt to set the time just once and then quit, but log to /tmp/foo.  Look there for messages.  I'm still thinking that you might have networking issues.

this is the result

```

24 Sep 12:00:44 ntpd[2254]: proto: precision = 0.883 usec
24 Sep 12:00:44 ntpd[2254]: ntp_io: estimated max descriptors: 1024, initial so$
24 Sep 12:00:44 ntpd[2254]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
24 Sep 12:00:44 ntpd[2254]: Listen and drop on 1 v6wildcard :: UDP 123
24 Sep 12:00:44 ntpd[2254]: Listen normally on 2 lo 127.0.0.1 UDP 123
24 Sep 12:00:44 ntpd[2254]: Listen normally on 3 eth0 192.168.1.4 UDP 123
24 Sep 12:00:44 ntpd[2254]: Listen normally on 4 eth0 fe80::20b:6aff:fe91:89d6 $
24 Sep 12:00:44 ntpd[2254]: Listen normally on 5 lo ::1 UDP 123
24 Sep 12:00:44 ntpd[2254]: peers refreshed
24 Sep 12:00:44 ntpd[2254]: Listening on routing socket on fd #22 for interface$
24 Sep 12:00:44 ntpd[2254]: io_setbclient: Opened broadcast client on interface$
24 Sep 12:00:55 ntpd[2254]: ntpd: no servers found

```

but I can ping the server
```

64 bytes from 192.168.100.3: icmp_req=1 ttl=63 time=0.297 ms
64 bytes from 192.168.100.3: icmp_req=2 ttl=63 time=0.255 ms
64 bytes from 192.168.100.3: icmp_req=3 ttl=63 time=0.285 ms
64 bytes from 192.168.100.3: icmp_req=4 ttl=63 time=0.262 ms
64 bytes from 192.168.100.3: icmp_req=5 ttl=63 time=0.252 ms
64 bytes from 192.168.100.3: icmp_req=6 ttl=63 time=0.242 ms
64 bytes from 192.168.100.3: icmp_req=7 ttl=63 time=0.248 ms
64 bytes from 192.168.100.3: icmp_req=8 ttl=63 time=0.285 ms
64 bytes from 192.168.100.3: icmp_req=9 ttl=63 time=0.263 ms
64 bytes from 192.168.100.3: icmp_req=10 ttl=63 time=0.245 ms


--- 192.168.100.3 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8999ms
rtt min/avg/max/mdev = 0.242/0.263/0.297/0.023 ms

```

How can I fix this issue? Maybe I have a wrong setup in ntp.conf?

---

### Post by Lars Noodén on 2013-09-24
Ok.  How is ntpd set up on 192.168.100.3?  You need to have it listening for queries and have the firewall allow new incoming UDP and TCP connections on [port 123 for NTP](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.txt).

---

### Post by gianfranco3 on 2013-09-24
> **Lars Noodén said:**
> Ok.  How is ntpd set up on 192.168.100.3?  You need to have it listening for queries and have the firewall allow new incoming UDP and TCP connections on [port 123 for NTP]("https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.txt").

this is the ntp.conf in 192.168.100.3

```

# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help


driftfile /var/lib/ntp/ntp.drift




# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/


statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# Specify one or more NTP servers.


# Use servers from the NTP Pool Project. Approved by Ubuntu Technical Board
# on 2011-02-08 (LP: #104525). See [http://www.pool.ntp.org/join.html](http://www.pool.ntp.org/join.html) for
# more information.
#server 0.ubuntu.pool.ntp.org
#server 1.ubuntu.pool.ntp.org
#server 2.ubuntu.pool.ntp.org
#server 3.ubuntu.pool.ntp.org
server 127.127.1.0
fudge 127.127.1.0 stratum 10

# Use Ubuntu's ntp server as a fallback.
server ntp.ubuntu.com


# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details.  The web page <http://support.ntp.org/bin/view/Support/AccessRestrictions>
# might also be helpful.
#
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.


# By default, exchange time with everybody, but don't allow configuration.
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery


# Local users may interrogate the ntp server more closely.
restrict 192.168.100.0 mask 255.255.255.0 nomodify notrap
restrict 192.168.100.200 mask 255.255.255.255 nomodify notrap
restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap
restrict 192.168.1.4 mask 255.255.255.255 nomodify notrap
restrict ::1


# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
#restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap




# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
broadcast 192.168.100.255
broadcast 192.168.1.255
#broadcast 192.168.1.255


# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient

```

and I have enabled the 123 port in the server (192.168.100.3) using these commands
```

iptables -A INPUT -p udp --dport 123 -j ACCEPT
iptables -A OUTPUT -p udp --sport 123 -j ACCEPT

```

and I have enabled the 123 port in the client (192.168.1.4) using these commands
```

iptables -A INPUT -p udp --sport 123 -j ACCEPT
iptables -A OUTPUT -p udp --dport 123 -j ACCEPT

```

I don't know if I have to set up something in the PC that connects the server to the client. (IP 192.168.100.200 and IP 192.168.1.300)

Gianfranco

---

### Post by SeijiSensei on 2013-09-24
If your firewalling rules end with generic REJECT rules for non-matching packets, try adding logging like this:

```

/sbin/iptables -A INPUT -j LOG
/sbin/iptables -A INPUT -j REJECT

```

If you reject by policy, just add the LOG rule to the end of the INPUT chain.

Now you will see entries in /var/log/syslog reporting packets that have been blocked by firewalling rules.

Another test you can run is to install **nmap** on the client, then run the command:

```
sudo nmap -sU -p 123 192.168.1.3
```

to see if the port is open and a listener can be detected.

---

