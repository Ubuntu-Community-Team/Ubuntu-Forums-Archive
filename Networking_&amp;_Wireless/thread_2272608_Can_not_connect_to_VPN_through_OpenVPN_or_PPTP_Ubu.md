---
title: "Can not connect to VPN through OpenVPN or PPTP Ubuntu 14.04"
date: 2015-04-07
forum: Networking &amp; Wireless
---

### Post by jordan42 on 2015-04-07
I'm using Ubuntu 14.04 and I'm trying to setup my VPN, I get my VPN through Newshosting and followed their instructions for both PPTP and OpenVPN.  After I set everything up I check it off from the Network Manager dropdown and a check appears next to my saved VPN but nothing happens.  Any ideas?

---

### Post by michi1983 on 2015-04-08
what about you post a link to the instructions you followed and some infos (content of file which you changed) that we can see what you have done already?

---

### Post by jordan42 on 2015-04-08
i ran install for openvpn network manager and it's gnome plugin.  I followed these guides.
[https://www.newshosting.com/vpn/setup.php#ubuntu](https://www.newshosting.com/vpn/setup.php#ubuntu)
[http://grantcurell.com/2014/07/22/setting-up-a-vpn-server-on-ubuntu-14-04/](http://grantcurell.com/2014/07/22/setting-up-a-vpn-server-on-ubuntu-14-04/)
[http://ubuntuhandbook.org/index.php/2014/05/establish-openvpn-connection-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2014/05/establish-openvpn-connection-ubuntu-1404/)
[http://ubuntuforums.org/showthread.php?t=2222063](http://ubuntuforums.org/showthread.php?t=2222063)

---

### Post by jordan42 on 2015-04-08
when i run from terminal for openvpn to connect via config file path it appears to connect but does not give me a confirmation and I lose internet connection.

---

### Post by jordan42 on 2015-04-08
when i run sudo openvpn --config ~/path.to.file i get this

Wed Apr  8 14:30:59 2015 OpenVPN 2.3.2 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Dec  1 2014
Enter Auth Username:xxxxxxxx
Enter Auth Password:
Wed Apr  8 14:31:07 2015 Socket Buffers: R=[212992->131072] S=[212992->131072]
Wed Apr  8 14:31:07 2015 UDPv4 link local: [undef]
Wed Apr  8 14:31:07 2015 UDPv4 link remote: [AF_INET]2xxxxxxx4
Wed Apr  8 14:31:07 2015 TLS: Initial packet from [AF_INET]216.151.180.3:1194, sid=d8785d35 612ff554
Wed Apr  8 14:31:07 2015 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Wed Apr  8 14:31:07 2015 VERIFY OK: depth=1, C=US, ST=VPN, L=VPN, O=VPN, OU=VPN, CN=VPN, name=VPN, emailAddress=VPN
Wed Apr  8 14:31:07 2015 Validating certificate key usage
Wed Apr  8 14:31:07 2015 ++ Certificate has key usage  00a0, expects 00a0
Wed Apr  8 14:31:07 2015 VERIFY KU OK
Wed Apr  8 14:31:07 2015 Validating certificate extended key usage
Wed Apr  8 14:31:07 2015 ++ Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server Authentication
Wed Apr  8 14:31:07 2015 VERIFY EKU OK
Wed Apr  8 14:31:07 2015 VERIFY OK: depth=0, C=US, ST=VPN, L=VPN, O=VPN, OU=VPN, CN=vpn, name=VPN
Wed Apr  8 14:31:07 2015 Data Channel Encrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Wed Apr  8 14:31:07 2015 Data Channel Encrypt: Using 256 bit message hash 'SHA256' for HMAC authentication
Wed Apr  8 14:31:07 2015 Data Channel Decrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Wed Apr  8 14:31:07 2015 Data Channel Decrypt: Using 256 bit message hash 'SHA256' for HMAC authentication
Wed Apr  8 14:31:07 2015 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Wed Apr  8 14:31:07 2015 [vpn] Peer Connection Initiated with [AF_INET]2xxxxxxxxxxx4
Wed Apr  8 14:31:10 2015 SENT CONTROL [vpn]: 'PUSH_REQUEST' (status=1)
Wed Apr  8 14:31:10 2015 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1 bypass-dhcp,dhcp-option DNS 198.18.0.1,dhcp-option DNS 1xxxxx.2,rcvbuf 262144,explicit-exit-notify 5,route-gateway 1xxxx1,topology subnet,ping 20,ping-restart 40,ifconfig 1xxxxxxxxxx1 2xxxxxxxx0'
Wed Apr  8 14:31:10 2015 OPTIONS IMPORT: timers and/or timeouts modified
Wed Apr  8 14:31:10 2015 OPTIONS IMPORT: explicit notify parm(s) modified
Wed Apr  8 14:31:10 2015 OPTIONS IMPORT: --sndbuf/--rcvbuf options modified
Wed Apr  8 14:31:10 2015 Socket Buffers: R=[131072->425984] S=[131072->131072]
Wed Apr  8 14:31:10 2015 OPTIONS IMPORT: --ifconfig/up options modified
Wed Apr  8 14:31:10 2015 OPTIONS IMPORT: route options modified
Wed Apr  8 14:31:10 2015 OPTIONS IMPORT: route-related options modified
Wed Apr  8 14:31:10 2015 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Wed Apr  8 14:31:10 2015 ROUTE_GATEWAYxxxx1/2xxxxxxx0 IFACE=em1 HWADDR=4xxxxxxxxxa
Wed Apr  8 14:31:10 2015 TUN/TAP device tun0 opened
Wed Apr  8 14:31:10 2015 TUN/TAP TX queue length set to 100
Wed Apr  8 14:31:10 2015 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Wed Apr  8 14:31:10 2015 /sbin/ip link set dev tun0 up mtu 1500
Wed Apr  8 14:31:10 2015 /sbin/ip addr add dev tun0 1xxxxxxxxx2 broadcast 1xxxxxxxxxxxxx5
Wed Apr  8 14:31:10 2015 /sbin/ip route add 2xxxxxxxxxxxx3/32 via 1xxxxxxxxxxx1
Wed Apr  8 14:31:10 2015 /sbin/ip route add 0.0.0.0/1 via 1xxxxxxxxxx1
Wed Apr  8 14:31:10 2015 /sbin/ip route add 1xxxxxxxxxx.0/1 via 1xxxxxxxx1
Wed Apr  8 14:31:10 2015 Initialization Sequence Completed
^CWed Apr  8 14:31:30 2015 event_wait : Interrupted system call (code=4)
Wed Apr  8 14:31:30 2015 SIGTERM received, sending exit notification to peer
^CWed Apr  8 14:31:30 2015 event_wait : Interrupted system call (code=4)
Wed Apr  8 14:31:30 2015 /sbin/ip route del 2xxxxxxxxx.3/x2
Wed Apr  8 14:31:30 2015 /sbin/ip route del 0.0.0.0/1
Wed Apr  8 14:31:30 2015 /sbin/ip route del 128.0.0.0/1
Wed Apr  8 14:31:30 2015 Closing TUN/TAP interface
Wed Apr  8 14:31:30 2015 /sbin/ip addr del dev tun0 1xxxxxxxxxxx1/2xx
Wed Apr  8 14:31:30 2015 SIGINT[hard,] received, process exiting

---

### Post by jordan42 on 2015-04-08
you'll see way down there i pushed control+c, if i don't it just sits forever and i lose internet. also is it safe for me to post what i just did?

---

### Post by jordan42 on 2015-04-08
I do also show in my network manager that my ethernet network is not managed, is this a possible issue?

---

### Post by jordan42 on 2015-04-09
bump

---

### Post by ger3 on 2015-04-14
Hello all,

I am completely new to Ubuntu/Linux, and I'm loving it so far with a HTPC running Kodibuntu 14.04, a file server running Ubuntu 14.04 and a dual boot Laptop running W7 and Ubuntu 14.04. This last machine is meant to replace Windows completely, however the dual boot will be there for some time. At least until programs as iTunes are available in Linux, and then I mean syncing my iPhone as well.

At this point however the laptop is giving me headaches whilst trying to configure a VPN connection. Here's my situation. Like  I said I have a laptop running dual boot. I also have a Draytek Vigor V2130n wireless router with built in VPN server. This server van manage PPTP an IP-Sec VPN tunnels. Therefor OpenVPN is no option for me I think. I have absolutely no issue connecting to my router when using my iPhone, my Laptop (in W7) or the Laptop (also W7) that I have from work, but i can't find the correct settings for network manager in Ubuntu. Every tutorial that I found this far sais something different. So as a last resort I hope someone here can tell me how to set up the darn thing.

I'm using the GUI version, whilst being to unfamiliar using the terminal, but in my opinion this should make no difference.

The settings I made this far are as follows:
Connection name: VPN
Gateway: XX.XXX.XX.X (my IP adress checked hundreds of times so that's correct)
Username and Password as configured in my router settings. 
NT-domain: [empty] since i do not have a DNS server.

Advanced settings:
PAP, CHAP and EAP unchecked
MSCHAP and MSCHAPv2 checked
MPPE checked (this should be necessary for my iPhone to be able to connect)
Security: Standard (all available)
Statefull encryption allowed checked
BSD, Deflate and TCP are also checked
PPP is unchecked.

One tutorial said to have the CHAP-box checked, but 1 found out that checking the MPPE afterwards will automatically uncheck this box, and after reading the reply in this topic that box should be unchecked.
Another tutorial sais to have the BSD, Deflate and TCP box unchecked and the PPP box checked, but that doesn't work either.

I hope this gives you enough information about the issue and that the community will be able to help me out here.

---

