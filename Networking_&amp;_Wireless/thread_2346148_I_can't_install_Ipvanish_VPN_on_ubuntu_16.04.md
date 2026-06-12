---
title: "I can't install Ipvanish VPN on ubuntu 16.04"
date: 2016-12-11
forum: Networking &amp; Wireless
---

### Post by daves77 on 2016-12-11
I've been having trouble installing Ipvanish for the last few days and it's quite frustrating. I've been working with their support and have not resolved the issue. I do live in an area that censors Ipvanish.com; I have tried going to a city where there is no censorship and it works perfectly, but when I go back(censorship) I run into errors. So now I'm here in need of some help.

To start off I ran this command;
```
sudo apt-get install openvpn
```

Then I
```
sudo update-rc.d -f openvpn remove
```

I downloaded the config files and extracted them and then
```
sudo openvpn --config SERVERNAME.ovpn
```

I would get this error
```
$ sudo openvpn --config ipvanish-AU-Sydney-syd-a02.ovpn
Mon Dec 12 09:17:33 2016 OpenVPN 2.3.10 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Feb  2 2016
Mon Dec 12 09:17:33 2016 library versions: OpenSSL 1.0.2g  1 Mar 2016, LZO 2.08
Enter Auth Username: ********************
Enter Auth Password: ********
Mon Dec 12 09:18:09 2016 Socket Buffers: R=[212992->212992] S=[212992->212992]
Mon Dec 12 09:18:09 2016 UDPv4 link local: [undef]
Mon Dec 12 09:18:09 2016 UDPv4 link remote: [AF_INET]204.155.146.114:443
Mon Dec 12 09:19:09 2016 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Mon Dec 12 09:19:09 2016 TLS Error: TLS handshake failed
Mon Dec 12 09:19:09 2016 SIGUSR1[soft,tls-error] received, process restarting
Mon Dec 12 09:19:09 2016 Restart pause, 2 second(s)
Mon Dec 12 09:19:11 2016 Socket Buffers: R=[212992->212992] S=[212992->212992]
Mon Dec 12 09:19:11 2016 TCP/UDP: Preserving recently used remote address: [AF_INET]204.155.146.114:443
Mon Dec 12 09:19:11 2016 UDPv4 link local: [undef]
Mon Dec 12 09:19:11 2016 UDPv4 link remote: [AF_INET]204.155.146.114:443
Mon Dec 12 09:20:11 2016 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)

```

This error would just loop and repeat. Help please.

---

