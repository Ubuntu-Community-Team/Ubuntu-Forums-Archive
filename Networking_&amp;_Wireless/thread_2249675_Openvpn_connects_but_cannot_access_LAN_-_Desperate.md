---
title: "Openvpn connects but cannot access LAN - Desperate"
date: 2014-10-23
forum: Networking &amp; Wireless
---

### Post by Chris_Boyd on 2014-10-23
I have spent so much time on this.

The client is my Android phone. I am able to connect to my Openvpn server running on 14.04. 

Both my phone and my VPN server can ping each other.

My phone is unable to reach any other devices on my LAN. 

Android does not support dev tap. Thus I cannot use tap on Unbuntu, thus I cannot use bridging

Simple routing problem? I can't figure it out. I'm not a networking guy but I am a Linux systems guy who is obsessed to resolve this. You have no idea how much time I've spent trying to solve this.

Somebody please, please provide me the route commands or iptable commands to resolve this for me..

External domain name: chrisdom.com
VLAN Network: 10.20.30.0/24
LAN: 192.168.10.0/24
VPN Server LAN IP: 192.168.10.1
VPN Server VPN IP: 10.20.30.1
Phone's IP: 70.192.100.2
Phone's VLAN IP: 10.20.30.2

Added these two lines in /etc/sysctl.conf
net.ipv4.ip_forward=1
net.ipv4.conf.all.forwarding=1

Ifconfig -a looks like:

```

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:30843 (30.8 KB)  TX bytes:30843 (30.8 KB)


p1p1      Link encap:Ethernet  HWaddr c8:0a:a9:1e:62:7a
          inet addr:192.168.10.104  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::ca0a:a9ff:fe1e:627a/64 Scope:Link
          inet6 addr: 2002:458c:dd27:0:2574:afec:f5b0:3d79/64 Scope:Global
          inet6 addr: 2002:458c:dd27:0:ca0a:a9ff:fe1e:627a/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:433202 (433.2 KB)  TX bytes:300418 (300.4 KB)


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.20.30.1  P-t-P:10.20.30.1  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:634 errors:0 dropped:0 overruns:0 frame:0
          TX packets:393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:41431 (41.4 KB)  TX bytes:26998 (26.9 KB)


wlan0     Link encap:Ethernet  HWaddr 00:26:c7:08:0f:68
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


server.conf:

```

topology subnet
server 10.20.30.0 255.255.255.0
dev tun
proto udp
dev tun
port 1194


tls-auth /etc/openvpn/ta.key
ca /etc/openvpn/ca.crt
cert /etc/openvpn/server.crt
key /etc/openvpn/server.key
dh /etc/openvpn/dh1024.pem


push "redirect-gateway def1"
push "route 192.168.10.0 255.255.255.0"
push "dhcp-option DNS 192.168.10.104"


duplicate-cn
verb 4
user nobody
group nogroup
persist-key
persist-tun
comp-lzo
keepalive 10 120
ping-timer-rem
status /var/log/openvpn-status.log

```


Client Config:

```

[FONT=arial]# Enables connection to GUI
management /data/data/de.blinkt.openvpn/cache/mgmtsocket unix
management-client
management-query-passwords
management-hold[/FONT]
[FONT=arial]setenv IV_GUI_VER "de.blinkt.openvpn 0.6.17" 
machine-readable-output
client
verb 4
connect-retry-max 5
connect-retry 5
resolv-retry 60
dev tun
remote [chrisdom.com]("http://chrisbb61.com/") 1194 udp-client
route-ipv6 ::/0[/FONT]
[FONT=arial]route 0.0.0.0 0.0.0.0 vpn_gateway
remote-cert-tls server[/FONT]

```


Server LOG

```

Thu Oct 23 21:21:52 2014 us=699710 OpenVPN 2.3.2 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Feb  4 2014
Thu Oct 23 21:21:52 2014 us=701867 Diffie-Hellman initialized with 1024 bit key
Thu Oct 23 21:21:52 2014 us=702426 Control Channel Authentication: using '/etc/openvpn/ta.key' as a OpenVPN static key file
Thu Oct 23 21:21:52 2014 us=702460 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Oct 23 21:21:52 2014 us=702484 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Oct 23 21:21:52 2014 us=702535 TLS-Auth MTU parms [ L:1544 D:168 EF:68 EB:0 ET:0 EL:0 ]
Thu Oct 23 21:21:52 2014 us=702597 Socket Buffers: R=[87380->131072] S=[16384->131072]
Thu Oct 23 21:21:52 2014 us=702968 TUN/TAP device tun0 opened
Thu Oct 23 21:21:52 2014 us=703012 TUN/TAP TX queue length set to 100
Thu Oct 23 21:21:52 2014 us=703051 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Thu Oct 23 21:21:52 2014 us=703120 /sbin/ip link set dev tun0 up mtu 1500
Thu Oct 23 21:21:52 2014 us=704443 /sbin/ip addr add dev tun0 10.20.30.1/24 broadcast 10.20.30.255
Thu Oct 23 21:21:52 2014 us=707126 Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Thu Oct 23 21:21:52 2014 us=707892 GID set to nogroup
Thu Oct 23 21:21:52 2014 us=707939 UID set to nobody
Thu Oct 23 21:21:52 2014 us=707975 Listening for incoming TCP connection on [undef]
Thu Oct 23 21:21:52 2014 us=708016 TCPv4_SERVER link local (bound): [undef]
Thu Oct 23 21:21:52 2014 us=708055 TCPv4_SERVER link remote: [undef]
Thu Oct 23 21:21:52 2014 us=708099 MULTI: multi_init called, r=256 v=256
Thu Oct 23 21:21:52 2014 us=708161 IFCONFIG POOL: base=10.20.30.2 size=252, ipv6=0
Thu Oct 23 21:21:52 2014 us=708216 MULTI: TCP INIT maxclients=1024 maxevents=1028
Thu Oct 23 21:21:52 2014 us=708277 Initialization Sequence Completed
Thu Oct 23 21:21:57 2014 us=598259 MULTI: multi_create_instance called
Thu Oct 23 21:21:57 2014 us=598357 Re-using SSL/TLS context
Thu Oct 23 21:21:57 2014 us=598425 LZO compression initialized
Thu Oct 23 21:21:57 2014 us=598654 Control Channel MTU parms [ L:1544 D:168 EF:68 EB:0 ET:0 EL:0 ]
Thu Oct 23 21:21:57 2014 us=598727 Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Thu Oct 23 21:21:57 2014 us=598816 Local Options String: 'V4,dev-type tun,link-mtu 1544,tun-mtu 1500,proto TCPv4_SERVER,comp-lzo,cipher BF-CBC,auth SHA1,keysize 128,tls-auth,key-method 2,tls-server'
Thu Oct 23 21:21:57 2014 us=598862 Expected Remote Options String: 'V4,dev-type tun,link-mtu 1544,tun-mtu 1500,proto TCPv4_CLIENT,comp-lzo,cipher BF-CBC,auth SHA1,keysize 128,tls-auth,key-method 2,tls-client'
Thu Oct 23 21:21:57 2014 us=598935 Local Options hash (VER=V4): '64e96fc1'
Thu Oct 23 21:21:57 2014 us=598992 Expected Remote Options hash (VER=V4): '863ad621'
Thu Oct 23 21:21:57 2014 us=599065 TCP connection established with [AF_INET]70.192.193.10:7095
Thu Oct 23 21:21:57 2014 us=599111 TCPv4_SERVER link local: [undef]
Thu Oct 23 21:22:01 2014 us=417139 70.192.193.10:7095 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Thu Oct 23 21:22:01 2014 us=417192 70.192.193.10:7095 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Oct 23 21:22:01 2014 us=417315 70.192.193.10:7095 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Thu Oct 23 21:22:01 2014 us=417366 70.192.193.10:7095 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Oct 23 21:22:01 2014 us=677236 70.192.193.10:7095 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Thu Oct 23 21:22:01 2014 us=677314 70.192.193.10:7095 [HTC6525LVW] Peer Connection Initiated with [AF_INET]70.192.193.10:7095
Thu Oct 23 21:22:01 2014 us=677391 HTC6525LVW/70.192.193.10:7095 MULTI_sva: pool returned IPv4=10.20.30.2, IPv6=(Not enabled)
Thu Oct 23 21:22:01 2014 us=677514 HTC6525LVW/70.192.193.10:7095 MULTI: Learn: 10.20.30.2 -> HTC6525LVW/70.192.193.10:7095
Thu Oct 23 21:22:01 2014 us=677562 HTC6525LVW/70.192.193.10:7095 MULTI: primary virtual IP for HTC6525LVW/70.192.193.10:7095: 10.20.30.2
Thu Oct 23 21:22:03 2014 us=645486 HTC6525LVW/70.192.193.10:7095 PUSH: Received control message: 'PUSH_REQUEST'
Thu Oct 23 21:22:03 2014 us=645546 HTC6525LVW/70.192.193.10:7095 send_push_reply(): safe_cap=940
Thu Oct 23 21:22:03 2014 us=645637 HTC6525LVW/70.192.193.10:7095 SENT CONTROL [HTC6525LVW]: 'PUSH_REPLY,redirect-gateway def1,route 192.168.10.0 255.255.255.0,dhcp-option DNS 192.168.10.104,route-gateway 10.20.30.1,topology subnet,ping 10,ping-restart 120,ifconfig 10.20.30.2 255.255.255.0' (status=1)
Thu Oct 23 21:22:07 2014 us=797255 HTC6525LVW/70.192.193.10:7095 Connection reset, restarting [0]
Thu Oct 23 21:22:07 2014 us=797294 HTC6525LVW/70.192.193.10:7095 SIGUSR1[soft,connection-reset] received, client-instance restarting
Thu Oct 23 21:22:07 2014 us=797534 TCP/UDP: Closing socket
Thu Oct 23 21:22:12 2014 us=65157 MULTI: multi_create_instance called
Thu Oct 23 21:22:12 2014 us=65222 Re-using SSL/TLS context
Thu Oct 23 21:22:12 2014 us=65261 LZO compression initialized
Thu Oct 23 21:22:12 2014 us=65351 Control Channel MTU parms [ L:1544 D:168 EF:68 EB:0 ET:0 EL:0 ]
Thu Oct 23 21:22:12 2014 us=65380 Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Thu Oct 23 21:22:12 2014 us=65425 Local Options String: 'V4,dev-type tun,link-mtu 1544,tun-mtu 1500,proto TCPv4_SERVER,comp-lzo,cipher BF-CBC,auth SHA1,keysize 128,tls-auth,key-method 2,tls-server'
Thu Oct 23 21:22:12 2014 us=65439 Expected Remote Options String: 'V4,dev-type tun,link-mtu 1544,tun-mtu 1500,proto TCPv4_CLIENT,comp-lzo,cipher BF-CBC,auth SHA1,keysize 128,tls-auth,key-method 2,tls-client'
Thu Oct 23 21:22:12 2014 us=65463 Local Options hash (VER=V4): '64e96fc1'
Thu Oct 23 21:22:12 2014 us=65482 Expected Remote Options hash (VER=V4): '863ad621'
Thu Oct 23 21:22:12 2014 us=65512 TCP connection established with [AF_INET]70.192.193.10:7075
Thu Oct 23 21:22:12 2014 us=65527 TCPv4_SERVER link local: [undef]
Thu Oct 23 21:22:12 2014 us=65541 TCPv4_SERVER link remote: [AF_INET]70.192.193.10:7075
Thu Oct 23 21:22:12 2014 us=995672 70.192.193.10:7075 TLS: Initial packet from [AF_INET]70.192.193.10:7075, sid=8370fba8 be877713
Thu Oct 23 21:22:15 2014 us=406167 70.192.193.10:7075 VERIFY OK: depth=1, C=US, ST=MD, L=Gaithersburg, O=chrisbb61.com, OU=BOYDHOUSE, CN=chrisbb61, name=EasyRSA, emailAddress=chrisbb61@chrisbb61.com
Thu Oct 23 21:22:15 2014 us=406456 70.192.193.10:7075 VERIFY OK: depth=0, C=US, ST=MD, L=Gaithersburg, O=chrisbb61.com, OU=BOYDHOUSE, CN=HTC6525LVW, name=EasyRSA, emailAddress=chrisbb61@chrisbb61.com
Thu Oct 23 21:22:15 2014 us=785345 70.192.193.10:7075 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Thu Oct 23 21:22:15 2014 us=785400 70.192.193.10:7075 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Oct 23 21:22:15 2014 us=785524 70.192.193.10:7075 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Thu Oct 23 21:22:15 2014 us=785575 70.192.193.10:7075 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Oct 23 21:22:16 2014 us=57199 70.192.193.10:7075 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Thu Oct 23 21:22:16 2014 us=57278 70.192.193.10:7075 [HTC6525LVW] Peer Connection Initiated with [AF_INET]70.192.193.10:7075
Thu Oct 23 21:22:16 2014 us=57349 HTC6525LVW/70.192.193.10:7075 MULTI_sva: pool returned IPv4=10.20.30.2, IPv6=(Not enabled)
Thu Oct 23 21:22:16 2014 us=57462 HTC6525LVW/70.192.193.10:7075 MULTI: Learn: 10.20.30.2 -> HTC6525LVW/70.192.193.10:7075
Thu Oct 23 21:22:16 2014 us=57507 HTC6525LVW/70.192.193.10:7075 MULTI: primary virtual IP for HTC6525LVW/70.192.193.10:7075: 10.20.30.2
Thu Oct 23 21:22:18 2014 us=428985 HTC6525LVW/70.192.193.10:7075 PUSH: Received control message: 'PUSH_REQUEST'
Thu Oct 23 21:22:18 2014 us=429047 HTC6525LVW/70.192.193.10:7075 send_push_reply(): safe_cap=940
Thu Oct 23 21:22:18 2014 us=429136 HTC6525LVW/70.192.193.10:7075 SENT CONTROL [HTC6525LVW]: 'PUSH_REPLY,redirect-gateway def1,route 192.168.10.0 255.255.255.0,dhcp-option DNS 192.168.10.104,route-gateway 10.20.30.1,topology subnet,ping 10,ping-restart 120,ifconfig 10.20.30.2 255.255.255.0' (status=1)

```


Client Log:

```

[FONT=arial]2014-10-23 21:25:23 Running on HTC6525LVW (MSM8974) htc, Android API 19, version 0.6.17, official build[/FONT]
[FONT=arial]2014-10-23 21:25:23 Log cleared.[/FONT]
[FONT=arial]2014-10-23 21:25:40 Building configuration&#8230;[/FONT]
[FONT=arial]2014-10-23 21:25:42 started Socket Thread[/FONT]
[FONT=arial]2014-10-23 21:25:43 P:Initializing Google Breakpad![/FONT]
[FONT=arial]2014-10-23 21:25:43 Current Parameter Settings:[/FONT]
[FONT=arial]2014-10-23 21:25:43   config = '/data/data/de.blinkt.openvpn/[/FONT][FONT=arial]cache/android.conf'[/FONT]
[FONT=arial]2014-10-23 21:25:43   mode = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   show_ciphers = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   show_digests = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   show_engines = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   genkey = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   key_pass_file = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   show_tls_ciphers = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   connect_retry_max = 5[/FONT]
[FONT=arial]2014-10-23 21:25:43 Connection profiles [0]:[/FONT]
[FONT=arial]2014-10-23 21:25:43   proto = tcp-client[/FONT]
[FONT=arial]2014-10-23 21:25:43   local = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   local_port = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote = '[/FONT][chrisdom.com]("http://chrisbb61.com/")[FONT=arial]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_port = '1194'[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_float = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   bind_defined = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   bind_local = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   bind_ipv6_only = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   connect_retry_seconds = 5[/FONT]
[FONT=arial]2014-10-23 21:25:43   connect_timeout = 10[/FONT]
[FONT=arial]2014-10-23 21:25:43   socks_proxy_server = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   socks_proxy_port = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   socks_proxy_retry = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   tun_mtu = 1500[/FONT]
[FONT=arial]2014-10-23 21:25:43   tun_mtu_defined = ENABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   link_mtu = 1500[/FONT]
[FONT=arial]2014-10-23 21:25:43   link_mtu_defined = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   tun_mtu_extra = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   tun_mtu_extra_defined = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   mtu_discover_type = -1[/FONT]
[FONT=arial]2014-10-23 21:25:43   fragment = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   mssfix = 1450[/FONT]
[FONT=arial]2014-10-23 21:25:43   explicit_exit_notification = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43 Connection profiles END[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_random = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   ipchange = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   dev = 'tun'[/FONT]
[FONT=arial]2014-10-23 21:25:43   dev_type = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   dev_node = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   lladdr = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   topology = 1[/FONT]
[FONT=arial]2014-10-23 21:25:43   tun_ipv6 = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   ifconfig_local = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   ifconfig_remote_netmask = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   ifconfig_noexec = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   ifconfig_nowarn = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   ifconfig_ipv6_local = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   ifconfig_ipv6_netbits = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   ifconfig_ipv6_remote = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   shaper = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   mtu_test = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   mlock = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   keepalive_ping = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   keepalive_timeout = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   inactivity_timeout = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   ping_send_timeout = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   ping_rec_timeout = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   ping_rec_timeout_action = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   ping_timer_remote = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   remap_sigusr1 = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   persist_tun = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   persist_local_ip = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   persist_remote_ip = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   persist_key = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   passtos = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   resolve_retry_seconds = 60[/FONT]
[FONT=arial]2014-10-23 21:25:43   resolve_in_advance = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   username = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   groupname = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   chroot_dir = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   cd_dir = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   writepid = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   up_script = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   down_script = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   down_pre = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   up_restart = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   up_delay = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   daemon = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   inetd = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   log = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   suppress_timestamps = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   machine_readable_output = ENABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   nice = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   verbosity = 4[/FONT]
[FONT=arial]2014-10-23 21:25:43   mute = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   gremlin = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   status_file = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   status_file_version = 1[/FONT]
[FONT=arial]2014-10-23 21:25:43   status_file_update_freq = 60[/FONT]
[FONT=arial]2014-10-23 21:25:43   occ = ENABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   rcvbuf = 65536[/FONT]
[FONT=arial]2014-10-23 21:25:43   sndbuf = 65536[/FONT]
[FONT=arial]2014-10-23 21:25:43   sockflags = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   fast_io = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   comp.alg = 2[/FONT]
[FONT=arial]2014-10-23 21:25:43   comp.flags = 1[/FONT]
[FONT=arial]2014-10-23 21:25:43   route_script = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   route_default_gateway = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   route_default_metric = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   route_noexec = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   route_delay = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   route_delay_window = 30[/FONT]
[FONT=arial]2014-10-23 21:25:43   route_delay_defined = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   route_nopull = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   route_gateway_via_dhcp = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   allow_pull_fqdn = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   route [/FONT][0.0.0.0/0.0.0.0/vpn_gateway/nil]("http://0.0.0.0/0.0.0.0/vpn_gateway/nil")
[FONT=arial]2014-10-23 21:25:43   management_addr = '/data/data/de.blinkt.openvpn/[/FONT][FONT=arial]cache/mgmtsocket'[/FONT]
[FONT=arial]2014-10-23 21:25:43   management_port = 'unix'[/FONT]
[FONT=arial]2014-10-23 21:25:43   management_user_pass = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   management_log_history_cache = 250[/FONT]
[FONT=arial]2014-10-23 21:25:43   management_echo_buffer_size = 100[/FONT]
[FONT=arial]2014-10-23 21:25:43   management_write_peer_info_[/FONT][FONT=arial]file = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   management_client_user = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   management_client_group = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   management_flags = 294[/FONT]
[FONT=arial]2014-10-23 21:25:43   shared_secret_file = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   key_direction = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   ciphername_defined = ENABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   ciphername = 'BF-CBC'[/FONT]
[FONT=arial]2014-10-23 21:25:43   authname_defined = ENABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   authname = 'SHA1'[/FONT]
[FONT=arial]2014-10-23 21:25:43   prng_hash = 'SHA1'[/FONT]
[FONT=arial]2014-10-23 21:25:43   prng_nonce_secret_len = 16[/FONT]
[FONT=arial]2014-10-23 21:25:43   keysize = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   engine = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   replay = ENABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   mute_replay_warnings = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   replay_window = 64[/FONT]
[FONT=arial]2014-10-23 21:25:43   replay_time = 15[/FONT]
[FONT=arial]2014-10-23 21:25:43   packet_id_file = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   use_iv = ENABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   test_crypto = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   tls_server = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   tls_client = ENABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   key_method = 2[/FONT]
[FONT=arial]2014-10-23 21:25:43   ca_file = '[[INLINE]]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   ca_path = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   dh_file = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   cert_file = '[[INLINE]]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   priv_key_file = '[[INLINE]]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   pkcs12_file = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   cipher_list = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   tls_verify = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   tls_export_cert = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   verify_x509_type = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   verify_x509_name = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   crl_file = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   ns_cert_type = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_ku[i] = 160[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_ku[i] = 136[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_ku[i] = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_ku[i] = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_ku[i] = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_ku[i] = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_ku[i] = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_ku[i] = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_ku[i] = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_ku[i] = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_ku[i] = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_ku[i] = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_ku[i] = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_ku[i] = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_ku[i] = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_ku[i] = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   remote_cert_eku = 'TLS Web Server Authentication'[/FONT]
[FONT=arial]2014-10-23 21:25:43   ssl_flags = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   tls_timeout = 2[/FONT]
[FONT=arial]2014-10-23 21:25:43   renegotiate_bytes = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   renegotiate_packets = 0[/FONT]
[FONT=arial]2014-10-23 21:25:43   renegotiate_seconds = 3600[/FONT]
[FONT=arial]2014-10-23 21:25:43   handshake_window = 60[/FONT]
[FONT=arial]2014-10-23 21:25:43   transition_window = 3600[/FONT]
[FONT=arial]2014-10-23 21:25:43   single_session = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   push_peer_info = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   tls_exit = DISABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   tls_auth_file = '[[INLINE]]'[/FONT]
[FONT=arial]2014-10-23 21:25:43   client = ENABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   pull = ENABLED[/FONT]
[FONT=arial]2014-10-23 21:25:43   auth_user_pass_file = '[UNDEF]'[/FONT]
[FONT=arial]2014-10-23 21:25:43 OpenVPN 2.4-icsopenvpn [git:icsopenvpn_615-[/FONT][FONT=arial]c430ab0e0cef9994] android-14-armeabi-v7a [SSL (OpenSSL)] [LZO] [SNAPPY] [LZ4] [EPOLL] [MH] [IPv6] built on Jun 24 2014[/FONT]
[FONT=arial]2014-10-23 21:25:43 library versions: OpenSSL 1.0.1h 5 Jun 2014, LZO 2.06[/FONT]
[FONT=arial]2014-10-23 21:25:43 MANAGEMENT: Connected to management server at /data/data/de.blinkt.openvpn/[/FONT][FONT=arial]cache/mgmtsocket[/FONT]
[FONT=arial]2014-10-23 21:25:43 MANAGEMENT: CMD 'hold release'[/FONT]
[FONT=arial]2014-10-23 21:25:43 Control Channel Authentication: tls-auth using INLINE static key file[/FONT]
[FONT=arial]2014-10-23 21:25:43 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication[/FONT]
[FONT=arial]2014-10-23 21:25:43 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication[/FONT]
[FONT=arial]2014-10-23 21:25:43 LZO compression initializing[/FONT]
[FONT=arial]2014-10-23 21:25:43 Control Channel MTU parms [ L:1544 D:168 EF:68 EB:0 ET:0 EL:0 ][/FONT]
[FONT=arial]2014-10-23 21:25:43 Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:393 ET:0 EL:0 ][/FONT]
[FONT=arial]2014-10-23 21:25:43 Local Options String: 'V4,dev-type tun,link-mtu 1544,tun-mtu 1500,proto TCPv4_CLIENT,comp-lzo,cipher BF-CBC,auth SHA1,keysize 128,tls-auth,key-method 2,tls-client'[/FONT]
[FONT=arial]2014-10-23 21:25:43 Expected Remote Options String: 'V4,dev-type tun,link-mtu 1544,tun-mtu 1500,proto TCPv4_SERVER,comp-lzo,cipher BF-CBC,auth SHA1,keysize 128,tls-auth,key-method 2,tls-server'[/FONT]
[FONT=arial]2014-10-23 21:25:43 Local Options hash (VER=V4): '863ad621'[/FONT]
[FONT=arial]2014-10-23 21:25:43 Expected Remote Options hash (VER=V4): '64e96fc1'[/FONT]
[FONT=arial]2014-10-23 21:25:43 TCP/UDP: Preserving recently used remote address: [AF_INET][/FONT][69.140.221.39:1194]("http://69.140.221.39:1194/")
[FONT=arial]2014-10-23 21:25:43 Socket Buffers: R=[1048576->131072] S=[524288->131072][/FONT]
[FONT=arial]2014-10-23 21:25:43 Attempting to establish TCP connection with [AF_INET][/FONT][69.140.221.39:1194]("http://69.140.221.39:1194/")[FONT=arial] [nonblock][/FONT]
[FONT=arial]2014-10-23 21:25:43 Protecting socket fd 4[/FONT]
[FONT=arial]2014-10-23 21:25:43 MANAGEMENT: CMD 'bytecount 2'[/FONT]
[FONT=arial]2014-10-23 21:25:43 MANAGEMENT: CMD 'needok 'PROTECTFD' ok'[/FONT]
[FONT=arial]2014-10-23 21:25:43 MANAGEMENT: CMD 'state on'[/FONT]
[FONT=arial]2014-10-23 21:25:43 Network Status: CONNECTED LTE to mobile vzwinternet[/FONT]
[FONT=arial]2014-10-23 21:25:44 TCP connection established with [AF_INET][/FONT][69.140.221.39:1194]("http://69.140.221.39:1194/")
[FONT=arial]2014-10-23 21:25:44 Protecting socket fd 4[/FONT]
[FONT=arial]2014-10-23 21:25:44 MANAGEMENT: CMD 'needok 'PROTECTFD' ok'[/FONT]
[FONT=arial]2014-10-23 21:25:44 TCP_CLIENT link local: (not bound)[/FONT]
[FONT=arial]2014-10-23 21:25:45 Validating certificate key usage[/FONT]
[FONT=arial]2014-10-23 21:25:45 ++ Certificate has key usage  00a0, expects 00a0[/FONT]
[FONT=arial]2014-10-23 21:25:45 VERIFY KU OK[/FONT]
[FONT=arial]2014-10-23 21:25:45 Validating certificate extended key usage[/FONT]
[FONT=arial]2014-10-23 21:25:45 ++ Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server Authentication[/FONT]
[FONT=arial]2014-10-23 21:25:45 VERIFY EKU OK[/FONT]
[FONT=arial]2014-10-23 21:25:47 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key[/FONT]
[FONT=arial]2014-10-23 21:25:47 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication[/FONT]
[FONT=arial]2014-10-23 21:25:47 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key[/FONT]
[FONT=arial]2014-10-23 21:25:47 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication[/FONT]
[FONT=arial]2014-10-23 21:25:47 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA[/FONT]
[FONT=arial]2014-10-23 21:25:48 MANAGEMENT: >STATE:1414113948,GET_CONFIG,,[/FONT][FONT=arial],[/FONT]
[FONT=arial]2014-10-23 21:25:49 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)[/FONT]
[FONT=arial]2014-10-23 21:25:50 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1,route 192.168.10.0 255.255.255.0,dhcp-option DNS 192.168.10.104,route-gateway 10.20.30.1,topology subnet,ping 10,ping-restart 120,ifconfig 10.20.30.2 255.255.255.0'[/FONT]
[FONT=arial]2014-10-23 21:25:50 OPTIONS IMPORT: timers and/or timeouts modified[/FONT]
[FONT=arial]2014-10-23 21:25:50 OPTIONS IMPORT: --ifconfig/up options modified[/FONT]
[FONT=arial]2014-10-23 21:25:50 OPTIONS IMPORT: route options modified[/FONT]
[FONT=arial]2014-10-23 21:25:50 OPTIONS IMPORT: route-related options modified[/FONT]
[FONT=arial]2014-10-23 21:25:50 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified[/FONT]
[FONT=arial]2014-10-23 21:25:50 ROUTE_GATEWAY [/FONT][10.175.199.213/255.255.255.248]("http://10.175.199.213/255.255.255.248")[FONT=arial] IFACE=rmnet0 HWADDR=00:00:00:00:00:00[/FONT]
[FONT=arial]2014-10-23 21:25:50 ROUTE6: default_gateway=UNDEF[/FONT]
[FONT=arial]2014-10-23 21:25:50 OpenVPN ROUTE6: OpenVPN needs a gateway parameter for a --route-ipv6 option and no default was specified by either --route-ipv6-gateway or --ifconfig-ipv6 options[/FONT]
[FONT=arial]2014-10-23 21:25:50 OpenVPN ROUTE: failed to parse/resolve route for host/network: ::/0[/FONT]
[FONT=arial]2014-10-23 21:25:50 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0[/FONT]
[FONT=arial]2014-10-23 21:25:50 MANAGEMENT: >STATE:1414113950,ASSIGN_IP,,[/FONT][FONT=arial]10.20.30.2,[/FONT]
[FONT=arial]2014-10-23 21:25:50 MANAGEMENT: CMD 'needok 'IFCONFIG' ok'[/FONT]
[FONT=arial]2014-10-23 21:25:50 MANAGEMENT: CMD 'needok 'ROUTE' ok'[/FONT]
[FONT=arial]2014-10-23 21:25:50 MANAGEMENT: CMD 'needok 'ROUTE' ok'[/FONT]
[FONT=arial]2014-10-23 21:25:50 MANAGEMENT: >STATE:1414113950,ADD_ROUTES,,[/FONT][FONT=arial],[/FONT]
[FONT=arial]2014-10-23 21:25:50 MANAGEMENT: CMD 'needok 'ROUTE' ok'[/FONT]
[FONT=arial]2014-10-23 21:25:50 MANAGEMENT: CMD 'needok 'ROUTE' ok'[/FONT]
[FONT=arial]2014-10-23 21:25:50 MANAGEMENT: CMD 'needok 'DNSSERVER' ok'[/FONT]
[FONT=arial]2014-10-23 21:25:50 MANAGEMENT: CMD 'needok 'PERSIST_TUN_ACTION' OPEN_BEFORE_CLOSE'[/FONT]
[FONT=arial]2014-10-23 21:25:50 Opening tun interface:[/FONT]
[FONT=arial]2014-10-23 21:25:50 Local IPv4: [/FONT][10.20.30.2/24]("http://10.20.30.2/24")[FONT=arial] IPv6: null MTU: 1500[/FONT]
[FONT=arial]2014-10-23 21:25:50 DNS Server: 192.168.10.104, Domain: null[/FONT]
[FONT=arial]2014-10-23 21:25:50 Routes: [/FONT][0.0.0.0/1]("http://0.0.0.0/1")[FONT=arial], [/FONT][0.0.0.0/0]("http://0.0.0.0/0")[FONT=arial], [/FONT][128.0.0.0/1]("http://128.0.0.0/1")[FONT=arial], [/FONT][192.168.10.0/24]("http://192.168.10.0/24")
[FONT=arial]2014-10-23 21:25:50 Routes excluded:  [/FONT]
[FONT=arial]2014-10-23 21:25:50 VpnService routes installed: [/FONT][0.0.0.0/0]("http://0.0.0.0/0")
[FONT=arial]2014-10-23 21:25:50 MANAGEMENT: CMD 'needok 'OPENTUN' ok'[/FONT]
[FONT=arial]2014-10-23 21:25:50 Initialization Sequence Completed[/FONT]
[FONT=arial]2014-10-23 21:25:50 MANAGEMENT: >STATE:1414113950,CONNECTED,[/FONT][FONT=arial]SUCCESS,10.20.30.2,69.140.221.[/FONT][FONT=arial]39[/FONT]
[FONT=arial]2014-10-23 21:25:57 MANAGEMENT: CMD 'signal SIGINT'[/FONT]
[FONT=arial]2014-10-23 21:25:57 TCP/UDP: Closing socket[/FONT]
[FONT=arial]2014-10-23 21:25:57 Sorry, deleting routes on Android is not possible. The VpnService API allows routes to be set on connect only.[/FONT]
[FONT=arial]2014-10-23 21:25:57 Sorry, deleting routes on Android is not possible. The VpnService API allows routes to be set on connect only.[/FONT]
[FONT=arial]2014-10-23 21:25:57 Closing TUN/TAP interface[/FONT]
[FONT=arial]2014-10-23 21:25:59 SIGINT[hard,] received, process exiting[/FONT]
[FONT=arial]2014-10-23 21:25:59 MANAGEMENT: >STATE:1414113959,EXITING,[/FONT][FONT=arial]SIGINT,,[/FONT]

```

---

### Post by weatherman2 on 2014-10-23
I haven't setup a TUN OpenVPN server in a while - the last time I did was on a DD-WRT router.  I used this config:

[http://www.dd-wrt.com/wiki/index.php/VPN_(the_easy_way)_v24%2B](http://www.dd-wrt.com/wiki/index.php/VPN_(the_easy_way)_v24%2B)

Taking a wild guess, these iptables lines might be what you need:

```

iptables -I FORWARD 1 --source 10.20.30.0/24 -j ACCEPT
iptables -I FORWARD -i p1p1 -o tun0 -j ACCEPT
iptables -I FORWARD -i tun0 -o p1p1 -j ACCEPT

```

---

