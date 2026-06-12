---
title: "PPTP VPN connection connected, almost there, just need a little help!"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by speedothebrief on 2007-02-15
Hi everyone,
Here is my problem:

I've connected to my work's M$ PPTP VPN. Everything seems to be ok, I can ping the server at work , and I can ping names at work. So DNS seems to be working.

However, there is one name I can't ping without adding it to the /etc/hosts file, and it happens to be the vpn/mail server. I can ping it's IP address, but not it's name. If I add the host to the hosts file, then I can use the name. I can even access my IMAP email and download messages from my inbox.

Here is where it gets strange: I can browse the top level of computers in the samba browser, but nothing below the top level of the tree. I can only get email from my inbox, any other folder times out fetching headers. I can vnc into my work computers, but it only authenticates and get's desktop meta-data, so I never actually see any images from my desktop.

When I use ethereal to capture the data going into the PPTP tunnel, I can see that the protocol is PPP compressed data. Could it be the compression? I thought that I had turned off compression protocols by adding the following to my /etc/ppp/options.pptp file:
```
# Compression
# Turn off compression protocols we know won't be used
nobsdcomp
nodeflate
novj
novjccomp

```

Anybody have any ideas here? I'm completely stumped, my network admin is completely stumped, and I'm not sure where to go from here.

To add some complexity to the situation: I have connected this computer to another network and had no problem getting email, browing computers, or vnc'ing into my work computer. Could this be a router configuation? If so, how do I prevent this from happening when I'm in uncontrolled environments (when I'm on the road in hotels)?

Thanks everyone... All the help I've received here so far has been incredible!

---

### Post by avfangel on 2007-02-15
try checking the routes with 
~$ip route
if your tunnel is not the default route make it the default route with
~$sudo ip route replace default dev ppp0
where ppp0 is your tunnel interface name.
also because you are tunneling to a vpn server you need to keep a route to it: let's assume eth0 is the network interface you are using to connect to a vpn server 192.168.5.5, then add a route to it with:
~$sudo ip route add 192.168.5.5 dev eth0

i would also check firewall so try looking at iptables with ~$iptables -L

good luck.

---

### Post by speedothebrief on 2007-02-15
OK, I"ve got my solution!

Thanks to the IRC channel #PPTP at freenode, where the implementer of the PPTP linux tools resides during Australian business hours! God Bless You James Cameron!!!!!!!

Here is a link:
[http://pptpclient.sourceforge.net/howto-diagnosis.phtml#connections_freeze](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#connections_freeze)

and the text from the link:
Problem: TCP connections via the tunnel freeze once they attempt to transfer large amounts of data.

Diagnosis: path MTU discovery may be failing due to ICMP blocking by hosts after the PPTP server.

Solution: manually restrict the MTU on the interface, by adding mtu 1404 or some smaller value as an option to the pppd program, either in the peers file for the tunnel, in the options file, or on the command line. You can also restrict the MTU on the interface after the tunnel has connected, using a command like ifconfig ppp1 mtu 1400.

The effect is that new TCP connections from your host will use an maximum segment size (MSS) that is lower. This may prevent path MTU discovery from being necessary.
--------------------------------
so,
I utilized the following link in my tunnel's file "/etc/ppp/peers/$TUNNEL_CONFIG_FILENAME"
```
mtu 1404
```
And presto! It works!

---

