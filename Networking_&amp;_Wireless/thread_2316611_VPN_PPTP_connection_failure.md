---
title: "VPN PPTP connection failure"
date: 2016-03-09
forum: Networking &amp; Wireless
---

### Post by donsy on 2016-03-09
I'm having a great deal of difficulty setting up a VPN connection. I'm using one of the "free" VPN servers: freevpn.me using their gateway address, username and password. The /var/log/syslog entries are posted below. Can someone tell me why the connection fails?
```
Mar  9 07:51:57 BSWZ1S1 NetworkManager[1035]: <info> Starting VPN service 'pptp'...Mar  9 07:51:57 BSWZ1S1 NetworkManager[1035]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 3319
Mar  9 07:51:57 BSWZ1S1 NetworkManager[1035]: <info> VPN service 'pptp' appeared; activating connections
Mar  9 07:51:57 BSWZ1S1 NetworkManager[1035]: <info> VPN plugin state changed: init (1)
Mar  9 07:51:58 BSWZ1S1 NetworkManager[1035]: <info> VPN plugin state changed: starting (3)
Mar  9 07:51:58 BSWZ1S1 NetworkManager[1035]: <info> VPN connection 'PPTP' (Connect) reply received.
Mar  9 07:51:58 BSWZ1S1 pppd[3321]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Mar  9 07:51:58 BSWZ1S1 pppd[3321]: pppd 2.4.5 started by root, uid 0
Mar  9 07:51:58 BSWZ1S1 pptp[3325]: nm-pptp-service-3319 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Mar  9 07:51:58 BSWZ1S1 pppd[3321]: Using interface ppp0
Mar  9 07:51:58 BSWZ1S1 pppd[3321]: Connect: ppp0 <--> /dev/pts/8
Mar  9 07:51:58 BSWZ1S1 NetworkManager[1035]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar  9 07:51:58 BSWZ1S1 NetworkManager[1035]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Mar  9 07:51:58 BSWZ1S1 NetworkManager[1035]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Mar  9 07:51:58 BSWZ1S1 pptp[3342]: nm-pptp-service-3319 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Mar  9 07:51:58 BSWZ1S1 pptp[3342]: nm-pptp-service-3319 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Mar  9 07:51:58 BSWZ1S1 pptp[3342]: nm-pptp-service-3319 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Mar  9 07:51:59 BSWZ1S1 pptp[3342]: nm-pptp-service-3319 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Mar  9 07:51:59 BSWZ1S1 pptp[3342]: nm-pptp-service-3319 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Mar  9 07:51:59 BSWZ1S1 pptp[3342]: nm-pptp-service-3319 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 25728).
Mar  9 07:51:59 BSWZ1S1 pptp[3342]: nm-pptp-service-3319 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Mar  9 07:51:59 BSWZ1S1 pptp[3342]: nm-pptp-service-3319 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Mar  9 07:51:59 BSWZ1S1 pptp[3342]: nm-pptp-service-3319 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Mar  9 07:51:59 BSWZ1S1 pppd[3321]: Modem hangup
Mar  9 07:51:59 BSWZ1S1 pppd[3321]: Connection terminated.
Mar  9 07:51:59 BSWZ1S1 avahi-daemon[962]: Withdrawing workstation service for ppp0.
Mar  9 07:51:59 BSWZ1S1 NetworkManager[1035]: <warn> VPN plugin failed: 1
Mar  9 07:51:59 BSWZ1S1 NetworkManager[1035]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar  9 07:51:59 BSWZ1S1 pppd[3321]: Exit.
Mar  9 07:51:59 BSWZ1S1 NetworkManager[1035]: <warn> VPN plugin failed: 1
Mar  9 07:51:59 BSWZ1S1 NetworkManager[1035]: <warn> VPN plugin failed: 1
Mar  9 07:51:59 BSWZ1S1 NetworkManager[1035]: <info> VPN plugin state changed: stopped (6)
Mar  9 07:51:59 BSWZ1S1 NetworkManager[1035]: <info> VPN plugin state change reason: 0
Mar  9 07:51:59 BSWZ1S1 NetworkManager[1035]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Mar  9 07:51:59 BSWZ1S1 NetworkManager[1035]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Mar  9 07:52:05 BSWZ1S1 NetworkManager[1035]: <info> VPN service 'pptp' disappeared

```

---

### Post by QDR06VV9 on 2016-03-09
Hi donsy some of the free VPN providers require you to to re-vist their site every 5-6 days because they change the login credentials..
freevpnme [URL="http://freevpn.me/"]http://freevpn.me/
[/URL]
There is a script that will hook you up with
Supported free services:
[www.vpnbook.com]("http://www.vpnbook.com")
[www.freevpn.me]("http://www.freevpn.me")
[URL="http://www.vpnkeys.com"]www.vpnkeys.com
[/URL]
**Credit to Sebastijan Bandur**
Free VPN Connect for Linux
I just created script for automatic instant free OpenVPN connections to multiple free VPN services.
You can download it on [https://github.com/sbandur84/Free-OpenVPN-Connect-for-Linux](https://github.com/sbandur84/Free-OpenVPN-Connect-for-Linux)
Script is automatic and takes all advertising money from service providers for not visiting their web pages, so please donate.
Source: [http://askubuntu.com/questions/6853/is-there-a-free-service-like-hotspot-shield-for-ubuntu](http://askubuntu.com/questions/6853/is-there-a-free-service-like-hotspot-shield-for-ubuntu)
Hope this is helpful and Good Luck

---

### Post by donsy on 2016-03-10
I ran the script but it hangs after "Initialization Sequence Completed" and I have to ctrl-c to exit. I tried with and without sudo. Here is the output:
```
––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– Free VPN Connect for linux - MAIN MENU –––––––––––––––––––––
––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––
––––– Supported services: www.FreeVPN.me, www.VPNbook.com, www.VPNkeys.com –––––
––––––––––– Please donate to continue supporting free VPN services –––––––––––––
––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––
Profile:  vpnbook-us2-tcp443.ovpn
Username: vpnbook
Password: takuPhu5
––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––
INFO: Profile selected: vpnbook-us2-tcp443.ovpn
––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––
1) Profile   3) Download  5) Ports     7) Credits   9) Quit
2) Connect   4) Clean      6) Install   8) Help
#? 2
Thu Mar 10 06:55:15 2016 OpenVPN 2.3.2 i686-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Dec  1 2014
Thu Mar 10 06:55:15 2016 WARNING: file '/home/donsy/PROFILES/vpnuserpass' is group or others accessible
Thu Mar 10 06:55:15 2016 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Thu Mar 10 06:55:15 2016 NOTE: --fast-io is disabled since we are not using UDP
Thu Mar 10 06:55:15 2016 Socket Buffers: R=[87380->131072] S=[16384->131072]
Thu Mar 10 06:55:15 2016 Attempting to establish TCP connection with [AF_INET]198.7.58.147:443 [nonblock]
Thu Mar 10 06:55:16 2016 TCP connection established with [AF_INET]198.7.58.147:443
Thu Mar 10 06:55:16 2016 TCPv4_CLIENT link local: [undef]
Thu Mar 10 06:55:16 2016 TCPv4_CLIENT link remote: [AF_INET]198.7.58.147:443
Thu Mar 10 06:55:16 2016 TLS: Initial packet from [AF_INET]198.7.58.147:443, sid=ac1fa675 d75038a0
Thu Mar 10 06:55:16 2016 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Thu Mar 10 06:55:17 2016 VERIFY OK: depth=1, C=CH, ST=Zurich, L=Zurich, O=vpnbook.com, OU=IT, CN=vpnbook.com, name=vpnbook.com, emailAddress=admin@vpnbook.com
Thu Mar 10 06:55:17 2016 VERIFY OK: depth=0, C=CH, ST=Zurich, L=Zurich, O=vpnbook.com, OU=IT, CN=vpnbook.com, name=vpnbook.com, emailAddress=admin@vpnbook.com
Thu Mar 10 06:55:18 2016 Data Channel Encrypt: Cipher 'AES-128-CBC' initialized with 128 bit key
Thu Mar 10 06:55:18 2016 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Mar 10 06:55:18 2016 Data Channel Decrypt: Cipher 'AES-128-CBC' initialized with 128 bit key
Thu Mar 10 06:55:18 2016 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Mar 10 06:55:18 2016 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Thu Mar 10 06:55:18 2016 [vpnbook.com] Peer Connection Initiated with [AF_INET]198.7.58.147:443
Thu Mar 10 06:55:20 2016 SENT CONTROL [vpnbook.com]: 'PUSH_REQUEST' (status=1)
Thu Mar 10 06:55:20 2016 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1,dhcp-option DNS  8.8.8.8,dhcp-option DNS  91.239.100.100,route 10.9.0.1,topology net30,ping 5,ping-restart 30,ifconfig 10.9.0.154 10.9.0.153'
Thu Mar 10 06:55:20 2016 OPTIONS IMPORT: timers and/or timeouts modified
Thu Mar 10 06:55:20 2016 OPTIONS IMPORT: --ifconfig/up options modified
Thu Mar 10 06:55:20 2016 OPTIONS IMPORT: route options modified
Thu Mar 10 06:55:20 2016 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Thu Mar 10 06:55:20 2016 ROUTE_GATEWAY 192.168.1.1/255.255.255.0 IFACE=eth0 HWADDR=00:12:3f:1e:58:4f
Thu Mar 10 06:55:21 2016 TUN/TAP device tun1 opened
Thu Mar 10 06:55:21 2016 TUN/TAP TX queue length set to 100
Thu Mar 10 06:55:21 2016 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Thu Mar 10 06:55:21 2016 /sbin/ip link set dev tun1 up mtu 1500
Thu Mar 10 06:55:21 2016 /sbin/ip addr add dev tun1 local 10.9.0.154 peer 10.9.0.153
Thu Mar 10 06:55:23 2016 /sbin/ip route add 198.7.58.147/32 via 192.168.1.1
Thu Mar 10 06:55:23 2016 /sbin/ip route add 0.0.0.0/1 via 10.9.0.153
Thu Mar 10 06:55:23 2016 /sbin/ip route add 128.0.0.0/1 via 10.9.0.153
Thu Mar 10 06:55:23 2016 /sbin/ip route add 10.9.0.1/32 via 10.9.0.153
Thu Mar 10 06:55:23 2016 Initialization Sequence Completed



```

---

### Post by QDR06VV9 on 2016-03-10
What is the content of this file
```
/etc/resolv.conf
```

---

### Post by donsy on 2016-03-10
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search lv.cox.net

```

---

### Post by QDR06VV9 on 2016-03-10
Well it looks to me that there is no CA Cert...as per the the warning you showed
> WARNING: No server certificate verification method has been enabled.
You will have to add that to your network config by way of the network manager.
But that script you ran should have that for you.
```

```

---

### Post by donsy on 2016-03-10
> **runrickus said:**
> Well it looks to me that there is no CA Cert...as per the the warning you showed

You will have to add that to your network config by way of the network manager.
But that script you ran should have that for you.


How to I do that?

---

### Post by donsy on 2016-03-10
I know how to configure in network manager, my question is does that have to be done first before running the script?

---

### Post by slickymaster on 2016-03-10
*Moved to ***Networking & Wireless*** sub-forum*

---

### Post by QDR06VV9 on 2016-03-10
It really dose not matter when... just has to be done is all.

EDIT: Just wanted to add this just to be informative..
> PPTP is very insecure (even its co-creator Microsoft has abandoned it, and it has been compromised by the NSA) and should therefore be avoided. While its ease of setup and cross platform compatibility are attractive, L2PT/IPsec has the same advantages and is much more secure.

**OpenVPN is easily the best all round VPN solution, despite needing third party software on all platforms. It is reliable, fast, and (most importantly) secure (even against the NSA), although it usually needs a bit more setting up than the other protocols**
Regards

---

