---
title: "VPN connection problem"
date: 2014-12-19
forum: Networking &amp; Wireless
---

### Post by claudio.gambella on 2014-12-19
Hello everybody
I have always connected to a VPN network in order to connect to a server. I used to launch a .opvn file with the command opevpn and it worked.
Now, there have been some problems on the server and several reboot and I cannot connect to the VPN like I used to.
 I post the extract of the log file of openvpn.
```

Fri Dec 19 15:15:46 2014 OpenVPN 2.3.2 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Dec  1 2014
Fri Dec 19 15:15:46 2014 WARNING: file '***.p12' is group or others accessible
Fri Dec 19 15:15:46 2014 WARNING: file '***.key' is group or others accessible
Fri Dec 19 15:15:46 2014 Control Channel Authentication: using '***.key' as a OpenVPN static key file
Fri Dec 19 15:15:46 2014 Attempting to establish TCP connection with [AF_INET]xxxxxx:x [nonblock]
Fri Dec 19 15:15:47 2014 TCP connection established with [AF_INET]xxxxxx:x
Fri Dec 19 15:15:47 2014 TCPv4_CLIENT link local (bound): [undef]
Fri Dec 19 15:15:47 2014 TCPv4_CLIENT link remote: [AF_INET]xxxxxx:x
Fri Dec 19 15:15:47 2014 [openvpn1] Peer Connection Initiated with [AF_INET]xxxxxx:x
Fri Dec 19 15:15:50 2014 TUN/TAP device tun3 opened
Fri Dec 19 15:15:50 2014 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Fri Dec 19 15:15:50 2014 /sbin/ip link set dev tun3 up mtu 1500
Fri Dec 19 15:15:50 2014 /sbin/ip addr add dev tun3 local xxxxxx.x2 peer xxxxxx.x1
RTNETLINK answers: File exists
Fri Dec 19 15:15:50 2014 ERROR: Linux route add command failed: external program exited with error status: 2
RTNETLINK answers: File exists
Fri Dec 19 15:15:50 2014 ERROR: Linux route add command failed: external program exited with error status: 2
RTNETLINK answers: File exists
Fri Dec 19 15:15:50 2014 ERROR: Linux route add command failed: external program exited with error status: 2
Fri Dec 19 15:15:50 2014 Initialization Sequence Completed
Fri Dec 19 15:15:51 2014 Connection reset, restarting [0]
Fri Dec 19 15:15:51 2014 SIGUSR1[soft,connection-reset] received, process restarting
Fri Dec 19 15:15:56 2014 Attempting to establish TCP connection with [AF_INET]xxxxxx:x [nonblock]
Fri Dec 19 15:15:57 2014 TCP connection established with [AF_INET]xxxxxx:x
Fri Dec 19 15:15:57 2014 TCPv4_CLIENT link local (bound): [undef]
Fri Dec 19 15:15:57 2014 TCPv4_CLIENT link remote: [AF_INET]xxxxxx:x
Fri Dec 19 15:15:58 2014 [openvpn1] Peer Connection Initiated with [AF_INET]xxxxxx:x
Fri Dec 19 15:15:59 2014 Connection reset, restarting [0]
Fri Dec 19 15:15:59 2014 SIGUSR1[soft,connection-reset] received, process restarting
```


Any help is very much appreciated. Thank you.

---

