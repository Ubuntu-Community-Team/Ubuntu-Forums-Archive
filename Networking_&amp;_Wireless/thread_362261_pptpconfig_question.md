---
title: "pptpconfig question"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by lcohen999 on 2007-02-15
It seems that pptpconfig now works with Edgy Eft (no idea why!)

However, I would like it so all my traffic goes through the VPN tunnel.

No matter what I do, once the connection is established, and I do a whatismyip.com it always reports the NON-VPN ip adddress.

Any thoughts on how I can fix this?

---

### Post by lcohen999 on 2007-02-15
Here is what my log gives me:

```
Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/1
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP
local  IP address 10.2.0.38
remote IP address XX.XXX.XXX.X
primary   DNS address XX.XXX.XXX.14
secondary DNS address XX.XX.XXX.230
pptpconfig: pppd process exit status 0 (started)
ip route replace XX.XXX.XXX.8 via 192.168.100.1 dev eth1  src 192.168.100.138
pptpconfig: routes added to remote networks
ip route replace default dev 'ppp0'
Cannot find device "ppp0"

pptpconfig: command failed, exit code 255
pptpconfig: default route changed to use tunnel
pptpconfig: DNS changes made to /etc/resolv.conf
pptpconfig: connected

```

---

### Post by RiffRaff06078 on 2007-03-23
You're getting farther than I am.  My connection stops dead after I get the "
Cannot determine ethernet address for proxy ARP"  message.

I can't help you with your problem, but maybe you could give me a tip on where I might be going wrong in my configuration?  I'm trying to do Client to LAN.

Thanks,
Riff

---

### Post by jakala on 2007-04-04
Hello,

I have too the connection problem with pptpconfig.

I found an other solution realy more usefull :

[vpn-connection-in-edgy]("http://customisinglife.wordpress.com/2006/11/20/vpn-connection-in-edgy/")

It work very good for me (for the past hour :KS )

I just need to setup correctly the routing (it's realy easy)

---

