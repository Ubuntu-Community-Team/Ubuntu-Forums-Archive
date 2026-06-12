---
title: "iptables configuration for vpn/eth traffic split"
date: 2019-08-31
forum: Networking &amp; Wireless
---

### Post by S2267 on 2019-08-31
Hello everybody,

I browsed the forum but I haven't found an answer to my problem. I apologize in case it's there and I couldn't find it...

Here is my problem: I have a Minix with Ubuntu. I have been using it as vpn gateway for some time now (expressvpn) and it works great. Basically it routes all the traffic to the vpn.

Here are the iptables rules in place (minix's ip is 10.25.20.2):

[FONT=courier new]sudo iptables -F
sudo iptables -t nat -F
sudo /bin/su -c "echo -e '\n#Enable IP Routing\nnet.ipv4.ip_forward = 1' > /etc/sysctl.conf"
sudo iptables -t nat -A POSTROUTING -s 10.25.20.0/24 -o tun0 -j MASQUERADE
sudo iptables -A FORWARD -i enp1s0 -o tun0 -j ACCEPT
sudo iptables -A FORWARD -i tun0 -o enp1s0 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INPUT -i enp1s0 -j ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT[/FONT]


I recently added HomeAssistant in order to control my lights and sensors.
It works great and vpn routing performance is not impacted.

My problem is: I'd like to access home assistant on tcp port 8123 from outside (I have reasons for not connecting in vpn, so I must use http on port 8123) and I cannot figure out which are the iptables rules I need to add/modify.

Basically, the desired behavior is:
[LIST]
[*]traffic incoming to port 8123 through interface enp1s0 (it's minix's eth0) should get to H.A. and responses should go out through enp1s0
[*]traffic generated in the LAN (10.25.20.0/24) should go out through vpn (tun0)
[/LIST]

Any idea or suggestion?
Thank you all and Best
Stefano

---

