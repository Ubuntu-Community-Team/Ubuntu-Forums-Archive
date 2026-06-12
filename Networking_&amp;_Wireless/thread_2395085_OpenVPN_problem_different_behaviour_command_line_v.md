---
title: "OpenVPN problem: different behaviour command line vs gnome-network-manager"
date: 2018-06-26
forum: Networking &amp; Wireless
---

### Post by erotavlas on 2018-06-26
Hi,
I would like to use a free VPN service. I have tried both ubuntu 16.04 and ubuntu 18.04 and I'm only able to connect to via openVPN by using network-manager installed from repository
```
sudo apt-get install openvpn network-manager-openvpn-gnome resolvconf
```
Whereas by using openVPN via command line the service does not authenticate me. Both are configured by using the same .ovpn file.
This is the output log by using openVPN from network-manager:
```

Jun 26 08:54:05 user NetworkManager[932]: <info>  [1529823125.9849] audit: op="connection-activate" uuid="a14d46ee-d190-4145-b6ce-5ddc9beeb44e" name="nl-file" pid=2032 uid=1000 result="success"
Jun 26 08:54:05 user NetworkManager[932]: <info>  [1529823125.9896] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",0]: Started the VPN service, PID 13805
Jun 26 08:54:05 user NetworkManager[932]: <info>  [1529823125.9971] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",0]: Saw the service appear; activating connection
Jun 26 08:54:06 user nm-myvpn[13812]: OpenVPN 2.3.10 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Jun 22 2017
Jun 26 08:54:06 user nm-myvpn[13812]: library versions: OpenSSL 1.0.2g  1 Mar 2016, LZO 2.08
Jun 26 08:54:06 user NetworkManager[932]: nm-myvpn-Message: myvpn[13812] started
Jun 26 08:54:06 user NetworkManager[932]: <info>  [1529823126.1310] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",0]: VPN plugin: state changed: starting (3)
Jun 26 08:54:06 user NetworkManager[932]: <info>  [1529823126.1320] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",0]: VPN connection: (ConnectInteractive) reply received
Jun 26 08:54:06 user nm-myvpn[13812]: WARNING: --ping should normally be used with --ping-restart or --ping-exit
Jun 26 08:54:06 user nm-myvpn[13812]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Jun 26 08:54:06 user nm-myvpn[13812]: Control Channel Authentication: using '/home/user/.cert/nm-myvpn/nl-file-tls-auth.pem' as a OpenVPN static key file
Jun 26 08:54:06 user nm-myvpn[13812]: NOTE: chroot will be delayed because of --client, --pull, or --up-delay
Jun 26 08:54:06 user nm-myvpn[13812]: NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Jun 26 08:54:06 user nm-myvpn[13812]: UDPv4 link local: [undef]
Jun 26 08:54:06 user nm-myvpn[13812]: UDPv4 link remote: [AF_INET]217.23.3.171:1194
Jun 26 08:54:07 user nm-myvpn[13812]: WARNING: 'link-mtu' is used inconsistently, local='link-mtu 1602', remote='link-mtu 1634'
Jun 26 08:54:07 user nm-myvpn[13812]: WARNING: 'tun-mtu' is used inconsistently, local='tun-mtu 1500', remote='tun-mtu 1532'
Jun 26 08:54:07 user nm-myvpn[13812]: [server.com] Peer Connection Initiated with [AF_INET]217.23.3.171:1194
Jun 26 08:54:09 user nm-myvpn[13812]: TUN/TAP device tun0 opened
Jun 26 08:54:09 user nm-myvpn[13812]: /usr/lib/NetworkManager/nm-myvpn-service-myvpn-helper --bus-name org.freedesktop.NetworkManager.myvpn.Connection_4 --tun -- tun0 1500 1605 10.8.0.43 255.255.0.0 init
Jun 26 08:54:09 user NetworkManager[932]: <info>  [1529823129.2250] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",0]: VPN connection: (IP Config Get) reply received.
Jun 26 08:54:09 user nm-myvpn[13812]: chroot to '/var/lib/myvpn/chroot' and cd to '/' succeeded
Jun 26 08:54:09 user nm-myvpn[13812]: GID set to nm-myvpn
Jun 26 08:54:09 user nm-myvpn[13812]: UID set to nm-myvpn
Jun 26 08:54:09 user nm-myvpn[13812]: Initialization Sequence Completed
Jun 26 08:54:09 user NetworkManager[932]: <info>  [1529823129.2351] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",6:(tun0)]: VPN connection: (IP4 Config Get) reply received
Jun 26 08:54:09 user NetworkManager[932]: <info>  [1529823129.2363] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",6:(tun0)]: Data: VPN Gateway: 217.23.3.171
Jun 26 08:54:09 user NetworkManager[932]: <info>  [1529823129.2366] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",6:(tun0)]: Data: Tunnel Device: "tun0"
Jun 26 08:54:09 user NetworkManager[932]: <info>  [1529823129.2369] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",6:(tun0)]: Data: IPv4 configuration:
Jun 26 08:54:09 user NetworkManager[932]: <info>  [1529823129.2369] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",6:(tun0)]: Data:   Internal Gateway: 10.8.0.1
Jun 26 08:54:09 user NetworkManager[932]: <info>  [1529823129.2369] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",6:(tun0)]: Data:   Internal Address: 10.8.0.43
Jun 26 08:54:09 user NetworkManager[932]: <info>  [1529823129.2369] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",6:(tun0)]: Data:   Internal Prefix: 16
Jun 26 08:54:09 user NetworkManager[932]: <info>  [1529823129.2369] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",6:(tun0)]: Data:   Internal Point-to-Point Address: 10.8.0.43
Jun 26 08:54:09 user NetworkManager[932]: <info>  [1529823129.2370] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",6:(tun0)]: Data:   Maximum Segment Size (MSS): 0
Jun 26 08:54:09 user NetworkManager[932]: <info>  [1529823129.2370] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",6:(tun0)]: Data:   Forbid Default Route: no
Jun 26 08:54:09 user NetworkManager[932]: <info>  [1529823129.2370] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",6:(tun0)]: Data:   Internal DNS: 10.8.0.1
Jun 26 08:54:09 user NetworkManager[932]: <info>  [1529823129.2370] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",6:(tun0)]: Data:   DNS Domain: '(none)'
Jun 26 08:54:09 user NetworkManager[932]: <info>  [1529823129.2370] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",6:(tun0)]: Data: No IPv6 configuration
Jun 26 08:54:09 user NetworkManager[932]: <info>  [1529823129.2371] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",6:(tun0)]: VPN plugin: state changed: started (4)
Jun 26 08:54:09 user NetworkManager[932]: <info>  [1529823129.2412] vpn-connection[0x13773e0,a14d46ee-d190-4145-b6ce-5ddc9beeb44e,"nl-file",6:(tun0)]: VPN connection: (IP Config Get) complete
Jun 26 08:54:09 user nm-dispatcher: req:1 'vpn-up' [tun0]: new request (2 scripts)
Jun 26 08:54:09 user nm-dispatcher: req:1 'vpn-up' [tun0]: start running ordered scripts...

```
While this is the output log by using openVPN from command line:
```

sudo openvpn file.ovpn
Sun Jun 24 08:50:55 2018 OpenVPN 2.3.10 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Jun 22 2017
Sun Jun 24 08:50:55 2018 library versions: OpenSSL 1.0.2g  1 Mar 2016, LZO 2.08
Enter Auth Username: ************************
Enter Auth Password: ************************
Sun Jun 26 08:52:11 2018 WARNING: --ping should normally be used with --ping-restart or --ping-exit
Sun Jun 26 08:52:11 2018 NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Sun Jun 26 08:52:11 2018 Control Channel Authentication: tls-auth using INLINE static key file
Sun Jun 26 08:52:11 2018 Outgoing Control Channel Authentication: Using 512 bit message hash 'SHA512' for HMAC authentication
Sun Jun 26 08:52:11 2018 Incoming Control Channel Authentication: Using 512 bit message hash 'SHA512' for HMAC authentication
Sun Jun 26 08:52:11 2018 Socket Buffers: R=[212992->212992] S=[212992->212992]
Sun Jun 26 08:52:11 2018 UDPv4 link local: [undef]
Sun Jun 26 08:52:11 2018 UDPv4 link remote: [AF_INET]46.166.142.216:1194
Sun Jun 26 08:52:11 2018 TLS: Initial packet from [AF_INET]46.166.142.216:1194, sid=b51e2d4f 0bc5c704
Sun Jun 26 08:52:11 2018 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Sun Jun 26 08:52:11 2018 VERIFY OK: depth=2, C=CH, O=myVPN AG, CN=myVPN Root CA
Sun Jun 26 08:52:11 2018 VERIFY OK: depth=1, C=CH, O=myVPN AG, CN=myVPN Intermediate CA 1
Sun Jun 26 08:52:11 2018 Validating certificate key usage
Sun Jun 26 08:52:11 2018 ++ Certificate has key usage  00a0, expects 00a0
Sun Jun 26 08:52:11 2018 VERIFY KU OK
Sun Jun 26 08:52:11 2018 Validating certificate extended key usage
Sun Jun 26 08:52:11 2018 ++ Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server Authentication
Sun Jun 26 08:52:11 2018 VERIFY EKU OK
Sun Jun 26 08:52:11 2018 VERIFY OK: depth=0, CN=server.com
Sun Jun 26 08:52:14 2018 Data Channel Encrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Sun Jun 26 08:52:14 2018 Data Channel Encrypt: Using 512 bit message hash 'SHA512' for HMAC authentication
Sun Jun 26 08:52:14 2018 Data Channel Decrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Sun Jun 26 08:52:14 2018 Data Channel Decrypt: Using 512 bit message hash 'SHA512' for HMAC authentication
Sun Jun 26 08:52:14 2018 Control Channel: TLSv1.2, cipher TLSv1/SSLv3 ECDHE-RSA-AES256-GCM-SHA384, 2048 bit RSA
Sun Jun 26 08:52:14 2018 [server.com] Peer Connection Initiated with [AF_INET]46.166.142.216:1194
Sun Jun 26 08:52:16 2018 SENT CONTROL [server.com]: 'PUSH_REQUEST' (status=1)
Sun Jun 26 08:52:19 2018 AUTH: Received control message: AUTH_FAILED
Sun Jun 26 08:52:19 2018 SIGTERM[soft,auth-failure] received, process exiting

```
I have investigated on the Web without founding a solution. Do you have any idea?
Thank you

---

