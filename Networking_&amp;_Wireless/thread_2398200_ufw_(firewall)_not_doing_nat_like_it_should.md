---
title: "ufw (firewall) not doing nat like it should?"
date: 2018-08-08
forum: Networking &amp; Wireless
---

### Post by ulao3 on 2018-08-08
I'm new to 18.04 and the new networking stuff. First thing that sort of confused me was the new labels enp2s0 instead of eth0. Assuming this is just a name, I set up my nat like so .

/etc/default/ufw change
DEFAULT_FORWARD_POLICY="ACCEPT" 



 /etc/ufw/sysctl.conf (not sure if I need to disable the ip6?)
net.ipv4.ip_forward=1 
net/ipv6/conf/default/forwarding=1 
net/ipv6/conf/all/forwarding=1 

and in my /etc/ufw/before.rules
*nat
: POSTROUTING ACCEPT [0:0]

#-A POSTROUTING -s  192.168.0.1/24  -o enp2s0 -j MASQUERADE
#-A POSTROUTING -s enp3s5   -o enp2s0 -j MASQUERADE
-A POSTROUTING  -o enp2s0 -j MASQUERADE
COMMIT

As you can see from the comments I tried a few ways. 

enp3s5   is my intrAnet card
enp2s0   is my internat card

-------------------------------------------
This is what I did in 14.04
sudo modprobe iptable_nat
sudo iptables -t nat -A POSTROUTING -o eth3 -j MASQUERADE
sudo iptables -t mangle -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu
echo 1 > /proc/sys/net/ipv4/ip_forward


eth3 was my intra and eth0 was internet


Did I do something wrong?

---

