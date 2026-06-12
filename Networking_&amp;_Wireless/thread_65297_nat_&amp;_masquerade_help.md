---
title: "nat &amp; masquerade help"
date: 2005-09-13
forum: Networking &amp; Wireless
---

### Post by danielgc on 2005-09-13
I have hoary runing in a  PIII 800EB.  I connect to internet via a USB speedtouch
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html).  IT WORKS FINE

I installed a dhcp server whit the next configuration
--------------------------------------------------------------------------------

 sudo gedit /etc/default/dhcp3-server
INTERFACES="eth0"

sudo gedit /etc/dhcp3/dhcpd.conf
# A slightly different configuration for an internal subnet.
subnet 192.168.1.0 netmask 255.255.255.0 {
 range 192.168.1.100 192.168.1.200;
 option domain-name-servers 202.188.0.133, 202.188.1.5;
 option domain-name "tm.net.my";
 option routers 192.168.1.1;
 option broadcast-address 192.168.1.255;
 default-lease-time 600;
 max-lease-time 7200;
}
--------------------------------------------------------------------------------
AND IT WORKS FINE TOO.

Now, i would like to share internet whit 3 Ms Windows Pcs.

I have read everything about NAT and MASQUERADE.  I tried using the next scrips:
(my inner NIC is eth0 and my outer NIC is ppp0,  ppp0 conects to internet)

--------------------------------------------------------------------------------

#!/bin/bash
# Masquerade out ppp0
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

# Disallow NEW and INVALID incoming or forwarded packets from ppp0.
iptables -A INPUT -i ppp0 -m state --state NEW,INVALID -j DROP
iptables -A FORWARD -i ppp0 -m state --state NEW,INVALID -j DROP

# Turn on IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

--------------------------------------------------------------------------------

#!/bin/bash
LAN_IP_NET=192.168.1.0/24
LAN_NIC=eth0
OUT_NIC=ppp0
iptables -t nat -A POSTROUTING -s $LAN_IP_NET -o $OUT_NIC -j MASQUERADE
iptables -A FORWARD -j ACCEPT -i $LAN_NIC -s $LAN_IP_NET
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

--------------------------------------------------------------------------------

IN BOTH CASES SHARING INTERNET FROM UBUNTU DIDN´T WORK.
WHAT IS WRONG?  

P.D.
THE Ms Windows PCs WORKS FINE WHEN I SHARE INTERNET VIA WINDOWS XP/ISC  AND THEY RECEIVE AUTOMATIC IP ADDRESS WHEN UBUNTU DCHP IS RUNING.

---

### Post by s_p_a_r_k_y on 2005-09-13
do the windows clients pull up an IP? if so, can they ping addresses outside of the network? When I say addresses can they ping IPs? Also try the tracert tool on windows to see where packets are dying. Did you second script set the 1 in /proc/sys/net/ipv4/ip_forward ? without that one in the file it wont work, and it has to be set on every boot or in some system configuration fle (/etc/network/options
) if i'm correct

---

