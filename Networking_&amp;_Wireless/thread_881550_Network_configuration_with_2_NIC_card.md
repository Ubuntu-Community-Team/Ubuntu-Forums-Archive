---
title: "Network configuration with 2 NIC card"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by anindya23 on 2008-08-06
how can i configure networking with 2 NIC cards(one for real ip and another for local network) in ubuntu server edition 8.04?

I am a newbie in linux. so i need step by step solution to do this.

thanx in advance.

---

### Post by SillyChild on 2008-08-06
Step 1:
Connect eth0 to the Internet. This can be either via ADSL (PPoE) or what ever way you are connecting to your ISP.

Step 2:
Connect eth1 to your switch. Assign IP 10.0.1.1 with subnet 255.255.255.0. I'm assuming that you are happy to use this particular subnet.

Then you have to configure an iptables script that will work as a nat. First you have to read up on iptables. Anyway, below is very tiny script that will get you started:

```

# Firewall Script
# This is the basic script. Needs further editing

#
# Set default policies
#
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

#
# Flush (-F) all specific rules
#
iptables -F INPUT
iptables -F FORWARD
iptables -F OUTPUT
iptables -F -t nat

#
# Define variables
#
lan=eth1
wan_ip=123.49.32.109
wan=eth0
lan_net1=10.0.1.0/255.255.255.0

#
# Forward all packets from internal network (lan) to the internet (wan)
#
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT

#
# Forward all packets from Internet (wan/eth0) to the internal network (lan/eth1)
#
iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT

#
# Maintain existing established connections
#
iptables -A FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT

#
# Drop all incoming packets from the Internet from Port 1 to 21 and 23 to 1024. This is a basic security measure that I follow, but your can edit/ignore this (your risk).
#
iptables -A INPUT -i eth0 -p tcp -j DROP --dport 1:21
iptables -A INPUT -i eth0 -p tcp -j DROP --dport 23:1024

#
# Accept incoming to port 22 from the Internet for ssh (remote login)
#
iptables -A INPUT -i eth0 -p tcp -j ACCEPT --dport 22

#
# Allow all inputs to firewall from the internal network and local interfaces
#
iptables -A INPUT -i eth1 -s 0/0 -d 0/0 -j ACCEPT
iptables -A INPUT -i lo -s 0/0 -d 0/0 -j ACCEPT
iptables -A FORWARD -i lo -s 0/0 -d 0/0 -j ACCEPT

#
# Direct connection to internet snat
#
iptables -t nat -A POSTROUTING -o ${wan} -j SNAT --to-source ${wan_ip}

#
# Masquerade rule
#
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s ${lan_net1}


```

Save this script in /etc/init.d/myFirewall.sh

Then run the script to get things working.

Hope that will get you started.

---

