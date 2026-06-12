---
title: "IP forwarding not working after upgrading Xubuntu to 14.04"
date: 2014-11-26
forum: Networking &amp; Wireless
---

### Post by roderick3 on 2014-11-26
I have a home network running xubuntu LTS which has served me well for the past few years until last week when I upgraded from version 12 to version 14. The host computers all lost their internet access.

I found that the upgrade had deleted my old firewall, Firestarter, and replaced it with ufw. I tried setting up the firewall first using Gufw then the command line for ufw. During my investigations I found that the hosts have no internet access even with the firewall disabled. So this makes me think that IP forwarding is not working.The hosts and the gateway can ping each other okay but the hosts cannot ping the internet, eg google or 8.8.8.8. The gateway can access the internet but the hosts cannot. 

I have made the recommended edits in /etc/ufw/sysctl.conf and when I run "sysctl net.ipv4.ip_forward" I get "net.ipv4.ip_forward = 1".

Just in case ufw had some default configuration that was preventing ip forwarding I took the drastic step of uninstalling Gufw and ufw. Still no internet access for the host computers. I found another sysctl.conf in /etc and uncommented the line, net.ipv4.ip_forward=1 then ran sudo sysctl -p /etc/sysctl.conf and got the response, net.ipv4.ip_forward = 1. But it's still not working. The hosts can ping the gateway but they cannot reach the internet.

I re-installed ufw. Here is the output from running "sudo ufw status verbose" (My home network is on 192.168.0.0/24):

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), allow (routed)
New profiles: skip

To                                                 Action                    From
--                                                    ------                    ----
192.168.0.2                           ALLOW IN           192.168.0.0/24
22                                                 LIMIT IN              Anywhere
Anywhere on eth0               ALLOW IN            192.168.0.0/24
22 (v6)                                     LIMIT IN               Anywhere (v6)


 I next tried following the instructions here, [https://help.ubuntu.com/lts/serverguide/firewall.html#other-firewall-tools](https://help.ubuntu.com/lts/serverguide/firewall.html#other-firewall-tools), and I edited /etc/ufw/before.rules by adding these lines:
# nat Table rules
*nat
:POSTROUTING ACCEPT [0:0]

# Forward traffic from eth1 through eth0.
-A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE

However when I restarted the firewall I got this error message:

Firewall stopped and disabled on system startup
ERROR: problem running ufw-init
Bad argument `*filter'
Error occurred at line: 22
Try `iptables-restore -h' or 'iptables-restore --help' for more information.

Problem running '/etc/ufw/before.rules'


I didn't touch line 22! I restored the file to its original state and the firewall started up okay. 
I suspect a lot has changed in the system config files since I first set up this network so I could really use some help as my family uses this network for work and children's homework, not as a hobby.

I solved the problem by adding a line "COMMIT" after the line "-A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE". I thought it was not required because it appears at the end of the file but it is.

---

