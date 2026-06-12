---
title: "Create Internet sharing over wireless network(Ad-Hoc)"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by aslamrahman on 2008-01-28
Can anyone give the step-by-step, how to create internet sharing over
wireless ( AD-HOC).
 i use ubuntu 7.10 , my client win xp.

---

### Post by angelot on 2008-01-28
HOWTO SETUP NAT

1. sudo apt-get install dnsmasq

2. Add (at the end) in /etc/sysctl.conf
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1

3. Empty iptables for existing rules
sudo iptables -F

4. Check that iptables is empty
sudo iptables -L

5. sudo iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
...where eth0 is internet and eth1 is the local network
6. sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
7. sudo iptables -A POSTROUTING -t nat -j MASQUERADE

8. sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

9. sudo iptables-save > /etc/iptables.up.rules

10. Add, under the local network-configuration (eth1) in /etc/network/interfaces
pre-up iptables-restore < /etc/iptables.up.rules

11. sudo /etc/init.d/networking restart

Resources:
[https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28iptables%29%7C%28nat%29](https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28iptables%29%7C%28nat%29)

---

### Post by aslamrahman on 2008-01-28
Thanks

this extra for ad-hoc configure 
[https://help.ubuntu.com/community/WifiDocs/Adhoc?highlight=%28ad-hoc%29](https://help.ubuntu.com/community/WifiDocs/Adhoc?highlight=%28ad-hoc%29)

---

### Post by goldsniper on 2008-01-28
it is much simpler if this  are done within a script. Dont you think?

---

