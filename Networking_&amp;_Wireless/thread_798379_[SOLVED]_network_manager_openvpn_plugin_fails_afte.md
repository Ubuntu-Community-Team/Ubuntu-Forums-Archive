---
title: "[SOLVED] network manager openvpn plugin fails after upgrade"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by jonathan.hofman on 2008-05-18
I'm currently using Hardy.

After the security upgrade for openssl my VPN client connection fails. For this connection I use the openvpn plugin of the network manager. The connection fails with the message: 

'The VPN login failed because the VPN program could not connect to the VPN server.'

Before the upgrade everything worked fine. Also I can still connect using the command line openvpn command and an appropriate configuration file. So the server is still accessible.

In some cases when I try to connect with the network manager it seems the connection is made even though the error is generated. In this case the network manager does not show the VPN connection is active and therefore I'm unable to disconnect the VPN connection.   

I have regenerated the certificates to be sure these where not the problem. Anybody else has this problem? Is there a way to get more information why the connection failed. I could get the following from syslog (I've replaced the IP and username for privacy reasons), but this does not give any clue.


```
May 18 10:38:34 osmium NetworkManager: <info>  Will activate VPN connection 'Company VPN', service 'org.freedesktop.NetworkManager.openvpn', user_name 'jonathan', vpn_data 'connection-type / x509userpass / dev / tun / remote / XXX.XXX.XXX.XXX / port / 1194 / proto / udp / servercert-insecure / yes / ca / /home/jonathan/server/algemeen/configuraties/vpn/cert/tl.pem / cert / /home/jonathan/server/algemeen/configuraties/vpn/cert/tl.crt / key / /home/jonathan/server/algemeen/configuraties/vpn/cert/tl.key / comp-lzo / yes / shared-key /  / local-ip /  / remote-ip /  / username / user.name', route '172.16.0.0/16'. 
May 18 10:38:34 osmium NetworkManager: <info>  VPN Activation (Company VPN) Stage 1 of 4 (Connection Prepare) scheduled... 
May 18 10:38:34 osmium NetworkManager: <info>  VPN Activation (Company VPN) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.openvpn (PID 6323) 
May 18 10:38:34 osmium NetworkManager: <info>  VPN Activation (Company VPN) Stage 1 of 4 (Connection Prepare) complete. 
May 18 10:38:34 osmium NetworkManager: <info>  VPN Activation (Company VPN) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
May 18 10:38:34 osmium kernel: [  127.432819] tun: Universal TUN/TAP device driver, 1.6
May 18 10:38:34 osmium kernel: [  127.432827] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
May 18 10:38:34 osmium NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' signaled state change 1 -> 6. 
May 18 10:38:34 osmium NetworkManager: <info>  VPN Activation (Company VPN) Stage 2 of 4 (Connection Prepare Wait) waiting... 
May 18 10:38:34 osmium NetworkManager: <info>  VPN Activation (Company VPN) Stage 2 of 4 (Connection Prepare Wait) complete. 
May 18 10:38:34 osmium NetworkManager: <info>  VPN Activation (Company VPN) Stage 3 of 4 (Connect) scheduled... 
May 18 10:38:34 osmium NetworkManager: <info>  VPN Activation (Company VPN) Stage 3 of 4 (Connect) sending connect request. 
May 18 10:38:34 osmium NetworkManager: <info>  VPN Activation (Company VPN) Stage 3 of 4 (Connect) request sent, waiting for reply... 
May 18 10:38:34 osmium NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' signaled state change 6 -> 3. 
May 18 10:38:34 osmium NetworkManager: <info>  VPN Activation (Company VPN) Stage 3 of 4 (Connect) reply received. 
May 18 10:38:34 osmium NetworkManager: <info>  VPN Activation (Company VPN) Stage 4 of 4 (IP Config Get) timeout scheduled... 
May 18 10:38:34 osmium NetworkManager: <info>  VPN Activation (Company VPN) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
May 18 10:38:34 osmium nm-openvpn[6329]: OpenVPN 2.1_rc7 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on May 14 2008
May 18 10:38:34 osmium nm-openvpn[6329]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
May 18 10:38:34 osmium nm-openvpn[6329]: /usr/sbin/openssl-vulnkey -q /home/jonathan/server/algemeen/configuraties/vpn/cert/tl.key
May 18 10:38:49 osmium NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.openvpn', signal 'ConnectFailed', with message 'The VPN login failed because the VPN program could not connect to the VPN server.'. 
May 18 10:38:49 osmium NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' signaled state change 3 -> 5. 
May 18 10:38:49 osmium NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' signaled state change 5 -> 6. 
May 18 10:38:49 osmium NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.openvpn): could not stop connection 'Company VPN' because service was 6. 
```

---

### Post by statesec on 2008-05-20
Same exact problem here.  Working perfectly with keys thankfully generated on a non-Ubuntu distribution until the "SSL" fix since when it has been busted (this on Hardy).  My logs are identical to your's.  Also like you the OpenVPN does connect sometimes even though the network manager GUI says it has failed.

---

### Post by statesec on 2008-05-20
It looks to be related to this bug...

[https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/230197](https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/230197)

---

### Post by jonathan.hofman on 2008-05-21
Thanks, this indeed points to the problem I have. I hope a solution will be made soon. I have made the 'quick and dirty' fix to replace openssl-vulnkey with openvpn-vulnkey, which indeed solves the problem for now.

---

