---
title: "Ping Lan through hostpot nated behind VPN"
date: 2017-10-22
forum: Networking &amp; Wireless
---

### Post by f1rstsurf on 2017-10-22
Hello, 

i'm facing a problem while trying to access to my lan  (192.168.1.0/24) through my hotspot which provide a DHCP connexion nated  behind a VPN.
  Currently my hotspot is working well, DHCP connexion is functionnal, i  succeed to surf on the web trough it, but i would like to allow the  ping to my LAN.

  to be clearer, i would like to be able to ping 192.168.1.0/24 from 192.168.220.0/24

  Please to find below my Iptables script :

  ```
#!/bin/bash

#On flush les anciennes règles
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

#On autorise les requêtes local
sudo iptables -A INPUT -i lo -j ACCEPT

#On autorise les requêtes DNS 
sudo iptables -t filter -A OUTPUT -p tcp --dport 53 -j ACCEPT
sudo iptables -t filter -A OUTPUT -p udp --dport 53 -j ACCEPT
sudo iptables -t filter -A INPUT -p tcp --dport 53 -j ACCEPT
sudo iptables -t filter -A INPUT -p udp --dport 53 -j ACCEPT

#On autorise le ping pour eth0 et  wlan0
sudo iptables -A INPUT -i eth0 -p icmp -j ACCEPT
sudo iptables -A INPUT -i wlan0 -p icmp -j ACCEPT

#On autorise le ssh pour eth0 et  wlan0
sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -j ACCEPT
sudo iptables -A INPUT -i wlan0 -p tcp --dport 22 -j ACCEPT

#On envoie tous le traffic vers le tunnel VPN
sudo iptables -t nat -A POSTROUTING -o tun0 -j MASQUERADE
sudo iptables -A FORWARD -i eth0 -o tun0 -j ACCEPT
sudo iptables -A FORWARD -i tun0 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT

#On envoie tous le traffic de wlan0 vers le tunnel
sudo iptables -A FORWARD -i tun0 -o wlan0 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -i wlan0 -o tun0 -j ACCEPT
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#On jette tous le reste
sudo iptables -P FORWARD DROP
sudo iptables -P INPUT DROP

#On sauvegarde les règles persistentes
sudo systemctl enable netfilter-persistent

```  

for information :
      eth0 : 192.168.1.48 (GW 192.168.1.254)
    wlan0 : 192.168.220.1 (DHCP Range 192.168.220.10 - 50/24)
    tun0 : VPN Interface

  Thank.

---

