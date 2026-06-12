---
title: "vpnserver ubuntu server 14.04"
date: 2014-04-26
forum: Networking &amp; Wireless
---

### Post by xtra2 on 2014-04-26
Hello all
maybe somebody can help and tell me what i'm doing wrong.
i have static ip from my ISP, have netgear router and ubuntu server 14.04 which connected via LAN to router.
i want to setup ubuntu server as gate, i want connect to my computer via VPN, so wherever i go to internet, all traffic was going to ubuntu server first.

so what i got:


setup pptpd with internet instructions. i can connect from my macbook to VPN, but don't have any ping (but dns name resolves fine) and go surf websites/anytghing.
:


nano /etc/sysctl.conf
```

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

```


nano /etc/pptpd.conf
```

option /etc/ppp/pptpd-options
logwtmp
localip 192.168.1.133 - lan ip of ubuntu server
remoteip 192.168.1.200-254


bcrelay eth0



```




nano /etc/ppp/chap-secrets
```
# Secrets for authentication using CHAP
# client        server  secret                  IP addresses
xtra    pptpd   password       192.168.1.200
```




nano /etc/ppp/pptpd-options
```



refuse-pap
refuse-chap
refuse-mschap


require-mschap-v2


require-mppe-128


ms-dns 192.168.1.1 - my router have this ip


nodefaultroute
lock
nobsdcomp
```


on router i opened 1723 port
```

xtra@oink:/etc/apache2/sites-available$ netstat -alpn | grep :1723
(No info could be read for "-p": geteuid()=1000 but you should be root.)
tcp        0      0 0.0.0.0:1723            0.0.0.0:*               LISTEN      -     

```


and do: sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 




no ping. no internet. but DNS seems ok.
[img]http://i.ynblpb.com/u/2014/04/1398513549.png[/img]
[img]http://i.ynblpb.com/u/2014/04/1398513564.png[/img]


somebody can help?)):P

---

### Post by TheFu on 2014-04-26
pptp is the weakest of the VPN choices. It has been hacked.  I've never used it because it was hacked multiple times in the last decade.

The easiest way to handle 1 port forwarded as you describe is with ssh-tunneling. Lots of how-to guides for that, google finds them.

The next easiest is probably OpenVPN, but with openSSL hacks coming out more and more weekly, I'd be inclined towards IPSec-based VPNs.  We use openVPN where I am and it works, but we don't care if the NSA sees all our traffic.

When discussing VPNs, it is critical to be extremely clear on where the client is, where the server is and what programs run on each. Routing is extremely important too. So ... what do the routes show from the client AND what do the routes show from the connected server?

What do the log files show on the server? Can you turn up the verbosity for the client-connect command to get more debug output?

---

