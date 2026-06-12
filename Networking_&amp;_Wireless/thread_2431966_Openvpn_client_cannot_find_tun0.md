---
title: "Openvpn client cannot find tun0"
date: 2019-11-25
forum: Networking &amp; Wireless
---

### Post by afan1 on 2019-11-25
Hello all,

I am trying to setup an openvpn so I can visit the ubuntu box at home from my laptop, say, at my office. But at the client side I cannot find tun0 and cannot ping server.

I followed the instructions from ubuntu server guide -> VPN. I am using ubuntu desktop instead of server though. At the server side it seems openvpn was setup. ifconfig tun0 returns:

tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 10.8.0.1  netmask 255.255.255.255  destination 10.8.0.2
        inet6 fe80::4629:bb76:7487:22ff  prefixlen 64  scopeid 0x20<link>
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (UNSPEC)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 11  bytes 528 (528.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

and I can ping 10.8.0.1.

But the client cannot find tun0:
tun0: error fetching interface information: Device not found

Here is my server's .conf file:
port 1194
proto udp
dev tun
ca ca.crt
cert OpenVPN_Tom.crt
key OpenVPN_Tom.key 
dh dh4096.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist /var/log/openvpn/ipp.txt
keepalive 10 120
tls-auth ta.key 0
cipher AES-256-CBC
user nobody
group nogroup
persist-key
persist-tun
status /var/log/openvpn/openvpn-status.log
verb 3
explicit-exit-notify 1

Client's .conf file
client
dev tun
proto udp
remote [my desktop ip found from what is my ip] 1194
resolv-retry infinite
nobind
user nobody
group nogroup
persist-key
persist-tun
ca ca.crt
cert openvpn_laptop.crt
key openvpn_laptop.key
remote-cert-tls server
tls-auth ta.key 1
cipher AES-256-CBC
verb 3

The ta.key was generated at server by "openvpn --genkey --secret /etc/openvpn/ta.key" and copied to client as well.
I also uncommented "#net.ipv4.ip_forward=1" from /etc/sysctl.conf in both server and client.

At the server side I added firewall port rule in gufw: 
Name: openvpn; Policy: Allow; Direction: In; Interface: All Interfaces; Log: Log All; Protocol: UDP; From: IP (port 1194); To: IP (port 1194)

At the client here is result of "systemctl status openvpn@openvpn_laptop"
&#9679; [EMAIL="openvpn@openvpn_laptop.servic"]openvpn@openvpn_laptop.servic[/EMAIL]e - OpenVPN connection to openvpn_laptop
   Loaded: loaded (/lib/systemd/system/openvpn@.service; indirect; vendor preset: enabled)
   Active: active (running) since Sun 2019-11-24 23:41:42 EST; 42min ago
     Docs: man:openvpn(8)
           [https://community.openvpn.net/openvpn/wiki/Openvpn24ManPage](https://community.openvpn.net/openvpn/wiki/Openvpn24ManPage)
           [https://community.openvpn.net/openvpn/wiki/HOWTO](https://community.openvpn.net/openvpn/wiki/HOWTO)
 Main PID: 2076 (openvpn)
   Status: "Pre-connection initialization successful"
    Tasks: 1 (limit: 4432)
   CGroup: /system.slice/system-openvpn.slice/openvpn@openvpn_laptop.service
           &#9492;&#9472;2076 /usr/sbin/openvpn --daemon ovpn-openvpn_laptop --status /run/openvpn/openvpn_laptop.status 10 --cd /etc/openvpn --script-security 2 --config /etc/openvpn/openvpn_laptop.conf --writepid /run

Nov 25 00:15:14 tom-Studio-1558 ovpn-openvpn_laptop[2076]: SIGUSR1[soft,tls-error] received, process restarting
Nov 25 00:15:14 tom-Studio-1558 ovpn-openvpn_laptop[2076]: Restart pause, 300 second(s)
Nov 25 00:20:14 tom-Studio-1558 ovpn-openvpn_laptop[2076]: TCP/UDP: Preserving recently used remote address: [AF_INET]xx.xxx.xxx.xxx:1194
Nov 25 00:20:14 tom-Studio-1558 ovpn-openvpn_laptop[2076]: Socket Buffers: R=[212992->212992] S=[212992->212992]
Nov 25 00:20:14 tom-Studio-1558 ovpn-openvpn_laptop[2076]: UDP link local: (not bound)
Nov 25 00:20:14 tom-Studio-1558 ovpn-openvpn_laptop[2076]: UDP link remote: [AF_INET][LEFT][COLOR=#222222][FONT=Verdana]xx.xxx.xxx.xxx[/FONT][/COLOR][/LEFT]:1194
Nov 25 00:21:14 tom-Studio-1558 ovpn-openvpn_laptop[2076]: TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Nov 25 00:21:14 tom-Studio-1558 ovpn-openvpn_laptop[2076]: TLS Error: TLS handshake failed
Nov 25 00:21:14 tom-Studio-1558 ovpn-openvpn_laptop[2076]: SIGUSR1[soft,tls-error] received, process restarting
Nov 25 00:21:14 tom-Studio-1558 ovpn-openvpn_laptop[2076]: Restart pause, 300 second(s)

But if I run the above command immediately after starting openvpn, there is no complain about TLS Error:
"systemctl stop openvpn@openvpn_laptop; systemctl start openvpn@openvpn_laptop; systemctl status openvpn@openvpn_laptop"
&#9679; [EMAIL="openvpn@openvpn_laptop.servic"]openvpn@openvpn_laptop.servic[/EMAIL]e - OpenVPN connection to openvpn_laptop
   Loaded: loaded (/lib/systemd/system/openvpn@.service; indirect; vendor preset: enabled)
   Active: active (running) since Mon 2019-11-25 00:25:20 EST; 12ms ago
     Docs: man:openvpn(8)
           [https://community.openvpn.net/openvpn/wiki/Openvpn24ManPage](https://community.openvpn.net/openvpn/wiki/Openvpn24ManPage)
           [https://community.openvpn.net/openvpn/wiki/HOWTO](https://community.openvpn.net/openvpn/wiki/HOWTO)
 Main PID: 3445 (openvpn)
   Status: "Pre-connection initialization successful"
    Tasks: 1 (limit: 4432)
   CGroup: /system.slice/system-openvpn.slice/openvpn@openvpn_laptop.service
           &#9492;&#9472;3445 /usr/sbin/openvpn --daemon ovpn-openvpn_laptop --status /run/openvpn/openvpn_laptop.status 10 --cd /etc/openvpn --script-security 2 --config /etc/openvpn/openvpn_laptop.conf --writepid /run

Nov 25 00:25:20 tom-Studio-1558 systemd[1]: Starting OpenVPN connection to openvpn_laptop...
Nov 25 00:25:20 tom-Studio-1558 ovpn-openvpn_laptop[3445]: library versions: OpenSSL 1.1.1  11 Sep 2018, LZO 2.08
Nov 25 00:25:20 tom-Studio-1558 systemd[1]: Started OpenVPN connection to openvpn_laptop.
Nov 25 00:25:20 tom-Studio-1558 ovpn-openvpn_laptop[3445]: Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Nov 25 00:25:20 tom-Studio-1558 ovpn-openvpn_laptop[3445]: Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Nov 25 00:25:20 tom-Studio-1558 ovpn-openvpn_laptop[3445]: TCP/UDP: Preserving recently used remote address: [AF_INET][LEFT][COLOR=#222222][FONT=Verdana]xx.xxx.xxx.xxx[/FONT][/COLOR][/LEFT]:1194
Nov 25 00:25:20 tom-Studio-1558 ovpn-openvpn_laptop[3445]: Socket Buffers: R=[212992->212992] S=[212992->212992]
Nov 25 00:25:20 tom-Studio-1558 ovpn-openvpn_laptop[3445]: UDP link local: (not bound)
Nov 25 00:25:20 tom-Studio-1558 ovpn-openvpn_laptop[3445]: UDP link remote: [AF_INET][LEFT][COLOR=#222222][FONT=Verdana]xx.xxx.xxx.xxx[/FONT][/COLOR][/LEFT]:1194
Nov 25 00:25:20 tom-Studio-1558 ovpn-openvpn_laptop[3445]: NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay

Sorry for the clumsy description. Anyone can help me with it? Many thanks.

---

### Post by SeijiSensei on 2019-11-25
Does the client machine have a /dev/net/tun device? It should, but just in case it doesn't, you can create one like this:
```

sudo mkdir -p /dev/net/tun
sudo mknod /dev/net/tun c 10 200
sudo chmod 0666 /dev/net/tun

```

I use static VPNs for point-to-point connections: [https://openvpn.net/community-resources/static-key-mini-howto/](https://openvpn.net/community-resources/static-key-mini-howto/)

Much simpler to create and maintain.

---

### Post by afan1 on 2019-11-25
Thanks SeijiSensei. Don't know if the device exists. "ls -al /dev/net/tun" shows "crw-rw-rw- 1 root root 10,  200 Nov 25 14:24 /dev/net/tun".

I plan to access it through two laptops, so I skipped static VPN. I will revisit this idea if eventually I could not make it. Thanks.

---

### Post by SeijiSensei on 2019-11-25
Then the device is there.  You might increase the log-level in your configuration files and see if that helps.

I have a client with half-a-dozen people who connect with static tunnels. Each one has a different client-side IP address.

---

### Post by afan1 on 2019-11-25
Thanks for your help. I am not an expert in computer at all. I should adopt your suggestion to make things simpler. I just want to access my home ubuntu remotely and safely after all.

---

### Post by afan1 on 2020-03-14
The static VPN didn't work either. Eventually I read a news by chance about router safety, which gave me a hint that I might need to open the port at the router. After setting up the router it worked perfectly.

---

