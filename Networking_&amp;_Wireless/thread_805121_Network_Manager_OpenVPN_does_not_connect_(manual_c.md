---
title: "Network Manager OpenVPN does not connect (manual connect works)"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by RedKrieg on 2008-05-23
I can't connect to my openvpn server using network manager (error: "Could not start the VPN connection 'connectionname' due to a connection error.  The VPN login failed because the VPN program could not connect to the VPN server.), but a manual connection to the server works fine with the following configuration file:

```

client
dev tap
proto udp
remote xxxxxx.xxxxxxx.net
resolv-retry infinite
nobind
persist-key
persist-tun
ca /home/username/certificate.pem
auth-user-pass
comp-lzo

```

I've done a ps aux | grep openvpn immediately after attempting to connect via nm and found this:

```

root     14469  0.0  0.2   4264  2400 ?        S    17:22   0:00 /usr/sbin/openvpn --remote xxxxxx.xxxxxxxx.net --ns-cert-type server --comp-lzo --nobind --dev tap --proto udp --port 1194 --syslog nm-openvpn --up /usr/lib/network-manager-openvpn/nm-openvpn-service-openvpn-helper --up-restart --persist-key --persist-tun --management 127.0.0.1 1194 --management-query-passwords --client --auth-user-pass --ca /home/username/certificate.pem

```

I found that by removing the "management" and "syslog" related parameters I could interactively attempt to connect.  This is what I get:

```

Enter Auth Username:username
Enter Auth Password:
Fri May 23 17:16:24 2008 LZO compression initialized
Fri May 23 17:16:24 2008 UDPv4 link local: [undef]
Fri May 23 17:16:24 2008 UDPv4 link remote: 10.0.1.1:1194
Fri May 23 17:16:27 2008 TLS_ERROR: BIO read tls_read_plaintext error: error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
Fri May 23 17:16:27 2008 TLS Error: TLS object -> incoming plaintext read error
Fri May 23 17:16:27 2008 TLS Error: TLS handshake failed
Fri May 23 17:16:27 2008 SIGUSR1[soft,tls-error] received, process restarting
Fri May 23 17:16:29 2008 Re-using SSL/TLS context
Fri May 23 17:16:29 2008 LZO compression initialized
Fri May 23 17:16:29 2008 UDPv4 link local: [undef]
Fri May 23 17:16:29 2008 UDPv4 link remote: 10.0.1.1:1194
Fri May 23 17:16:29 2008 TLS_ERROR: BIO read tls_read_plaintext error: error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
Fri May 23 17:16:29 2008 TLS Error: TLS object -> incoming plaintext read error
Fri May 23 17:16:29 2008 TLS Error: TLS handshake failed
Fri May 23 17:16:29 2008 SIGUSR1[soft,tls-error] received, process restarting
Fri May 23 17:16:30 2008 SIGINT[hard,init_instance] received, process exiting

```

My question is: what have I done differently between the network-manager configuration and the raw openvpn configuration that prevents me from connecting?  The server log just repeats "Re-using SSL/TLS context" and "LZO compression initialized" followed by a bunch of "Connection refused (code=111)"

Has anyone seen this before?  It's quite annoying to have to use the command line to connect to my VPN when there's an icon just sitting there doing nothing that's supposed to take care of this.

---

