---
title: "Problem with WCCPV2 redirection and squid 2.6"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by rrogier on 2007-05-10
I am attempting to configure squid2.6STABLE to do transparent caching using WCCP.  I am running Ubuntu Server 7.04 with all patches.  I have setup squid by reading multiple documents on the Internet.  I have created a GRE tunnel interface pointing to my router.  I have created two tunnels.  The first tunnel is created between the eth1 interface on the server and the inside ip on the router.  The second was done by creating an interface called gre1 on the server and assigning an IP to it.  When I bring this interface up it can be pinged.  I then created a gre tunnel between that interface and the router.  I can start squid and the cache.log file shows as follows:
2007/05/10 15:35:44| Starting Squid Cache version 2.6.STABLE5 for i386-debian-linux-gnu...
2007/05/10 15:35:44| Process ID 6656
2007/05/10 15:35:44| With 1024 file descriptors available
2007/05/10 15:35:44| Using epoll for the IO loop
2007/05/10 15:35:44| DNS Socket created at 0.0.0.0, port 32783, FD 6
2007/05/10 15:35:44| Adding nameserver 4.4.4.2 from squid.conf
2007/05/10 15:35:44| Adding nameserver 4.4.4.1 from squid.conf
2007/05/10 15:35:44| Adding nameserver 4.4.4.3 from squid.conf
2007/05/10 15:35:44| Adding nameserver 192.168.4.15 from squid.conf
2007/05/10 15:35:44| Adding nameserver 192.168.4.17 from squid.conf
2007/05/10 15:35:44| User-Agent logging is disabled.
2007/05/10 15:35:44| Referer logging is disabled.
2007/05/10 15:35:44| Swap maxSize 102400 KB, estimated 7876 objects
2007/05/10 15:35:44| Target number of buckets: 393
2007/05/10 15:35:44| Using 8192 Store buckets
2007/05/10 15:35:44| Max Mem  size: 32768 KB
2007/05/10 15:35:44| Max Swap size: 102400 KB
2007/05/10 15:35:44| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
2007/05/10 15:35:44| Rebuilding storage in /var/spool/squid (CLEAN)
2007/05/10 15:35:44| Using Least Load store dir selection
2007/05/10 15:35:44| Current Directory is /
2007/05/10 15:35:44| Loaded Icons.
2007/05/10 15:35:44| Accepting transparently proxied HTTP connections at 0.0.0.0, port 3128, FD 13.
2007/05/10 15:35:44| Accepting ICP messages at 0.0.0.0, port 3130, FD 14.
2007/05/10 15:35:44| Accepting HTCP messages on port 4827, FD 15.
2007/05/10 15:35:44| WCCP Disabled.
2007/05/10 15:35:44| Accepting WCCPv2 messages on port 2048, FD 16.
2007/05/10 15:35:44| Initialising all WCCPv2 lists
2007/05/10 15:35:44| Ready to serve requests.
2007/05/10 15:35:44| Done reading /var/spool/squid swaplog (32 entries)
2007/05/10 15:35:44| Finished rebuilding storage from disk.
2007/05/10 15:35:44|        32 Entries scanned
2007/05/10 15:35:44|         0 Invalid entries.
2007/05/10 15:35:44|         0 With invalid flags.
2007/05/10 15:35:44|        32 Objects loaded.
2007/05/10 15:35:44|         0 Objects expired.
2007/05/10 15:35:44|         0 Objects cancelled.
2007/05/10 15:35:44|         0 Duplicate URLs purged.
2007/05/10 15:35:44|         0 Swapfile clashes avoided.
2007/05/10 15:35:44|   Took 0.0 seconds ( 675.8 objects/sec).
2007/05/10 15:35:44| Beginning Validation Procedure
2007/05/10 15:35:44|   Completed Validation Procedure
2007/05/10 15:35:44|   Validated 32 Entries
2007/05/10 15:35:44|   store_swap_size = 552k
2007/05/10 15:35:45| storeLateRelease: released 0 objects
2007/05/10 17:08:56| Preparing for shutdown after 0 requests

As you can see the  proxy is listening for WCCP V2 packets.  When I enable WCCP on the router, the proxy registers with it and packets are being redirected correctly.  However, I never get a response and the access.log doesn't show any requests coming to it.  I did try just pointing my browser to squid as a proxy server and it worked.  The access.log increments correctly and the proxy caches objects to the disk as it should.    I have attached my current squid.conf file for review.  I edited a few items out to "protect the innocent."

Hopefully someone out there has experience with this and can help me out.  Thank you.

---

