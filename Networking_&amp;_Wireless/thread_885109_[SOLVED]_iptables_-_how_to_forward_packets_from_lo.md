---
title: "[SOLVED] iptables - how to forward packets from localhost through SSH tunnel?"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by swerner on 2008-08-09
I would like to have the situation described below:

```

                    SSH Tunnel                     
my PC (localhost)================Remote SSH Server----------some-web-server.com
                     Internet                      Internet
```
*some-web-server.com* can only be accessed via the *Remote SSH Server*.  I have successfully set up an SSH tunnel to the remote SSH Server to do some port forwarding between *my PC* and *some-web-server.com*. If I want to access *some-web-server.com* from Firefox I use "http://localhost:80".

I want this to be transparent, such that I do not need to use "http://localhost:80", I just want to type "http://some-web-server.com" in the URL on *my PC*.
**How do I set up iptables on localhost to forward all traffic bound for *some-web-server.com* through the SSH tunnel?**

I have tried the following command (and many others) without success:
iptables -t nat -A OUTPUT --out-interface lo --source 127.0.0.1 -p tcp --destination-port 80 -j DNAT --to-destination 123.456.78.9

---

### Post by superm1 on 2008-08-09
> **swerner said:**
> I would like to have the situation described below:

```

                    SSH Tunnel                     
my PC (localhost)================Remote SSH Server----------some-web-server.com
                     Internet                      Internet
```*some-web-server.com* can only be accessed via the *Remote SSH Server*.  I have successfully set up an SSH tunnel to the remote SSH Server to do some port forwarding between *my PC* and *some-web-server.com*. If I want to access *some-web-server.com* from Firefox I use "http://localhost:80".

I want this to be transparent, such that I do not need to use "http://localhost:80", I just want to type "http://some-web-server.com" in the URL on *my PC*.
**How do I set up iptables on localhost to forward all traffic bound for *some-web-server.com* through the SSH tunnel?**

I have tried the following command (and many others) without success:
iptables -t nat -A OUTPUT --out-interface lo --source 127.0.0.1 -p tcp --destination-port 80 -j DNAT --to-destination 123.456.78.9
Well two options.  If you are just needing web browsing, use the -D forward option.  Set up a local SOCKS proxy in your web browser.

If you need more, forward a VPN connection over the SSH tunnel.

---

### Post by swerner on 2008-08-14
> **superm1 said:**
> Well two options.  If you are just needing web browsing, use the -D forward option.  Set up a local SOCKS proxy in your web browser.

If you need more, forward a VPN connection over the SSH tunnel.

Thanks for your reply. I investigated both options and neither were suitable.  The proxy did not work because I required multiple connections. The VPN connection did not work because I did not have root access to the sshd server.

Instead I came up with a less-than-elegant method and used rinetd.  It is suitable for the temporary time I need the connection.  To do this I did the following:
1) Set up virtual network devices
```

sudo ifconfig eth0:1 192.168.0.128 netmask 255.255.255.0
sudo ifconfig eth0:2 192.168.0.129 netmask 255.255.255.0
```

2) for all the web servers I wanted to connect to I added them in the /etc/hosts file and pointed them to the virtual network device:
```

192.168.0.128   webserver1.com
192.168.0.129   webserver2.com
```

3) Then I needed to redirect the localhost ports with rinetd.  In the /etc/rinetd.conf file I added the following:
```

allow 192.168.0.*

# bindadress    bindport  connectaddress  connectport
192.168.0.128   80        127.0.0.1       82
192.168.0.129   80        127.0.0.1       81

```

4) Then I set up my SSH tunnel
```

sudo ssh -f simon@$SSHD_SERVER -L 81:123.123.0.1:80 -L 82:123.123.0.2:80
```

This acted like a transparent proxy.  Although the method is not ideal, it works.  This would be much more elegant using iptables.

---

### Post by Bobkins on 2008-08-14
Wherever he functioned Nicolas was certainly cock of the walk.

---

