---
title: "L2TP VPN PROBLEM on 14.1"
date: 2015-04-04
forum: Networking &amp; Wireless
---

### Post by j-c-n on 2015-04-04
Hello, please can anybody help me or to write me which ubuntu page to use?

I have fresh 14.1 installation and I cannot use L2TP VPN.
I have only PPTP accessible from my taskbar network menu.
I found some ubuntu pages for older Ubuntu versions there were recomendations to use  l2tp-ipsec-vpn-daemon,  strongswan, openswan but nothing is working in 14.1.


Thank you for advice.
Regards Jiri Cvrk
(sorry for my poor english)

---

### Post by j-c-n on 2015-04-05
after 2 days, no progress :(

I have Strongswan installed, but I have only  pptp, ipsec/ikev2 choices to configure vpn, but I need l2tp with preshared key :(

In MS windows all I need was l2tp, server (Zyxel)  address, preshared key and to decide if I need to use CHAP, that was all.

As I found on internet there was possible to use *Werner Jaeger's solution*

$> sudo apt-add-repository ppa:werner-jaeger/ppa-werner-vpn
$> sudo apt-get update
$> sudo apt-get install l2tp-ipsec-vpn
$> sudo apt-get install l2tp-ipsec-vpn-daemon

BUT: it works not under 14.1 with "no candidate for installation"
(sudo apt-get update is "waiting for headers" in endless loop)

Please, there is really no solution for l2tp under Ubuntu 14.1 desktop??

Or.. it is possible to establish connection using terminal ?

I tried 
modprobe l2tp_eth

sudo ip l2tp add tunnel remote 194.108.111.111 local 192.168.33.249 tunnel_id 4001 peer_tunnel_id 4000 encap udp udp_sport 4001 udp_dport 4000
sudo ip l2tp show tunnel
sudo ip l2tp add session tunnel_id 4001 session_id 4001 peer_session_id 4000

And it is doing something..
But... I need to use port 500?? And where to write "preshared key" and username and password, where to specify CHAP and MSCHAP and trusted connection only?

Next I found 
[https://wiki.archlinux.org/index.php/L2TP/IPsec_VPN_client_setup](https://wiki.archlinux.org/index.php/L2TP/IPsec_VPN_client_setup)
it looks quite good, but it is not for Ubuntu.

Thank you for any Ubuntu help.


Thank you for any help..

---

