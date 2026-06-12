---
title: "OpenVPN connects, internet worked once stopped working"
date: 2014-06-11
forum: Networking &amp; Wireless
---

### Post by felix12 on 2014-06-11
The problem resolved itself while writing the thread... I have no idea what happened or why but nevertheless this is solved.

Today I used Openvpn to connect to my university network. It connects completely and sets up the routing (as far as I can tell correct):

Before tunnel:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```

After tunnel:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.8.0.1        128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
10.8.0.0        0.0.0.0         255.248.0.0     U     0      0        0 tun0
128.0.0.0       10.8.0.1        128.0.0.0       UG    0      0        0 tun0
131.188.12.11   192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```

OpenVPN Log:
```



Wed Jun 11 18:56:48 2014 Socket Buffers: R=[212992->131072] S=[212992->131072]
Wed Jun 11 18:56:48 2014 UDPv4 link local: [undef]
Wed Jun 11 18:56:48 2014 UDPv4 link remote: [AF_INET]131.188.12.11:1194
Wed Jun 11 18:56:49 2014 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Wed Jun 11 18:56:54 2014 VERIFY OK: depth=1, C=DE, ST=Bayern, L=Erlangen, O=Universitaet Erlangen-Nuernberg, OU=RRZE, CN=RRZE-VPN-CA, emailAddress=vpn@fau.de
Wed Jun 11 18:56:54 2014 VERIFY OK: nsCertType=SERVER
Wed Jun 11 18:56:54 2014 VERIFY OK: depth=0, C=DE, ST=Bayern, L=Erlangen, O=Universitaet Erlangen-Nuernberg, OU=RRZE, CN=openvpn.rrze.uni-erlangen.de, emailAddress=vpn@fau.de
Wed Jun 11 18:56:55 2014 Data Channel Encrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Wed Jun 11 18:56:55 2014 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Jun 11 18:56:55 2014 NOTE: --mute triggered...
Wed Jun 11 18:56:55 2014 3 variation(s) on previous 5 message(s) suppressed by --mute
Wed Jun 11 18:56:55 2014 [openvpn.rrze.uni-erlangen.de] Peer Connection Initiated with [AF_INET]131.188.12.11:1194
Wed Jun 11 18:56:58 2014 SENT CONTROL [openvpn.rrze.uni-erlangen.de]: 'PUSH_REQUEST' (status=1)
Wed Jun 11 18:56:58 2014 PUSH: Received control message: 'PUSH_REPLY,topology subnet,route-gateway 10.8.0.1,explicit-exit-notify,redirect-gateway autolocal def1 bypass-dhcp,dhcp-option DNS 131.188.0.10,dhcp-option DNS 131.188.0.11,ping 10,ping-exit 60,ifconfig 10.11.124.183 255.248.0.0'
Wed Jun 11 18:56:58 2014 OPTIONS IMPORT: timers and/or timeouts modified
Wed Jun 11 18:56:58 2014 OPTIONS IMPORT: explicit notify parm(s) modified
Wed Jun 11 18:56:58 2014 OPTIONS IMPORT: --ifconfig/up options modified
Wed Jun 11 18:56:58 2014 NOTE: --mute triggered...
Wed Jun 11 18:56:58 2014 3 variation(s) on previous 5 message(s) suppressed by --mute
Wed Jun 11 18:56:58 2014 ROUTE_GATEWAY 192.168.1.1/255.255.255.0 IFACE=wlan0 HWADDR=60:67:20:99:f8:8a
Wed Jun 11 18:56:58 2014 TUN/TAP device tun0 opened
Wed Jun 11 18:56:58 2014 TUN/TAP TX queue length set to 100
Wed Jun 11 18:56:58 2014 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Wed Jun 11 18:56:58 2014 /sbin/ifconfig tun0 10.11.124.183 netmask 255.248.0.0 mtu 1500 broadcast 10.15.255.255
Wed Jun 11 18:56:58 2014 ROUTE remote_host is NOT LOCAL
Wed Jun 11 18:56:58 2014 /sbin/route add -net 131.188.12.11 netmask 255.255.255.255 gw 192.168.1.1
Wed Jun 11 18:56:58 2014 /sbin/route add -net 0.0.0.0 netmask 128.0.0.0 gw 10.8.0.1
Wed Jun 11 18:56:58 2014 /sbin/route add -net 128.0.0.0 netmask 128.0.0.0 gw 10.8.0.1
Wed Jun 11 18:56:58 2014 Initialization Sequence Completed

```
This worked fine the first couple of times I used it. I could use the internet as usual over the full tunnel provided and ping everything.

After rebooting once after installing updates I can now still connect to the VPN however I can no longer access anything on the internet once the tunnel is established. I can ping the VPN Server itself fine after the tunnel is up and also the gateway however trying to ping google or the 8.8.8.8 nameserver does not work anymore. 

I have tried removing the second default route which leads to the local router gateway with no effect. 

I tried downgrading my packages however the old versions seem to be no longer available. 

I have also tried building OpenVPN from source which did not help.

I have verified that the server is working by connecting with my windows machine which works alright, so the problem is definitely a local one. 

I am now at the point where I either reinstall and see if that solves the issue (which I'd rather not do) or start digging around what might solve the problem (which I'd rather do). 

I think it would help much more to understand where the problem comes from than simply search for a way to make it go away.

Oh and I read other threads pertaining to the topic which suggested that a firewall is at fault.

I removed ufw after reading that which did not alleviate the problem, however it would also be strange that it worked once then.

I would be happy for any and all suggestions pertaining to the solution of this problem and I will try to provide log files that might help asap.

Thanks in advance

---

