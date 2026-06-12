---
title: "Squid problems: Invalid Request"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by teel on 2008-10-10
Hi,
I just configured Squid, it starts, iptables redirect all port 80 traffic to 3128 correctly. But trying to open any website ends up with:

```
ERROR
The requested URL could not be retrieved
While trying to process the request:
...
The following error was encountered:
    * Invalid Request
Some aspect of the HTTP Request is invalid. Possible problems:
    * Missing or unknown request method
    * Missing URL
    * Missing HTTP Identifier (HTTP/1.0)
    * Request is too large
    * Content-Length missing for POST or PUT requests
    * Illegal character in hostname; underscores are not allowed
```

The problem is that the URL is very simple: [http://www.onet.pl](http://www.onet.pl), so no syntax problem should be the reason. The configuration is standard: 

http_port 3128 transparent

Could you please help?
teel

Below is the content of /var/log/squid/cache.log:

```
# cat cache.log
2008/10/10 23:03:42| Starting Squid Cache version 2.6.STABLE18 for
i386-debian-linux-gnu...
2008/10/10 23:03:42| Process ID 25521
2008/10/10 23:03:42| With 1024 file descriptors available
2008/10/10 23:03:42| Using epoll for the IO loop
2008/10/10 23:03:42| DNS Socket created at 0.0.0.0, port 34218, FD 6
2008/10/10 23:03:42| Adding domain home.aster.pl from /etc/resolv.conf
2008/10/10 23:03:42| Adding nameserver 212.76.33.102 from /etc/
resolv.conf
2008/10/10 23:03:42| Adding nameserver 212.76.33.104 from /etc/
resolv.conf
2008/10/10 23:03:42| User-Agent logging is disabled.
2008/10/10 23:03:42| Referer logging is disabled.
2008/10/10 23:03:42| Unlinkd pipe opened on FD 11
2008/10/10 23:03:42| Swap maxSize 102400 KB, estimated 7876 objects
2008/10/10 23:03:42| Target number of buckets: 393
2008/10/10 23:03:42| Using 8192 Store buckets
2008/10/10 23:03:42| Max Mem  size: 8192 KB
2008/10/10 23:03:42| Max Swap size: 102400 KB
2008/10/10 23:03:42| Local cache digest enabled; rebuild/rewrite every
3600/3600 sec
2008/10/10 23:03:42| Rebuilding storage in /var/spool/squid (CLEAN)
2008/10/10 23:03:42| Using Least Load store dir selection
2008/10/10 23:03:42| Set Current Directory to /var/spool/squid
2008/10/10 23:03:42| Loaded Icons.
2008/10/10 23:03:42| Accepting proxy HTTP connections at 0.0.0.0, port
3128, FD 13.
2008/10/10 23:03:42| commBind: Cannot bind socket FD 14 to *:3128:
(98) Address already in use
2008/10/10 23:03:42| Accepting ICP messages at 0.0.0.0, port 3130, FD
14.
2008/10/10 23:03:42| HTCP Disabled.
2008/10/10 23:03:42| WCCP Disabled.
2008/10/10 23:03:42| Ready to serve requests.
2008/10/10 23:03:42| Done reading /var/spool/squid swaplog (0 entries)
2008/10/10 23:03:42| Finished rebuilding storage from disk.
2008/10/10 23:03:42|         0 Entries scanned
2008/10/10 23:03:42|         0 Invalid entries.
2008/10/10 23:03:42|         0 With invalid flags.
2008/10/10 23:03:42|         0 Objects loaded.
2008/10/10 23:03:42|         0 Objects expired.
2008/10/10 23:03:42|         0 Objects cancelled.
2008/10/10 23:03:42|         0 Duplicate URLs purged.
2008/10/10 23:03:42|         0 Swapfile clashes avoided.
2008/10/10 23:03:42|   Took 0.3 seconds (   0.0 objects/sec).
2008/10/10 23:03:42| Beginning Validation Procedure
2008/10/10 23:03:42|   Completed Validation Procedure
2008/10/10 23:03:42|   Validated 0 Entries
2008/10/10 23:03:42|   store_swap_size = 0k
2008/10/10 23:03:43| storeLateRelease: released 0 objects
2008/10/10 23:04:30| clientReadRequest: FD 12 (192.168.0.12:54031)
Invalid Request
```

---

