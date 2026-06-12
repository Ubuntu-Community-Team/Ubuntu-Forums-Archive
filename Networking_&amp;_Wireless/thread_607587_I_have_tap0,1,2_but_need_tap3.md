---
title: "I have tap0,1,2 but need tap3"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by moxen93 on 2007-11-09
Hello

I have set up openvpn server (Ubuntu) and a gentoo-Linux client that functions as I want it.
Now I copied all client files over to another Ubuntu 7.10 and there I have some problems again.
On the new Ubuntu client after startup ifconfig shows tap0 (10.0.0.1), tap1 (10.0.0.2), tap2 (10.0.0.2). 
I need none of them by default. I don't know why they show up after startup (I think since I have done "apt-get install openvpn".) 
"/etc/init.d/openvpn stop" shows that it is not running by default (no PID).
Anyway tap3 does not exist (ifconfig tap3 ..up  -> "no such device"). Not that I need it but on this client the openvpn-command would obviously like it:
What can I do ?

root@Neuro-Ubuntu:/etc/openvpn# openvpn --config /etc/openvpn/client.conf
Fri Nov  9 08:51:41 2007 OpenVPN 2.0.9 i486-pc-linux-gnu [SSL] [LZO] [EPOLL] built on May 21 2007
Fri Nov  9 08:51:41 2007 IMPORTANT: OpenVPN's default port number is now 1194, based on an official port number assignment by IANA.  OpenVPN 2.0-beta16 and earlier used 5000 as the default port.
Fri Nov  9 08:51:41 2007 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Fri Nov  9 08:51:41 2007 WARNING: file '/etc/openvpn/certs/serverkey.pem' is group or others accessible
Fri Nov  9 08:51:41 2007 LZO compression initialized
Fri Nov  9 08:51:41 2007 WARNING: normally if you use --mssfix and/or --fragment, you should also set --tun-mtu 1500 (currently it is 1492)
Fri Nov  9 08:51:41 2007 Control Channel MTU parms [ L:1568 D:140 EF:40 EB:0 ET:0 EL:0 ]
Fri Nov  9 08:51:41 2007 Data Channel MTU parms [ L:1568 D:1450 EF:44 EB:135 ET:32 EL:0 AF:3/1 ]
Fri Nov  9 08:51:41 2007 Local Options hash (VER=V4): 'e16d6f87'
Fri Nov  9 08:51:41 2007 Expected Remote Options hash (VER=V4): '29f4dc48'
Fri Nov  9 08:51:41 2007 Attempting to establish TCP connection with 10.196.8.14:3128
Fri Nov  9 08:51:41 2007 TCP connection established with 10.196.8.14:3128
Fri Nov  9 08:51:41 2007 Send to HTTP proxy: 'CONNECT 85.127.141.32:443 HTTP/1.0'
Fri Nov  9 08:51:42 2007 HTTP proxy returned: 'HTTP/1.0 200 Connection established'
Fri Nov  9 08:51:42 2007 TCPv4_CLIENT link local: [undef]
Fri Nov  9 08:51:42 2007 TCPv4_CLIENT link remote: 10.196.8.14:3128
Fri Nov  9 08:51:42 2007 TLS: Initial packet from 10.196.8.14:3128, sid=d7357f4b b7c547bc
Fri Nov  9 08:51:43 2007 VERIFY OK: depth=1, /C=AT/ST=Niederosterreich/L=Wiener_Neustadt/O=LKH/OU=Neuro/CN=Maxi/emailAddress=markus.klein@laposte.net
Fri Nov  9 08:51:43 2007 VERIFY OK: depth=0, /C=AT/ST=Niederosterreich/L=Wiener_Neustadt/O=LKH/OU=Neuro/CN=Moxen/emailAddress=markus.klein@laposte.net
Fri Nov  9 08:51:43 2007 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Fri Nov  9 08:51:43 2007 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Nov  9 08:51:43 2007 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Fri Nov  9 08:51:43 2007 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Nov  9 08:51:43 2007 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Fri Nov  9 08:51:43 2007 [Moxen] Peer Connection Initiated with 10.196.8.14:3128
Fri Nov  9 08:51:44 2007 SENT CONTROL [Moxen]: 'PUSH_REQUEST' (status=1)
Fri Nov  9 08:51:45 2007 PUSH: Received control message: 'PUSH_REPLY,ping 10,ping-restart 120,ifconfig 10.0.0.2 255.255.255.0'
Fri Nov  9 08:51:45 2007 OPTIONS IMPORT: timers and/or timeouts modified
Fri Nov  9 08:51:45 2007 OPTIONS IMPORT: --ifconfig/up options modified
Fri Nov  9 08:51:45 2007 TUN/TAP device tap3 opened
Fri Nov  9 08:51:45 2007 ifconfig tap3 10.0.0.2 netmask 255.255.255.0 mtu 1492 broadcast 10.0.0.255
Fri Nov  9 08:51:45 2007 Initialization Sequence Completed
Fri Nov  9 08:51:46 2007 Connection reset, restarting [0]
Fri Nov  9 08:51:46 2007 TCP/UDP: Closing socket
Fri Nov  9 08:51:46 2007 SIGUSR1[soft,connection-reset] received, process restarting
Fri Nov  9 08:51:46 2007 Restart pause, 5 second(s)
Fri Nov  9 08:51:51 2007 IMPORTANT: OpenVPN's default port number is now 1194, based on an official port number assignment by IANA.  OpenVPN 2.0-beta16 and earlier used 5000 as the default port.
Fri Nov  9 08:51:51 2007 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Fri Nov  9 08:51:51 2007 Re-using SSL/TLS context
Fri Nov  9 08:51:51 2007 LZO compression initialized
Fri Nov  9 08:51:51 2007 WARNING: normally if you use --mssfix and/or --fragment, you should also set --tun-mtu 1500 (currently it is 1492)
Fri Nov  9 08:51:51 2007 Control Channel MTU parms [ L:1568 D:140 EF:40 EB:0 ET:0 EL:0 ]
Fri Nov  9 08:51:51 2007 Data Channel MTU parms [ L:1568 D:1450 EF:44 EB:135 ET:32 EL:0 AF:3/1 ]
Fri Nov  9 08:51:51 2007 Local Options hash (VER=V4): 'e16d6f87'
Fri Nov  9 08:51:51 2007 Expected Remote Options hash (VER=V4): '29f4dc48'
Fri Nov  9 08:51:51 2007 Attempting to establish TCP connection with 10.196.8.14:3128
Fri Nov  9 08:51:51 2007 TCP connection established with 10.196.8.14:3128
Fri Nov  9 08:51:51 2007 Send to HTTP proxy: 'CONNECT 85.127.141.32:443 HTTP/1.0'
Fri Nov  9 08:51:52 2007 HTTP proxy returned: 'HTTP/1.0 200 Connection established'
Fri Nov  9 08:51:52 2007 TCPv4_CLIENT link local: [undef]
Fri Nov  9 08:51:52 2007 TCPv4_CLIENT link remote: 10.196.8.14:3128
Fri Nov  9 08:51:52 2007 TLS: Initial packet from 10.196.8.14:3128, sid=4e61ed3c c57396e8
Fri Nov  9 08:51:53 2007 VERIFY OK: depth=1, /C=AT/ST=Niederosterreich/L=Wiener_Neustadt/O=LKH/OU=Neuro/CN=Maxi/emailAddress=markus.klein@laposte.net
Fri Nov  9 08:51:53 2007 VERIFY OK: depth=0, /C=AT/ST=Niederosterreich/L=Wiener_Neustadt/O=LKH/OU=Neuro/CN=Moxen/emailAddress=markus.klein@laposte.net
Fri Nov  9 08:51:54 2007 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Fri Nov  9 08:51:54 2007 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Nov  9 08:51:54 2007 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Fri Nov  9 08:51:54 2007 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Nov  9 08:51:54 2007 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Fri Nov  9 08:51:54 2007 [Moxen] Peer Connection Initiated with 10.196.8.14:3128
[SIZE="6"]Fri Nov  9 08:51:55 2007 SENT CONTROL [Moxen]: 'PUSH_REQUEST' (status=1)[/SIZE]
Fri Nov  9 08:51:55 2007 PUSH: Received control message: 'PUSH_REPLY,ping 10,ping-restart 120,ifconfig 10.0.0.2 255.255.255.0'
Fri Nov  9 08:51:55 2007 OPTIONS IMPORT: timers and/or timeouts modified
Fri Nov  9 08:51:55 2007 OPTIONS IMPORT: --ifconfig/up options modified
[SIZE="3"][SIZE="6"]Fri Nov  9 08:51:55 2007 Preserving previous TUN/TAP instance: tap3[/SIZE][/SIZE]
Fri Nov  9 08:51:55 2007 Initialization Sequence Completed
Fri Nov  9 08:51:58 2007 Connection reset, restarting [0]
Fri Nov  9 08:51:58 2007 TCP/UDP: Closing socket
Fri Nov  9 08:51:58 2007 SIGUSR1[soft,connection-reset] received, process restarting
Fri Nov  9 08:51:58 2007 Restart pause, 5 second(s)
Fri Nov  9 08:52:01 2007 Closing TUN/TAP interface
Fri Nov  9 08:52:01 2007 SIGINT[hard,init_instance] received, process exiting
root@Neuro-Ubuntu:/etc/openvpn#

---

### Post by moxen93 on 2007-11-12
Withdrawal !
I rebooted again and tried '/etc/init.d/openvpn stop' and there it stopped. 
So the server was running on the clientside. That was the problem. No tap0,1,2 anymore.
Note to myself: more coffee, more thinking !

---

