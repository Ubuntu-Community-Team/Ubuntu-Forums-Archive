---
title: "OpenVPN: no Internet access after &quot;successful&quot; connection"
date: 2015-09-08
forum: Networking &amp; Wireless
---

### Post by NepenthesXD on 2015-09-08
Hello,

I'm writing here because I'm currently having a VPN configuration issue. I am trying to connect to a VPN with OpenVPN, and after a "successful" connection to this service, I completely lose access to any Internet service.
Once disconnected from the VPN, everything goes back to normal.

This happens both using the Network-Manager OpenVPN plugin, and the command line openvpn tool.

Here are a few logs I gathered :
```
sudo openvpn client.ovpn 
[sudo] password for loris: 
Tue Sep  8 11:45:36 2015 OpenVPN 2.3.2 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Apr 13 2015
Enter Auth Username: *******
Enter Auth Password: ********
Tue Sep  8 11:45:47 2015 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Tue Sep  8 11:45:47 2015 WARNING: file 'myname.key' is group or others accessible
Tue Sep  8 11:45:47 2015 WARNING: file 'ta.key' is group or others accessible
Tue Sep  8 11:45:47 2015 Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Tue Sep  8 11:45:47 2015 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Tue Sep  8 11:45:47 2015 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Tue Sep  8 11:45:47 2015 Socket Buffers: R=[87380->131072] S=[16384->131072]
Tue Sep  8 11:45:47 2015 Attempting to establish TCP connection with [AF_INET]/ip obscured for privacy/:1199 [nonblock]
Tue Sep  8 11:45:48 2015 TCP connection established with [AF_INET]/ip obscured for privacy/:1199
Tue Sep  8 11:45:48 2015 TCPv4_CLIENT link local: [undef]
Tue Sep  8 11:45:48 2015 TCPv4_CLIENT link remote: [AF_INET]/ip obscured for privacy/:1199
Tue Sep  8 11:45:48 2015 TLS: Initial packet from [AF_INET]/ip obscured for privacy/:1199, sid=43da9e4a 770cc5d7
Tue Sep  8 11:45:48 2015 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Tue Sep  8 11:45:48 2015 VERIFY OK: depth=1, /adress obscured for privacy/
Tue Sep  8 11:45:48 2015 VERIFY OK: depth=0, /adress obscured for privacy/
Tue Sep  8 11:45:50 2015 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Tue Sep  8 11:45:50 2015 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Tue Sep  8 11:45:50 2015 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Tue Sep  8 11:45:50 2015 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Tue Sep  8 11:45:50 2015 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Tue Sep  8 11:45:50 2015 [/domain obscured for privacy/] Peer Connection Initiated with [AF_INET]/ip obscured for privacy/:1199
Tue Sep  8 11:45:52 2015 SENT CONTROL [/domain obscured for privacy/]: 'PUSH_REQUEST' (status=1)
Tue Sep  8 11:45:52 2015 PUSH: Received control message: 'PUSH_REPLY,ping 10,ping-restart 120,route 172.16.110.0 255.255.255.0 172.16.83.1,route 172.16.200.0 255.255.255.0 172.16.83.1,route /ip obscured for privacy/ 255.255.255.0 172.16.83.1,route /ip obscured for privacy/ 255.255.255.192 172.16.83.1,route 192.168.1.0 255.255.255.0 172.16.83.1,route 172.16.204.0 255.255.255.0 172.16.83.1,ifconfig 172.16.83.20 255.255.255.0'
Tue Sep  8 11:45:52 2015 OPTIONS IMPORT: timers and/or timeouts modified
Tue Sep  8 11:45:52 2015 OPTIONS IMPORT: --ifconfig/up options modified
Tue Sep  8 11:45:52 2015 OPTIONS IMPORT: route options modified
Tue Sep  8 11:45:52 2015 ROUTE_GATEWAY 192.168.1.1/255.255.255.0 IFACE=wlan0 HWADDR=48:d2:24:7a:51:83
Tue Sep  8 11:45:52 2015 TUN/TAP device tap0 opened
Tue Sep  8 11:45:52 2015 TUN/TAP TX queue length set to 100
Tue Sep  8 11:45:52 2015 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Tue Sep  8 11:45:52 2015 /sbin/ip link set dev tap0 up mtu 1500
Tue Sep  8 11:45:52 2015 /sbin/ip addr add dev tap0 172.16.83.20/24 broadcast 172.16.83.255
Tue Sep  8 11:45:52 2015 /sbin/ip route add 172.16.110.0/24 via 172.16.83.1
Tue Sep  8 11:45:52 2015 /sbin/ip route add 172.16.200.0/24 via 172.16.83.1
Tue Sep  8 11:45:52 2015 /sbin/ip route add /ip obscured for privacy//24 via 172.16.83.1
Tue Sep  8 11:45:52 2015 /sbin/ip route add /ip obscured for privacy//26 via 172.16.83.1
Tue Sep  8 11:45:52 2015 /sbin/ip route add 192.168.1.0/24 via 172.16.83.1
RTNETLINK answers: File exists
Tue Sep  8 11:45:52 2015 ERROR: Linux route add command failed: external program exited with error status: 2
Tue Sep  8 11:45:52 2015 /sbin/ip route add 172.16.204.0/24 via 172.16.83.1
Tue Sep  8 11:45:52 2015 Initialization Sequence Completed
^CTue Sep  8 11:46:51 2015 event_wait : Interrupted system call (code=4)
Tue Sep  8 11:46:51 2015 /sbin/ip route del 172.16.204.0/24
Tue Sep  8 11:46:51 2015 /sbin/ip route del /ip obscured for privacy//26
Tue Sep  8 11:46:51 2015 /sbin/ip route del /ip obscured for privacy//24
Tue Sep  8 11:46:51 2015 /sbin/ip route del 172.16.200.0/24
Tue Sep  8 11:46:51 2015 /sbin/ip route del 172.16.110.0/24
Tue Sep  8 11:46:51 2015 Closing TUN/TAP interface
Tue Sep  8 11:46:51 2015 /sbin/ip addr del dev tap0 172.16.83.20/24
Tue Sep  8 11:46:51 2015 SIGINT[hard,] received, process exiting
```

I'm especially curious about this part "ERROR: Linux route add command failed: external program exited with error status: 2"

Also, here's what I get once "connected" to the VPN if trying to reach Google:
```
traceroute to www.google.com (216.58.209.68), 30 hops max, 60 byte packets
 1  172.16.83.20 (172.16.83.20)  2998.973 ms !H  2998.955 ms !H  2998.935 ms !H
```

Any idea what's happening ?
(also, you need some private information to understand the issue, I can give it to you via MP. If I forgot to obscure some private info, please let me know, I'll be glad !)

---

### Post by SeijiSensei on 2015-09-08
```
 /sbin/ip route add 192.168.1.0/24 via 172.16.83.1
RTNETLINK answers: File exists
```
I'm guessing your computer's interface has an address in 192.168.1.0/24.  You can't reroute those packets because they are already being directed to the upstream router.  You have two choices.  One is to make the other end of the VPN connection the default gateway for the machine and send all your traffic over the VPN.  That will still require you to set up a separate route over the Internet from your client to the machine hosting the VPN.  The other option is to use the VPN only for some traffic and leave the default gateway on the client machine alone.  If you're trying to route all your traffic over the VPN, you'll need solution one.  I just use my VPN to talk to my remote servers; I send all my other traffic directly out over the Internet.

---

### Post by NepenthesXD on 2015-09-08
I changed the addressing range of my router from 192.*.*.* to 193.*.*.* . This fixed the following error :
RTNETLINK answers: File exists
Tue Sep  8 11:45:52 2015 ERROR: Linux route add command failed: external program exited with error status: 2

However, I still don't have access to any service through the VPN connection.

Could you please give me more details about the two possible solutions (routing everything through the VPN, or having a separate route for internet) ?

---

### Post by SeijiSensei on 2015-09-08
Let's start with the first option, where you route all your outgoing traffic over the tunnel.  That means your client computer needs a route that points directly to the VPN server over the public Internet.  You'll also need another route that makes the remote end of the tunnel the client's "default gateway."  

Suppose the remote VPN server has an IP address of 10.10.10.10, and your computer has a network connection with an address of 192.168.1.10 that talks to your router at 192.168.1.1.  When the VPN is set up, suppose its remote address is 172.16.0.1 and your VPN address is 172.16.0.2.  Then you would need a combination of routes like this:
```

ip route add 10.10.10.10 via 192.168.1.1
ip route del default via 192.168.1.1
ip route add default via 172.16.0.2

```
Both commands need to be run with root privileges either via "sudo" or by being included in a script run by the root user. You may need other routes as well depending on the overall network configuration.  

The first command tells the client to send traffic for the remote server's public address directly via your router and thus over the Internet.  That lets the two machines create and maintain the tunnel.  The second command deletes the existing "default" route that sent all Internet traffic out through the router at 192.168.1.1.  The third command replaces the default route with one that forwards outbound traffic over the tunnel.

If your OpenVPN configuration runs routing scripts, as it appears to do, I'd disable all of them (use "#up" in the .conf file) and just try to get a tunnel working between the two machines.  Once you can reliably ping each end of the connection from both machines, then you can start to play around with routing.  With the tunnel up, run the commands above and see whether that enables web traffic to flow through the tunnel.  One test is to visit [whatismyip.com]("http://whatismyip.com") and see what address you are connecting from.  If you're using the tunnel, it should be something other than the public address assigned to your local router.

You'll need to change the addresses in those commands to match your local configuration, of course.

---

