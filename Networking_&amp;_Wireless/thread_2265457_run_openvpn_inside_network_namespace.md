---
title: "run openvpn inside network namespace"
date: 2015-02-15
forum: Networking &amp; Wireless
---

### Post by foxmark2 on 2015-02-15
Welcome,

My first post on this forum - so if this is the wrong place please forgive me.
This subject has been mentioned a few times but after weeks of searching I'm still no way closer to solution of my problem.

I'm running my small media server using Ubuntu
```

Ubuntu 14.04.1 LTS (GNU/Linux 3.13.0-32-generic i686)

```

My server has apache installed (PHP+MySQL) nothing special
```

Server version: Apache/2.4.7 (Ubuntu)

```

I'm also running uttorent severe and plex
I'm using openvpn to connect to cyberghostvpn.com
This is my config file:
```

client
remote gb-openvpn.cyberghostvpn.com 20
dev tun
proto udp
auth-user-pass /etc/openvpn/vpn/login.conf

ca /etc/openvpn/vpn/ca.crt
cert /etc/openvpn/vpn/client.crt
key /etc/openvpn/vpn/client.key
log-append /etc/openvpn/vpn/run.log

resolv-retry infinite
redirect-gateway def1
persist-key
persist-tun
nobind
cipher AES-256-CBC
auth MD5
ping 5
ping-exit 60
ping-timer-rem
explicit-exit-notify 2
script-security 2
remote-cert-tls server
route-delay 5
tun-mtu 1500
fragment 1300
mssfix 1300
verb 4
comp-lzo

```

Everything is working fine locally (LAN) but every time I'm connected to vpn I'm unable to ssh or get access to my server using HTTP/HTTPS from outside LAN
I have my router configured so if VPN is not running I can use my router WAN IP to connect to my server - no problem
I used this commands to test if my router farwording traffic from outside LAN and it does:
```

/usr/sbin/tcpdump -n -s 0 -i any port 22
/usr/sbin/tcpdump -n -s 0 -i any port 80
/usr/sbin/tcpdump -n -s 0 -i any port 443

```


The moment I connect to VPN this functionality is gone but works fien for LAN IP. I have been trying to fix that problem for a very long time but it looks like I keep finding the same posts leading nowhere.
All I want to do is to hide my utorrent traffic and keep my www server and ssh running at the same time. Is that even possible?

After another endless search session I found you can run process in designated network namespace

I create and setup my network namespace [cyberghost]
```

ip netns add cyberghost
ip link add veth0 type veth peer name veth1
ip link set veth1 netns cyberghost
ip netns exec cyberghost ip link set dev lo up
ifconfig veth0 192.168.42.1 netmask 255.255.255.0 up
ip netns exec cyberghost ifconfig veth1 192.168.42.2 netmask 255.255.255.0 up
ip netns exec cyberghost route add default gw 192.168.42.1
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -s 192.168.42.0/24 -o eth0 -j MASQUERADE

```

after this I can run
```

ip netns exec cyberghost lynx --dump http://wtfismyip.com/text

``` or 

```


root@UVM:/home/fox# ip netns exec cyberghost ping www.google.co.uk
PING www.google.co.uk (74.125.195.94) 56(84) bytes of data.
64 bytes from wj-in-f94.1e100.net (74.125.195.94): icmp_seq=1 ttl=49 time=19.5 ms
64 bytes from wj-in-f94.1e100.net (74.125.195.94): icmp_seq=2 ttl=49 time=20.5 ms
64 bytes from wj-in-f94.1e100.net (74.125.195.94): icmp_seq=3 ttl=49 time=20.3 ms
64 bytes from wj-in-f94.1e100.net (74.125.195.94): icmp_seq=4 ttl=49 time=21.8 ms
64 bytes from wj-in-f94.1e100.net (74.125.195.94): icmp_seq=5 ttl=49 time=19.4 ms

--- www.google.co.uk ping statistics ---
6 packets transmitted, 5 received, 16% packet loss, time 5011ms
rtt min/avg/max/mdev = 19.495/20.370/21.844/0.860 ms


```

I know my namespace is connected to outside world,last thing is to run openvpn inside the namespace
(since openvpn is removed from autostart I run)
```

root@UVM:/home/fox# ip netns exec cyberghost service openvpn start uk
 * Starting virtual private network daemon(s)...                                                                                                                                                                                              *   Starting VPN 'uk'  

```

Log file: 
```

Sun Feb 15 13:55:07 2015 us=135461 Current Parameter Settings:
Sun Feb 15 13:55:07 2015 us=135600   config = '/etc/openvpn/uk.conf'
Sun Feb 15 13:55:07 2015 us=135619   mode = 0
Sun Feb 15 13:55:07 2015 us=135628   persist_config = DISABLED
Sun Feb 15 13:55:07 2015 us=135637   persist_mode = 1
Sun Feb 15 13:55:07 2015 us=135645   show_ciphers = DISABLED
Sun Feb 15 13:55:07 2015 us=135653   show_digests = DISABLED
Sun Feb 15 13:55:07 2015 us=135662   show_engines = DISABLED
Sun Feb 15 13:55:07 2015 us=135671   genkey = DISABLED
Sun Feb 15 13:55:07 2015 us=135679   key_pass_file = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=135687   show_tls_ciphers = DISABLED
Sun Feb 15 13:55:07 2015 us=135695 Connection profiles [default]:
Sun Feb 15 13:55:07 2015 us=135704   proto = udp
Sun Feb 15 13:55:07 2015 us=135712   local = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=135720   local_port = 0
Sun Feb 15 13:55:07 2015 us=135729   remote = 'gb-openvpn.cyberghostvpn.com'
Sun Feb 15 13:55:07 2015 us=135737   remote_port = 20
Sun Feb 15 13:55:07 2015 us=135746   remote_float = DISABLED
Sun Feb 15 13:55:07 2015 us=135753   bind_defined = DISABLED
Sun Feb 15 13:55:07 2015 us=135762   bind_local = DISABLED
Sun Feb 15 13:55:07 2015 us=135787   connect_retry_seconds = 5
Sun Feb 15 13:55:07 2015 us=135799   connect_timeout = 10
Sun Feb 15 13:55:07 2015 us=135807   connect_retry_max = 0
Sun Feb 15 13:55:07 2015 us=135816   socks_proxy_server = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=135824   socks_proxy_port = 0
Sun Feb 15 13:55:07 2015 us=135832   socks_proxy_retry = DISABLED
Sun Feb 15 13:55:07 2015 us=135840   tun_mtu = 1500
Sun Feb 15 13:55:07 2015 us=135848   tun_mtu_defined = ENABLED
Sun Feb 15 13:55:07 2015 us=135857   link_mtu = 1500
Sun Feb 15 13:55:07 2015 us=135865   link_mtu_defined = DISABLED
Sun Feb 15 13:55:07 2015 us=135873   tun_mtu_extra = 0
Sun Feb 15 13:55:07 2015 us=135881   tun_mtu_extra_defined = DISABLED
Sun Feb 15 13:55:07 2015 us=135890   mtu_discover_type = -1
Sun Feb 15 13:55:07 2015 us=135898   fragment = 1300
Sun Feb 15 13:55:07 2015 us=135931   mssfix = 1300
Sun Feb 15 13:55:07 2015 us=135943   explicit_exit_notification = 2
Sun Feb 15 13:55:07 2015 us=135957 Connection profiles END
Sun Feb 15 13:55:07 2015 us=135983   remote_random = DISABLED
Sun Feb 15 13:55:07 2015 us=135995   ipchange = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=136046   dev = 'tun'
Sun Feb 15 13:55:07 2015 us=136059   dev_type = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=136068   dev_node = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=136076   lladdr = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=136084   topology = 1
Sun Feb 15 13:55:07 2015 us=136092   tun_ipv6 = DISABLED
Sun Feb 15 13:55:07 2015 us=136100   ifconfig_local = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=136108   ifconfig_remote_netmask = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=136116   ifconfig_noexec = DISABLED
Sun Feb 15 13:55:07 2015 us=136124   ifconfig_nowarn = DISABLED
Sun Feb 15 13:55:07 2015 us=136132   ifconfig_ipv6_local = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=136140   ifconfig_ipv6_netbits = 0
Sun Feb 15 13:55:07 2015 us=136148   ifconfig_ipv6_remote = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=136156   shaper = 0
Sun Feb 15 13:55:07 2015 us=136165   mtu_test = 0
Sun Feb 15 13:55:07 2015 us=136173   mlock = DISABLED
Sun Feb 15 13:55:07 2015 us=136184   keepalive_ping = 0
Sun Feb 15 13:55:07 2015 us=136192   keepalive_timeout = 0
Sun Feb 15 13:55:07 2015 us=136200   inactivity_timeout = 0
Sun Feb 15 13:55:07 2015 us=136208   ping_send_timeout = 5
Sun Feb 15 13:55:07 2015 us=136216   ping_rec_timeout = 60
Sun Feb 15 13:55:07 2015 us=136224   ping_rec_timeout_action = 1
Sun Feb 15 13:55:07 2015 us=136232   ping_timer_remote = ENABLED
Sun Feb 15 13:55:07 2015 us=136240   remap_sigusr1 = 0
Sun Feb 15 13:55:07 2015 us=136248   persist_tun = ENABLED
Sun Feb 15 13:55:07 2015 us=136256   persist_local_ip = DISABLED
Sun Feb 15 13:55:07 2015 us=136264   persist_remote_ip = DISABLED
Sun Feb 15 13:55:07 2015 us=136272   persist_key = ENABLED
Sun Feb 15 13:55:07 2015 us=136280   passtos = DISABLED
Sun Feb 15 13:55:07 2015 us=136288   resolve_retry_seconds = 1000000000
Sun Feb 15 13:55:07 2015 us=136313   username = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=136322   groupname = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=136330   chroot_dir = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=136338   cd_dir = '/etc/openvpn'
Sun Feb 15 13:55:07 2015 us=136346   writepid = '/run/openvpn/uk.pid'
Sun Feb 15 13:55:07 2015 us=136353   up_script = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=136383   down_script = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=136394   down_pre = DISABLED
Sun Feb 15 13:55:07 2015 us=136403   up_restart = DISABLED
Sun Feb 15 13:55:07 2015 us=136427   up_delay = DISABLED
Sun Feb 15 13:55:07 2015 us=136439   daemon = ENABLED
Sun Feb 15 13:55:07 2015 us=136463   inetd = 0
Sun Feb 15 13:55:07 2015 us=136474   log = ENABLED
Sun Feb 15 13:55:07 2015 us=136498   suppress_timestamps = DISABLED
Sun Feb 15 13:55:07 2015 us=136509   nice = 0
Sun Feb 15 13:55:07 2015 us=136533   verbosity = 4
Sun Feb 15 13:55:07 2015 us=136544   mute = 0
Sun Feb 15 13:55:07 2015 us=136568   gremlin = 0
Sun Feb 15 13:55:07 2015 us=136580   status_file = '/run/openvpn/uk.status'
Sun Feb 15 13:55:07 2015 us=136604   status_file_version = 1
Sun Feb 15 13:55:07 2015 us=136615   status_file_update_freq = 10
Sun Feb 15 13:55:07 2015 us=136639   occ = ENABLED
Sun Feb 15 13:55:07 2015 us=136650   rcvbuf = 65536
Sun Feb 15 13:55:07 2015 us=136674   sndbuf = 65536
Sun Feb 15 13:55:07 2015 us=136685   mark = 0
Sun Feb 15 13:55:07 2015 us=136709   sockflags = 0
Sun Feb 15 13:55:07 2015 us=136720   fast_io = DISABLED
Sun Feb 15 13:55:07 2015 us=136743   lzo = 7
Sun Feb 15 13:55:07 2015 us=136755   route_script = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=136763   route_default_gateway = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=136784   route_default_metric = 0
Sun Feb 15 13:55:07 2015 us=136822   route_noexec = DISABLED
Sun Feb 15 13:55:07 2015 us=136841   route_delay = 5
Sun Feb 15 13:55:07 2015 us=136869   route_delay_window = 30
Sun Feb 15 13:55:07 2015 us=136881   route_delay_defined = ENABLED
Sun Feb 15 13:55:07 2015 us=136907   route_nopull = DISABLED
Sun Feb 15 13:55:07 2015 us=136919   route_gateway_via_dhcp = DISABLED
Sun Feb 15 13:55:07 2015 us=136943   max_routes = 100
Sun Feb 15 13:55:07 2015 us=136954   allow_pull_fqdn = DISABLED
Sun Feb 15 13:55:07 2015 us=136965   [redirect_default_gateway local=0]
Sun Feb 15 13:55:07 2015 us=136994   management_addr = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=137006   management_port = 0
Sun Feb 15 13:55:07 2015 us=137015   management_user_pass = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=137038   management_log_history_cache = 250
Sun Feb 15 13:55:07 2015 us=137050   management_echo_buffer_size = 100
Sun Feb 15 13:55:07 2015 us=137074   management_write_peer_info_file = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=137085   management_client_user = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=137110   management_client_group = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=137122   management_flags = 0
Sun Feb 15 13:55:07 2015 us=137130   shared_secret_file = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=137153   key_direction = 0
Sun Feb 15 13:55:07 2015 us=137165   ciphername_defined = ENABLED
Sun Feb 15 13:55:07 2015 us=137189   ciphername = 'AES-256-CBC'
Sun Feb 15 13:55:07 2015 us=137200   authname_defined = ENABLED
Sun Feb 15 13:55:07 2015 us=137233   authname = 'MD5'
Sun Feb 15 13:55:07 2015 us=137245   prng_hash = 'SHA1'
Sun Feb 15 13:55:07 2015 us=137268   prng_nonce_secret_len = 16
Sun Feb 15 13:55:07 2015 us=137280   keysize = 0
Sun Feb 15 13:55:07 2015 us=137304   engine = DISABLED
Sun Feb 15 13:55:07 2015 us=137315   replay = ENABLED
Sun Feb 15 13:55:07 2015 us=137345   mute_replay_warnings = DISABLED
Sun Feb 15 13:55:07 2015 us=137357   replay_window = 64
Sun Feb 15 13:55:07 2015 us=137380   replay_time = 15
Sun Feb 15 13:55:07 2015 us=137392   packet_id_file = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=137416   use_iv = ENABLED
Sun Feb 15 13:55:07 2015 us=137427   test_crypto = DISABLED
Sun Feb 15 13:55:07 2015 us=137457   tls_server = DISABLED
Sun Feb 15 13:55:07 2015 us=137468   tls_client = ENABLED
Sun Feb 15 13:55:07 2015 us=137500   key_method = 2
Sun Feb 15 13:55:07 2015 us=137514   ca_file = '/etc/openvpn/vpn/ca.crt'
Sun Feb 15 13:55:07 2015 us=137522   ca_path = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=137546   dh_file = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=137557   cert_file = '/etc/openvpn/vpn/client.crt'
Sun Feb 15 13:55:07 2015 us=137588   priv_key_file = '/etc/openvpn/vpn/client.key'
Sun Feb 15 13:55:07 2015 us=137616   pkcs12_file = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=137628   cipher_list = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=137652   tls_verify = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=137663   tls_export_cert = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=137687   verify_x509_type = 0
Sun Feb 15 13:55:07 2015 us=137699   verify_x509_name = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=137728   crl_file = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=137740   ns_cert_type = 0
Sun Feb 15 13:55:07 2015 us=137781   remote_cert_ku[i] = 160
Sun Feb 15 13:55:07 2015 us=137807   remote_cert_ku[i] = 136
Sun Feb 15 13:55:07 2015 us=137819   remote_cert_ku[i] = 0
Sun Feb 15 13:55:07 2015 us=137826   remote_cert_ku[i] = 0
Sun Feb 15 13:55:07 2015 us=137834   remote_cert_ku[i] = 0
Sun Feb 15 13:55:07 2015 us=137841   remote_cert_ku[i] = 0
Sun Feb 15 13:55:07 2015 us=137849   remote_cert_ku[i] = 0
Sun Feb 15 13:55:07 2015 us=137856   remote_cert_ku[i] = 0
Sun Feb 15 13:55:07 2015 us=137864   remote_cert_ku[i] = 0
Sun Feb 15 13:55:07 2015 us=137871   remote_cert_ku[i] = 0
Sun Feb 15 13:55:07 2015 us=137880   remote_cert_ku[i] = 0
Sun Feb 15 13:55:07 2015 us=137907   remote_cert_ku[i] = 0
Sun Feb 15 13:55:07 2015 us=137918   remote_cert_ku[i] = 0
Sun Feb 15 13:55:07 2015 us=137926   remote_cert_ku[i] = 0
Sun Feb 15 13:55:07 2015 us=137959   remote_cert_ku[i] = 0
Sun Feb 15 13:55:07 2015 us=137986   remote_cert_ku[i] = 0
Sun Feb 15 13:55:07 2015 us=137997   remote_cert_eku = 'TLS Web Server Authentication'
Sun Feb 15 13:55:07 2015 us=138028   ssl_flags = 0
Sun Feb 15 13:55:07 2015 us=138039   tls_timeout = 2
Sun Feb 15 13:55:07 2015 us=138063   renegotiate_bytes = 0
Sun Feb 15 13:55:07 2015 us=138075   renegotiate_packets = 0
Sun Feb 15 13:55:07 2015 us=138098   renegotiate_seconds = 3600
Sun Feb 15 13:55:07 2015 us=138109   handshake_window = 60
Sun Feb 15 13:55:07 2015 us=138133   transition_window = 3600
Sun Feb 15 13:55:07 2015 us=138144   single_session = DISABLED
Sun Feb 15 13:55:07 2015 us=138169   push_peer_info = DISABLED
Sun Feb 15 13:55:07 2015 us=138181   tls_exit = DISABLED
Sun Feb 15 13:55:07 2015 us=138189   tls_auth_file = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=138213   pkcs11_protected_authentication = DISABLED
Sun Feb 15 13:55:07 2015 us=138224   pkcs11_protected_authentication = DISABLED
Sun Feb 15 13:55:07 2015 us=138233   pkcs11_protected_authentication = DISABLED
Sun Feb 15 13:55:07 2015 us=138256   pkcs11_protected_authentication = DISABLED
Sun Feb 15 13:55:07 2015 us=138268   pkcs11_protected_authentication = DISABLED
Sun Feb 15 13:55:07 2015 us=138298   pkcs11_protected_authentication = DISABLED
Sun Feb 15 13:55:07 2015 us=138309   pkcs11_protected_authentication = DISABLED
Sun Feb 15 13:55:07 2015 us=138333   pkcs11_protected_authentication = DISABLED
Sun Feb 15 13:55:07 2015 us=138344   pkcs11_protected_authentication = DISABLED
Sun Feb 15 13:55:07 2015 us=138372   pkcs11_protected_authentication = DISABLED
Sun Feb 15 13:55:07 2015 us=138383   pkcs11_protected_authentication = DISABLED
Sun Feb 15 13:55:07 2015 us=138407   pkcs11_protected_authentication = DISABLED
Sun Feb 15 13:55:07 2015 us=138418   pkcs11_protected_authentication = DISABLED
Sun Feb 15 13:55:07 2015 us=138443   pkcs11_protected_authentication = DISABLED
Sun Feb 15 13:55:07 2015 us=138454   pkcs11_protected_authentication = DISABLED
Sun Feb 15 13:55:07 2015 us=138483   pkcs11_protected_authentication = DISABLED
Sun Feb 15 13:55:07 2015 us=138498   pkcs11_private_mode = 00000000
Sun Feb 15 13:55:07 2015 us=138523   pkcs11_private_mode = 00000000
Sun Feb 15 13:55:07 2015 us=138535   pkcs11_private_mode = 00000000
Sun Feb 15 13:55:07 2015 us=138559   pkcs11_private_mode = 00000000
Sun Feb 15 13:55:07 2015 us=138602   pkcs11_private_mode = 00000000
Sun Feb 15 13:55:07 2015 us=138630   pkcs11_private_mode = 00000000
Sun Feb 15 13:55:07 2015 us=138641   pkcs11_private_mode = 00000000
Sun Feb 15 13:55:07 2015 us=138665   pkcs11_private_mode = 00000000
Sun Feb 15 13:55:07 2015 us=138676   pkcs11_private_mode = 00000000
Sun Feb 15 13:55:07 2015 us=138704   pkcs11_private_mode = 00000000
Sun Feb 15 13:55:07 2015 us=138715   pkcs11_private_mode = 00000000
Sun Feb 15 13:55:07 2015 us=138739   pkcs11_private_mode = 00000000
Sun Feb 15 13:55:07 2015 us=138750   pkcs11_private_mode = 00000000
Sun Feb 15 13:55:07 2015 us=138772   pkcs11_private_mode = 00000000
Sun Feb 15 13:55:07 2015 us=138799   pkcs11_private_mode = 00000000
Sun Feb 15 13:55:07 2015 us=138812   pkcs11_private_mode = 00000000
Sun Feb 15 13:55:07 2015 us=138820   pkcs11_cert_private = DISABLED
Sun Feb 15 13:55:07 2015 us=138865   pkcs11_cert_private = DISABLED
Sun Feb 15 13:55:07 2015 us=138892   pkcs11_cert_private = DISABLED
Sun Feb 15 13:55:07 2015 us=138903   pkcs11_cert_private = DISABLED
Sun Feb 15 13:55:07 2015 us=138927   pkcs11_cert_private = DISABLED
Sun Feb 15 13:55:07 2015 us=138938   pkcs11_cert_private = DISABLED
Sun Feb 15 13:55:07 2015 us=138968   pkcs11_cert_private = DISABLED
Sun Feb 15 13:55:07 2015 us=138979   pkcs11_cert_private = DISABLED
Sun Feb 15 13:55:07 2015 us=139002   pkcs11_cert_private = DISABLED
Sun Feb 15 13:55:07 2015 us=139013   pkcs11_cert_private = DISABLED
Sun Feb 15 13:55:07 2015 us=139041   pkcs11_cert_private = DISABLED
Sun Feb 15 13:55:07 2015 us=139053   pkcs11_cert_private = DISABLED
Sun Feb 15 13:55:07 2015 us=139077   pkcs11_cert_private = DISABLED
Sun Feb 15 13:55:07 2015 us=139088   pkcs11_cert_private = DISABLED
Sun Feb 15 13:55:07 2015 us=139117   pkcs11_cert_private = DISABLED
Sun Feb 15 13:55:07 2015 us=139128   pkcs11_cert_private = DISABLED
Sun Feb 15 13:55:07 2015 us=139151   pkcs11_pin_cache_period = -1
Sun Feb 15 13:55:07 2015 us=139163   pkcs11_id = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=139187   pkcs11_id_management = DISABLED
Sun Feb 15 13:55:07 2015 us=139210   server_network = 0.0.0.0
Sun Feb 15 13:55:07 2015 us=139223   server_netmask = 0.0.0.0
Sun Feb 15 13:55:07 2015 us=139237   server_network_ipv6 = ::
Sun Feb 15 13:55:07 2015 us=139245   server_netbits_ipv6 = 0
Sun Feb 15 13:55:07 2015 us=139270   server_bridge_ip = 0.0.0.0
Sun Feb 15 13:55:07 2015 us=139283   server_bridge_netmask = 0.0.0.0
Sun Feb 15 13:55:07 2015 us=139310   server_bridge_pool_start = 0.0.0.0
Sun Feb 15 13:55:07 2015 us=139322   server_bridge_pool_end = 0.0.0.0
Sun Feb 15 13:55:07 2015 us=139330   ifconfig_pool_defined = DISABLED
Sun Feb 15 13:55:07 2015 us=139355   ifconfig_pool_start = 0.0.0.0
Sun Feb 15 13:55:07 2015 us=139367   ifconfig_pool_end = 0.0.0.0
Sun Feb 15 13:55:07 2015 us=139392   ifconfig_pool_netmask = 0.0.0.0
Sun Feb 15 13:55:07 2015 us=139403   ifconfig_pool_persist_filename = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=139411   ifconfig_pool_persist_refresh_freq = 600
Sun Feb 15 13:55:07 2015 us=139450   ifconfig_ipv6_pool_defined = DISABLED
Sun Feb 15 13:55:07 2015 us=139470   ifconfig_ipv6_pool_base = ::
Sun Feb 15 13:55:07 2015 us=139478   ifconfig_ipv6_pool_netbits = 0
Sun Feb 15 13:55:07 2015 us=139486   n_bcast_buf = 256
Sun Feb 15 13:55:07 2015 us=139494   tcp_queue_limit = 64
Sun Feb 15 13:55:07 2015 us=139518   real_hash_size = 256
Sun Feb 15 13:55:07 2015 us=139531   virtual_hash_size = 256
Sun Feb 15 13:55:07 2015 us=139539   client_connect_script = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=139563   learn_address_script = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=139574   client_disconnect_script = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=139604   client_config_dir = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=139616   ccd_exclusive = DISABLED
Sun Feb 15 13:55:07 2015 us=139645   tmp_dir = '/tmp'
Sun Feb 15 13:55:07 2015 us=139657   push_ifconfig_defined = DISABLED
Sun Feb 15 13:55:07 2015 us=139687   push_ifconfig_local = 0.0.0.0
Sun Feb 15 13:55:07 2015 us=139715   push_ifconfig_remote_netmask = 0.0.0.0
Sun Feb 15 13:55:07 2015 us=139749   push_ifconfig_ipv6_defined = DISABLED
Sun Feb 15 13:55:07 2015 us=139775   push_ifconfig_ipv6_local = ::/0
Sun Feb 15 13:55:07 2015 us=139802   push_ifconfig_ipv6_remote = ::
Sun Feb 15 13:55:07 2015 us=139814   enable_c2c = DISABLED
Sun Feb 15 13:55:07 2015 us=139844   duplicate_cn = DISABLED
Sun Feb 15 13:55:07 2015 us=139856   cf_max = 0
Sun Feb 15 13:55:07 2015 us=139884   cf_per = 0
Sun Feb 15 13:55:07 2015 us=139896   max_clients = 1024
Sun Feb 15 13:55:07 2015 us=139925   max_routes_per_client = 256
Sun Feb 15 13:55:07 2015 us=139953   auth_user_pass_verify_script = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=139964   auth_user_pass_verify_script_via_file = DISABLED
Sun Feb 15 13:55:07 2015 us=139988   port_share_host = '[UNDEF]'
Sun Feb 15 13:55:07 2015 us=139999   port_share_port = 0
Sun Feb 15 13:55:07 2015 us=140024   client = ENABLED
Sun Feb 15 13:55:07 2015 us=140036   pull = ENABLED
Sun Feb 15 13:55:07 2015 us=140044   auth_user_pass_file = '/etc/openvpn/vpn/login.conf'
Sun Feb 15 13:55:07 2015 us=140070 OpenVPN 2.3.2 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Dec  1 2014
Sun Feb 15 13:55:07 2015 us=140130 WARNING: file '/etc/openvpn/vpn/login.conf' is group or others accessible
Sun Feb 15 13:55:07 2015 us=156902 WARNING: file '/etc/openvpn/vpn/client.key' is group or others accessible
Sun Feb 15 13:55:07 2015 us=158006 LZO compression initialized
Sun Feb 15 13:55:07 2015 us=158191 Control Channel MTU parms [ L:1558 D:138 EF:38 EB:0 ET:0 EL:0 ]
Sun Feb 15 13:55:07 2015 us=158343 Socket Buffers: R=[212992->131072] S=[212992->131072]
Sun Feb 15 13:55:08 2015 us=9189 Data Channel MTU parms [ L:1558 D:1300 EF:58 EB:135 ET:0 EL:0 AF:3/1 ]
Sun Feb 15 13:55:08 2015 us=9289 Fragmentation MTU parms [ L:1558 D:1300 EF:57 EB:135 ET:1 EL:0 AF:3/1 ]
Sun Feb 15 13:55:08 2015 us=9355 Local Options String: 'V4,dev-type tun,link-mtu 1558,tun-mtu 1500,proto UDPv4,comp-lzo,mtu-dynamic,cipher AES-256-CBC,auth MD5,keysize 256,key-method 2,tls-client'
Sun Feb 15 13:55:08 2015 us=9367 Expected Remote Options String: 'V4,dev-type tun,link-mtu 1558,tun-mtu 1500,proto UDPv4,comp-lzo,mtu-dynamic,cipher AES-256-CBC,auth MD5,keysize 256,key-method 2,tls-server'
Sun Feb 15 13:55:08 2015 us=9584 Local Options hash (VER=V4): '8f40a5db'
Sun Feb 15 13:55:08 2015 us=9631 Expected Remote Options hash (VER=V4): '6ce7e20d'
Sun Feb 15 13:55:08 2015 us=11026 UDPv4 link local: [undef]
Sun Feb 15 13:55:08 2015 us=11288 UDPv4 link remote: [AF_INET]88.150.198.100:20
Sun Feb 15 13:55:08 2015 us=30566 TLS: Initial packet from [AF_INET]88.150.198.100:20, sid=49768433 964d6f2e
Sun Feb 15 13:55:08 2015 us=30965 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Sun Feb 15 13:55:08 2015 us=130518 VERIFY OK: depth=1, C=DE, O=CyberGhost VPN, OU=CyberGhost, CN=CyberGhost
Sun Feb 15 13:55:08 2015 us=131124 Validating certificate key usage
Sun Feb 15 13:55:08 2015 us=131223 ++ Certificate has key usage  00a0, expects 00a0
Sun Feb 15 13:55:08 2015 us=131256 VERIFY KU OK
Sun Feb 15 13:55:08 2015 us=131281 Validating certificate extended key usage
Sun Feb 15 13:55:08 2015 us=131303 ++ Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server Authentication
Sun Feb 15 13:55:08 2015 us=131379 VERIFY EKU OK
Sun Feb 15 13:55:08 2015 us=131401 VERIFY OK: depth=0, C=RO, ST=RO, L=Bucharest, O=CyberGhost VPN, OU=CyberGhost, CN=CyberGhost, name=CyberGhost VPN, emailAddress=webmaster@cyberghostvpn.com
Sun Feb 15 13:55:08 2015 us=608983 Data Channel Encrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Sun Feb 15 13:55:08 2015 us=609218 Data Channel Encrypt: Using 128 bit message hash 'MD5' for HMAC authentication
Sun Feb 15 13:55:08 2015 us=609262 Data Channel Decrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Sun Feb 15 13:55:08 2015 us=609286 Data Channel Decrypt: Using 128 bit message hash 'MD5' for HMAC authentication
Sun Feb 15 13:55:08 2015 us=609583 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Sun Feb 15 13:55:08 2015 us=609758 [CyberGhost] Peer Connection Initiated with [AF_INET]88.150.198.100:20
Sun Feb 15 13:55:10 2015 us=790703 SENT CONTROL [CyberGhost]: 'PUSH_REQUEST' (status=1)
Sun Feb 15 13:55:10 2015 us=808389 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1,dhcp-option DNS 95.169.183.219,dhcp-option DNS 89.41.60.38,dhcp-option DNS 37.221.175.198,comp-lzo yes,route 10.129.0.1,topology net30,ping 10,ping-restart 60,ifconfig 10.129.40.194 10.129.40.193'
Sun Feb 15 13:55:10 2015 us=808916 OPTIONS IMPORT: timers and/or timeouts modified
Sun Feb 15 13:55:10 2015 us=809036 OPTIONS IMPORT: LZO parms modified
Sun Feb 15 13:55:10 2015 us=809182 OPTIONS IMPORT: --ifconfig/up options modified
Sun Feb 15 13:55:10 2015 us=809263 OPTIONS IMPORT: route options modified
Sun Feb 15 13:55:10 2015 us=809339 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Sun Feb 15 13:55:10 2015 us=810004 ROUTE_GATEWAY 192.168.42.1/255.255.255.0 IFACE=veth1 HWADDR=82:22:3f:48:a9:08
Sun Feb 15 13:55:10 2015 us=810763 TUN/TAP device tun0 opened
Sun Feb 15 13:55:10 2015 us=810920 TUN/TAP TX queue length set to 100
Sun Feb 15 13:55:10 2015 us=811032 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Sun Feb 15 13:55:10 2015 us=811226 /sbin/ip link set dev tun0 up mtu 1500
Sun Feb 15 13:55:10 2015 us=817338 /sbin/ip addr add dev tun0 local 10.129.40.194 peer 10.129.40.193
Sun Feb 15 13:55:16 2015 us=3974 /sbin/ip route add 88.150.198.100/32 via 192.168.42.1
Sun Feb 15 13:55:16 2015 us=6690 /sbin/ip route add 0.0.0.0/1 via 10.129.40.193
Sun Feb 15 13:55:16 2015 us=10234 /sbin/ip route add 128.0.0.0/1 via 10.129.40.193
Sun Feb 15 13:55:16 2015 us=13023 /sbin/ip route add 10.129.0.1/32 via 10.129.40.193
Sun Feb 15 13:55:16 2015 us=15409 Initialization Sequence Completed

```

after that if I try access any host I see this
```

 root@UVM:/home/fox# ip netns exec cyberghost lynx --dump http://wtfismyip.com/text

Looking up wtfismyip.com
Unable to locate remote host wtfismyip.com.
Alert!: Unable to connect to remote host.

lynx: Can't access startfile http://wtfismyip.com/text

```

What I'm doing wrong?
I looked at the log file looking for any clues but this is outside my networks skills

ifconfig for my neamespace:
```

root@UVM:/home/fox# ip netns exec cyberghost ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.129.40.194  P-t-P:10.129.40.193  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:492 (492.0 B)

veth1     Link encap:Ethernet  HWaddr 82:22:3f:48:a9:08
          inet addr:192.168.42.2  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::8022:3fff:fe48:a908/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:22081 (22.0 KB)  TX bytes:15017 (15.0 KB)


```

---

### Post by TheFu on 2015-02-15
Wow.  I haven't learned the 'ip' commands ... 

You are an openvpn client.  Lots of people here are trying to get an openvpn server running. That is an important differences.

The way I'd attack the root issue is to setup a VM or container and put the bt VPN inside there and leave the normal system with standard networking. All WAN traffic inside the container would route thru the VPN. Relatively easy, right?  LXC containers are fairly light.  Trying to deal with split vpn tunnels is non-trivial.

Just to be clear, it is probably possible to do what you want by managing the routes per interface for the bt userid with iptables.  [http://blog.sebastien.raveau.name/2009/04/per-process-routing.html](http://blog.sebastien.raveau.name/2009/04/per-process-routing.html)   Hope that makes sense.

There are probably 5 others ways to solve this.

---

### Post by foxmark2 on 2015-02-15
> **TheFu said:**
> The way I'd attack the root issue is to setup a VM or container and put the bt VPN inside there and leave the normal system with standard networking. 

There are probably 5 others ways to solve this.

Thank you TheFu. Since I also have a samba and plex server with a large library running on this installation it will be less painful to create a container for apache and keep the rest running as it is now. Will install lxc and give it a try.

I must be close with network namespace approach but can't put everything together.

I'll post the solution when I find one, in the meantime I'm open for othere ideas

---

### Post by SeijiSensei on 2015-02-15
The "ip" commands also give you access to [advanced routing options]("http://www.lartc.org/lartc.html") like using named routing tables.

---

