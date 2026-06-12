---
title: "Route only Internet traffic through OpenVPN"
date: 2014-04-17
forum: Networking &amp; Wireless
---

### Post by Kocrachon on 2014-04-17
Hello All,

I currently have a small office where we all use Ubuntu devices, and we currently have an AWS server setup for our VPN connections. Right now I have all internet traffic going through it by using the -push "redirect-gateway def1 bypass-dhcp"- option setup. However, The issue I run into this is it breaks my LAN in a sense. With this, I no longer have access to communicate with my local computers. 

This also comes into a problem with a few other areas. Not every computer runs openVPN, and I don't want every computer to have openVPN, it is specifically for people that I want to have more security because of some of the work they do. So I am looking for a way to set it up as follows.

If traffic is 10.0.0.0/0, then use gateway 10.0.0.1, if traffic is 0.0.0.0/0, then use 54.200.5.8 (my OpenVPN server on AWS). How do I define this on either the client side or the server side?

---

### Post by Kocrachon on 2014-04-18
Thought I had it working with this, but it appears to no longer work..

server 192.168.100.0 255.255.255.0

;push "redirect-gateway def1 bypass-dhcp"
push "redirect-gateway def1"
push "redirect-gateway local def1"
push "dhcp-option DNS 8.8.8.8"
route 10.0.0.0 255.0.0.0 net_gateway
route 192.168.1.0 255.255.255.0 net_gateway

here is what my route -n looks like

[http://pastebin.com/r5cRMsT5](http://pastebin.com/r5cRMsT5)

---

### Post by SeijiSensei on 2014-04-18
I have a somewhat similar arrangement between my office and a remote Linode server.  I maintain only one OpenVPN connection, a [simple static-key tunnel]("http://openvpn.net/static.html") between a machine in my office and the server.  Let's say the tunnel uses 10.10.10.0/24.  On my office router I've set up a static route to point traffic for that subnet to the machine running OpenVPN on this end. Then traffic for the server is routed over the tunnel, but everything else remains untouched.

I don't have any rules about which machines can connect over the tunnel, but you could use iptables rules on the gateway for that task.  If there is a small list of authorized machines, you can have rules like
```

/sbin/iptables -A INPUT -s 192.168.1.1 -d 10.10.10.0/24 -j ACCEPT
/sbin/iptables -A INPUT -s 192.168.1.2 -d 10.10.10.0/24 -j ACCEPT
/sbin/iptables -A INPUT -s 192.168.1.3 -d 10.10.10.0/24 -j ACCEPT
/sbin/iptables -A INPUT -d 10.10.10.0/24 -j REJECT

```
With more than a few hosts, or for more flexibility, I use scripts for this task.  Put the authorized addresses in a file, then iterate over them in the script and set up the iptables rules accordingly.

I don't see much reason to push generic Internet traffic through the tunnel.  Once it reaches the other side, it is sent out to the Internet unencrypted.

---

### Post by Kocrachon on 2014-04-18
Its more of a security issue of, I don't want my offices Public IP out with some of the content they are accessing. So by using an AWS server, it shows up as a generic 54.x.x.x website hosted by Amazon.

---

### Post by SeijiSensei on 2014-04-19
You could run Squid on the AWS box and configure the users' browsers to connect to that.  

If you put a Linux box between the network and the router, you could intercept outbound port 80 requests from the appropriate hosts with iptables and push them to the Squid proxy on the AWS box.  Something like this:
```

iptables -t nat -A PREROUTING -p tcp -s 192.168.1.1 --dport 80 -j DNAT --to-destination 10.10.10.10:3128
```
One side benefit of using Squid is that you will have a log of all requested URLs.

---

