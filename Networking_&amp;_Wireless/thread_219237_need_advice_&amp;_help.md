---
title: "need advice &amp; help"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by renaissance on 2006-07-19
I have small localnetwork with 30 pc's. I have Ubuntu Dapper Drake 6.06 server. Also i have 194.40.121.192-194.40.121.224 ip-s space. My Ubuntu server must be work as firewall and internet router. I use dhcp3-server for connection sharing. And i want to use iptables to secure my network. But i have some problems with iptables. MASQUERADE dont work

My /etc/network/interfaces look like inside:

auto eth0
iface eth0 inet static
address 194.40.121.198 (my gigabit switch address)
netmask 255.255.255.224
broadcast 194.40.121.223
gateway 194.40.121.193

auto eth1
iface eth1 inet static
address 194.40.121.194
netmask 255.255.255.224 
network 194.40.121.192 
broadcast 194.40.121.223
gateway 194.40.121.193

My iptables rules look like:

# iptables -F
# iptables -t nat -F
# iptables -P INPUT ACCEPT
# iptables -P OUTPUT ACCEPT
# iptables -P FORWARD DROP
# export LAN=eth1
# export WAN=eth0
# iptables -I INPUT 1 -i ${LAN} -j ACCEPT
# iptables -I INPUT 1 -i lo -j ACCEPT
# iptables -A INPUT -p UDP --dport bootps -i ! ${LAN} -j REJECT
# iptables -A INPUT -p UDP --dport domain -i ! ${LAN} -j REJECT
# iptables -A INPUT -p TCP --dport ssh -i ${WAN} -j ACCEPT
# iptables -A INPUT -p TCP -i ! ${LAN} -d 0/0 --dport 0:1023 -j DROP
# iptables -A INPUT -p UDP -i ! ${LAN} -d 0/0 --dport 0:1023 -j DROP
# iptables -I FORWARD -i ${LAN} -d 194.40.121.192/255.255.255.224 -j DROP
# iptables -A FORWARD -i ${LAN} -s 194.40.121.192/255.255.255.224 -j ACCEPT
# iptables -A FORWARD -i ${WAN} -d 194.40.121.192/255.255.255.224 -j ACCEPT
# iptables -t nat -A POSTROUTING -o ${WAN} -j MASQUERADE

and after that, if i use iptables -L, i cant see anywere MASQUERADE rule.
And after that:
echo 1 > /proc/sys/net/ipv4/ip_forward
At the moment my server shares another pc-s ip-s, but dont share connection. Something is wery wrong, how i can fix it ?
Special thanks to everyone who can help me or give me somes ideas

---

### Post by fadumpt on 2006-07-19
firestarter is a GUI iptables shell that has an option where you can enable internet connection sharing (IP Masquerade). 

Also, you may just want to install ipcop on a slower box and use that as a firewall router, it does an awesome job and is already set up out of the box to be a router, no initial configurations.

---

