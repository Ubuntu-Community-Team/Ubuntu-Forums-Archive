---
title: "OpenVPN Port Forwarding with iptables"
date: 2016-04-02
forum: Networking &amp; Wireless
---

### Post by Bahador_Boroumand on 2016-04-02
Hi,


I have a NAS server which I should do port forwarding for it in order to make its services accessible from internet. However my ISP is blocking ports, so I've managed to buy myself a cheap Ubuntu VPS to run an OpenVPN server there and then somehow redirect the whole NAS traffic and the required ports to there.
My setup is as the following:. My setup is as the following:

[IMG]http://s28.postimg.org/dbv61v9xp/2016_04_02_21_19_22_Untitled_Notepad.png[/IMG]

The VPS side is configured correctly I guess, as I am able to SSH into my Raspberry Pi using my VPS IP. That's what I've done there in order to make it work:

```
iptables -t nat -A PREROUTING -d A.B.C.D -p tcp --dport 22 -j DNAT --to-dest 10.8.0.6:22
iptables -t nat -A POSTROUTING -d 10.8.0.6 -p tcp --dport 22 -j SNAT --to-source 10.8.0.1
```


My OpenVPN server config:


```
port X
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key
dh dh2048.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
client-config-dir ccd
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 208.67.222.222"
push "dhcp-option DNS 208.67.220.220"
keepalive 10 120
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3
```


I have also done:


```
sysctl -w net.ipv4.ip_forward=1
```


and put ```
DEFAULT_FORWARD_POLICY="ACCEPT"
```in ```
/etc/default/ufw
```and also added

```
# START OPENVPN RULES
# NAT table rules
*nat
OSTROUTING ACCEPT [0:0] 
# Allow traffic from OpenVPN client to eth0
-A POSTROUTING -s 10.8.0.0/8 -o eth0 -j MASQUERADE
COMMIT
# END OPENVPN RULES
```


to


```
/etc/ufw/before.rules
```


OpenVPN client config:


```
client
dev tun
proto udp
remote A.B.C.D X
resolv-retry infinite
nobind
user nobody
group nogroup
persist-key
persist-tun
ns-cert-type server
comp-lzo
verb 3


<ca>
XXX
</ca>
<cert>
YYY
</cert>
<key>
ZZZ
</key>
```


How do I redirect eth0 traffic to tun0 and forward ports Y and Z through the tunnel?
I just know that for the other ports I should reconfigure my VPS accordingly as I did for port 22.

---

### Post by Bahador_Boroumand on 2016-04-02
**UPDATE:**


I've managed to redirect the traffic on my Raspi with the following command:


```
iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o tun0 -j MASQUERADE
```


When I traceroute out of my NAS it goes through the tunnel. Now I only need to forward ports in this tunnel.

---

### Post by Bahador_Boroumand on 2016-04-02
**UPDATE 2 (solving the whole project):**


I finally found the correct port forwarding commands after hours of searching. I've ran the following commands on my Raspi:

```
iptables -t nat -I PREROUTING -p tcp -i tun0 -d 10.8.0.6 --dport <port> -j DNAT --to 192.168.1.102:<port>
iptables -I FORWARD -p tcp -i tun0 -d 192.168.1.102 --dport <port> -j ACCEPT
```


And also these commands on my VPS as I've done at first for port 22 at the beginning of this thread:

```
iptables -t nat -A PREROUTING -d 217.160.14.45 -p tcp --dport <port> -j DNAT --to-dest 10.8.0.6:<port>
iptables -t nat -A POSTROUTING -d 10.8.0.6 -p tcp --dport <port> -j SNAT --to-source 10.8.0.1
```


So now I've bypassed the firewall of my ISP and I am able to access my NAS and its services using port forwarding on the VPS side. You can use this as a tutorial :)

---

