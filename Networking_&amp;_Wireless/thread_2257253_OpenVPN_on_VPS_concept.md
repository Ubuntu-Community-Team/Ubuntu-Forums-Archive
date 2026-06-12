---
title: "OpenVPN on VPS concept"
date: 2014-12-18
forum: Networking &amp; Wireless
---

### Post by LaloTik on 2014-12-18
Hy Guys
What I'm trying to do is to create a OpenVPN Serve on a VPS so I can host my mailserver at home with the Public IP of the VPS because my home connection has a dynamic IP.

I'v configured the server on the VPS , I want to use TUN but I cant understand how to put openvpn port accessible from the wan so i can connect fom home with the openvpn client.

From WAN side that is what i want to do.

->-Public IP VPS-->--VPS with OPENVPN-->-.-.-.-.-.-.-tunnel-.-.-.-.-.-.--->RouterOS OPENVPN CLIENT-->--MailServer.

My problem now is to configure the VPS with TUN, the vpn server and certificates are ok I have already the tun0 up but i cant see the service from my public IP nmap cant fine the port open and netstat .

netstat -na
```

udp        0      0 0.0.0.0:1194            0.0.0.0:*                    

```


```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35413 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2913718 (2.9 MB)  TX bytes:2913718 (2.9 MB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:127.0.0.2  P-t-P:127.0.0.2  Bcast:0.0.0.0  Mask:255.255.255.255
          inet6 addr: 2001:41d0:52:100::14b9/56 Scope:Global
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:827309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:795874 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76538798 (76.5 MB)  TX bytes:95304993 (95.3 MB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:92.*.*.*  P-t-P:92.*.*.*  Bcast:92.222.46.255  Mask:255.255.255.0
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1


```



Thanks to all
&
Sorry for my bad english

---

### Post by TheFu on 2014-12-18
I'd simplify this solution - drop the vpn and just use an email front-end/gateway server that accepts email then forwards it wherever you need.
ScrolloutF1 [http://www.scrolloutf1.com/](http://www.scrolloutf1.com/) is an easy Debian solution for this with good spam filters and noob-friendly setup.  Be certain to have the MX records point to the VPS public IP for your email domain.  You'll also need to dynamically have your home machine found by the VPS when the IP changes ... most people would pay a dyndns provider $15/yr and be done. If you pick the provider supported in the RouterOS, it will be much easier.

Of course, you CAN still run a VPN on the VPS, if you like.  With OpenVPN (at least the most common use), you connect clients to the server and the server provides an IP for the client to use.  Did you get an extra public IP for your VPS?  I'm uncertain whether openvpn can perform single port forwarding, like you appear to desire.  Perhaps ssh port forwarding would be better - assuming this is really the way you still want to head.  Keeping that connection live may be problematic.  Definitely use the reconnect option.

---

