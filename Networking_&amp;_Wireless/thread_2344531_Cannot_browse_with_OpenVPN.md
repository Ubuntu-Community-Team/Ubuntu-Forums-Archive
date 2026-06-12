---
title: "Cannot browse with OpenVPN"
date: 2016-11-26
forum: Networking &amp; Wireless
---

### Post by pugstah on 2016-11-26
Several hours after looking up on the internet for a possible fix, still had no luck. After following every bit of instructions of [this]("https://www.linode.com/docs/networking/vpn/set-up-a-hardened-openvpn-server") & [this]("https://www.linode.com/docs/networking/vpn/configuring-openvpn-client-devices") OpenVPN for VPS tutorial, still my lubuntu 16.04 could not browse the internet after connecting. I'm not really sure with what I'm doing since I'm still fresh on linux. Take note that I also tried connecting via windows, Its says this "Connecting to client has failed". A Help from you guys are much appreciated! Thank you. I'll provide you with the certain config files if needed.

Output of - journalctl -f | grep vpn
```
Nov 26 19:08:08 Harvey-Lenovo-VM sudo[11880]:   harvey : TTY=pts/0 ; PWD=/etc/openvpn ; USER=root ; COMMAND=/bin/chmod 777 keys
Nov 26 19:08:39 Harvey-Lenovo-VM sudo[11893]:   harvey : TTY=pts/0 ; PWD=/etc/openvpn ; USER=root ; COMMAND=/bin/chmod -R 777 keys
Nov 26 19:16:13 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158973.4214] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",0]: Started the VPN service, PID 11946
Nov 26 19:16:13 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158973.4385] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",0]: Saw the service appear; activating connection
Nov 26 19:16:13 Harvey-Lenovo-VM NetworkManager[709]: nm-openvpn-Message: openvpn[11951] started
Nov 26 19:16:13 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158973.4650] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",0]: VPN plugin: state changed: starting (3)
Nov 26 19:16:13 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158973.4657] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",0]: VPN connection: (ConnectInteractive) reply received
Nov 26 19:16:13 Harvey-Lenovo-VM nm-openvpn[11951]: OpenVPN 2.3.10 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Feb  2 2016
Nov 26 19:16:13 Harvey-Lenovo-VM nm-openvpn[11951]: library versions: OpenSSL 1.0.2g  1 Mar 2016, LZO 2.08
Nov 26 19:16:13 Harvey-Lenovo-VM nm-openvpn[11951]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Nov 26 19:16:13 Harvey-Lenovo-VM nm-openvpn[11951]: WARNING: file '/etc/openvpn/keys/client1.key' is group or others accessible
Nov 26 19:16:13 Harvey-Lenovo-VM nm-openvpn[11951]: WARNING: file '/etc/openvpn/keys/ta.key' is group or others accessible
Nov 26 19:16:13 Harvey-Lenovo-VM nm-openvpn[11951]: Control Channel Authentication: using '/etc/openvpn/keys/ta.key' as a OpenVPN static key file
Nov 26 19:16:13 Harvey-Lenovo-VM nm-openvpn[11951]: NOTE: chroot will be delayed because of --client, --pull, or --up-delay
Nov 26 19:16:13 Harvey-Lenovo-VM nm-openvpn[11951]: NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Nov 26 19:16:13 Harvey-Lenovo-VM nm-openvpn[11951]: UDPv4 link local: [undef]
Nov 26 19:16:13 Harvey-Lenovo-VM nm-openvpn[11951]: UDPv4 link remote: [AF_INET]193.70.43.65:1194
Nov 26 19:16:27 Harvey-Lenovo-VM nm-openvpn[11951]: [server] Peer Connection Initiated with [AF_INET]193.70.43.65:1194
Nov 26 19:16:30 Harvey-Lenovo-VM nm-openvpn[11951]: TUN/TAP device tun0 opened
Nov 26 19:16:30 Harvey-Lenovo-VM nm-openvpn[11951]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper --bus-name org.freedesktop.NetworkManager.openvpn.Connection_25 --tun -- tun0 1500 1602 10.8.0.6 10.8.0.5 init
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3591] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",0]: VPN connection: (IP Config Get) reply received.
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3628] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: VPN connection: (IP4 Config Get) reply received
Nov 26 19:16:30 Harvey-Lenovo-VM nm-openvpn[11951]: chroot to '/var/lib/openvpn/chroot' and cd to '/' succeeded
Nov 26 19:16:30 Harvey-Lenovo-VM nm-openvpn[11951]: GID set to nm-openvpn
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3640] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: Data: VPN Gateway: 193.70.43.65
Nov 26 19:16:30 Harvey-Lenovo-VM nm-openvpn[11951]: UID set to nm-openvpn
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3641] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: Data: Tunnel Device: tun0
Nov 26 19:16:30 Harvey-Lenovo-VM nm-openvpn[11951]: Initialization Sequence Completed
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3641] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: Data: IPv4 configuration:
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3641] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: Data:   Internal Gateway: 10.8.0.5
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3641] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: Data:   Internal Address: 10.8.0.6
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3642] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: Data:   Internal Prefix: 32
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3642] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: Data:   Internal Point-to-Point Address: 10.8.0.5
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3642] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: Data:   Maximum Segment Size (MSS): 0
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3642] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: Data:   Static Route: 10.8.0.1/32   Next Hop: 10.8.0.5
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3643] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: Data:   Forbid Default Route: no
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3643] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: Data:   Internal DNS: 127.0.0.1
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3643] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: Data:   Internal DNS: 8.8.8.8
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3643] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: Data:   DNS Domain: '(none)'
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3644] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: Data: No IPv6 configuration
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3645] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: VPN plugin: state changed: started (4)
Nov 26 19:16:30 Harvey-Lenovo-VM NetworkManager[709]: <info>  [1480158990.3664] vpn-connection[0x1e0b7d0,ac382680-bb22-49b5-800b-427d2d25c120,"VPN connection 1",13:(tun0)]: VPN connection: (IP Config Get) complete
Nov 26 19:16:30 Harvey-Lenovo-VM nm-dispatcher[11974]: req:1 'vpn-up' [tun0]: new request (1 scripts)
Nov 26 19:16:30 Harvey-Lenovo-VM nm-dispatcher[11974]: req:1 'vpn-up' [tun0]: start running ordered scripts...


```

---

