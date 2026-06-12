---
title: "OpenVPn connection setting"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by Khalis7 on 2008-09-25
Hi everyone. I'm in dying need of your help. Recently, I have subscribed to a VPN service and the service provider sent me the files required to allow me to use their service. The  problem now is I can't connect to the server even though I've install openvpn and in openvpn, I've setup the required parameters such as ca,certificate and key directory as in attached thumbnail below and copied those files together with openvpn.conf into /etc/openvpn folder as what was told to me by the VPN service provider administration person in charge. Whenever I tried to connect to the vpn server, it says  

```
Could not start the VPN connection 'BolehVPN' due to a connection error.

The VPN login failed because the VPN program could not connect to the VPN server.
```

Any ideas anyone??please...:cry:

---

### Post by sonofusion82 on 2008-09-25
hmm.. hard to know wat's wrong?
how about firewall?
perhaps you can try to use wireshark to figure out what is the cause of failing to connect.

---

