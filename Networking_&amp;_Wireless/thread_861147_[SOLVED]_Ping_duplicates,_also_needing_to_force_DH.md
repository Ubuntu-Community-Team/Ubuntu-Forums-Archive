---
title: "[SOLVED] Ping duplicates, also needing to force DHCP request"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by vree13 on 2008-07-16
I am running 8.04 and am having a couple strange problems with networking and I'm hoping someone can help out. I was trying to get Nagios up and running but kept getting duplicate ping response messages, but after investigating further, it's not a problem with the program, my machine does it at the command line.

```
64 bytes from 10.1.xxx.x: icmp_seq=1 ttl=254 time=1.82 ms
64 bytes from 10.1.xxx.x: icmp_seq=1 ttl=254 time=2.17 ms (DUP!)
64 bytes from 10.1.xxx.x: icmp_seq=1 ttl=254 time=2.52 ms (DUP!)

--- 10.1.xxx.x ping statistics ---
1 packets transmitted, 1 received, +2 duplicates, 0% packet loss, time 0ms
```

I've tried this on another connection on a different switch, my friend who is also running 8.04 can ping the same address and doesn't get duplicate ping responses when plugged into the same switch I was previously plugged into. I've tried a different NIC, which does the same thing. I've tried turning off IPv6, no change. I'd rather not have to reinstall Ubuntu to see if it's just something messed up... I'm afraid I would still have the same problem! Any ideas? 


Also, after trying to get this fixed, my machine doesn't automatically request an IP address, I have to run dhclient -1 to get it to request one and it comes back fine. Any thoughts on how I messed that up and how I can have it request an address on boot? Thanks!

edit: I wanted to clarify that the duplicate ping issue is across the board for any of the IP addresses that I ping, not just one specific address, so this is not a problem with duplicate hosts replying.

---

### Post by vree13 on 2008-07-18
After a fresh format and install the DHCP issue is resolved however the duplicate ping problem is not. 

After a lot of digging, I found that [oping ]("http://packages.ubuntu.com/hardy/net/oping")returned no duplicates but [fping]("http://packages.ubuntu.com/hardy/fping") did return duplicates just like the ping command. After looking further at Nagios, I switched all check_ping command references to check_icmp and that, for some reason, does not return duplicates. This doesn't solve the actual problem but lets me operate Nagios without getting the PING WARNING - DUPLICATES FOUND! error in the log.

---

