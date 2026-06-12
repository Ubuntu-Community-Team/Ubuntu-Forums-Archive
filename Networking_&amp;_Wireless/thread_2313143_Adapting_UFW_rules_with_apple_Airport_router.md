---
title: "Adapting UFW rules with apple Airport router"
date: 2016-02-10
forum: Networking &amp; Wireless
---

### Post by zephyr2 on 2016-02-10
I'm still relatively new to Ubuntu (I'm semi-comfortable with the command line, long as I have an idea what each part of the command is doing, but then I'm also more comfortable with, say, GUFW than iptables). I'm also a greenhorn with networking.:(

I'm trying to follow [this straightforward guide]("https://ubuntu-mate.community/t/vpn-how-to-connect-successfully-securely-ufw-openvpn-ubuntumate-15-04/1452") from the UbuntuMate forums on setting UFW rules as a 'kill switch' with OpenVPN. I feel I understand the first half fairly well, but I'm uncertain of what IP range I should write into the UFW rule in order to make it work with my Apple Airport router. I'm also unclear on what the suggested code for changing /etc/ufw/before.rules is doing, and whether I need to adapt that code as well.


First part I need help with:

```
sudo ufw status 
sudo ufw enable
sudo ufw default deny incoming
sudo ufw default deny outgoing
sudo ufw allow out on tun0
sudo ufw allow out on eth0 to 192.168.1.0/24
```


I understand all of this except the last line. I know it's supposed to allow traffic to my router/internal network and I should add additional rules with the same range for each connecting device (wlan0, eth0, etc.) and that `192.168.1.0/24` is an IP range for the local network given in the example. 

My problem is, my router utility tells me it has DHCP range 10.0.1.2 - 10.0.1.200 (the router itself has IP 10.0.1.1, I believe). So I'm not sure how to rewrite the ufw rule above using my IP range. Any takers who can help with this?

```
sudo ufw allow out to **vpn serv ip** **port number** proto tcp or udp

```

Here, too, I'm a bit stumped. My VPN service has far too many IPs to include (hundreds per gateway), so I'm thinking of scrapping this line altogether in favor of:

```
sudo ufw allow out 1194 proto udp
```

and leave it at that. The likelihood of this inviting a security risk seems low to me; can someone let me know if I'm missing something here...?


Final part I'm concerned with is the change to /etc/ufw/before.rules

```

     # START OPENVPN RULES
     # NAT table rules
     *nat
     :POSTROUTING ACCEPT [0:0]
     # Allow traffic from OpenVPN client to eth0 and Wlan0
     -A POSTROUTING -s 10.8.0.0/8 -o eth0 -j MASQUERADE
     -A POSTROUTING -s 10.8.0.0/8 -o wlan0 -j MASQUERADE
     COMMIT
     # END OPENVPN RULES

```

I don't know what the postrouting 10.8.0.0/8 range typically covers or represents, so I don't know if this range also needs to change given my router IP range. Can someone briefly explain what this code is doing and what changes I might need to make?

Any help is greatly appreciated!  :D

---

