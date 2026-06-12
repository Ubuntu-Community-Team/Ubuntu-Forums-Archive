---
title: "DNS issue"
date: 2023-10-05
forum: Networking &amp; Wireless
---

### Post by cygnia2 on 2023-10-05
Hi,

I'm running into some DNS issues on Ubuntu 22.04.3 LTS. I tried to set up a static IP and ran into these DNS issues, but then i thought I solved them by setting up the IP on my router instead of the machine. I'm new to linux so any help is appreciated.  

```
$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=60 time=18.4 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=60 time=9.16 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=60 time=8.38 ms
^C
--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 8.376/11.979/18.399/4.550 ms
$ ping google.com
ping: google.com: Temporary failure in name resolution
```

This is the contents of `/etc/resolv.conf`

```
$ cat /etc/resolv.conf
# This is /run/systemd/resolve/stub-resolv.conf managed by man:systemd-resolved(8)
# Do not edit.
#
# This file might be symlinked as /etc/resolv.conf. If you're looking at
# /etc/resolv.conf and seeing this text, you have followed the symlink. 
#                                                                                                                    
# This is a dynamic resolv.conf file for connecting local clients to the                                             
# internal DNS stub resolver of systemd-resolved. This file lists all                                                
# configured search domains.                                                                                         
#                                                                                                                    
# Run "resolvectl status" to see details about the uplink DNS servers                                                
# currently in use.                                                                                                  
#                                                                                                                    
# Third party programs should typically not access this file directly, but only                                      
# through the symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a                                         
# different way, replace this symlink by a static file or a different symlink.                                       
#                                                                                                                    
# See man:systemd-resolved.service(8) for details about the supported modes of                                       
# operation for /etc/resolv.conf.                                                                                                                                                                                                         
nameserver 127.0.0.53                                                                                                
options edns0 trust-ad                                                                                               
search .  
```

---

### Post by TheFu on 2023-10-07
I've had issues with systemd-resolved too.  Because I run a pair of local LAN DNS that will also do upstream lookups, I don't need a local caching DNS on every system.

In short, I disable and mask systemd-resolved, then delete the symlink for  /etc/resolv.conf and manually create a normal  /etc/resolv.conf that points at my DNSes.  Because **sudo** is tied into DNS resolution, I actually create the new resolv.conf first under a different filename and pre-create the delete and mv on a single command line. If there's too much time between the deletions and replacement, it is possible to be locked out of sudo. That's bad.

Also, since I don't use AD or mDNS, I remove those from the resolv.conf and nsswitch.conf, but your needs could be different. Only you know.

---

