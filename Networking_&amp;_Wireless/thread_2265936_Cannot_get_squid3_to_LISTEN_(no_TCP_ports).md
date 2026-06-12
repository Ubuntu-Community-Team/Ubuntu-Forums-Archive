---
title: "Cannot get squid3 to LISTEN (no TCP ports?)"
date: 2015-02-18
forum: Networking &amp; Wireless
---

### Post by Visual Echo on 2015-02-18
Hi!  I've recently upgraded a machine which I use as a home firewall/router from Precise to Trusty.  I was using a version of Squid v3.0.0-BETA... something like that, and I had it set up as a transparent proxy for my slow (but unmetered) DSL internet connection.  It listened on TCPv4 port 3128, and I had it firewalled with iptables to be accessible only from localhost and my own internal network.  It worked great.

After upgrading to Trusty, I replaced the old configuration with the one for the new squid3 (v3.3.8) from the distribution package, checked the http_port setting, and fired it up.  It runs, but doesn't listen on TCPv4 3128, or any TCP ports v4 or v6.  This post ( [http://ubuntuforums.org/showthread.php?t=2235784](http://ubuntuforums.org/showthread.php?t=2235784) ) showed how to set up the file cache, so I did that, and I've messed with the ACLs, but no configuration setting I can find seems to affect this behavior.  I've purged and reinstalled a few times.   I've run with the -X (force full debugging) option, and while that gives oodles of output, there's nothing there that indicates any show-stopper problem that prevents binding to a TCP port.  Here's the config, with the http_port changed to 22222 and the file cache dir set up, the rest is original dpkg-new:

```
rcv@silky-lee:/var/spool$ cat /etc/squid3/squid.conf | grep -v ^# | grep -v ^$
acl SSL_ports port 443
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl CONNECT method CONNECT
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost manager
http_access deny manager
http_access allow localhost
http_access deny all
http_port 22222
cache_dir ufs /var/spool/squid3 8192 16 256
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0     0%      0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .               0       20%     4320
rcv@silky-lee:/var/spool$ sudo invoke-rc.d squid3 start
squid3 start/running, process 31444
rcv@silky-lee:/var/spool$ sudo netstat -peanut | grep squid
udp        0      0 0.0.0.0:39238           0.0.0.0:*                           13         642633      31444/squid3    
udp6       0      0 ::1:39436               ::1:36651               ESTABLISHED 13         642639      31444/squid3    
udp6       0      0 ::1:36651               ::1:39436               ESTABLISHED 13         642640      31444/squid3    
udp6       0      0 :::53068                :::*                                13         642632      31444/squid3    
rcv@silky-lee:/var/spool$

```

Am I wrong in thinking this should work?  What can I do?  I've searched through a few different web engines and I can't seem to find any suggestions or solutions that work.  Is there a missing package, something IPv6 that got forgotten?  I have trouble believing I'm the only person that is seeing this, or I'm missing something really, really silly.

---

### Post by SeijiSensei on 2015-02-18
```
http_port 22222
```
You told Squid to listen on 22222, not 3128.  You also need the "transparent" keyword like this:
```
http_port 3128 transparent
```
You also need an iptables rule to push outbound HTTP traffic through the proxy, but I presume you had that set up if the proxy was running beforehand.

---

### Post by Visual Echo on 2015-02-19
Either way, any port = no TCP port open for listening.  What prevents squid3 from opening a TCP port?

---

### Post by Visual Echo on 2015-02-23
It seems to have something to do with IPv6, as I've converted another machine (from Lucid -> Precise -> Trusty) which is having the same trouble.

Anybody have any ideas?  What critical package introduced in Trusty changed the IP stack?

And why am I being ignored?   The only response I get is from somebody who didn't even read my question?

---

### Post by madwoota on 2015-04-20
Change "http_port" to "0.0.0.0:22222" rather than just the port number.

---

