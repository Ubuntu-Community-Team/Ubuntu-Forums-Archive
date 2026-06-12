---
title: "Squid random https failure"
date: 2013-10-30
forum: Networking &amp; Wireless
---

### Post by rcmn on 2013-10-30
i'm using 
the latest Squid3 on a headless server with Ubuntu 12.04.3 LTS (GNU/Linux 3.2.0-55-generic x86_64)
System load:  0.01
Usage of /:   3.6% of 291.28GB
Memory usage: 23% 
Swap usage:   0%
accessing the proxy from wan(1.5Mbs D / 1Mbs U adsl) and lan.
Proxy on cable (20Mbs D/ 1Mbs U).

squid.conf
```

auth_param digest program /usr/lib/squid3/digest_pw_auth -c /etc/squid3/passwords
auth_param digest realm squidrealm
acl authenticated proxy_auth REQUIRED
http_access allow authenticated
http_port 8888

```

this very short config file come from here [http://dabase.com/blog/Minimal_squid3_proxy_configuration/](http://dabase.com/blog/Minimal_squid3_proxy_configuration/)

So the issue i have is ,when using https it will randomly break and the following error will show in 
FF :"ssl_error_rx_record_too_long"
opera:"Secure connection: fatal error (47) Transmission failure."

Then the proxy will be responsive for other protocol but https .Then after a while https will be available again. 
testing locally using telnet throw a similar error.

I have tried to use more coventional config file but with no success.

the logs :
access.log I get bunch of "TCP_MISS"
cache.log 
```

2013/10/30 05:40:28| Starting Squid Cache version 3.1.19 for x86_64-pc-linux-gnu...
2013/10/30 05:40:28| Process ID 20216
2013/10/30 05:40:28| With 65535 file descriptors available
2013/10/30 05:40:28| Initializing IP Cache...
2013/10/30 05:40:28| DNS Socket created at [::], FD 5
2013/10/30 05:40:28| DNS Socket created at 0.0.0.0, FD 6
2013/10/30 05:40:28| Adding nameserver x.x.x.x from /etc/resolv.conf
2013/10/30 05:40:28| helperOpenServers: Starting 5/5 'digest_pw_auth' processes
2013/10/30 05:40:29| Unlinkd pipe opened on FD 21
2013/10/30 05:40:29| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
2013/10/30 05:40:29| Store logging disabled
2013/10/30 05:40:29| Swap maxSize 0 + 262144 KB, estimated 20164 objects
2013/10/30 05:40:29| Target number of buckets: 1008
2013/10/30 05:40:29| Using 8192 Store buckets
2013/10/30 05:40:29| Max Mem  size: 262144 KB
2013/10/30 05:40:29| Max Swap size: 0 KB
2013/10/30 05:40:29| Using Least Load store dir selection
2013/10/30 05:40:29| Current Directory is /
2013/10/30 05:40:29| Loaded Icons.
2013/10/30 05:40:29| Accepting  HTTP connections at [::]:8888, FD 22.
2013/10/30 05:40:29| HTCP Disabled.
2013/10/30 05:40:29| Squid plugin modules loaded: 0
2013/10/30 05:40:29| Adaptation support is off.
2013/10/30 05:40:29| Ready to serve requests.
2013/10/30 05:40:30| storeLateRelease: released 0 objects

```

---

