---
title: "iptables question"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by Betelgeuse on 2008-02-24
I have an ubuntu server (ubuntu server edition 7.10) that will act as a gateway on my server network.

I have 3 web servers (windows 2000 and linux web servers) and two database servers (postgresql and ms sql) and a linux server gateway.

I have rented a rack from a isp datacenter and I'll put my server to that rack and I'll access them from the office, so I need to route some more ports to my office static ip too. 

the configurations looks like this:

ubuntu 7.10 server with two NICs:
eth0 : 13 public ip address assigned to me by my isp
xx.xx.xx.66 to xx.xx.xx.78
eth1: 10.1.1.1 /subnet mask 255.255.255.0

web server 1 : ubuntu 7.10 server with apache 2.
eth0 : 10.1.1.67
          10.1.1.68

web server 2 : windows 2000 (IIS 5)
10.1.1.69
10.1.1.70
...
10.1.1.78

postgresql server : (ubuntu 7.10)
10.1.1.200

ms sql server :
10.1.1.210

as you see, the servers are on private ip address and I want to route only post 80 and 443 (http and https ports) to them.

I want to route the servers by looking at destinations address. if destination is xx.xx.xx.67 then it go to 10.1.1.67 and if destination is xx.xx.xx.69 then it will go to 10.1.1.69.
and I want to route the other ports from my office static ip (zzz.zzz.zzz.zzz) to access database servers remotely like 
zzz.zzz.zzz.zzz --> xx.xx.xx.66 --> 10.1.1.200  (postgresql port)
zzz.zzz.zzz.zzz --> xx.xx.xx.66 --> 10.1.1.210 (TCP 1433, ms sql port)
zzz.zzz.zzz.zzz --> xx.xx.xx.66 --> 10.1.1.210 (TCP 3389, windows rdp)

is there any example iptables script that I can look at and modify and use? 
currently, I'm using ipcop linux for this and it works fine but later, I'll have to install vmware-server and convert all the servers virtual machines bridged to second nic inside the server so I need to do the routing on ubuntu server. 

Some people suggested to use shorewall but this setup will be mostly static, there will not be any frequent changes to an iptables script will be better. I do not want to install any packages other than necessary.

---

### Post by update_manager on 2008-02-24
> **Betelgeuse said:**
> 
as you see, the servers are on private ip address and I want to route only post 80 and 443 (http and https ports) to them.

I want to route the servers by looking at destinations address. if destination is xx.xx.xx.67 then it go to 10.1.1.67 and if destination is xx.xx.xx.69 then it will go to 10.1.1.69.
and I want to route the other ports from my office static ip (zzz.zzz.zzz.zzz) to access database servers remotely like 
zzz.zzz.zzz.zzz --> xx.xx.xx.66 --> 10.1.1.200  (postgresql port)
zzz.zzz.zzz.zzz --> xx.xx.xx.66 --> 10.1.1.210 (TCP 1433, ms sql port)
zzz.zzz.zzz.zzz --> xx.xx.xx.66 --> 10.1.1.210 (TCP 3389, windows rdp)

is there any example iptables script that I can look at and modify and use? 
currently, I'm using ipcop linux for this and it works fine but later, I'll have to install vmware-server and convert all the servers virtual machines bridged to second nic inside the server so I need to do the routing on ubuntu server. 


Check out DNAT. 

iptables -A FORWARD -i eth[WAN Interface] -p [TCP or UDP]  --dport [PORT] -m state --state NEW -j ACCEPT

iptables -t nat -A PREROUTING -i eth[WAN Interface] -p tcp --dport [PORT] -j DNAT --to [IP]


See also:
[http://www.sjdjweis.com/linux/proxyarp/rc.firewall.txt]("http://www.sjdjweis.com/linux/proxyarp/rc.firewall.txt")
[http://www.slackware.com/~alien/efg/]("http://www.slackware.com/~alien/efg/")


**THIS will probably not work with VMWare Server.**

Instead, use the instructions here [http://www.vmware.com/support/ws55/doc/ws_net_nat_advanced.html]("http://www.vmware.com/support/ws55/doc/ws_net_nat_advanced.html") to set up port forwarding, then create iptables rules like:
iptables -A INPUT  -i eth[WAN Interface] -p [TCP or UDP]  --dport [PORT] -m state --state NEW -j ACCEPT

---

