---
title: "I can't connect with openvpn"
date: 2016-10-29
forum: Networking &amp; Wireless
---

### Post by Frank_Blah on 2016-10-29
Hello,
I need to use ftp, but every port except 80 is blocked here, so I decided to try this vpn provider: [http://www.vpnbook.com/freevpn](http://www.vpnbook.com/freevpn). I have ubuntu 16.04, this is what /var/log/syslog is showing:

Oct 29 20:02:15 sitnarf-Inspiron-5559 kernel: [26284.040352] [UFW BLOCK] IN=wlp2s0 OUT= MAC=78:0c:b8:ec:14:09:50:46:5d:bc:76:c4:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Oct 29 20:02:45 sitnarf-Inspiron-5559 kernel: [26314.143253] [UFW BLOCK] IN=wlp2s0 OUT= MAC=78:0c:b8:ec:14:09:50:46:5d:bc:76:c4:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Oct 29 20:03:15 sitnarf-Inspiron-5559 kernel: [26344.143901] [UFW BLOCK] IN=wlp2s0 OUT= MAC=78:0c:b8:ec:14:09:50:46:5d:bc:76:c4:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Oct 29 20:03:45 sitnarf-Inspiron-5559 kernel: [26374.144539] [UFW BLOCK] IN=wlp2s0 OUT= MAC=78:0c:b8:ec:14:09:50:46:5d:bc:76:c4:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Oct 29 20:04:15 sitnarf-Inspiron-5559 kernel: [26404.144438] [UFW BLOCK] IN=wlp2s0 OUT= MAC=78:0c:b8:ec:14:09:50:46:5d:bc:76:c4:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Oct 29 20:04:39 sitnarf-Inspiron-5559 NetworkManager[966]: <info>  [1477764279.4700] audit: op="connection-activate" uuid="e2299d05-cbf8-4b3f-b37b-3888f200769b" name="vpnbook-euro1-tcp80" pid=1680 uid=1000 result="success"
Oct 29 20:04:39 sitnarf-Inspiron-5559 NetworkManager[966]: <info>  [1477764279.4818] vpn-connection[0x26a93e0,e2299d05-cbf8-4b3f-b37b-3888f200769b,"vpnbook-euro1-tcp80",0]: Started the VPN service, PID 23743
Oct 29 20:04:39 sitnarf-Inspiron-5559 NetworkManager[966]: <info>  [1477764279.4954] vpn-connection[0x26a93e0,e2299d05-cbf8-4b3f-b37b-3888f200769b,"vpnbook-euro1-tcp80",0]: Saw the service appear; activating connection
Oct 29 20:04:39 sitnarf-Inspiron-5559 NetworkManager[966]: nm-openvpn-Message: openvpn[23751] started
Oct 29 20:04:39 sitnarf-Inspiron-5559 nm-openvpn[23751]: OpenVPN 2.3.10 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Feb  2 2016
Oct 29 20:04:39 sitnarf-Inspiron-5559 nm-openvpn[23751]: library versions: OpenSSL 1.0.2g  1 Mar 2016, LZO 2.08
Oct 29 20:04:39 sitnarf-Inspiron-5559 NetworkManager[966]: <info>  [1477764279.5888] vpn-connection[0x26a93e0,e2299d05-cbf8-4b3f-b37b-3888f200769b,"vpnbook-euro1-tcp80",0]: VPN plugin: state changed: starting (3)
Oct 29 20:04:39 sitnarf-Inspiron-5559 NetworkManager[966]: <info>  [1477764279.5891] vpn-connection[0x26a93e0,e2299d05-cbf8-4b3f-b37b-3888f200769b,"vpnbook-euro1-tcp80",0]: VPN connection: (ConnectInteractive) reply received
Oct 29 20:04:39 sitnarf-Inspiron-5559 nm-openvpn[23751]: WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Oct 29 20:04:39 sitnarf-Inspiron-5559 nm-openvpn[23751]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Oct 29 20:04:39 sitnarf-Inspiron-5559 nm-openvpn[23751]: NOTE: chroot will be delayed because of --client, --pull, or --up-delay
Oct 29 20:04:39 sitnarf-Inspiron-5559 nm-openvpn[23751]: NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Oct 29 20:04:39 sitnarf-Inspiron-5559 nm-openvpn[23751]: Attempting to establish TCP connection with [AF_INET]176.126.237.217:80 [nonblock]
Oct 29 20:04:40 sitnarf-Inspiron-5559 nm-openvpn[23751]: TCP connection established with [AF_INET]176.126.237.217:80
Oct 29 20:04:40 sitnarf-Inspiron-5559 nm-openvpn[23751]: TCPv4_CLIENT link local: [undef]
Oct 29 20:04:40 sitnarf-Inspiron-5559 nm-openvpn[23751]: TCPv4_CLIENT link remote: [AF_INET]176.126.237.217:80
Oct 29 20:04:45 sitnarf-Inspiron-5559 kernel: [26434.145486] [UFW BLOCK] IN=wlp2s0 OUT= MAC=78:0c:b8:ec:14:09:50:46:5d:bc:76:c4:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Oct 29 20:05:15 sitnarf-Inspiron-5559 kernel: [26464.146119] [UFW BLOCK] IN=wlp2s0 OUT= MAC=78:0c:b8:ec:14:09:50:46:5d:bc:76:c4:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Oct 29 20:05:39 sitnarf-Inspiron-5559 NetworkManager[966]: <warn>  [1477764339.7270] vpn-connection[0x26a93e0,e2299d05-cbf8-4b3f-b37b-3888f200769b,"vpnbook-euro1-tcp80",0]: VPN connection: connect timeout exceeded.
Oct 29 20:05:39 sitnarf-Inspiron-5559 NetworkManager[966]: libnm-Message: Connect timer expired, disconnecting.
Oct 29 20:05:39 sitnarf-Inspiron-5559 NetworkManager[966]: nm-openvpn-Message: openvpn[23751]: send SIGTERM
Oct 29 20:05:39 sitnarf-Inspiron-5559 nm-openvpn[23751]: SIGTERM[hard,] received, process exiting
Oct 29 20:05:39 sitnarf-Inspiron-5559 NetworkManager[966]: <warn>  [1477764339.7378] vpn-connection[0x26a93e0,e2299d05-cbf8-4b3f-b37b-3888f200769b,"vpnbook-euro1-tcp80",0]: VPN plugin: failed: connect-failed (1)
Oct 29 20:05:39 sitnarf-Inspiron-5559 NetworkManager[966]: nm-openvpn-Message: openvpn[23751] exited with success
Oct 29 20:05:39 sitnarf-Inspiron-5559 NetworkManager[966]: <info>  [1477764339.7391] vpn-connection[0x26a93e0,e2299d05-cbf8-4b3f-b37b-3888f200769b,"vpnbook-euro1-tcp80",0]: VPN plugin: state changed: stopping (5)
Oct 29 20:05:39 sitnarf-Inspiron-5559 NetworkManager[966]: <info>  [1477764339.7394] vpn-connection[0x26a93e0,e2299d05-cbf8-4b3f-b37b-3888f200769b,"vpnbook-euro1-tcp80",0]: VPN plugin: state changed: stopped (6)

---

