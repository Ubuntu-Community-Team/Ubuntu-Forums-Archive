---
title: "VPN connected but internet doesn't seem to be working."
date: 2016-05-28
forum: Networking &amp; Wireless
---

### Post by aayushdhuria on 2016-05-28
I'm using OpenVPN on Xubuntu 16.04 via Network Manager and it looks like I can't access the internet once the VPN is connected. The other method 

```
openvpn --config ~/.openvpn/client.ovpn
```

gives me this error

```
ERROR: Cannot ioctl TUNSETIFF tun: Operation not permitted (errno=1)
```

When I try the same with sudo, it gets stuck at this after a bunch of /sbin/ip/route add 

```
Initialization Sequence Completed
```

Now back to Network Manager, if I check the "use this connection only for resources on its network", I can access internet after connecting but my location doesn't change nor is my connection encrypted.

I've set ufw to allow all outgoing using Gufw so it can't be firewall. What else can I look into? I'm using privatetunnel config profile and it seems be working alright on my phone.

Edit: Kernel IP routing tables pre VPN

```
Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.2.1     0.0.0.0         UG    600    0        0 wlp3s0
link-local      *               255.255.0.0     U     1000   0        0 wlp3s0
192.168.2.0     *               255.255.255.0   U     600    0        0 wlp3s0

```

post VPN

```
Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.9.0.1        0.0.0.0         UG    50     0        0 tun0
default         192.168.2.1     0.0.0.0         UG    600    0        0 wlp3s0
10.9.0.0        *               255.255.0.0     U     50     0        0 tun0
149.255.32.231  192.168.2.1     255.255.255.255 UGH   600    0        0 wlp3s0
link-local      *               255.255.0.0     U     1000   0        0 wlp3s0
192.168.2.0     *               255.255.255.0   U     600    0        0 wlp3s0

```

I've uncommented 

```
net.ipv4.ip_forward = 1
``` 

in sysctl.conf

---

### Post by pedro_rodriguez2 on 2016-05-28
Hi, I'm very interested in a solution too! I'm having a similar problem.

I followed the instructions here:

[https://www.digitalocean.com/communi...n-ubuntu-14-04]("https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-14-04")

and here:

[https://vexxhost.com/resources/tutor...-ubuntu-14-04/]("https://vexxhost.com/resources/tutorials/how-to-setup-openvpn-server-and-client-on-ubuntu-14-04/")

I got no errors.

If I enter ifconfig I see:

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

but how to tell Ubu 14.04 to connect through this, I don't know!!

[https://www.dnsleaktest.com/](https://www.dnsleaktest.com/) shows my ip as China.

I am getting this kind of thing:

pedro@pedro-schule:~$ openvpn --config /etc/openvpn/RapidResults.ovpn
Sat May 28 17:09:55 2016 OpenVPN 2.3.2 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Dec  1 2014
Sat May 28 17:09:55 2016 Socket Buffers: R=[212992->131072] S=[212992->131072]
Sat May 28 17:09:55 2016 NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Sat May 28 17:09:55 2016 UDPv4 link local: [undef]
Sat May 28 17:09:55 2016 UDPv4 link remote: [AF_INET]202.102.110.203:1194
Sat May 28 17:10:55 2016 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Sat May 28 17:10:55 2016 TLS Error: TLS handshake failed
Sat May 28 17:10:55 2016 SIGUSR1[soft,tls-error] received, process restarting
Sat May 28 17:10:55 2016 Restart pause, 2 second(s)
Sat May 28 17:10:57 2016 Socket Buffers: R=[212992->131072] S=[212992->131072]
Sat May 28 17:10:57 2016 UDPv4 link local: [undef]
Sat May 28 17:10:57 2016 UDPv4 link remote: [AF_INET]202.102.110.203:1194

I put this in server.conf

# The hostname/IP and port of the server.
# You can have multiple remote entries
# to load balance between the servers.
remote localhost 1194

Is that a mistake?

Something is not set right.

What to do??

---

### Post by aayushdhuria on 2016-05-28
I used instructions very similar to these - [http://howto.praqma.net/ubuntu/vpn/openvpn-access-server-client-on-ubuntu](http://howto.praqma.net/ubuntu/vpn/openvpn-access-server-client-on-ubuntu)

I added crt files in the appropriate boxes and connected. The VPN does connect - I just can't access the internet. I've previously used the very same config file and method to successfully connect to VPN with working internet on xubuntu itself. I did a fresh install of xubuntu-core on the same laptop and now it doesn't work. I've added all the required packages, done what I was within the purview of my knowledge.

---

### Post by pedro_rodriguez2 on 2016-05-28
Could you send me or post your server.conf and client.conf? I think I have something wrong in there. I'd like to compare.

---

### Post by pedro_rodriguez2 on 2016-05-28
Also, trying the instructions here:

[http://howto.praqma.net/ubuntu/vpn/o...ient-on-ubuntu]("http://howto.praqma.net/ubuntu/vpn/openvpn-access-server-client-on-ubuntu")

2 problems:
1.

I do not have any tls-auth file or ta.key

How do I make that?

2. I have a file RapidResults.ovpn which is, I thought, the basis file  for the vpn connection. When I try and import it in Network Manager, I  get an import error (see thumbnail).

What kind of file does Network Manager want?? I tried renaming it .pptp and .conf

I also tried importing /etc/openvpn/client.conf but I still get the same error window.

---

### Post by aayushdhuria on 2016-05-29
server.conf and client.conf? For openvpn? I don't think I have those files... (or don't know about them)

1) my .ovpn file had a tls-key b/w the tags <TLS-AUTH>. Can't share it, sorry, paid VPN.

2) You can only import .ovpn file in OpenVPN afaik. It's probably not accepting the format of the file.

Edit: Yup, no server.conf or client.conf files in /etc/openvpn... weird.

---

