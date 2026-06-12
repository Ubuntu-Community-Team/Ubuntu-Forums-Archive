---
title: "Please help me add the correct routes for my openVPN setup"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by harisund on 2006-10-18
To begin with, here's the setup:

Internet -> Cable modem -> Router(192.168.5.5)
Router --> Web server (192.168.5.100)
       --> Proxy server (192.168.5.101)
       --> VM test machine (192.168.5.103)
       --> Another_Box (192.168.5.104)
       --> Other room mates' machines (192.168.5.105-110)

Now I have a Windows XP laptop, and want to VPN into this Linux home network. 

I create a .conf file on my Another_Box like this:
```
dev tun
ifconfig 172.16.1.5 172.16.1.6
secret /etc/openvpn/myhomelan/myhomelan-key.txt
comp-lzo
port 1194
user root
group root
```

I then create a .ovpn file on my Windows laptop like this
```
remote harisund.com 1194
dev tun
ifconfig 172.16.1.6 172.16.1.5
secret myhomelan-key.txt
comp-lzo
```

I have created a port forward 1194 on my router to 192.168.5.104 (UDP)

I launch OpenVPN on both end with the required config files, and they are seemingly connected. I can ping 172.16.1.6 from 172.16.1.5 and vice versa. 

Now, how can I tell my Windows box that if I want to access 192.168.5.103 it is through the VPN adaptor??

I know it has something to do with the route command (either on my Windows box or on my Linux box)...

---

### Post by spd106 on 2006-10-18
Have a look through **man ip**. It should be something like **ip route add to 10.0.0.1 dev tun0**. Check the routing table with **ip route show**.

---

