---
title: "Keepalived not masquerading"
date: 2018-12-17
forum: Networking &amp; Wireless
---

### Post by fayelund on 2018-12-17
I have tried to set up keepalived following multiple guides online. Unfortunately I really struggle to get masquerading to work.
The server has mutliple interfaces(front end, back end and management)
When sending traffic from the front end network the packet is forwarded to the back end network without any masquerading happening. (I have applied iptables rule to masquerade everything going out on the backend interface) 
When sending traffic from outside the front end network the packet is not forwarded at all.

Iptables is set to accept for all. When checking counters for the masquerading rule it states that it is used on the packets.

Running Ubuntu server 18.04.1 LTS

After over a week of troubleshooting and reverting im at the point of giving up :(

Here is my keepalived conf:
```
global_defs {
        enable_script_security
        }
vrrp_sync_group main {
        group {
                VS_EXT
                VS_INT
                }
        }
vrrp_instance VS_EXT {
        interface ens224
        virtual_router_id 201
        priority 255
        advert_int 1
        authentication {
                auth_type PASS
                auth_pass XXXXXX
                }
        virtual_ipaddress {
                192.168.9.60 dev ens224 label ens224:1
                }
        }
vrrp_instance VS_INT {
        interface ens256
        virtual_router_id 202
        priority 255
        advert_int 1
        authentication {
                auth_type PASS
                auth_pass XXXXXX
                }
        virtual_ipaddress {
                192.168.11.254 dev ens256 label ens256:1
                }
        }
virtual_server 192.168.9.60 514 {
        delay_loop 5
        lb_algo rr
        lb_kind NAT
        persistence_timeout 60
        protocol UDP
        real_server 192.168.11.41 5140 {
                }
        }
virtual_server 192.168.9.60 80 {
        delay_loop 5
        lb_algo rr
        lb_kind NAT
        persistence_timeout 60
        protocol TCP
        real_server 192.168.11.41 5601 {
                }

        }

```

---

