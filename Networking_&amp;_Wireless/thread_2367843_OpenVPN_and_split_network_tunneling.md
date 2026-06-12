---
title: "OpenVPN and split network tunneling"
date: 2017-08-03
forum: Networking &amp; Wireless
---

### Post by derekcentrico on 2017-08-03
I've been looking all over for a solution that will do the following:
1.  keep an OpenVPN service alive
2.  put only certain applications through the VPN based upon the user/group launched -or- assigned device (eth0 vs tun0)

Initially, I installed OpenVPN via Network Manager.  All data was passed through the VPN at that point.  I couldn't limit the data.

So, I googled around and found this:  [https://www.htpcguides.com/force-torrent-traffic-vpn-split-tunnel-debian-8-ubuntu-16-04/](https://www.htpcguides.com/force-torrent-traffic-vpn-split-tunnel-debian-8-ubuntu-16-04/)

I followed all of the steps.  However, it seems like certain aspects aren't working which means the entire data still goes through the VPN and the supposed VPN user is stuck at 127.0.0.1 no data flow.

> [COLOR=#2A2E2E][FONT=&quot]Job for [email]openvpn@openvpn.service.servic[/email]e failed because the control process exited with error code. See "systemctl status [email]openvpn@openvpn.service.servic[/email]e" and "journalctl -xe" for details.[/FONT][/COLOR]


[COLOR=#2A2E2E][FONT=&quot]Journalctl said:
> -- Unit [email]openvpn@openvpn.service.servic[/email]e has begun starting up.
Aug 03 17:25:19 homeserver ovpn-openvpn.service[4316]: Options error: In [CMD-LINE]:1: Error opening configuration file: /etc/openvpn/openvpn.service.conf
Aug 03 17:25:19 homeserver ovpn-openvpn.service[4316]: Use --help for more information.
Aug 03 17:25:19 homeserver systemd[1]: [email]openvpn@openvpn.service.servic[/email]e: Control process exited, code=exited status=1
Aug 03 17:25:19 homeserver systemd[1]: Failed to start OpenVPN connection to openvpn.service.
-- Subject: Unit [email]openvpn@openvpn.service.servic[/email]e has failed
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.or...]("http://disq.us/url?url=http%3A%2F%2Flists.freedesktop.org%2Fmailman%2Flistinfo%2Fsystemd-devel%3AYEcsPrwG3uGlsQONKVATo_Uxzg0&cuid=3389144")[/FONT][/COLOR]
[COLOR=#2A2E2E][FONT=&quot]So, I cat'ed openvpn.conf into openvpn.service.conf and it seemed to start okay.[/FONT][/COLOR]
[COLOR=#2A2E2E][FONT=&quot]Status says this, though:
> &#9679; [email]openvpn@openvpn.servic[/email]e - OpenVPN connection to openvpn
Loaded: loaded (/etc/systemd/system/openvpn@openvpn.service; enabled; vendor preset: enabled)
Active: inactive (dead) since Thu 2017-08-03 17:11:46 EDT; 11min ago
Docs: man:openvpn(8)
[https://community.openvpn.n...]("https://disq.us/url?url=https%3A%2F%2Fcommunity.openvpn.net%2Fopenvpn%2Fwiki%2FOpenvpn23ManPage%3Ad3tq7m0WkG7I6YMY3AjElbFk3dI&cuid=3389144")
[https://community.openvpn.n...]("https://disq.us/url?url=https%3A%2F%2Fcommunity.openvpn.net%2Fopenvpn%2Fwiki%2FHOWTO%3AmsXk87I6qUpdHGn3kLl608hWLUg&cuid=3389144")
Main PID: 1167 (code=exited, status=0/SUCCESS)[/FONT][/COLOR]
[COLOR=#2A2E2E][FONT=&quot]Aug 03 17:11:38 homeserver ovpn-openvpn[1167]: VERIFY OK: depth=0, C=PA, ST=PA, L=Panama, O=NordVPN, OU=NordVPN, CN=[us663.nordvpn.com]("http://disq.us/url?url=http%3A%2F%2Fus663.nordvpn.com%3AWC42qqtdCF115SCteHCDjSB-oUY&cuid=3389144"), name=NordVPN, emailAddress=cert@nordvpn.com
Aug 03 17:11:40 homeserver ovpn-openvpn[1167]: Data Channel Encrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Aug 03 17:11:40 homeserver ovpn-openvpn[1167]: Data Channel Encrypt: Using 512 bit message hash 'SHA512' for HMAC authentication
Aug 03 17:11:40 homeserver ovpn-openvpn[1167]: Data Channel Decrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Aug 03 17:11:40 homeserver ovpn-openvpn[1167]: Data Channel Decrypt: Using 512 bit message hash 'SHA512' for HMAC authentication
Aug 03 17:11:40 homeserver ovpn-openvpn[1167]: Control Channel: TLSv1.2, cipher TLSv1/SSLv3 ECDHE-RSA-AES256-GCM-SHA384, 2048 bit RSA
Aug 03 17:11:40 homeserver ovpn-openvpn[1167]: [[us663.nordvpn.com]("http://disq.us/url?url=http%3A%2F%2Fus663.nordvpn.com%3AWC42qqtdCF115SCteHCDjSB-oUY&cuid=3389144")] Peer Connection Initiated with [AF_INET]23.227.207.85:443
Aug 03 17:11:43 homeserver ovpn-openvpn[1167]: SENT CONTROL [[us663.nordvpn.com]("http://disq.us/url?url=http%3A%2F%2Fus663.nordvpn.com%3AWC42qqtdCF115SCteHCDjSB-oUY&cuid=3389144")]: 'PUSH_REQUEST' (status=1)
Aug 03 17:11:46 homeserver ovpn-openvpn[1167]: AUTH: Received control message: AUTH_FAILED
Aug 03 17:11:46 homeserver ovpn-openvpn[1167]: SIGTERM[soft,auth-failure] received, process exiting[/FONT][/COLOR]


[COLOR=#2A2E2E][FONT=&quot]I ran the IPTABLES command. I do not see it on iptables -S though. It is listed at the top of the persistent file and tons of PGL rules below it.  But, it appears not to be utilized.[/FONT][/COLOR]
[COLOR=#2A2E2E][FONT=&quot]My IP for all users except VPN show up as the VPN IP and not my assigned internet IP.  The VPN user times out running the curl command.
[/FONT][/COLOR]
[COLOR=#2A2E2E][FONT=&quot]The VPN resolv.conf is just 127.0.0.1 although I added three other DNS IPs as instructions say to do.

Any and all help is truly appreciated.[/FONT][/COLOR]

---

### Post by nariub on 2017-08-03
I have only ever split horizon based on destination IP address, never tried by application

---

### Post by derekcentrico on 2017-08-04
In my scenario, I cannot dely upon destination IP address if we're talking about the final IP addresses sought.  The only IP address I could rely upon would be routing to the VPN IP address vs. the WAN IP address.

---

