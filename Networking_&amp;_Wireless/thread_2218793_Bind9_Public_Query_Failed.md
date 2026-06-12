---
title: "Bind9 Public Query Failed"
date: 2014-04-22
forum: Networking &amp; Wireless
---

### Post by Bullz3y3 on 2014-04-22
I've installed bind9 on Ubuntu 12 and it's behind pfSense firewall and have setup 1:1 NAT and all the ports are open. When I create a zone a try to lookup from outside it gives me server unreachable error. Inside lookup works perfectly. Haven't configured any views just a basic setup.

He's the /etc/bind/named.conf.options

```


        dnssec-validation auto;


        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};



```

netstat
```
root@ns1:~# netstat -pluntActive Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN      20229/sendmail: MTA
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      19140/apache2
tcp        0      0 10.10.10.22:53          0.0.0.0:*               LISTEN      20734/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      20734/named
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      18991/sshd
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      20734/named
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      20229/sendmail: MTA
tcp6       0      0 :::53                   :::*                    LISTEN      20734/named
tcp6       0      0 :::22                   :::*                    LISTEN      18991/sshd
tcp6       0      0 ::1:953                 :::*                    LISTEN      20734/named
udp        0      0 10.10.10.22:53          0.0.0.0:*                           20734/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           20734/named
udp6       0      0 :::53                   :::*                                20734/named



```

Any ideas.

---

### Post by PapaNerd on 2014-04-23
I am not familiar with the pfSense firewall, but your description does sound like the firewall isn't allowing the query to pass through.  When you say "all the ports are open," did you open both tcp and udp (since DNS queries to port 53 are udp)?  Can you break the problem in half by turning off the firewall?

---

### Post by SeijiSensei on 2014-04-23
You only allowed connections using IPv6 with the directive
```
listen-on-v6 { any; };
```
You also need the 
```
listen-on { any; };
```
option to accept queries on good-old IPv4.  Place it right above the v6 directive.

On my (CentOS) server with BIND 9.8.2, that directive now reads:
```
listen-on port 53 { any; };
```
though I suspect you can omit the "port 53" part since that's the default.  Still it doesn't hurt to include it unless BIND complains when you start it up.

---

