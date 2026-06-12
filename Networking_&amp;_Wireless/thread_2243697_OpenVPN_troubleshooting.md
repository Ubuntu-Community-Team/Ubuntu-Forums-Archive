---
title: "OpenVPN troubleshooting"
date: 2014-09-10
forum: Networking &amp; Wireless
---

### Post by brandon-bilbo on 2014-09-10
So I have what I thought was a "working" configuration for my VPN setup. I have a Ubuntu 12.04 server at home that is the gateway to my home LAN (its got 2 NICs, one connected to internet, other to my LAN, obviously). I've been using it as an OpenVPN server to route all my web traffic and access my home LAN from my work laptop (screw you corporate web filters). This has been working for over a year. I recently bought a new laptop and want to do the same with this computer (both laptops running window 8.1). I made a new certificate for my new laptop, and used the same config that the working laptop uses. I connect to the vpn, everything looks good, but it's not. Once I'm connected to the VPN, I cannot ping anything, connect to the internet, etc.

The VPN network is 10.8.0.0 and my home network is 192.168.0.0. the working laptop always gets 10.8.0.6 and the new one gets 10.8.0.2. I've disabled the windows firewall on the new laptop to make sure that's not the issue. I'd assume my firewall/nat/ipforwarding/etc is all good on my server since the other client works fine. 

Configs.

server.conf
```

port 1194
proto udp
topology subnet
dev tun
ca ca.cert
key key.key
dh dh1024.pem

server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.0.0 255.255.255.0"
push "redirect-gateway def1"
push "dhcp-option DNS 192.168.0.3"
keepalive 10 120

comp-lzo
persist-key
persist-tun
log openvpn.log
verb 4

```

client.conf
```

client
remote ipaddress
port 1194
proto udp
dev tun
dev-type tun
ns-cert-type server
reneg-sec 86400
comp-lzo yes
verb 3
ca ca.crt
cert "C:\\Program Files\\OpenVPN\\config\\client1.crt"
key "C:\\Program Files\\OpenVPN\\config\\client1.key"
management 127.0.0.1 1194
management-hold
management-query-passwords
auth-retry interact

```

Anything else you would like me to post for you would be my pleasure. All input appreciated. Thanks.

P.S. I set all this up a year ago so I'm a little rusty on all my knowledge since it's been working and have not had to mess with it

---

### Post by weatherman2 on 2014-09-10
Look at your server openvpn.log file (probably in /etc/openvpn by default).  Look for the interactions with the new laptop - you should see messages that may help you debug.

I'd probably go back and use your original certificates (from laptop #1) for debugging and get that to work first, as you know they all work with laptop #1.  Once you get that to work, then if you really want to use separate certificates try the second set and if they don't work - then you can work from there.

FYI, sometimes due to time zone differences, brand new certificates won't work right after you generate them - it may take a few hours until they become valid if the server and the generating machine don't agree on the time.

---

### Post by brandon-bilbo on 2014-09-10
these certificates were generated months ago, and I put this problem on the back burner because I was so busy. I think they are good, here's why: I uninstalled openvpn client from new laptop (laptop #2), and installed an older version that laptop #1 is using. I connected, and it worked!!!! for about 5 minutes.. then back to same problem. no errors in the log, which I post anyway. It's mainly full of that bad source address from client, but it does that even when laptop #1 connects and works.

```

Wed Sep 10 15:12:10 2014 us=711912 209.64.127.194:5897 TLS: new session incoming connection from [AF_INET]209.64.127.194:5897
Wed Sep 10 15:12:11 2014 us=448839 209.64.127.194:5897 VERIFY OK: depth=1, /C=US/ST=TX/L=Seabrook/O=twlc/OU=cs/CN=provizon.org/name=Brandon_Bilbo/emailAddress=brandon.bilbo@gmail.com
Wed Sep 10 15:12:11 2014 us=448991 209.64.127.194:5897 VERIFY OK: depth=0, /C=US/ST=TX/L=Seabrook/O=twlc/OU=cs/CN=provizon.org/name=Brandon/emailAddress=brandon.bilbo@gmail.com
Wed Sep 10 15:12:17 2014 us=479567 209.64.127.194:5897 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Sep 10 15:12:17 2014 us=479609 209.64.127.194:5897 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Sep 10 15:12:17 2014 us=479672 209.64.127.194:5897 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Sep 10 15:12:17 2014 us=479688 209.64.127.194:5897 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Sep 10 15:12:17 2014 us=479719 209.64.127.194:5897 TLS: move_session: dest=TM_ACTIVE src=TM_UNTRUSTED reinit_src=1
Wed Sep 10 15:12:17 2014 us=479787 209.64.127.194:5897 TLS: tls_multi_process: untrusted session promoted to semi-trusted
Wed Sep 10 15:12:17 2014 us=514016 209.64.127.194:5897 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Wed Sep 10 15:12:17 2014 us=514075 209.64.127.194:5897 [provizon.org] Peer Connection Initiated with [AF_INET]209.64.127.194:5897
Wed Sep 10 15:12:17 2014 us=514135 provizon.org/209.64.127.194:5897 MULTI_sva: pool returned IPv4=10.8.0.2, IPv6=1::2000:0:e17f:0
Wed Sep 10 15:12:17 2014 us=514178 provizon.org/209.64.127.194:5897 MULTI: Learn: 10.8.0.2 -> provizon.org/209.64.127.194:5897
Wed Sep 10 15:12:17 2014 us=514194 provizon.org/209.64.127.194:5897 MULTI: primary virtual IP for provizon.org/209.64.127.194:5897: 10.8.0.2
Wed Sep 10 15:12:19 2014 us=839639 provizon.org/209.64.127.194:5897 PUSH: Received control message: 'PUSH_REQUEST'
Wed Sep 10 15:12:19 2014 us=839698 provizon.org/209.64.127.194:5897 send_push_reply(): safe_cap=960
Wed Sep 10 15:12:19 2014 us=839737 provizon.org/209.64.127.194:5897 SENT CONTROL [provizon.org]: 'PUSH_REPLY,route 192.168.0.0 255.255.255.0,redirect-gateway def1,dhcp-option DNS 192.168.0.3,route-gateway 10.8.0.1,topology subnet,ping 10,ping-restart 120,ifconfig 10.8.0.2 255.255.255.0' (status=1)
Wed Sep 10 15:12:19 2014 us=953008 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:19 2014 us=968649 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:19 2014 us=983055 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:20 2014 us=86240 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [::], packet dropped
Wed Sep 10 15:12:20 2014 us=146172 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:20 2014 us=148397 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:20 2014 us=149425 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:20 2014 us=476975 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:20 2014 us=488839 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:22 2014 us=554346 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:22 2014 us=556044 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:22 2014 us=585616 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:22 2014 us=645934 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:22 2014 us=873067 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:24 2014 us=239489 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:24 2014 us=242740 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:24 2014 us=640374 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:24 2014 us=748527 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:24 2014 us=750544 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:24 2014 us=795915 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:24 2014 us=845500 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:24 2014 us=868780 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:25 2014 us=23039 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:25 2014 us=52724 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:25 2014 us=64556 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:25 2014 us=311014 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:25 2014 us=377238 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:25 2014 us=453043 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:25 2014 us=454071 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:25 2014 us=458183 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:25 2014 us=474183 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:25 2014 us=489977 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:25 2014 us=561582 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:25 2014 us=653178 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:25 2014 us=851970 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:25 2014 us=852662 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:25 2014 us=879951 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:25 2014 us=880652 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=12624 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=22591 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=23703 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=253978 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=375438 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=399480 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=430095 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=435077 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=487730 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=505053 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=533342 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=582496 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=606086 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=692949 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=843158 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=844482 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=876449 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=982798 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:26 2014 us=988520 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:27 2014 us=144108 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:27 2014 us=336649 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:27 2014 us=496758 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:27 2014 us=496833 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:27 2014 us=520533 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:27 2014 us=543603 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:27 2014 us=544668 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:27 2014 us=547813 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:27 2014 us=562135 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:27 2014 us=756767 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:28 2014 us=86436 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:28 2014 us=91705 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:28 2014 us=92694 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:28 2014 us=153299 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:28 2014 us=272905 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:28 2014 us=412140 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:28 2014 us=613358 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:28 2014 us=618008 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:28 2014 us=623007 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:28 2014 us=852945 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:28 2014 us=854706 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:29 2014 us=51580 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:29 2014 us=88690 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:29 2014 us=155455 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:29 2014 us=157184 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:29 2014 us=183243 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:29 2014 us=641974 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:29 2014 us=762363 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:29 2014 us=962594 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:30 2014 us=193671 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:30 2014 us=218589 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:30 2014 us=280973 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:30 2014 us=294593 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:30 2014 us=309908 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:30 2014 us=492454 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:30 2014 us=579104 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:30 2014 us=631347 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:30 2014 us=983560 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:30 2014 us=986960 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:31 2014 us=190706 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:31 2014 us=376111 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:31 2014 us=592904 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:31 2014 us=612415 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:31 2014 us=741897 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:32 2014 us=375313 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped
Wed Sep 10 15:12:32 2014 us=591171 provizon.org/209.64.127.194:5897 MULTI: bad source address from client [fe80::d12e:1372:5802:efaa], packet dropped

```

i've disconnected and reconnected several times, but it only worked for a few minutes after the initial installation. I can't reproduce or explain that.

---

### Post by brandon-bilbo on 2014-09-10
well I think I found a place to start digging, can't believe I didn't notice this before. Here is the log from laptop#2 client.

```

Wed Sep 10 15:12:16 2014 OpenVPN 2.3.2 x86_64-w64-mingw32 [SSL (OpenSSL)] [LZO] [PKCS11] [eurephia] [IPv6] built on Aug  7 2014
Enter Management Password:
Wed Sep 10 15:12:16 2014 MANAGEMENT: TCP Socket listening on [AF_INET]127.0.0.1:25340
Wed Sep 10 15:12:16 2014 Need hold release from management interface, waiting...
Wed Sep 10 15:12:16 2014 MANAGEMENT: Client connected from [AF_INET]127.0.0.1:25340
Wed Sep 10 15:12:16 2014 MANAGEMENT: CMD 'state on'
Wed Sep 10 15:12:16 2014 MANAGEMENT: CMD 'log all on'
Wed Sep 10 15:12:16 2014 MANAGEMENT: CMD 'hold off'
Wed Sep 10 15:12:16 2014 MANAGEMENT: CMD 'hold release'
Wed Sep 10 15:12:17 2014 Socket Buffers: R=[65536->65536] S=[65536->65536]
Wed Sep 10 15:12:17 2014 UDPv4 link local (bound): [undef]
Wed Sep 10 15:12:17 2014 UDPv4 link remote: [AF_INET]73.183.129.168:1194
Wed Sep 10 15:12:17 2014 MANAGEMENT: >STATE:1410379937,WAIT,,,
Wed Sep 10 15:12:18 2014 TLS Error: Unroutable control packet received from [AF_INET]73.183.129.168:1194 (si=3 op=P_CONTROL_V1)
Wed Sep 10 15:12:19 2014 TLS Error: Unroutable control packet received from [AF_INET]73.183.129.168:1194 (si=3 op=P_CONTROL_V1)
Wed Sep 10 15:12:19 2014 MANAGEMENT: >STATE:1410379939,AUTH,,,
Wed Sep 10 15:12:19 2014 TLS: Initial packet from [AF_INET]73.183.129.168:1194, sid=339f1500 03168416
Wed Sep 10 15:12:19 2014 TLS Error: Unroutable control packet received from [AF_INET]73.183.129.168:1194 (si=3 op=P_CONTROL_V1)
Wed Sep 10 15:12:19 2014 VERIFY OK: depth=1, C=US, ST=TX, L=Seabrook, O=twlc, OU=cs, CN=provizon.org, name=Brandon Bilbo, emailAddress=brandon.bilbo@gmail.com
Wed Sep 10 15:12:19 2014 VERIFY OK: nsCertType=SERVER
Wed Sep 10 15:12:19 2014 VERIFY OK: depth=0, C=US, ST=tx, L=seabrook, O=twlc, OU=cs, CN=provizon.org, name=brandon, emailAddress=brandon.bilbo@gmail.com
Wed Sep 10 15:12:21 2014 TLS Error: Unroutable control packet received from [AF_INET]73.183.129.168:1194 (si=3 op=P_CONTROL_V1)
Wed Sep 10 15:12:26 2014 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Sep 10 15:12:26 2014 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Sep 10 15:12:26 2014 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Sep 10 15:12:26 2014 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Sep 10 15:12:26 2014 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Wed Sep 10 15:12:26 2014 [provizon.org] Peer Connection Initiated with [AF_INET]73.183.129.168:1194
Wed Sep 10 15:12:27 2014 MANAGEMENT: >STATE:1410379947,GET_CONFIG,,,
Wed Sep 10 15:12:28 2014 SENT CONTROL [provizon.org]: 'PUSH_REQUEST' (status=1)
Wed Sep 10 15:12:28 2014 PUSH: Received control message: 'PUSH_REPLY,route 192.168.0.0 255.255.255.0,redirect-gateway def1,dhcp-option DNS 192.168.0.3,route-gateway 10.8.0.1,topology subnet,ping 10,ping-restart 120,ifconfig 10.8.0.2 255.255.255.0'
Wed Sep 10 15:12:28 2014 OPTIONS IMPORT: timers and/or timeouts modified
Wed Sep 10 15:12:28 2014 OPTIONS IMPORT: --ifconfig/up options modified
Wed Sep 10 15:12:28 2014 OPTIONS IMPORT: route options modified
Wed Sep 10 15:12:28 2014 OPTIONS IMPORT: route-related options modified
Wed Sep 10 15:12:28 2014 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Wed Sep 10 15:12:28 2014 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Wed Sep 10 15:12:28 2014 MANAGEMENT: >STATE:1410379948,ASSIGN_IP,,10.8.0.2,
Wed Sep 10 15:12:28 2014 open_tun, tt->ipv6=0
Wed Sep 10 15:12:28 2014 TAP-WIN32 device [Local Area Connection] opened: \\.\Global\{82DF7A0F-A3B7-47C3-BB54-7D8C0021A371}.tap
Wed Sep 10 15:12:28 2014 TAP-Windows Driver Version 9.9 
Wed Sep 10 15:12:28 2014 Set TAP-Windows TUN subnet mode network/local/netmask = 10.8.0.0/10.8.0.2/255.255.255.0 [SUCCEEDED]
Wed Sep 10 15:12:28 2014 Notified TAP-Windows driver to set a DHCP IP/netmask of 10.8.0.2/255.255.255.0 on interface {82DF7A0F-A3B7-47C3-BB54-7D8C0021A371} [DHCP-serv: 10.8.0.254, lease-time: 31536000]
Wed Sep 10 15:12:28 2014 Successful ARP Flush on interface [35] {82DF7A0F-A3B7-47C3-BB54-7D8C0021A371}
Wed Sep 10 15:12:33 2014 TEST ROUTES: 2/2 succeeded len=1 ret=1 a=0 u/d=up
Wed Sep 10 15:12:33 2014 C:\Windows\system32\route.exe ADD 73.183.129.168 MASK 255.255.255.255 192.168.1.1
Wed Sep 10 15:12:33 2014 ROUTE: CreateIpForwardEntry succeeded with dwForwardMetric1=30 and dwForwardType=4
Wed Sep 10 15:12:33 2014 Route addition via IPAPI succeeded [adaptive]
Wed Sep 10 15:12:33 2014 C:\Windows\system32\route.exe ADD 0.0.0.0 MASK 128.0.0.0 10.8.0.1
Wed Sep 10 15:12:33 2014 ROUTE: CreateIpForwardEntry succeeded with dwForwardMetric1=30 and dwForwardType=4
Wed Sep 10 15:12:33 2014 Route addition via IPAPI succeeded [adaptive]
Wed Sep 10 15:12:33 2014 C:\Windows\system32\route.exe ADD 128.0.0.0 MASK 128.0.0.0 10.8.0.1
Wed Sep 10 15:12:33 2014 ROUTE: CreateIpForwardEntry succeeded with dwForwardMetric1=30 and dwForwardType=4
Wed Sep 10 15:12:33 2014 Route addition via IPAPI succeeded [adaptive]
Wed Sep 10 15:12:33 2014 MANAGEMENT: >STATE:1410379953,ADD_ROUTES,,,
Wed Sep 10 15:12:33 2014 C:\Windows\system32\route.exe ADD 192.168.0.0 MASK 255.255.255.0 10.8.0.1
Wed Sep 10 15:12:33 2014 ROUTE: CreateIpForwardEntry succeeded with dwForwardMetric1=30 and dwForwardType=4
Wed Sep 10 15:12:33 2014 Route addition via IPAPI succeeded [adaptive]
Wed Sep 10 15:12:33 2014 Initialization Sequence Completed
Wed Sep 10 15:12:33 2014 MANAGEMENT: >STATE:1410379953,CONNECTED,SUCCESS,10.8.0.2,73.183.129.168

```

think this is my problem
> 


Wed Sep 10 15:12:18 2014 TLS Error: Unroutable control packet received from [AF_INET]73.183.129.168:1194 (si=3 op=P_CONTROL_V1)
Wed Sep 10 15:12:19 2014 TLS Error: Unroutable control packet received from [AF_INET]73.183.129.168:1194 (si=3 op=P_CONTROL_V1)


googling now

---

### Post by brandon-bilbo on 2014-09-10
that log was a fluke, they normally look like this from laptop #2 although the connection does not work.

```

Wed Sep 10 15:53:27 2014 OpenVPN 2.3.2 x86_64-w64-mingw32 [SSL (OpenSSL)] [LZO] [PKCS11] [eurephia] [IPv6] built on Aug  7 2014
Enter Management Password:
Wed Sep 10 15:53:27 2014 MANAGEMENT: TCP Socket listening on [AF_INET]127.0.0.1:25340
Wed Sep 10 15:53:27 2014 Need hold release from management interface, waiting...
Wed Sep 10 15:53:27 2014 MANAGEMENT: Client connected from [AF_INET]127.0.0.1:25340
Wed Sep 10 15:53:27 2014 MANAGEMENT: CMD 'state on'
Wed Sep 10 15:53:27 2014 MANAGEMENT: CMD 'log all on'
Wed Sep 10 15:53:27 2014 MANAGEMENT: CMD 'hold off'
Wed Sep 10 15:53:27 2014 MANAGEMENT: CMD 'hold release'
Wed Sep 10 15:53:27 2014 Socket Buffers: R=[65536->65536] S=[65536->65536]
Wed Sep 10 15:53:27 2014 UDPv4 link local (bound): [undef]
Wed Sep 10 15:53:27 2014 UDPv4 link remote: [AF_INET]73.183.129.168:1194
Wed Sep 10 15:53:27 2014 MANAGEMENT: >STATE:1410382407,WAIT,,,
Wed Sep 10 15:53:28 2014 MANAGEMENT: >STATE:1410382408,AUTH,,,
Wed Sep 10 15:53:28 2014 TLS: Initial packet from [AF_INET]73.183.129.168:1194, sid=1d20820b 9f8e4fd0
Wed Sep 10 15:53:28 2014 VERIFY OK: depth=1, C=US, ST=TX, L=Seabrook, O=twlc, OU=cs, CN=provizon.org, name=Brandon Bilbo, emailAddress=brandon.bilbo@gmail.com
Wed Sep 10 15:53:28 2014 VERIFY OK: nsCertType=SERVER
Wed Sep 10 15:53:28 2014 VERIFY OK: depth=0, C=US, ST=tx, L=seabrook, O=twlc, OU=cs, CN=provizon.org, name=brandon, emailAddress=brandon.bilbo@gmail.com
Wed Sep 10 15:53:33 2014 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Sep 10 15:53:33 2014 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Sep 10 15:53:33 2014 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Sep 10 15:53:33 2014 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Sep 10 15:53:33 2014 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Wed Sep 10 15:53:33 2014 [provizon.org] Peer Connection Initiated with [AF_INET]73.183.129.168:1194
Wed Sep 10 15:53:34 2014 MANAGEMENT: >STATE:1410382414,GET_CONFIG,,,
Wed Sep 10 15:53:35 2014 SENT CONTROL [provizon.org]: 'PUSH_REQUEST' (status=1)
Wed Sep 10 15:53:35 2014 PUSH: Received control message: 'PUSH_REPLY,route 192.168.0.0 255.255.255.0,redirect-gateway def1,dhcp-option DNS 192.168.0.3,route-gateway 10.8.0.1,topology subnet,ping 10,ping-restart 120,ifconfig 10.8.0.2 255.255.255.0'
Wed Sep 10 15:53:35 2014 OPTIONS IMPORT: timers and/or timeouts modified
Wed Sep 10 15:53:35 2014 OPTIONS IMPORT: --ifconfig/up options modified
Wed Sep 10 15:53:35 2014 OPTIONS IMPORT: route options modified
Wed Sep 10 15:53:35 2014 OPTIONS IMPORT: route-related options modified
Wed Sep 10 15:53:35 2014 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Wed Sep 10 15:53:35 2014 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Wed Sep 10 15:53:35 2014 MANAGEMENT: >STATE:1410382415,ASSIGN_IP,,10.8.0.2,
Wed Sep 10 15:53:35 2014 open_tun, tt->ipv6=0
Wed Sep 10 15:53:35 2014 TAP-WIN32 device [Local Area Connection] opened: \\.\Global\{82DF7A0F-A3B7-47C3-BB54-7D8C0021A371}.tap
Wed Sep 10 15:53:35 2014 TAP-Windows Driver Version 9.9 
Wed Sep 10 15:53:35 2014 Set TAP-Windows TUN subnet mode network/local/netmask = 10.8.0.0/10.8.0.2/255.255.255.0 [SUCCEEDED]
Wed Sep 10 15:53:35 2014 Notified TAP-Windows driver to set a DHCP IP/netmask of 10.8.0.2/255.255.255.0 on interface {82DF7A0F-A3B7-47C3-BB54-7D8C0021A371} [DHCP-serv: 10.8.0.254, lease-time: 31536000]
Wed Sep 10 15:53:35 2014 Successful ARP Flush on interface [35] {82DF7A0F-A3B7-47C3-BB54-7D8C0021A371}
Wed Sep 10 15:53:40 2014 TEST ROUTES: 2/2 succeeded len=1 ret=1 a=0 u/d=up
Wed Sep 10 15:53:40 2014 C:\Windows\system32\route.exe ADD 73.183.129.168 MASK 255.255.255.255 192.168.1.1
Wed Sep 10 15:53:40 2014 ROUTE: CreateIpForwardEntry succeeded with dwForwardMetric1=30 and dwForwardType=4
Wed Sep 10 15:53:40 2014 Route addition via IPAPI succeeded [adaptive]
Wed Sep 10 15:53:40 2014 C:\Windows\system32\route.exe ADD 0.0.0.0 MASK 128.0.0.0 10.8.0.1
Wed Sep 10 15:53:40 2014 ROUTE: CreateIpForwardEntry succeeded with dwForwardMetric1=30 and dwForwardType=4
Wed Sep 10 15:53:40 2014 Route addition via IPAPI succeeded [adaptive]
Wed Sep 10 15:53:40 2014 C:\Windows\system32\route.exe ADD 128.0.0.0 MASK 128.0.0.0 10.8.0.1
Wed Sep 10 15:53:40 2014 ROUTE: CreateIpForwardEntry succeeded with dwForwardMetric1=30 and dwForwardType=4
Wed Sep 10 15:53:40 2014 Route addition via IPAPI succeeded [adaptive]
Wed Sep 10 15:53:40 2014 MANAGEMENT: >STATE:1410382420,ADD_ROUTES,,,
Wed Sep 10 15:53:40 2014 C:\Windows\system32\route.exe ADD 192.168.0.0 MASK 255.255.255.0 10.8.0.1
Wed Sep 10 15:53:40 2014 ROUTE: CreateIpForwardEntry succeeded with dwForwardMetric1=30 and dwForwardType=4
Wed Sep 10 15:53:40 2014 Route addition via IPAPI succeeded [adaptive]
Wed Sep 10 15:53:40 2014 Initialization Sequence Completed
Wed Sep 10 15:53:40 2014 MANAGEMENT: >STATE:1410382420,CONNECTED,SUCCESS,10.8.0.2,73.183.129.168

```

---

