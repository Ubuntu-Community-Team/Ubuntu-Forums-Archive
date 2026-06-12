---
title: "No more IPV6 after upgrading to Jammy."
date: 2022-10-24
forum: Networking &amp; Wireless
---

### Post by georgesgiralt on 2022-10-24
Hello,
I've a laptop which was running 20.04LTS. 
I could use the following command on it : 
```
$ ping6 freebox.local
PING freebox.local(xxxx:xxxx:xxx:xxxx::1 (xxxx:xxxx:xxx:xxxx::1)) 56 data bytes
64*octets de xxxx:xxxx:xxx:xxxx::1 (xxxx:xxxx:xxx:xxxx::1)*: icmp_seq=1 ttl=64 temps=1.19*ms
.............
```
where freebox.local is my ISP router. 
After going to Jammy, I get : 
```
ping6 freebox.local
ping6: freebox.local: Address family for hostname not supported

```
If I use another computer, I can ping the offender using ping6 so it has and use IPV6 (and register an IPV6 address on mDNS)... 
So I'm puzzled, and would be delighted to get some answers and help ! 
Thanks for that !
P.S. : that computer register itself on mDNS as <hostname>-2 since the very same upgrade.

---

