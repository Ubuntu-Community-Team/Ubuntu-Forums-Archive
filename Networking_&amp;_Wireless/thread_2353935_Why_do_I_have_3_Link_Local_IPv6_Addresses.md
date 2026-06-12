---
title: "Why do I have 3 Link Local IPv6 Addresses?"
date: 2017-02-26
forum: Networking &amp; Wireless
---

### Post by uRock on 2017-02-26
Hi all,
I am studying for my next Cisco certification and while going over IPv6 addressing I ran **ifconfig** and found that my interface has three IPv6 addresses.

Does anyone know why?

Thanks,
uRock

```
wlp3s0    Link encap:Ethernet  HWaddr xxxx.xxxx.xxxx
          inet addr:10.1.1.1  Bcast:10.255.255.255  Mask:255.0.0.0
          [B]inet6 addr: fe80::58ba:19bd:44b3:c2f3/64 Scope:Link
          inet6 addr: fe80::d2c6:36f:cb35:a6cf/64 Scope:Link
          inet6 addr: fe80::5ace:e809:7ab6:68bc/64 Scope:Link[/B]
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:110980129 (110.9 TB)  TX bytes:5714380 (5.7 TB)

```

---

### Post by uRock on 2017-02-28
Took the time to RTM here [https://wiki.ubuntu.com/IPv6](https://wiki.ubuntu.com/IPv6), but not seeing any info on this.

I have read that Microsoft uses a hashing algorithm to conceal the MAC address and am wondering if ubuntu uses multiple algorithms.

I am sure the reason is something simple, but can't find any documentation to explain it.

---

### Post by #&amp;thj^% on 2017-03-02
The way I was "told" or lead to belive was the address containing "fe80::58ba:19bd:44b3:c2f3" is an automatically configured address based on your Ethernet MAC address. You can recognize them because they contain ...ff:fe... in the middle of the last 64 bits. The rest of the bits is derived from your MAC address. Compare:

**fe80::58ba:19bd:44b3:c2f3**

with

**fe80::d2c6:36f:cb35:a6cf**

another tool to see IPv6 addresses is

```
ip -6 addr
```
Mine Shows:
```
$ ip -6 addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 state UNKNOWN qlen 1
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 state UP qlen 1000
    inet6 fe80::ec8d:46b0:90b3:d875/64 scope link 
       valid_lft forever preferred_lft forever
4: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 state UNKNOWN qlen 100
    inet6 fe80::fe16:77a4:c3d0:a80d/64 scope link flags 800 
       valid_lft forever preferred_lft forever

```

It will show you a bit more detail. You will see the word temporary after the privacy address, which indicates what it is. Or even "forever"
Or even this:
```
sysctl -a | grep ipv6
```
Mine Shows:
```
$ sysctl -a | grep ipv6
sysctl: permission denied on key 'fs.protected_hardlinks'
sysctl: permission denied on key 'fs.protected_symlinks'
sysctl: permission denied on key 'kernel.cad_pid'
sysctl: permission denied on key 'kernel.usermodehelper.bset'
sysctl: permission denied on key 'kernel.usermodehelper.inheritable'
sysctl: permission denied on key 'net.core.bpf_jit_harden'
sysctl: permission denied on key 'net.ipv4.tcp_fastopen_key'
sysctl: permission denied on key 'net.ipv6.conf.all.stable_secret'
net.ipv6.anycast_src_echo_reply = 0
net.ipv6.auto_flowlabels = 1
net.ipv6.bindv6only = 0
net.ipv6.calipso_cache_bucket_size = 10
net.ipv6.calipso_cache_enable = 1
net.ipv6.conf.all.accept_dad = 1
net.ipv6.conf.all.accept_ra = 1
net.ipv6.conf.all.accept_ra_defrtr = 1
net.ipv6.conf.all.accept_ra_from_local = 0
net.ipv6.conf.all.accept_ra_min_hop_limit = 1
net.ipv6.conf.all.accept_ra_mtu = 1
net.ipv6.conf.all.accept_ra_pinfo = 1
net.ipv6.conf.all.accept_ra_rt_info_max_plen = 0
net.ipv6.conf.all.accept_ra_rtr_pref = 1
net.ipv6.conf.all.accept_redirects = 0
net.ipv6.conf.all.accept_source_route = 0
net.ipv6.conf.all.autoconf = 1
net.ipv6.conf.all.dad_transmits = 1
net.ipv6.conf.all.disable_ipv6 = 0
net.ipv6.conf.all.drop_unicast_in_l2_multicast = 0
net.ipv6.conf.all.drop_unsolicited_na = 0
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
net.ipv6.conf.all.optimistic_dad = 0
net.ipv6.conf.all.proxy_ndp = 0
net.ipv6.conf.all.regen_max_retry = 3
net.ipv6.conf.all.router_probe_interval = 60
net.ipv6.conf.all.router_solicitation_delay = 1
net.ipv6.conf.all.router_solicitation_interval = 4
net.ipv6.conf.all.router_solicitation_max_interval = 3600
net.ipv6.conf.all.router_solicitations = -1
sysctl: permission denied on key 'net.ipv6.conf.default.stable_secret'
net.ipv6.conf.all.suppress_frag_ndisc = 1
net.ipv6.conf.all.temp_prefered_lft = 86400
net.ipv6.conf.all.temp_valid_lft = 604800
net.ipv6.conf.all.use_oif_addrs_only = 0
net.ipv6.conf.all.use_optimistic = 0
net.ipv6.conf.all.use_tempaddr = 0
net.ipv6.conf.default.accept_dad = 1
net.ipv6.conf.default.accept_ra = 1
net.ipv6.conf.default.accept_ra_defrtr = 1
net.ipv6.conf.default.accept_ra_from_local = 0
net.ipv6.conf.default.accept_ra_min_hop_limit = 1
net.ipv6.conf.default.accept_ra_mtu = 1
net.ipv6.conf.default.accept_ra_pinfo = 1
net.ipv6.conf.default.accept_ra_rt_info_max_plen = 0
net.ipv6.conf.default.accept_ra_rtr_pref = 1
net.ipv6.conf.default.accept_redirects = 0
net.ipv6.conf.default.accept_source_route = 0
net.ipv6.conf.default.autoconf = 1
net.ipv6.conf.default.dad_transmits = 1
net.ipv6.conf.default.disable_ipv6 = 0
net.ipv6.conf.default.drop_unicast_in_l2_multicast = 0
net.ipv6.conf.default.drop_unsolicited_na = 0
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
net.ipv6.conf.default.optimistic_dad = 0
net.ipv6.conf.default.proxy_ndp = 0
net.ipv6.conf.default.regen_max_retry = 3
net.ipv6.conf.default.router_probe_interval = 60
net.ipv6.conf.default.router_solicitation_delay = 1
net.ipv6.conf.default.router_solicitation_interval = 4
net.ipv6.conf.default.router_solicitation_max_interval = 3600
net.ipv6.conf.default.router_solicitations = -1
sysctl: permission denied on key 'net.ipv6.conf.enp4s0.stable_secret'
net.ipv6.conf.default.suppress_frag_ndisc = 1
net.ipv6.conf.default.temp_prefered_lft = 86400
net.ipv6.conf.default.temp_valid_lft = 604800
net.ipv6.conf.default.use_oif_addrs_only = 0
net.ipv6.conf.default.use_optimistic = 0
net.ipv6.conf.default.use_tempaddr = 0
net.ipv6.conf.enp4s0.accept_dad = 1
net.ipv6.conf.enp4s0.accept_ra = 1
net.ipv6.conf.enp4s0.accept_ra_defrtr = 0
net.ipv6.conf.enp4s0.accept_ra_from_local = 0
net.ipv6.conf.enp4s0.accept_ra_min_hop_limit = 1
net.ipv6.conf.enp4s0.accept_ra_mtu = 1
net.ipv6.conf.enp4s0.accept_ra_pinfo = 0
net.ipv6.conf.enp4s0.accept_ra_rt_info_max_plen = 0
net.ipv6.conf.enp4s0.accept_ra_rtr_pref = 0
net.ipv6.conf.enp4s0.accept_redirects = 1
net.ipv6.conf.enp4s0.accept_source_route = 0
net.ipv6.conf.enp4s0.autoconf = 1
net.ipv6.conf.enp4s0.dad_transmits = 1
net.ipv6.conf.enp4s0.disable_ipv6 = 0
net.ipv6.conf.enp4s0.drop_unicast_in_l2_multicast = 0
net.ipv6.conf.enp4s0.drop_unsolicited_na = 0
net.ipv6.conf.enp4s0.force_mld_version = 0
net.ipv6.conf.enp4s0.force_tllao = 0
net.ipv6.conf.enp4s0.forwarding = 0
net.ipv6.conf.enp4s0.hop_limit = 64
net.ipv6.conf.enp4s0.ignore_routes_with_linkdown = 0
net.ipv6.conf.enp4s0.keep_addr_on_down = 0
net.ipv6.conf.enp4s0.max_addresses = 16
net.ipv6.conf.enp4s0.max_desync_factor = 600
net.ipv6.conf.enp4s0.mc_forwarding = 0
net.ipv6.conf.enp4s0.mldv1_unsolicited_report_interval = 10000
net.ipv6.conf.enp4s0.mldv2_unsolicited_report_interval = 1000
net.ipv6.conf.enp4s0.mtu = 1500
net.ipv6.conf.enp4s0.ndisc_notify = 0
net.ipv6.conf.enp4s0.optimistic_dad = 0
net.ipv6.conf.enp4s0.proxy_ndp = 0
net.ipv6.conf.enp4s0.regen_max_retry = 3
net.ipv6.conf.enp4s0.router_probe_interval = 60
net.ipv6.conf.enp4s0.router_solicitation_delay = 1
net.ipv6.conf.enp4s0.router_solicitation_interval = 4
net.ipv6.conf.enp4s0.router_solicitation_max_interval = 3600
net.ipv6.conf.enp4s0.router_solicitations = -1
sysctl: permission denied on key 'net.ipv6.conf.lo.stable_secret'
net.ipv6.conf.enp4s0.suppress_frag_ndisc = 1
net.ipv6.conf.enp4s0.temp_prefered_lft = 86400
net.ipv6.conf.enp4s0.temp_valid_lft = 604800
net.ipv6.conf.enp4s0.use_oif_addrs_only = 0
net.ipv6.conf.enp4s0.use_optimistic = 0
net.ipv6.conf.enp4s0.use_tempaddr = 0
net.ipv6.conf.lo.accept_dad = -1
net.ipv6.conf.lo.accept_ra = 1
net.ipv6.conf.lo.accept_ra_defrtr = 1
net.ipv6.conf.lo.accept_ra_from_local = 0
net.ipv6.conf.lo.accept_ra_min_hop_limit = 1
net.ipv6.conf.lo.accept_ra_mtu = 1
net.ipv6.conf.lo.accept_ra_pinfo = 1
net.ipv6.conf.lo.accept_ra_rt_info_max_plen = 0
net.ipv6.conf.lo.accept_ra_rtr_pref = 1
net.ipv6.conf.lo.accept_redirects = 1
net.ipv6.conf.lo.accept_source_route = 0
net.ipv6.conf.lo.autoconf = 1
net.ipv6.conf.lo.dad_transmits = 1
net.ipv6.conf.lo.disable_ipv6 = 0
net.ipv6.conf.lo.drop_unicast_in_l2_multicast = 0
net.ipv6.conf.lo.drop_unsolicited_na = 0
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
net.ipv6.conf.lo.optimistic_dad = 0
net.ipv6.conf.lo.proxy_ndp = 0
net.ipv6.conf.lo.regen_max_retry = 3
net.ipv6.conf.lo.router_probe_interval = 60
net.ipv6.conf.lo.router_solicitation_delay = 1
net.ipv6.conf.lo.router_solicitation_interval = 4
net.ipv6.conf.lo.router_solicitation_max_interval = 3600
net.ipv6.conf.lo.router_solicitations = -1
sysctl: permission denied on key 'net.ipv6.conf.tun0.stable_secret'
net.ipv6.conf.lo.suppress_frag_ndisc = 1
net.ipv6.conf.lo.temp_prefered_lft = 86400
net.ipv6.conf.lo.temp_valid_lft = 604800
net.ipv6.conf.lo.use_oif_addrs_only = 0
net.ipv6.conf.lo.use_optimistic = 0
net.ipv6.conf.lo.use_tempaddr = -1
net.ipv6.conf.tun0.accept_dad = -1
net.ipv6.conf.tun0.accept_ra = 1
net.ipv6.conf.tun0.accept_ra_defrtr = 1
net.ipv6.conf.tun0.accept_ra_from_local = 0
net.ipv6.conf.tun0.accept_ra_min_hop_limit = 1
net.ipv6.conf.tun0.accept_ra_mtu = 1
net.ipv6.conf.tun0.accept_ra_pinfo = 1
net.ipv6.conf.tun0.accept_ra_rt_info_max_plen = 0
net.ipv6.conf.tun0.accept_ra_rtr_pref = 1
net.ipv6.conf.tun0.accept_redirects = 1
net.ipv6.conf.tun0.accept_source_route = 0
net.ipv6.conf.tun0.autoconf = 1
net.ipv6.conf.tun0.dad_transmits = 1
net.ipv6.conf.tun0.disable_ipv6 = 0
net.ipv6.conf.tun0.drop_unicast_in_l2_multicast = 0
net.ipv6.conf.tun0.drop_unsolicited_na = 0
net.ipv6.conf.tun0.force_mld_version = 0
net.ipv6.conf.tun0.force_tllao = 0
net.ipv6.conf.tun0.forwarding = 0
net.ipv6.conf.tun0.hop_limit = 64
net.ipv6.conf.tun0.ignore_routes_with_linkdown = 0
net.ipv6.conf.tun0.keep_addr_on_down = 0
net.ipv6.conf.tun0.max_addresses = 16
net.ipv6.conf.tun0.max_desync_factor = 600
net.ipv6.conf.tun0.mc_forwarding = 0
net.ipv6.conf.tun0.mldv1_unsolicited_report_interval = 10000
net.ipv6.conf.tun0.mldv2_unsolicited_report_interval = 1000
net.ipv6.conf.tun0.mtu = 1500
net.ipv6.conf.tun0.ndisc_notify = 0
net.ipv6.conf.tun0.optimistic_dad = 0
net.ipv6.conf.tun0.proxy_ndp = 0
net.ipv6.conf.tun0.regen_max_retry = 3
net.ipv6.conf.tun0.router_probe_interval = 60
net.ipv6.conf.tun0.router_solicitation_delay = 1
net.ipv6.conf.tun0.router_solicitation_interval = 4
net.ipv6.conf.tun0.router_solicitation_max_interval = 3600
net.ipv6.conf.tun0.router_solicitations = -1
sysctl: permission denied on key 'net.ipv6.conf.wlp3s0.stable_secret'
net.ipv6.conf.tun0.suppress_frag_ndisc = 1
net.ipv6.conf.tun0.temp_prefered_lft = 86400
net.ipv6.conf.tun0.temp_valid_lft = 604800
net.ipv6.conf.tun0.use_oif_addrs_only = 0
net.ipv6.conf.tun0.use_optimistic = 0
net.ipv6.conf.tun0.use_tempaddr = -1
net.ipv6.conf.wlp3s0.accept_dad = 1
net.ipv6.conf.wlp3s0.accept_ra = 0
net.ipv6.conf.wlp3s0.accept_ra_defrtr = 0
net.ipv6.conf.wlp3s0.accept_ra_from_local = 0
net.ipv6.conf.wlp3s0.accept_ra_min_hop_limit = 1
net.ipv6.conf.wlp3s0.accept_ra_mtu = 1
net.ipv6.conf.wlp3s0.accept_ra_pinfo = 0
net.ipv6.conf.wlp3s0.accept_ra_rt_info_max_plen = 0
net.ipv6.conf.wlp3s0.accept_ra_rtr_pref = 0
net.ipv6.conf.wlp3s0.accept_redirects = 1
net.ipv6.conf.wlp3s0.accept_source_route = 0
net.ipv6.conf.wlp3s0.autoconf = 1
net.ipv6.conf.wlp3s0.dad_transmits = 1
net.ipv6.conf.wlp3s0.disable_ipv6 = 0
net.ipv6.conf.wlp3s0.drop_unicast_in_l2_multicast = 0
net.ipv6.conf.wlp3s0.drop_unsolicited_na = 0
net.ipv6.conf.wlp3s0.force_mld_version = 0
net.ipv6.conf.wlp3s0.force_tllao = 0
net.ipv6.conf.wlp3s0.forwarding = 0
net.ipv6.conf.wlp3s0.hop_limit = 64
net.ipv6.conf.wlp3s0.ignore_routes_with_linkdown = 0
net.ipv6.conf.wlp3s0.keep_addr_on_down = 0
net.ipv6.conf.wlp3s0.max_addresses = 16
net.ipv6.conf.wlp3s0.max_desync_factor = 600
net.ipv6.conf.wlp3s0.mc_forwarding = 0
net.ipv6.conf.wlp3s0.mldv1_unsolicited_report_interval = 10000
net.ipv6.conf.wlp3s0.mldv2_unsolicited_report_interval = 1000
net.ipv6.conf.wlp3s0.mtu = 1500
net.ipv6.conf.wlp3s0.ndisc_notify = 0
net.ipv6.conf.wlp3s0.optimistic_dad = 0
net.ipv6.conf.wlp3s0.proxy_ndp = 0
net.ipv6.conf.wlp3s0.regen_max_retry = 3
net.ipv6.conf.wlp3s0.router_probe_interval = 60
net.ipv6.conf.wlp3s0.router_solicitation_delay = 1
net.ipv6.conf.wlp3s0.router_solicitation_interval = 4
net.ipv6.conf.wlp3s0.router_solicitation_max_interval = 3600
net.ipv6.conf.wlp3s0.router_solicitations = -1
net.ipv6.conf.wlp3s0.suppress_frag_ndisc = 1
net.ipv6.conf.wlp3s0.temp_prefered_lft = 86400
net.ipv6.conf.wlp3s0.temp_valid_lft = 604800
net.ipv6.conf.wlp3s0.use_oif_addrs_only = 0
net.ipv6.conf.wlp3s0.use_optimistic = 0
net.ipv6.conf.wlp3s0.use_tempaddr = 0
net.ipv6.flowlabel_consistency = 1
net.ipv6.flowlabel_state_ranges = 0
net.ipv6.fwmark_reflect = 0
net.ipv6.icmp.ratelimit = 1000
net.ipv6.idgen_delay = 1
net.ipv6.idgen_retries = 3
net.ipv6.ip6frag_high_thresh = 4194304
net.ipv6.ip6frag_low_thresh = 3145728
net.ipv6.ip6frag_secret_interval = 0
net.ipv6.ip6frag_time = 60
net.ipv6.ip_nonlocal_bind = 0
net.ipv6.mld_max_msf = 64
net.ipv6.mld_qrv = 2
net.ipv6.neigh.default.anycast_delay = 99
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
net.ipv6.neigh.default.proxy_delay = 79
net.ipv6.neigh.default.proxy_qlen = 64
net.ipv6.neigh.default.retrans_time_ms = 1000
net.ipv6.neigh.default.ucast_solicit = 3
net.ipv6.neigh.default.unres_qlen = 31
net.ipv6.neigh.default.unres_qlen_bytes = 65536
net.ipv6.neigh.enp4s0.anycast_delay = 99
net.ipv6.neigh.enp4s0.app_solicit = 0
net.ipv6.neigh.enp4s0.base_reachable_time_ms = 30000
net.ipv6.neigh.enp4s0.delay_first_probe_time = 5
net.ipv6.neigh.enp4s0.gc_stale_time = 60
net.ipv6.neigh.enp4s0.locktime = 0
net.ipv6.neigh.enp4s0.mcast_resolicit = 0
net.ipv6.neigh.enp4s0.mcast_solicit = 3
net.ipv6.neigh.enp4s0.proxy_delay = 79
net.ipv6.neigh.enp4s0.proxy_qlen = 64
net.ipv6.neigh.enp4s0.retrans_time_ms = 1000
net.ipv6.neigh.enp4s0.ucast_solicit = 3
net.ipv6.neigh.enp4s0.unres_qlen = 31
net.ipv6.neigh.enp4s0.unres_qlen_bytes = 65536
net.ipv6.neigh.lo.anycast_delay = 99
net.ipv6.neigh.lo.app_solicit = 0
net.ipv6.neigh.lo.base_reachable_time_ms = 30000
net.ipv6.neigh.lo.delay_first_probe_time = 5
net.ipv6.neigh.lo.gc_stale_time = 60
net.ipv6.neigh.lo.locktime = 0
net.ipv6.neigh.lo.mcast_resolicit = 0
net.ipv6.neigh.lo.mcast_solicit = 3
net.ipv6.neigh.lo.proxy_delay = 79
net.ipv6.neigh.lo.proxy_qlen = 64
net.ipv6.neigh.lo.retrans_time_ms = 1000
net.ipv6.neigh.lo.ucast_solicit = 3
net.ipv6.neigh.lo.unres_qlen = 31
net.ipv6.neigh.lo.unres_qlen_bytes = 65536
net.ipv6.neigh.tun0.anycast_delay = 99
net.ipv6.neigh.tun0.app_solicit = 0
net.ipv6.neigh.tun0.base_reachable_time_ms = 30000
net.ipv6.neigh.tun0.delay_first_probe_time = 5
net.ipv6.neigh.tun0.gc_stale_time = 60
net.ipv6.neigh.tun0.locktime = 0
net.ipv6.neigh.tun0.mcast_resolicit = 0
net.ipv6.neigh.tun0.mcast_solicit = 3
net.ipv6.neigh.tun0.proxy_delay = 79
net.ipv6.neigh.tun0.proxy_qlen = 64
net.ipv6.neigh.tun0.retrans_time_ms = 1000
net.ipv6.neigh.tun0.ucast_solicit = 3
net.ipv6.neigh.tun0.unres_qlen = 31
net.ipv6.neigh.tun0.unres_qlen_bytes = 65536
net.ipv6.neigh.wlp3s0.anycast_delay = 99
net.ipv6.neigh.wlp3s0.app_solicit = 0
net.ipv6.neigh.wlp3s0.base_reachable_time_ms = 30000
net.ipv6.neigh.wlp3s0.delay_first_probe_time = 5
net.ipv6.neigh.wlp3s0.gc_stale_time = 60
net.ipv6.neigh.wlp3s0.locktime = 0
net.ipv6.neigh.wlp3s0.mcast_resolicit = 0
net.ipv6.neigh.wlp3s0.mcast_solicit = 3
net.ipv6.neigh.wlp3s0.proxy_delay = 79
net.ipv6.neigh.wlp3s0.proxy_qlen = 64
net.ipv6.neigh.wlp3s0.retrans_time_ms = 1000
net.ipv6.neigh.wlp3s0.ucast_solicit = 3
net.ipv6.neigh.wlp3s0.unres_qlen = 31
net.ipv6.neigh.wlp3s0.unres_qlen_bytes = 65536
net.ipv6.route.gc_elasticity = 9
net.ipv6.route.gc_interval = 30
net.ipv6.route.gc_min_interval = 0
net.ipv6.route.gc_min_interval_ms = 500
net.ipv6.route.gc_thresh = 1024
net.ipv6.route.gc_timeout = 60
net.ipv6.route.max_size = 4096
net.ipv6.route.min_adv_mss = 1220
net.ipv6.route.mtu_expires = 600
net.ipv6.xfrm6_gc_thresh = 2147483647
sysctl: permission denied on key 'vm.mmap_rnd_bits'
sysctl: permission denied on key 'vm.mmap_rnd_compat_bits'
net.netfilter.nf_log.10 = nf_log_ipv6
sysctl: permission denied on key 'vm.stat_refresh
```
uRock I wish I had more to offer here. ;)
Kind Regards

---

### Post by uRock on 2017-03-19
That's some good information. The** ip -6 addr **command leaves me scratching my head even more,
```
$ ip -6 addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 state UNKNOWN qlen 1
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 state UP qlen 1000
    inet6 fe80::8327:d9b9:afee:1ab3/64 scope link tentative dadfailed 
       valid_lft forever preferred_lft forever
    inet6 fe80::1bbe:8ff:5471:ccfc/64 scope link tentative dadfailed 
       valid_lft forever preferred_lft forever
    inet6 fe80::3a77:cb1d:6785:b8e2/64 scope link tentative dadfailed 
       valid_lft forever preferred_lft forever
4: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 state UP qlen 1000
    inet6 fe80::d2c6:36f:ca35:a6cf/64 scope link tentative dadfailed 
       valid_lft forever preferred_lft forever
    inet6 fe80::58ba:19bd:4463:c2f3/64 scope link tentative dadfailed 
       valid_lft forever preferred_lft forever
    inet6 fe80::5ace:e809:7aa6:68bc/64 scope link tentative dadfailed 
       valid_lft forever preferred_lft forever
```

---

### Post by #&amp;thj^% on 2017-03-19
uRock please bear in mind I am no expert or Guru on this subject.:)
The default source address is determined according to:  [https://tools.ietf.org/html/rfc6724](https://tools.ietf.org/html/rfc6724)
Good Grief so much information to absorb...I just keep comming back to it for referals.
If Needed this is a good resource also:  [https://support.cumulusnetworks.com/hc/en-us/articles/204184298-Disabling-IPv6-EUI-64-Link-local-Address-Autoconfiguration](https://support.cumulusnetworks.com/hc/en-us/articles/204184298-Disabling-IPv6-EUI-64-Link-local-Address-Autoconfiguration)

**The meaning of accept_dad:**
```
accept_dad - INTEGER
    Whether to accept DAD (Duplicate Address Detection).
        0: Disable DAD
        1: Enable DAD (default)
        2: Enable DAD, and disable IPv6 operation if MAC-based duplicate
            link-local address has been found.
```
More Useful Info Here: [https://www.kernel.org/doc/Documentation/networking/ip-sysctl.txt](https://www.kernel.org/doc/Documentation/networking/ip-sysctl.txt)

---

### Post by uRock on 2017-04-26
Thanks. I will look into that!

---

