---
title: "how to prevent tun0 device from being brought up during booting?"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by zhangweiwu on 2007-11-02
Dear all

On my home computer I have a script to setup tun0 which is an IP tunnel to another server. I used the script for more than half a year without any problem.

In recent two weeks I found this tun0 bring up automatically every time I boot the machine (usually I manually create tun0 with a script), this is strange and made me un-able to create another IP tunnel (if I do, the tunnel doesn't work).

I have checked /etc/network/interfaces and there are nothing like 'tun0'. I am very curious how tun0 is created and by which application/script? I also checked /etc/crontab. I don't know where else to look for.

I also attached my script which I use to manually set up tun0, just for reference. Can someone tell me how can I stop the machine boot with tun0 brought up?

Thanks!

My script:
```

renaissance=`LANG=en_US ifconfig ppp0 | sed -n '/inet/s/^[ ]*inet addr:\([0-9.]*\).*/\1/p'`
ip tunnel add tun0 mode ipip remote 218.193.55.198 local $renaissance dev ppp0
ifconfig tun0 10.0.0.1 netmask 255.255.255.252 pointopoint 10.0.0.2
ifconfig tun0 mtu 1500 up
route add -host exupery dev ppp0
route add -host sappho dev ppp0
route add -host www.linasp.com dev ppp0
route add -net 218.193.55.192 netmask 255.255.255.192 dev tun0
echo 1 > /proc/sys/net/ipv4/ip_forward
/sbin/iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
/sbin/iptables -A FORWARD -i ppp0 -o tun0 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A FORWARD -i tun0 -o ppp0 -j ACCEPT
/sbin/iptables -A FORWARD -i eth0 -o tun0 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A FORWARD -i eth0 -o ppp0 -j ACCEPT

# https
iptables -A PREROUTING -t nat -p tcp -i ppp0 --dport 443 -j DNAT --to 218.193.55.194:443
iptables -A INPUT -p tcp --dport 443 -j ACCEPT
iptables -A FORWARD -p tcp -d 218.193.55.194 --dport 443 -i ppp0 -o tun0 -j ACCEPT
iptables -A FORWARD -p tcp -s 218.193.55.194 --sport 443 -i tun0 -o ppp0 -j ACCEPT

# subversion
iptables -A PREROUTING -t nat -p tcp -i ppp0 --dport 3690 -j DNAT --to 218.193.55.194:3690
iptables -A INPUT -p tcp --dport 3690 -j ACCEPT
iptables -A FORWARD -p tcp -d 218.193.55.194 --dport 3690 -i ppp0 -o tun0 -j ACCEPT
iptables -A FORWARD -p tcp -s 218.193.55.194 --sport 3690 -i tun0 -o ppp0 -j ACCEPT

# TinyERP
iptables -A PREROUTING -t nat -p tcp -i ppp0 --dport 8069 -j DNAT --to 218.193.55.194:8069
iptables -A INPUT -p tcp --dport 8069 -j ACCEPT
iptables -A FORWARD -p tcp -d 218.193.55.194 --dport 8069 -i ppp0 -o tun0 -j ACCEPT
iptables -A FORWARD -p tcp -s 218.193.55.194 --sport 8069 -i tun0 -o ppp0 -j ACCEPT

for port in 119 111 830 679 2049
do
	iptables -A PREROUTING -t nat -p tcp -i ppp0 --dport $port -j DNAT --to 218.193.55.198:$port
	iptables -A INPUT -p tcp --dport 119 -j ACCEPT
	iptables -A FORWARD -p tcp -d 218.193.55.198 --dport $port -i ppp0 -o tun0 -j ACCEPT
	iptables -A FORWARD -p tcp -s 218.193.55.198 --sport $port -i tun0 -o ppp0 -j ACCEPT
done

```

---

### Post by mpokrywka on 2007-11-03
Did you check if this tun0 device has any IP address assigned? (ip addr)
If yes, then you should probably know the cause.
If not, maybe it is created by some OpenVPN script?
As a workaround you can:
```
rmmod ipip
rmmod tun
```
at start of your script (dangerous if you use any tunnels/vpn)

or 

use variable as your tunnel device name in script and use name that will not clash, f.e.
```
TUN_DEV="mytun0"
ifconfig $TUN_DEV 10.0.0.1 netmask 255.255.255.252 pointopoint 10.0.0.2
ifconfig $TUN_DEV mtu 1500 up
```

---

### Post by zhangweiwu on 2007-11-04
Thank you very much, following your suggestion I found the tun0/ppp0 do have IP address, which means I have a script activated it. Then I am able to look down and find the script included from /etc/ppp/ip-up

Thanks!

---

