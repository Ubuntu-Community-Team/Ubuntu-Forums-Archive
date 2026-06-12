---
title: "UFW broken"
date: 2018-09-20
forum: Networking &amp; Wireless
---

### Post by dylshe on 2018-09-20
I have UFW set up as a 'kill switch' for my VPN.  It has been set up in the same way for years without any problems, until yesterday, I can no longer connect to the Internet when it is on. I have checked the IP address range of the VPN and they have not changed. I am unsure why this all of a sudden no longer works, any help would be appreciated.

UFW is set up in the following way:
```

root@the-computer:/home/myHome# ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), deny (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
Anywhere                   ALLOW IN    10.10.10.66/10.10.10.99

Anywhere                   ALLOW OUT   Anywhere on tun0                         
10.10.10.66/10.10.10.99  ALLOW OUT   Anywhere                  
1194/udp                   ALLOW OUT   Anywhere                  
Anywhere (v6)              ALLOW OUT   Anywhere (v6) on tun0     
1194/udp (v6)              ALLOW OUT   Anywhere (v6)    

```


The output of my logs are:
```

root@the-computer:/home/myHome# tail -f /var/log/ufw.log
Sep 21 12:54:09 the-computer kernel: [235285.172748] [UFW BLOCK] IN=eno1 OUT= MAC=00:00:00 SRC=10.10.10.91 DST=192.168.2.1 LEN=124 TOS=0x00 PREC=0x00 TTL=55 ID=11216 DF PROTO=UDP SPT=443 DPT=54296 LEN=104
Sep 21 12:54:09 the-computer kernel: [235285.186354] [UFW BLOCK] IN=eno1 OUT= MAC=00:00:00 SRC=10.10.10.91 DST=192.168.2.1 LEN=124 TOS=0x00 PREC=0x00 TTL=55 ID=11217 DF PROTO=UDP SPT=443 DPT=54296 LEN=104
Sep 21 12:54:10 the-computer kernel: [235285.387283] [UFW BLOCK] IN=eno1 OUT= MAC=00:00:00 SRC=10.10.10.91 DST=192.168.2.1 LEN=188 TOS=0x00 PREC=0x00 TTL=55 ID=11218 DF PROTO=UDP SPT=443 DPT=54296 LEN=168
Sep 21 12:54:19 the-computer kernel: [235295.073669] [UFW BLOCK] IN= OUT=eno1 SRC=192.168.2.1 DST=10.10.10.91 LEN=116 TOS=0x00 PREC=0x00 TTL=64 ID=11767 DF PROTO=UDP SPT=60794 DPT=443 LEN=96

```

---

