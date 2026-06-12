---
title: "Ubuntu 20.04 not getting IPv6 SLAAC address"
date: 2023-08-30
forum: Networking &amp; Wireless
---

### Post by john163 on 2023-08-30
Other hosts on the network are.
v4 stack works just fine.
This laptop does get properly addressed when booted to Windows 10
I do get an fe80 address:

```
joliver@blinky:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether ec:f4:bb:15:41:6b brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.22/24 brd 192.168.0.255 scope global dynamic noprefixroute eno1
       valid_lft 85576sec preferred_lft 85576sec
    inet6 fe80::8be3:2840:4718:3a80/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp2s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether ac:7b:a1:2d:5a:af brd ff:ff:ff:ff:ff:ff
```

ufw is disabled, but there are ip6tables rules:

```
joliver@blinky:~$ sudo ip6tables -L -n --line-numbers
Chain INPUT (policy DROP)
num  target     prot opt source               destination         
1    ACCEPT     all      ::/0                 ::/0                
2    ACCEPT     all      ::/0                 ::/0                 state RELATED,ESTABLISHED
3    LOGGING    all      ::/0                 ::/0                

Chain FORWARD (policy DROP)
num  target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination         

Chain LOGGING (1 references)
num  target     prot opt source               destination         
1    LOG        all      ::/0                 ::/0                 LOG flags 0 level 4 prefix "iptables-fw "
2    DROP       all      ::/0                 ::/0                

```

Not sure whet else might be relevant.

---

### Post by #&amp;thj^% on 2023-08-30
Can you explain the problem, without the Windows 10 in the description. 
Also show me this on Ubuntu
```
less /etc/sysctl.conf | grep net.ipv6

```

---

### Post by john163 on 2023-08-31
> **1fallen said:**
> Can you explain the problem, without the Windows 10 in the description. 

It is not getting a routable IPv6 address.

```

joliver@blinky:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether ec:f4:bb:15:41:6b brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.22/24 brd 192.168.0.255 scope global dynamic noprefixroute eno1
       valid_lft 64347sec preferred_lft 64347sec
    inet6 fe80::eef4:bbff:fe15:416b/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 fe80::8be3:2840:4718:3a80/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```
Also show me this on Ubuntu
```
less /etc/sysctl.conf | grep net.ipv6

```[/QUOTE]

You should probably ask for "sysctl -a | grep ipv6", as catting /etc/sysctl.conf will miss everything in /etc/sysctl.d/

```

net.ipv6.anycast_src_echo_reply = 0
net.ipv6.auto_flowlabels = 1
net.ipv6.bindv6only = 0
net.ipv6.calipso_cache_bucket_size = 10
net.ipv6.calipso_cache_enable = 1
net.ipv6.conf.all.accept_dad = 0
net.ipv6.conf.all.accept_ra = 1
net.ipv6.conf.all.accept_ra_defrtr = 1
net.ipv6.conf.all.accept_ra_from_local = 0
net.ipv6.conf.all.accept_ra_min_hop_limit = 1
net.ipv6.conf.all.accept_ra_mtu = 1
net.ipv6.conf.all.accept_ra_pinfo = 1
net.ipv6.conf.all.accept_ra_rt_info_max_plen = 0
net.ipv6.conf.all.accept_ra_rt_info_min_plen = 0
net.ipv6.conf.all.accept_ra_rtr_pref = 1
net.ipv6.conf.all.accept_redirects = 1
net.ipv6.conf.all.accept_source_route = 0
net.ipv6.conf.all.addr_gen_mode = 0
net.ipv6.conf.all.autoconf = 1
net.ipv6.conf.all.dad_transmits = 1
net.ipv6.conf.all.disable_ipv6 = 0
net.ipv6.conf.all.disable_policy = 0
net.ipv6.conf.all.drop_unicast_in_l2_multicast = 0
net.ipv6.conf.all.drop_unsolicited_na = 0
net.ipv6.conf.all.enhanced_dad = 1
net.ipv6.conf.all.force_mld_version = 0
net.ipv6.conf.all.force_tllao = 0
net.ipv6.conf.all.forwarding = 0
net.ipv6.conf.all.hop_limit = 64
net.ipv6.conf.all.ignore_routes_with_linkdown = 0
net.ipv6.conf.all.keep_addr_on_down = 0
net.ipv6.conf.all.max_addresses = 16
net.ipv6.conf.all.max_desync_factor = 600
net.ipv6.conf.all.mc_forwarding = 0
net.ipv6.conf.all.mldv1_unsolicited_report_interval = 10000
net.ipv6.conf.all.mldv2_unsolicited_report_interval = 1000
net.ipv6.conf.all.mtu = 1280
net.ipv6.conf.all.ndisc_notify = 0
net.ipv6.conf.all.ndisc_tclass = 0
net.ipv6.conf.all.proxy_ndp = 0
net.ipv6.conf.all.regen_max_retry = 3
net.ipv6.conf.all.router_probe_interval = 60
net.ipv6.conf.all.router_solicitation_delay = 1
net.ipv6.conf.all.router_solicitation_interval = 4
net.ipv6.conf.all.router_solicitation_max_interval = 3600
net.ipv6.conf.all.router_solicitations = -1
net.ipv6.conf.all.seg6_enabled = 0
net.ipv6.conf.all.seg6_require_hmac = 0
sysctl: permission denied on key 'net.ipv6.conf.default.stable_secret'
net.ipv6.conf.all.suppress_frag_ndisc = 1
net.ipv6.conf.all.temp_prefered_lft = 86400
net.ipv6.conf.all.temp_valid_lft = 604800
net.ipv6.conf.all.use_oif_addrs_only = 0
net.ipv6.conf.all.use_tempaddr = 2
net.ipv6.conf.default.accept_dad = 1
net.ipv6.conf.default.accept_ra = 1
net.ipv6.conf.default.accept_ra_defrtr = 1
net.ipv6.conf.default.accept_ra_from_local = 0
net.ipv6.conf.default.accept_ra_min_hop_limit = 1
net.ipv6.conf.default.accept_ra_mtu = 1
net.ipv6.conf.default.accept_ra_pinfo = 1
net.ipv6.conf.default.accept_ra_rt_info_max_plen = 0
net.ipv6.conf.default.accept_ra_rt_info_min_plen = 0
net.ipv6.conf.default.accept_ra_rtr_pref = 1
net.ipv6.conf.default.accept_redirects = 1
net.ipv6.conf.default.accept_source_route = 0
net.ipv6.conf.default.addr_gen_mode = 0
net.ipv6.conf.default.autoconf = 1
net.ipv6.conf.default.dad_transmits = 1
net.ipv6.conf.default.disable_ipv6 = 0
net.ipv6.conf.default.disable_policy = 0
net.ipv6.conf.default.drop_unicast_in_l2_multicast = 0
net.ipv6.conf.default.drop_unsolicited_na = 0
net.ipv6.conf.default.enhanced_dad = 1
net.ipv6.conf.default.force_mld_version = 0
net.ipv6.conf.default.force_tllao = 0
net.ipv6.conf.default.forwarding = 0
net.ipv6.conf.default.hop_limit = 64
net.ipv6.conf.default.ignore_routes_with_linkdown = 0
net.ipv6.conf.default.keep_addr_on_down = 0
net.ipv6.conf.default.max_addresses = 16
net.ipv6.conf.default.max_desync_factor = 600
net.ipv6.conf.default.mc_forwarding = 0
net.ipv6.conf.default.mldv1_unsolicited_report_interval = 10000
net.ipv6.conf.default.mldv2_unsolicited_report_interval = 1000
net.ipv6.conf.default.mtu = 1280
net.ipv6.conf.default.ndisc_notify = 0
net.ipv6.conf.default.ndisc_tclass = 0
net.ipv6.conf.default.proxy_ndp = 0
net.ipv6.conf.default.regen_max_retry = 3
net.ipv6.conf.default.router_probe_interval = 60
net.ipv6.conf.default.router_solicitation_delay = 1
net.ipv6.conf.default.router_solicitation_interval = 4
net.ipv6.conf.default.router_solicitation_max_interval = 3600
net.ipv6.conf.default.router_solicitations = -1
net.ipv6.conf.default.seg6_enabled = 0
net.ipv6.conf.default.seg6_require_hmac = 0
sysctl: permission denied on key 'net.ipv6.conf.eno1.stable_secret'
net.ipv6.conf.default.suppress_frag_ndisc = 1
net.ipv6.conf.default.temp_prefered_lft = 86400
net.ipv6.conf.default.temp_valid_lft = 604800
net.ipv6.conf.default.use_oif_addrs_only = 0
net.ipv6.conf.default.use_tempaddr = 2
net.ipv6.conf.eno1.accept_dad = 1
net.ipv6.conf.eno1.accept_ra = 0
net.ipv6.conf.eno1.accept_ra_defrtr = 1
net.ipv6.conf.eno1.accept_ra_from_local = 0
net.ipv6.conf.eno1.accept_ra_min_hop_limit = 1
net.ipv6.conf.eno1.accept_ra_mtu = 1
net.ipv6.conf.eno1.accept_ra_pinfo = 1
net.ipv6.conf.eno1.accept_ra_rt_info_max_plen = 0
net.ipv6.conf.eno1.accept_ra_rt_info_min_plen = 0
net.ipv6.conf.eno1.accept_ra_rtr_pref = 1
net.ipv6.conf.eno1.accept_redirects = 1
net.ipv6.conf.eno1.accept_source_route = 0
net.ipv6.conf.eno1.addr_gen_mode = 0
net.ipv6.conf.eno1.autoconf = 1
net.ipv6.conf.eno1.dad_transmits = 1
net.ipv6.conf.eno1.disable_ipv6 = 0
net.ipv6.conf.eno1.disable_policy = 0
net.ipv6.conf.eno1.drop_unicast_in_l2_multicast = 0
net.ipv6.conf.eno1.drop_unsolicited_na = 0
net.ipv6.conf.eno1.enhanced_dad = 1
net.ipv6.conf.eno1.force_mld_version = 0
net.ipv6.conf.eno1.force_tllao = 0
net.ipv6.conf.eno1.forwarding = 0
net.ipv6.conf.eno1.hop_limit = 64
net.ipv6.conf.eno1.ignore_routes_with_linkdown = 0
net.ipv6.conf.eno1.keep_addr_on_down = 0
net.ipv6.conf.eno1.max_addresses = 16
net.ipv6.conf.eno1.max_desync_factor = 600
net.ipv6.conf.eno1.mc_forwarding = 0
net.ipv6.conf.eno1.mldv1_unsolicited_report_interval = 10000
net.ipv6.conf.eno1.mldv2_unsolicited_report_interval = 1000
net.ipv6.conf.eno1.mtu = 1500
net.ipv6.conf.eno1.ndisc_notify = 0
net.ipv6.conf.eno1.ndisc_tclass = 0
net.ipv6.conf.eno1.proxy_ndp = 0
net.ipv6.conf.eno1.regen_max_retry = 3
net.ipv6.conf.eno1.router_probe_interval = 60
net.ipv6.conf.eno1.router_solicitation_delay = 1
net.ipv6.conf.eno1.router_solicitation_interval = 4
net.ipv6.conf.eno1.router_solicitation_max_interval = 3600
net.ipv6.conf.eno1.router_solicitations = -1
net.ipv6.conf.eno1.seg6_enabled = 0
net.ipv6.conf.eno1.seg6_require_hmac = 0
sysctl: permission denied on key 'net.ipv6.conf.lo.stable_secret'
net.ipv6.conf.eno1.suppress_frag_ndisc = 1
net.ipv6.conf.eno1.temp_prefered_lft = 86400
net.ipv6.conf.eno1.temp_valid_lft = 604800
net.ipv6.conf.eno1.use_oif_addrs_only = 0
net.ipv6.conf.eno1.use_tempaddr = 2
net.ipv6.conf.lo.accept_dad = -1
net.ipv6.conf.lo.accept_ra = 1
net.ipv6.conf.lo.accept_ra_defrtr = 1
net.ipv6.conf.lo.accept_ra_from_local = 0
net.ipv6.conf.lo.accept_ra_min_hop_limit = 1
net.ipv6.conf.lo.accept_ra_mtu = 1
net.ipv6.conf.lo.accept_ra_pinfo = 1
net.ipv6.conf.lo.accept_ra_rt_info_max_plen = 0
net.ipv6.conf.lo.accept_ra_rt_info_min_plen = 0
net.ipv6.conf.lo.accept_ra_rtr_pref = 1
net.ipv6.conf.lo.accept_redirects = 1
net.ipv6.conf.lo.accept_source_route = 0
net.ipv6.conf.lo.addr_gen_mode = 0
net.ipv6.conf.lo.autoconf = 1
net.ipv6.conf.lo.dad_transmits = 1
net.ipv6.conf.lo.disable_ipv6 = 0
net.ipv6.conf.lo.disable_policy = 0
net.ipv6.conf.lo.drop_unicast_in_l2_multicast = 0
net.ipv6.conf.lo.drop_unsolicited_na = 0
net.ipv6.conf.lo.enhanced_dad = 1
net.ipv6.conf.lo.force_mld_version = 0
net.ipv6.conf.lo.force_tllao = 0
net.ipv6.conf.lo.forwarding = 0
net.ipv6.conf.lo.hop_limit = 64
net.ipv6.conf.lo.ignore_routes_with_linkdown = 0
net.ipv6.conf.lo.keep_addr_on_down = 0
net.ipv6.conf.lo.max_addresses = 16
net.ipv6.conf.lo.max_desync_factor = 600
net.ipv6.conf.lo.mc_forwarding = 0
net.ipv6.conf.lo.mldv1_unsolicited_report_interval = 10000
net.ipv6.conf.lo.mldv2_unsolicited_report_interval = 1000
net.ipv6.conf.lo.mtu = 65536
net.ipv6.conf.lo.ndisc_notify = 0
net.ipv6.conf.lo.ndisc_tclass = 0
net.ipv6.conf.lo.proxy_ndp = 0
net.ipv6.conf.lo.regen_max_retry = 3
net.ipv6.conf.lo.router_probe_interval = 60
net.ipv6.conf.lo.router_solicitation_delay = 1
net.ipv6.conf.lo.router_solicitation_interval = 4
net.ipv6.conf.lo.router_solicitation_max_interval = 3600
net.ipv6.conf.lo.router_solicitations = -1
net.ipv6.conf.lo.seg6_enabled = 0
net.ipv6.conf.lo.seg6_require_hmac = 0
sysctl: permission denied on key 'net.ipv6.conf.wlp2s0.stable_secret'
net.ipv6.conf.lo.suppress_frag_ndisc = 1
net.ipv6.conf.lo.temp_prefered_lft = 86400
net.ipv6.conf.lo.temp_valid_lft = 604800
net.ipv6.conf.lo.use_oif_addrs_only = 0
net.ipv6.conf.lo.use_tempaddr = -1
net.ipv6.conf.wlp2s0.accept_dad = 1
net.ipv6.conf.wlp2s0.accept_ra = 0
net.ipv6.conf.wlp2s0.accept_ra_defrtr = 1
net.ipv6.conf.wlp2s0.accept_ra_from_local = 0
net.ipv6.conf.wlp2s0.accept_ra_min_hop_limit = 1
net.ipv6.conf.wlp2s0.accept_ra_mtu = 1
net.ipv6.conf.wlp2s0.accept_ra_pinfo = 1
net.ipv6.conf.wlp2s0.accept_ra_rt_info_max_plen = 0
net.ipv6.conf.wlp2s0.accept_ra_rt_info_min_plen = 0
net.ipv6.conf.wlp2s0.accept_ra_rtr_pref = 1
net.ipv6.conf.wlp2s0.accept_redirects = 1
net.ipv6.conf.wlp2s0.accept_source_route = 0
net.ipv6.conf.wlp2s0.addr_gen_mode = 1
net.ipv6.conf.wlp2s0.autoconf = 1
net.ipv6.conf.wlp2s0.dad_transmits = 1
net.ipv6.conf.wlp2s0.disable_ipv6 = 0
net.ipv6.conf.wlp2s0.disable_policy = 0
net.ipv6.conf.wlp2s0.drop_unicast_in_l2_multicast = 0
net.ipv6.conf.wlp2s0.drop_unsolicited_na = 0
net.ipv6.conf.wlp2s0.enhanced_dad = 1
net.ipv6.conf.wlp2s0.force_mld_version = 0
net.ipv6.conf.wlp2s0.force_tllao = 0
net.ipv6.conf.wlp2s0.forwarding = 0
net.ipv6.conf.wlp2s0.hop_limit = 64
net.ipv6.conf.wlp2s0.ignore_routes_with_linkdown = 0
net.ipv6.conf.wlp2s0.keep_addr_on_down = 0
net.ipv6.conf.wlp2s0.max_addresses = 16
net.ipv6.conf.wlp2s0.max_desync_factor = 600
net.ipv6.conf.wlp2s0.mc_forwarding = 0
net.ipv6.conf.wlp2s0.mldv1_unsolicited_report_interval = 10000
net.ipv6.conf.wlp2s0.mldv2_unsolicited_report_interval = 1000
net.ipv6.conf.wlp2s0.mtu = 1500
net.ipv6.conf.wlp2s0.ndisc_notify = 0
net.ipv6.conf.wlp2s0.ndisc_tclass = 0
net.ipv6.conf.wlp2s0.proxy_ndp = 0
net.ipv6.conf.wlp2s0.regen_max_retry = 3
net.ipv6.conf.wlp2s0.router_probe_interval = 60
net.ipv6.conf.wlp2s0.router_solicitation_delay = 1
net.ipv6.conf.wlp2s0.router_solicitation_interval = 4
net.ipv6.conf.wlp2s0.router_solicitation_max_interval = 3600
net.ipv6.conf.wlp2s0.router_solicitations = -1
net.ipv6.conf.wlp2s0.seg6_enabled = 0
net.ipv6.conf.wlp2s0.seg6_require_hmac = 0
net.ipv6.conf.wlp2s0.suppress_frag_ndisc = 1
net.ipv6.conf.wlp2s0.temp_prefered_lft = 86400
net.ipv6.conf.wlp2s0.temp_valid_lft = 604800
net.ipv6.conf.wlp2s0.use_oif_addrs_only = 0
net.ipv6.conf.wlp2s0.use_tempaddr = 0
net.ipv6.fib_multipath_hash_policy = 0
net.ipv6.flowlabel_consistency = 1
net.ipv6.flowlabel_reflect = 0
net.ipv6.flowlabel_state_ranges = 0
net.ipv6.fwmark_reflect = 0
net.ipv6.icmp.echo_ignore_all = 0
net.ipv6.icmp.echo_ignore_anycast = 0
net.ipv6.icmp.echo_ignore_multicast = 0
net.ipv6.icmp.ratelimit = 1000
net.ipv6.icmp.ratemask = 0-1,3-127
net.ipv6.idgen_delay = 1
net.ipv6.idgen_retries = 3
net.ipv6.ip6frag_high_thresh = 4194304
net.ipv6.ip6frag_low_thresh = 3145728
net.ipv6.ip6frag_secret_interval = 0
net.ipv6.ip6frag_time = 60
net.ipv6.ip_nonlocal_bind = 0
net.ipv6.max_dst_opts_length = 2147483647
net.ipv6.max_dst_opts_number = 8
net.ipv6.max_hbh_length = 2147483647
net.ipv6.max_hbh_opts_number = 8
net.ipv6.mld_max_msf = 64
net.ipv6.mld_qrv = 2
net.ipv6.neigh.default.anycast_delay = 100
net.ipv6.neigh.default.app_solicit = 0
net.ipv6.neigh.default.base_reachable_time_ms = 30000
net.ipv6.neigh.default.delay_first_probe_time = 5
net.ipv6.neigh.default.gc_interval = 30
net.ipv6.neigh.default.gc_stale_time = 60
net.ipv6.neigh.default.gc_thresh1 = 128
net.ipv6.neigh.default.gc_thresh2 = 512
net.ipv6.neigh.default.gc_thresh3 = 1024
net.ipv6.neigh.default.locktime = 0
net.ipv6.neigh.default.mcast_resolicit = 0
net.ipv6.neigh.default.mcast_solicit = 3
net.ipv6.neigh.default.proxy_delay = 80
net.ipv6.neigh.default.proxy_qlen = 64
net.ipv6.neigh.default.retrans_time_ms = 1000
net.ipv6.neigh.default.ucast_solicit = 3
net.ipv6.neigh.default.unres_qlen = 101
net.ipv6.neigh.default.unres_qlen_bytes = 212992
net.ipv6.neigh.eno1.anycast_delay = 100
net.ipv6.neigh.eno1.app_solicit = 0
net.ipv6.neigh.eno1.base_reachable_time_ms = 30000
net.ipv6.neigh.eno1.delay_first_probe_time = 5
net.ipv6.neigh.eno1.gc_stale_time = 60
net.ipv6.neigh.eno1.locktime = 0
net.ipv6.neigh.eno1.mcast_resolicit = 0
net.ipv6.neigh.eno1.mcast_solicit = 3
net.ipv6.neigh.eno1.proxy_delay = 80
net.ipv6.neigh.eno1.proxy_qlen = 64
net.ipv6.neigh.eno1.retrans_time_ms = 1000
net.ipv6.neigh.eno1.ucast_solicit = 3
net.ipv6.neigh.eno1.unres_qlen = 101
net.ipv6.neigh.eno1.unres_qlen_bytes = 212992
net.ipv6.neigh.lo.anycast_delay = 100
net.ipv6.neigh.lo.app_solicit = 0
net.ipv6.neigh.lo.base_reachable_time_ms = 30000
net.ipv6.neigh.lo.delay_first_probe_time = 5
net.ipv6.neigh.lo.gc_stale_time = 60
net.ipv6.neigh.lo.locktime = 0
net.ipv6.neigh.lo.mcast_resolicit = 0
net.ipv6.neigh.lo.mcast_solicit = 3
net.ipv6.neigh.lo.proxy_delay = 80
net.ipv6.neigh.lo.proxy_qlen = 64
net.ipv6.neigh.lo.retrans_time_ms = 1000
net.ipv6.neigh.lo.ucast_solicit = 3
net.ipv6.neigh.lo.unres_qlen = 101
net.ipv6.neigh.lo.unres_qlen_bytes = 212992
net.ipv6.neigh.wlp2s0.anycast_delay = 100
net.ipv6.neigh.wlp2s0.app_solicit = 0
net.ipv6.neigh.wlp2s0.base_reachable_time_ms = 30000
net.ipv6.neigh.wlp2s0.delay_first_probe_time = 5
net.ipv6.neigh.wlp2s0.gc_stale_time = 60
net.ipv6.neigh.wlp2s0.locktime = 0
net.ipv6.neigh.wlp2s0.mcast_resolicit = 0
net.ipv6.neigh.wlp2s0.mcast_solicit = 3
net.ipv6.neigh.wlp2s0.proxy_delay = 80
net.ipv6.neigh.wlp2s0.proxy_qlen = 64
net.ipv6.neigh.wlp2s0.retrans_time_ms = 1000
net.ipv6.neigh.wlp2s0.ucast_solicit = 3
net.ipv6.neigh.wlp2s0.unres_qlen = 101
net.ipv6.neigh.wlp2s0.unres_qlen_bytes = 212992
net.ipv6.route.gc_elasticity = 9
net.ipv6.route.gc_interval = 30
net.ipv6.route.gc_min_interval = 0
net.ipv6.route.gc_min_interval_ms = 500
net.ipv6.route.gc_thresh = 1024
net.ipv6.route.gc_timeout = 60
net.ipv6.route.max_size = 4096
net.ipv6.route.min_adv_mss = 1220
net.ipv6.route.mtu_expires = 600
net.ipv6.route.skip_notify_on_dev_down = 0
net.ipv6.seg6_flowlabel = 0
net.ipv6.xfrm6_gc_thresh = 32768

```

---

### Post by #&amp;thj^% on 2023-08-31
> **john163 said:**
> 

You should probably ask for "sysctl -a | grep ipv6", as catting /etc/sysctl.conf will miss everything in /etc/sysctl.d/


Thanks for your view, I'm pretty sure I knew what 'I' wanted to see. ;)

Installing IPv6 on Ubuntu 20.04: [https://blog.eldernode.com/install-configure-ipv6-on-ubuntu-20-04/](https://blog.eldernode.com/install-configure-ipv6-on-ubuntu-20-04/)

---

