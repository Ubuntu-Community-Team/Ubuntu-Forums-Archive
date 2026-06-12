---
title: "Ubuntu 18.04 and 20.04 Server - Using as VPN gateway - IP tables Issue :("
date: 2021-09-06
forum: Networking &amp; Wireless
---

### Post by smurf786 on 2021-09-06
Hi Guys,

I have setup a Hyper-V VM of ubuntu server, i've tried both the latest 20.04 and 18.04 too. I am really new to linux so sorry if this is going to be something simple.

Basically i am following this video guide: [https://youtu.be/xFficDCEv3c](https://youtu.be/xFficDCEv3c)

I want to use Ubuntu server for openvpn with purevpn. I will then select the ubuntu server as the gateway for the individual devices to push traffic across the vpn.

I have managed to get the VM installed but everytime i run iptables i lose connection to the internet... I cannot ping google.com or even 8.8.8.8

Could someone check my iptables file and see what could be causing this?

```

[COLOR=black][FONT=&amp]#!/bin/bash
# Flush
iptables -t nat -F
iptables -t mangle -F
iptables -F
iptables -X[/FONT][/COLOR]
[COLOR=black][FONT=&amp]# Block All
iptables -P OUTPUT DROP
iptables -P INPUT DROP
iptables -P FORWARD DROP[/FONT][/COLOR]
[COLOR=black][FONT=&amp]# allow Localhost
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT[/FONT][/COLOR]
[COLOR=black][FONT=&amp]# Make sure you can communicate with any DHCPserver
iptables -A OUTPUT -d 255.255.255.255 -j ACCEPT
iptables -A INPUT -s 255.255.255.255 -j ACCEPT[/FONT][/COLOR]
[COLOR=black][FONT=&amp]# Make sure that you can communicate within your ownnetwork
iptables -A INPUT -s 192.168.233.0/24 -d 192.168.233.0/24 -jACCEPT
iptables -A OUTPUT -s 192.168.233.0/24 -d 192.168.233.0/24 -j ACCEPT[/FONT][/COLOR]
[COLOR=black][FONT=&amp]# Allow established sessions to receivetraffic:
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT[/FONT][/COLOR]
[COLOR=black][FONT=&amp]# Allow TUN
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -j ACCEPT
iptables -A FORWARD -o tun+ -j ACCEPT
iptables -t nat -A POSTROUTING -o tun+ -j MASQUERADE
iptables -A OUTPUT -o tun+ -j ACCEPT[/FONT][/COLOR]
[COLOR=black][FONT=&amp]# allow VPN connection
iptables -I OUTPUT 1 -p udp --destination-port 1194 -m comment --comment"Allow VPN connection" -j ACCEPT[/FONT][/COLOR]
[COLOR=black][FONT=&amp]# Block All
iptables -A OUTPUT -j DROP
iptables -A INPUT -j DROP
iptables -A FORWARD -j DROP[/FONT][/COLOR]
[COLOR=black][FONT=&amp]# Log all dropped packages, debug only.[/FONT][/COLOR]
[COLOR=black][FONT=&amp]iptables -N logging
iptables -A INPUT -j logging
iptables -A OUTPUT -j logging
iptables -A logging -m limit --limit 2/min -j LOG --log-prefix "IPTablesgeneral: " --log-level 7
iptables -A logging -j DROP[/FONT][/COLOR]
[COLOR=black][FONT=&amp]echo "saving"
iptables-save > /etc/iptables.rules
echo "done"
#echo 'openVPN - Rules successfully applied, we start "watch" toverify IPtables in realtime (you can cancel it as usual CTRL + c)'
#sleep 3
#watch -n 0 "sudo iptables -nvL"[/FONT][/COLOR]


```

Thank you

---

### Post by Doug S on 2021-09-07
Yes, you have a mess.
I am not going to watch a 17 minute video to attempt to determine what you are supposed to be doing.

For communicating with a DHCP server, suggest you do it via ports 67 and 68.

Your per chain DROP rules are before your logging rules, therefore your logging rules will never be hit.

Do not use generic logging, use a specific and different log prefix for every log call so that you know exactly where in the rule set the log entry came from.

I do not know much about VPN and "tun" interface devices, but I think more details about your setup are required. Is ip forwarding enabled?
```
cat /proc/sys/net/ipv4/ip_forward
```

---

### Post by smurf786 on 2021-09-09
> **Doug S said:**
> Yes, you have a mess.
I am not going to watch a 17 minute video to attempt to determine what you are supposed to be doing.

For communicating with a DHCP server, suggest you do it via ports 67 and 68.

Your per chain DROP rules are before your logging rules, therefore your logging rules will never be hit.

Do not use generic logging, use a specific and different log prefix for every log call so that you know exactly where in the rule set the log entry came from.

I do not know much about VPN and "tun" interface devices, but I think more details about your setup are required. Is ip forwarding enabled?
```
cat /proc/sys/net/ipv4/ip_forward
```

Hi Doug,

I have checked and IP forwarding is enabled.

```
net.ipv4.ip_forward = 1
```

If i ping 8.8.8.8 i get response as soon as i do but after running

```
sudo bash /etc/openvpn/iptables.sh
```

I get no ping and vpn hostname can't be resolved to connect...

The network is simple

i have router gateway that does DHCP on 192.168.233.1
This VM is on 192.168.233.2

The idea is to change the gateway on another device to 192.168.233.2 when i want to send traffic over vpn.

Thank you

---

### Post by smurf786 on 2021-09-09
Its ok guys think i fixed it... So looking at my vpn supplier port it is actually 53 and not 1194

Changing this has allowed the VPN traffic to go through port 53. 

It seems traffic through any other port is blocked.

Thank you

---

### Post by Doug S on 2021-09-10
Glad you got it sorted out.
Please mark this thread as "SOLVED"

---

