---
title: "[SOLVED] iptables Bad argument 'logdrop'"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by g4m3cub3 on 2008-07-01
I'm having a problem loading up a rules file. Pasted below is some terminal output and the rules file I'm trying to load. Does anyone have any ideas?


```
sudo iptables-restore /etc/iptables.rules
Bad argument `logdrop'
Error occurred at line: 14
Try `iptables-restore -h' or 'iptables-restore --help' for more information.
----------------------------------------------------------------------------


*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]
-N logdrop-A logdrop -j LOG --log-prefix "[INPUT]: "
-A logdrop -j DROP

-A INPUT -i wlan0 -f -j logdrop
-A INPUT -m state --state INVALID -j logdrop
-A INPUT -s 127.0.0.0/255.0.0.0 -i ! lo -j logdrop
-A INPUT -i lo -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,PSH,ACK,URG -j logdrop
-A INPUT -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j logdrop
-A INPUT -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j logdrop
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j logdrop
-A INPUT -p tcp -m tcp --tcp-flags FIN,RST FIN,RST -j logdrop
-A INPUT -p tcp -m tcp --tcp-flags FIN,ACK FIN -j logdrop
-A INPUT -p tcp -m tcp --tcp-flags PSH,ACK PSH -j logdrop
-A INPUT -p tcp -m tcp --tcp-flags ACK,URG URG -j logdrop

# bogons block list thanks to: 
# http://www.cymru.com/Documents/bogon-bn-agg.txt
# Cached on Tue Jul 1 19:36:13 EDT 2008
-A INPUT -s 0.0.0.0/7 -i wlan0 -j logdrop
-A INPUT -s 2.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 5.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 10.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 14.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 23.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 27.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 31.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 36.0.0.0/7 -i wlan0 -j logdrop
-A INPUT -s 39.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 42.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 46.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 49.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 50.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 100.0.0.0/6 -i wlan0 -j logdrop
-A INPUT -s 104.0.0.0/5 -i wlan0 -j logdrop
-A INPUT -s 127.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 169.254.0.0/16 -i wlan0 -j logdrop
-A INPUT -s 172.16.0.0/12 -i wlan0 -j logdrop
-A INPUT -s 175.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 176.0.0.0/5 -i wlan0 -j logdrop
-A INPUT -s 184.0.0.0/7 -i wlan0 -j logdrop
-A INPUT -s 192.0.2.0/24 -i wlan0 -j logdrop
-A INPUT -s 192.168.0.0/16 -i wlan0 -j logdrop
-A INPUT -s 197.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 198.18.0.0/15 -i wlan0 -j logdrop
-A INPUT -s 223.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 224.0.0.0/3 -i wlan0 -j logdrop
-A INPUT -s  -i wlan0 -j logdrop
	
	
	
# Cached results from:
# http://www.okean.com/antispam/iptables/rc.firewall.china 
# on Tue Jul 1 19:36:13 EDT 2008 
#firewall for china, port 25.
#http://www.okean.com/antispam/iptables/rc.firewall.china
#send comments, corrections, and additions to: comments20080430@okean.com
#last updated 2008.06.24 1105 PDT (UTC -7)

-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -p tcp -s 58.14.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.16.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.24.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.30.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.32.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.66.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.68.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.82.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.87.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.99.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.100.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.116.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.128.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.144.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.154.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.192.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.240.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.32.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.64.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.72.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.77.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.78.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.80.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.107.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.108.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.151.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.155.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.172.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.191.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.192.0.0/10 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.0.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.55.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.63.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.160.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.194.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.200.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.208.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.232.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.235.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.245.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.247.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.252.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.253.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.255.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.4.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.4.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.8.160.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.28.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.29.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.45.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.47.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.48.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.87.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.128.0.0/10 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.232.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.236.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.240.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.28.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.54.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.60.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.64.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.68.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.80.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.96.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.104.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.110.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.110.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.111.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.112.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.116.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.132.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.135.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.138.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.141.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.196.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.208.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.216.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.224.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.1.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.2.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.4.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.8.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.13.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.16.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.52.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.56.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.58.128.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.58.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.60.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.66.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.69.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.70.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.76.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.89.144.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.90.184.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.95.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.112.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.116.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.128.0.0/10 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.192.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.193.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.193.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.194.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.196.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.198.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.199.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.199.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.204.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.207.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.208.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.212.160.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.213.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.213.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.214.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.214.64.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.214.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.215.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.216.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.224.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.242.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.244.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.248.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.252.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.254.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.255.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.8.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.21.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.22.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.24.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.32.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.40.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.44.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.48.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.53.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.57.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.58.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.59.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.60.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.64.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.72.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.74.64.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.74.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.75.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.76.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.80.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.100.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.103.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.103.128.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.106.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.112.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.120.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.120.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.121.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.121.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.121.192.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.122.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.124.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.128.0.0/10 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.24.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.64.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.66.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.67.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.72.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.80.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.84.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.88.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.88.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.88.127.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.89.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.91.240.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.102.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.112.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.120.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.124.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.126.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.132.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.144.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.178.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.180.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.184.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.192.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.212.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.224.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.228.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.230.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.239.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.242.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.244.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.248.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.0.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.2.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.2.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.3.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.4.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.8.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.10.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.15.136.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.16.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.19.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.20.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.27.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.27.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.30.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.31.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.32.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.40.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.40.64.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.40.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.41.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.42.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.42.136.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.42.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.44.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.48.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.57.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.58.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.59.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.60.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.62.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.63.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.75.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.78.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.80.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.84.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.88.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.96.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.108.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.112.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.128.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.144.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.148.160.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.161.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.162.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.164.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.176.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.232.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.235.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.248.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.253.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.254.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.0.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.30.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.32.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.48.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.52.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.64.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.72.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.72.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.76.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.80.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.90.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.92.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.94.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.128.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.136.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.137.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.192.0.0/10 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.0.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.4.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.8.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.16.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.32.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.40.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.46.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.48.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.51.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.52.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.52.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.52.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.55.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.56.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.58.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.58.144.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.59.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.60.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.68.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.76.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.79.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.89.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.100.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.101.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.101.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.192.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.201.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.204.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.224.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.248.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.255.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.0.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.0.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.4.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.8.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.48.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.49.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.51.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.64.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.96.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.102.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.102.64.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.112.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.119.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.136.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.144.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.152.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.156.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.192.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.198.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.200.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.204.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.224.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.240.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.248.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.0.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.4.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.8.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.49.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.52.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.56.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.64.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.96.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.98.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.99.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.100.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.101.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.103.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.108.128.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.108.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.112.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.128.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.136.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.137.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.138.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.144.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.160.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.176.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.177.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.178.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.180.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.184.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.196.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.199.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.206.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.232.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.242.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.244.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.249.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.253.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.6.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.14.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.16.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.20.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.28.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.29.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.31.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.40.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.40.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.42.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.47.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.64.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.66.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.67.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.68.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.72.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.88.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.108.8.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.108.40.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.112.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.126.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.128.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.147.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.156.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.160.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.172.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.192.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.196.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.200.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.220.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.224.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.240.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.242.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.243.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.248.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.249.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.250.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.254.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.31.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.32.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.58.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.61.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.62.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.64.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.96.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.98.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.104.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.112.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.169.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.171.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.208.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.210.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.213.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.214.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.215.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.216.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.254.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 134.196.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 159.226.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 161.207.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 162.105.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 166.111.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 167.139.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.160.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 169.211.1.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.83.122.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.124.154.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.188.170.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 198.17.7.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 198.97.132.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.0.110.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.0.160.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.0.176.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.4.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.4.252.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.8.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.10.64.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.14.88.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.14.235.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.14.236.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.14.238.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.20.120.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.22.248.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.128.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.136.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.138.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.140.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.144.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.149.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.150.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.152.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.156.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.158.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.160.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.164.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.168.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.176.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.184.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.41.152.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.41.240.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.43.48.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.46.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.46.224.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.60.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.69.4.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.69.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.70.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.74.8.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.75.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.85.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.90.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.90.224.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.90.252.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.91.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.91.128.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.91.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.91.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.92.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.92.252.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.93.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.93.252.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.94.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.95.0.0/19	 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.95.252.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.96.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.112.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.120.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.122.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.122.32.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.122.64.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.122.112.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.122.128.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.123.96.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.124.24.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.125.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.127.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.127.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.127.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.127.160.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.127.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.130.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.130.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.131.16.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.131.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.131.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.136.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.136.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.136.224.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.141.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.142.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.143.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.148.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.149.160.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.149.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.150.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.152.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.153.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.158.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.160.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.164.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.164.25.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.165.96.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.165.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.165.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.168.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.170.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.170.216.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.173.8.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.173.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.179.240.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.180.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.181.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.189.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.192.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.18.50.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.79.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.80.144.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.81.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.83.56.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.86.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.86.64.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.88.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.88.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.88.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.89.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.90.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.90.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.90.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.91.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.91.96.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.91.120.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.92.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.92.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.93.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.94.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.95.0.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.95.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.99.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.99.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.100.32.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.100.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.100.92.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.100.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.110.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.118.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.119.24.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.119.32.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.128.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.128.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.128.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.130.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.132.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.134.240.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.135.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.135.160.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.142.219.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.148.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.152.64.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.156.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.158.16.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.161.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.166.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.171.224.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.174.7.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.174.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.175.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.175.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.176.168.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.184.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.187.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.190.96.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.191.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.191.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.191.144.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.192.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.196.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.207.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.207.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.208.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.208.16.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.208.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.209.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.212.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.212.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.222.192.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.223.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.0.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.2.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.5.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.5.32.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.5.144.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.12.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.14.64.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.14.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.14.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.15.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.15.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.16.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.21.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.22.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.23.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.25.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.26.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.28.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.32.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.51.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.52.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.56.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.72.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.76.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.78.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.79.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.79.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.82.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.87.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.185.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.192.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.64.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.80.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.96.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.136.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.144.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.160.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.0.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.56.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.64.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.96.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.104.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.108.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.185.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.192.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.240.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.249.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.72.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.82.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.128.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.216.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.224.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.242.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.244.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.101.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.112.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.152.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.154.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.160.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.192.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.231.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.231.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.232.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.234.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.242.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.248.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.0.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.8.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.12.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.12.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.13.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.14.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.122.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.129.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.130.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.133.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.136.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.172.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.176.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.192.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.196.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.198.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.199.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.199.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.199.192.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.199.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.200.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.208.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.224.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.16.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.32.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.64.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.125.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.126.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.128.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.160.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.168.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.176.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.192.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.240.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.248.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.249.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.249.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.249.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.249.224.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.249.240.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.249.248.0/23 --dport 25 -j logdrop

	
	
	
# Cached results from:
# http://www.okean.com/antispam/iptables/rc.firewall.korea 
# on Tue Jul 1 19:36:13 EDT 2008 
#firewall for korea, port 25
#http://www.okean.com/antispam/iptables/rc.firewall.korea
#send comments, corrections, and additions to: comments20080430@okean.com
#last updated 2008.07.01 1417 PDT (UTC -8)

-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -p tcp -s 58.29.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.65.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.72.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.87.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.102.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.120.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.138.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.140.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.145.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.146.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.148.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.180.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.181.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.184.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.224.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.0.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.86.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.150.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.151.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.152.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.186.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.196.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.4.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.5.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.32.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.40.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.47.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.72.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.80.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.84.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.96.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.245.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.247.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.247.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.247.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.248.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 66.232.136.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 66.232.144.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.29.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.29.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.30.0.0/19 --dport 25 -j logdrop

-A INPUT -p tcp -s 114.30.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.30.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.31.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.31.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.52.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.70.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.108.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.108.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.111.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.111.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.129.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.129.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.141.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.141.40.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.141.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.199.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.199.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.200.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 115.0.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 115.16.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.32.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.67.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.68.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.68.232.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.84.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.89.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.93.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.120.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.193.80.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.199.160.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.200.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.212.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.16.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.20.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.20.96.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.20.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.53.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.53.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.55.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.58.128.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.110.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.123.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.32.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.67.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.103.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.107.160.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.127.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.128.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.176.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.216.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.234.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.17.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.17.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.30.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.31.240.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.42.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.59.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.63.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.64.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.75.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.75.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.77.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.82.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.148.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.148.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.149.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.161.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.192.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.235.192.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.235.240.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.29.128.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.50.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.73.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.142.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.143.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.143.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.0.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.0.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.1.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.50.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.50.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.50.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.136.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.50.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.53.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.54.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.55.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.55.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.64.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.78.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.88.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.100.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.101.192.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.101.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.124.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.126.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.127.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.127.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.128.0.0/10 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.200.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.252.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.254.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.254.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.0.8.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.0.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.32.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.49.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.99.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.100.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.101.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.128.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.128.64.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.128.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.129.208.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.129.240.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.153.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.199.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.199.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.202.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.202.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.203.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.252.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.252.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.254.64.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.254.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.0.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.32.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.98.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.98.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.99.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.108.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.108.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.109.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.111.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.140.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.199.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.200.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.212.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.228.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.248.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.250.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.254.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.0.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.5.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.28.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.28.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.46.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.48.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.66.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.80.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.111.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.136.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.146.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.153.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.194.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.195.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.195.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.197.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.197.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.198.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.199.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.199.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.216.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.217.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.243.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.254.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.7.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.31.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.57.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.60.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.61.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.128.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.176.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.208.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.208.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.209.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.240.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.248.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.252.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 128.134.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 129.254.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 134.75.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 137.68.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 141.223.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 143.248.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 147.43.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 147.46.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 150.150.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 150.183.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 150.197.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 152.99.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 152.149.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 154.10.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 155.230.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 156.147.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 157.197.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 158.44.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 161.122.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 163.152.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 163.180.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 163.239.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 164.124.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.132.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.141.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.186.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.194.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.213.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.229.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.243.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.244.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.246.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 166.79.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 166.103.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 166.104.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 166.125.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.78.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.115.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.126.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.131.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.154.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.188.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.219.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.248.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 169.140.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 169.211.2.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.5.90.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.100.2.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.104.15.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.132.15.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.132.247.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.132.248.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.195.39.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.195.40.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.203.138.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.203.140.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.203.144.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.203.146.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.245.249.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.245.250.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.249.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 198.178.187.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.6.95.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.14.103.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.14.165.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.20.82.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.20.84.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.20.86.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.20.99.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.20.119.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.20.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.21.0.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.22.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.30.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.43.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.47.143.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.68.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.73.132.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.86.8.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.89.248.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.93.6.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.126.112.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.133.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.136.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.136.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.150.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.158.144.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.163.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.165.56.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.167.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.171.248.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.174.88.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.179.176.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.189.128.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.17.226.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.77.176.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.80.57.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.81.8.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.81.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.82.219.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.82.220.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.82.240.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.83.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.84.240.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.90.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.100.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.109.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.123.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.128.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.128.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.128.236.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.129.6.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.130.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.130.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.131.24.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.132.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.133.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.142.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.142.216.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.149.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.152.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.153.144.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.166.208.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.169.4.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.170.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.171.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.173.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.175.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.190.26.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.207.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.210.16.0/30 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.210.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.212.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.212.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.215.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.216.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.217.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.223.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.224.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.0.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.2.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.4.88.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.4.216.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.16.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.57.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.80.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.87.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.89.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.90.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.92.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.96.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.178.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.180.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.192.64.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.204.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.210.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.216.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.32.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.104.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.112.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.168.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.176.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.192.0.0/10 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.36.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.48.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.101.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.144.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.209.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.232.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.240.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.248.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.64.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.103.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.116.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.120.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.149.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.230.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.132.64.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.133.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.133.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.138.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.140.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.144.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.160.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.168.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.96.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.112.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.120.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.122.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.231.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.232.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.251.128.0/17 --dport 25 -j logdrop


# Public ports
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN --dport 22 -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN --dport 443 -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN --dport 2200 -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN --dport 1863 -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN --dport 5050 -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN --dport 5190 -j ACCEPT

# Accept good connections
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Drop the rest
-A INPUT -j logdrop

# Output filters
-A OUTPUT -o lo -j ACCEPT
-A OUTPUT -p tcp -m state --state NEW,ESTABLISHED -j ACCEPT
-A OUTPUT -p udp -m state --state NEW,ESTABLISHED -j ACCEPT
-A OUTPUT -p icmp -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
COMMIT
```

---

### Post by HalPomeranz on 2008-07-02
I believe the file should start as follows:

```

*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]
:logdrop - [0:0]
-A logdrop -j LOG --log-prefix "[INPUT]: "
-A logdrop -j DROP
*[... rest of the file as written ...]*

```

You don't use "-N" in these filter files, you use ":<filter> - [0:0]".  The "-N" option should only be used as a command-line option for the iptables command.

Also, you really shouldn't be editing these files by hand anyway.  Create your IP tables rules using the iptables command (or whatever firewall GUI you prefer) and then use iptables-save to dump the filters to a file so that they can be automatically loaded at next boot.

---

### Post by kevdog on 2008-07-03
It would be easier just to create a script file that you would pass your script to iptables on boot or when the network if brought up.  The rules contained in the script file are the same as passed on the command line.

You really don't want to be editing the iptables-save file.  There is not a lot of documentation, and it will get you into trouble.

Here's an example that I helped someone else with:

#!/bin/sh
#

IPTABLES=/sbin/iptables

### flush existing rules and set chain policy setting to DROP
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X

$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P FORWARD DROP

### state tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### Create a LOGDROP chain to log dropped packets
$IPTABLES -N LOGDROP

### Drop Log Ruleset (Logs all packets not captured above, before dropping)

#Change the Following Parameters to Limit the amount of Logging
LOGLIMIT="2/s"
LOGLIMITBURST="10"

#Log level may be one of the following: debug, info, notice, warning, warn, err, error, crit, alert, emerg, panic
LOGLEVEL=7

$IPTABLES -A LOGDROP -i ! lo -p tcp -j LOG --log-level $LOGLEVEL --log-prefix "TCP DROP: "
$IPTABLES -A LOGDROP -i ! lo -p udp -j LOG --log-level $LOGLEVEL --log-prefix "UDP DROP: "
$IPTABLES -A LOGDROP -i ! lo -p icmp -j LOG --log-level $LOGLEVEL --log-prefix "ICMP DROP: "

### Log All INPUT Network Traffic
$IPTABLES -A INPUT -j LOGDROP

### ACCEPT rules
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 80 -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 22 --source 131.0.0.0/8 -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -m limit --limit 10/second -j ACCEPT


exit

---

### Post by HalPomeranz on 2008-07-03
> **kevdog said:**
> It would be easier just to create a script file that you would pass your script to iptables on boot or when the network if brought up.

Actually, I disagree.  The "vendor supported interface" in Ubuntu is to use the iptables-save program to dump out your running rulebase into /etc/iptables.rules.  This mechanism is already built into the networking startup scripts (see /etc/NetworkManager/dispatcher.d/01firewall) so you don't need to hack in your own boot script.

I do agree with you that the original poster should not be hand-editing /etc/iptables.rules.  That's just going to lead to trouble.

---

### Post by kevdog on 2008-07-03
I dont get it then -- whats the best way to supply your rules if not hacking your own script?  In my opinion Network Manager is buggy, unreliable, and only works well for certain chipsets.  I use it on some computers and not others.  To tell me network manager is setup to load the firewall script is kind of pointless because this is only applicable to those running NetworkManager.

---

### Post by HalPomeranz on 2008-07-03
> **kevdog said:**
> I dont get it then -- whats the best way to supply your rules if not hacking your own script?  In my opinion Network Manager is buggy, unreliable, and only works well for certain chipsets.  I use it on some computers and not others.  To tell me network manager is setup to load the firewall script is kind of pointless because this is only applicable to those running NetworkManager.

Well, for better or worse, Network Manager is the way things are going.  You should file bugs against the items that aren't working for you.

But yeah if it's not working for you then you have to hack your own script into the boot process.

---

### Post by kevdog on 2008-07-03
Network Manager --- Ubuntu -- its a conspiracy.  That is one buggy piece of software.  Its a shame its the default.  I'm not touting WICD as a replacement, only wishing something would actually work with all the features -- static IPs, VPN -- as it is supposed to.  If you haven't read all the threads mentioning problems with NWM, then there is definitely a blind eye being turned to the problem.

---

### Post by TreeFinger on 2008-07-03
Whats best way to learn iptable?

---

### Post by g4m3cub3 on 2008-07-05
The code that HalPomeranz gave me worked but also on lines 53 and 771 in my code had some empty space of somekind that iptables didn't like. Here's the final code that works and thank you all for your replies.

```
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]
-N logdrop-A logdrop -j LOG --log-prefix "[INPUT]: "
-A logdrop -j DROP

-A INPUT -i wlan0 -f -j logdrop
-A INPUT -m state --state INVALID -j logdrop
-A INPUT -s 127.0.0.0/255.0.0.0 -i ! lo -j logdrop
-A INPUT -i lo -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,PSH,ACK,URG -j logdrop
-A INPUT -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j logdrop
-A INPUT -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j logdrop
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j logdrop
-A INPUT -p tcp -m tcp --tcp-flags FIN,RST FIN,RST -j logdrop
-A INPUT -p tcp -m tcp --tcp-flags FIN,ACK FIN -j logdrop
-A INPUT -p tcp -m tcp --tcp-flags PSH,ACK PSH -j logdrop
-A INPUT -p tcp -m tcp --tcp-flags ACK,URG URG -j logdrop

# bogons block list thanks to: 
# http://www.cymru.com/Documents/bogon-bn-agg.txt
# Cached on Tue Jul 1 19:36:13 EDT 2008
-A INPUT -s 0.0.0.0/7 -i wlan0 -j logdrop
-A INPUT -s 2.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 5.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 10.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 14.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 23.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 27.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 31.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 36.0.0.0/7 -i wlan0 -j logdrop
-A INPUT -s 39.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 42.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 46.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 49.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 50.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 100.0.0.0/6 -i wlan0 -j logdrop
-A INPUT -s 104.0.0.0/5 -i wlan0 -j logdrop
-A INPUT -s 127.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 169.254.0.0/16 -i wlan0 -j logdrop
-A INPUT -s 172.16.0.0/12 -i wlan0 -j logdrop
-A INPUT -s 175.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 176.0.0.0/5 -i wlan0 -j logdrop
-A INPUT -s 184.0.0.0/7 -i wlan0 -j logdrop
-A INPUT -s 192.0.2.0/24 -i wlan0 -j logdrop
-A INPUT -s 192.168.0.0/16 -i wlan0 -j logdrop
-A INPUT -s 197.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 198.18.0.0/15 -i wlan0 -j logdrop
-A INPUT -s 223.0.0.0/8 -i wlan0 -j logdrop
-A INPUT -s 224.0.0.0/3 -i wlan0 -j logdrop
-A INPUT -s  -i wlan0 -j logdrop
	
	
	
# Cached results from:
# http://www.okean.com/antispam/iptables/rc.firewall.china 
# on Tue Jul 1 19:36:13 EDT 2008 
#firewall for china, port 25.
#http://www.okean.com/antispam/iptables/rc.firewall.china
#send comments, corrections, and additions to: comments20080430@okean.com
#last updated 2008.06.24 1105 PDT (UTC -7)

-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -p tcp -s 58.14.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.16.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.24.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.30.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.32.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.66.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.68.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.82.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.87.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.99.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.100.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.116.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.128.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.144.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.154.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.192.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.240.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.32.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.64.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.72.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.77.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.78.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.80.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.107.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.108.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.151.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.155.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.172.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.191.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.192.0.0/10 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.0.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.55.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.63.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.160.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.194.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.200.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.208.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.232.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.235.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.245.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.247.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.252.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.253.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.255.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.4.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.4.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.8.160.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.28.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.29.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.45.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.47.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.48.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.87.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.128.0.0/10 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.232.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.236.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.240.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.28.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.54.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.60.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.64.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.68.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.80.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.96.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.104.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.110.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.110.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.111.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.112.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.116.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.132.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.135.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.138.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.141.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.196.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.208.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.216.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.224.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.1.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.2.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.4.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.8.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.13.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.16.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.52.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.56.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.58.128.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.58.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.60.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.66.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.69.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.70.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.76.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.89.144.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.90.184.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.95.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.112.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.116.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.128.0.0/10 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.192.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.193.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.193.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.194.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.196.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.198.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.199.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.199.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.204.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.207.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.208.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.212.160.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.213.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.213.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.214.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.214.64.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.214.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.215.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.216.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.224.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.242.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.244.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.248.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.252.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.254.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.255.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.8.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.21.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.22.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.24.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.32.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.40.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.44.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.48.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.53.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.57.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.58.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.59.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.60.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.64.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.72.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.74.64.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.74.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.75.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.76.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.80.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.100.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.103.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.103.128.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.106.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.112.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.120.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.120.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.121.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.121.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.121.192.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.122.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.124.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.128.0.0/10 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.24.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.64.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.66.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.67.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.72.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.80.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.84.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.88.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.88.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.88.127.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.89.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.91.240.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.102.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.112.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.120.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.124.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.126.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.132.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.144.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.178.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.180.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.184.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.192.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.212.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.224.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.228.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.230.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.239.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.242.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.244.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.248.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.0.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.2.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.2.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.3.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.4.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.8.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.10.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.15.136.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.16.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.19.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.20.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.27.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.27.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.30.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.31.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.32.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.40.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.40.64.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.40.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.41.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.42.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.42.136.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.42.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.44.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.48.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.57.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.58.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.59.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.60.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.62.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.63.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.75.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.78.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.80.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.84.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.88.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.96.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.108.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.112.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.128.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.144.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.148.160.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.161.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.162.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.164.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.176.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.232.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.235.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.248.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.253.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.254.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.0.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.30.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.32.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.48.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.52.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.64.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.72.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.72.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.76.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.80.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.90.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.92.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.94.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.128.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.136.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.137.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.192.0.0/10 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.0.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.4.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.8.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.16.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.32.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.40.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.46.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.48.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.51.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.52.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.52.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.52.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.55.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.56.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.58.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.58.144.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.59.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.60.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.68.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.76.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.79.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.89.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.100.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.101.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.101.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.192.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.201.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.204.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.224.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.248.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.255.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.0.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.0.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.4.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.8.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.48.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.49.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.51.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.64.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.96.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.102.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.102.64.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.112.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.119.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.136.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.144.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.152.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.156.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.192.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.198.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.200.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.204.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.224.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.240.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.248.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.0.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.4.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.8.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.49.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.52.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.56.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.64.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.96.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.98.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.99.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.100.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.101.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.103.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.108.128.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.108.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.112.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.128.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.136.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.137.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.138.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.144.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.160.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.176.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.177.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.178.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.180.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.184.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.196.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.199.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.206.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.232.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.242.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.244.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.249.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.253.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.6.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.14.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.16.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.20.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.28.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.29.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.31.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.40.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.40.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.42.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.47.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.64.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.66.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.67.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.68.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.72.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.88.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.108.8.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.108.40.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.112.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.126.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.128.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.147.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.156.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.160.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.172.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.192.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.196.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.200.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.220.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.224.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.240.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.242.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.243.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.248.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.249.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.250.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.254.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.31.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.32.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.58.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.61.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.62.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.64.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.96.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.98.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.104.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.112.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.169.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.171.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.208.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.210.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.213.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.214.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.215.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.216.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.254.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 134.196.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 159.226.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 161.207.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 162.105.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 166.111.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 167.139.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.160.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 169.211.1.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.83.122.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.124.154.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.188.170.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 198.17.7.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 198.97.132.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.0.110.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.0.160.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.0.176.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.4.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.4.252.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.8.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.10.64.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.14.88.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.14.235.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.14.236.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.14.238.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.20.120.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.22.248.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.128.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.136.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.138.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.140.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.144.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.149.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.150.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.152.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.156.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.158.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.160.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.164.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.168.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.176.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.184.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.38.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.41.152.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.41.240.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.43.48.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.46.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.46.224.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.60.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.69.4.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.69.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.70.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.74.8.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.75.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.85.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.90.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.90.224.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.90.252.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.91.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.91.128.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.91.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.91.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.92.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.92.252.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.93.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.93.252.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.94.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.95.0.0/19	 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.95.252.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.96.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.112.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.120.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.122.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.122.32.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.122.64.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.122.112.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.122.128.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.123.96.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.124.24.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.125.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.127.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.127.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.127.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.127.160.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.127.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.130.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.130.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.131.16.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.131.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.131.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.136.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.136.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.136.224.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.141.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.142.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.143.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.148.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.149.160.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.149.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.150.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.152.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.153.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.158.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.160.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.164.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.164.25.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.165.96.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.165.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.165.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.168.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.170.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.170.216.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.173.8.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.173.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.179.240.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.180.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.181.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.189.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.192.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.18.50.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.79.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.80.144.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.81.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.83.56.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.86.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.86.64.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.88.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.88.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.88.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.89.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.90.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.90.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.90.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.91.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.91.96.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.91.120.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.92.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.92.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.93.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.94.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.95.0.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.95.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.99.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.99.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.100.32.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.100.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.100.92.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.100.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.110.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.118.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.119.24.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.119.32.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.128.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.128.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.128.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.130.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.132.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.134.240.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.135.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.135.160.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.142.219.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.148.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.152.64.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.156.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.158.16.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.161.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.166.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.171.224.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.174.7.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.174.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.175.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.175.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.176.168.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.184.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.187.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.190.96.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.191.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.191.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.191.144.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.192.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.196.0.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.207.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.207.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.208.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.208.16.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.208.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.209.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.212.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.212.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.222.192.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.223.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.0.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.2.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.5.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.5.32.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.5.144.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.12.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.14.64.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.14.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.14.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.15.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.15.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.16.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.21.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.22.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.23.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.25.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.26.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.28.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.32.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.51.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.52.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.56.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.72.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.76.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.78.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.79.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.79.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.82.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.87.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.185.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.192.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.64.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.80.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.96.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.136.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.144.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.160.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.0.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.56.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.64.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.96.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.104.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.108.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.185.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.192.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.240.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.249.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.72.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.82.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.128.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.216.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.224.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.242.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.244.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.101.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.112.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.152.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.154.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.160.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.192.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.231.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.231.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.232.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.234.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.242.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.248.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.0.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.8.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.12.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.12.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.13.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.14.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.122.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.129.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.130.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.133.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.136.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.172.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.176.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.192.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.196.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.198.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.199.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.199.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.199.192.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.199.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.200.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.208.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.224.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.16.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.32.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.64.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.125.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.126.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.128.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.160.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.168.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.176.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.192.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.240.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.248.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.249.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.249.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.249.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.249.224.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.249.240.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.249.248.0/23 --dport 25 -j logdrop

	
	
	
# Cached results from:
# http://www.okean.com/antispam/iptables/rc.firewall.korea 
# on Tue Jul 1 19:36:13 EDT 2008 
#firewall for korea, port 25
#http://www.okean.com/antispam/iptables/rc.firewall.korea
#send comments, corrections, and additions to: comments20080430@okean.com
#last updated 2008.07.01 1417 PDT (UTC -8)

-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -p tcp -s 58.29.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.65.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.72.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.87.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.102.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.120.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.138.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.140.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.145.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.146.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.148.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.180.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.181.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.184.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 58.224.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.0.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.86.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.150.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.151.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.152.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 59.186.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 60.196.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.4.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.5.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.32.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.40.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.47.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.72.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.80.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.84.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.96.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.245.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.247.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.247.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.247.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 61.248.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 66.232.136.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 66.232.144.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.29.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.29.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.30.0.0/19 --dport 25 -j logdrop

-A INPUT -p tcp -s 114.30.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.30.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.31.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.31.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.52.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.70.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.108.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.108.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.111.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.111.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.129.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.129.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.141.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.141.40.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.141.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.199.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.199.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 114.200.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 115.0.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 115.16.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.32.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.67.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.68.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.68.232.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.84.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.89.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.93.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.120.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.193.80.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.199.160.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.200.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 116.212.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.16.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.20.80.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.20.96.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.20.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.53.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.53.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.55.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.58.128.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.110.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 117.123.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.32.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.67.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.103.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.107.160.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.127.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.128.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.176.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.216.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 118.234.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.17.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.17.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.30.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.31.240.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.42.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.59.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.63.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.64.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.75.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.75.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.77.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.82.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.148.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.148.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.149.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.161.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.192.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.235.192.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 119.235.240.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.29.128.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.50.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.73.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.142.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.143.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.143.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.0.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.0.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.1.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.50.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.50.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.50.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 120.136.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.50.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.53.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.54.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.55.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.55.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.64.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.78.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.88.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.100.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.101.192.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.101.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.124.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.126.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.127.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.127.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.128.0.0/10 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.200.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.252.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.254.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 121.254.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.0.8.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.0.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.32.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.49.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.99.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.100.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.101.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.128.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.128.64.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.128.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.129.208.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.129.240.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.153.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.199.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.199.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.202.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.202.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.203.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.252.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.252.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.254.64.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 122.254.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.0.0.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.32.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.98.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.98.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.99.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.108.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.108.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.109.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.111.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.140.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.199.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.200.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.212.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.228.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.248.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.250.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 123.254.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.0.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.5.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.28.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.28.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.46.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.48.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.66.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.80.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.111.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.136.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.146.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.153.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.194.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.195.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.195.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.197.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.197.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.198.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.199.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.199.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.216.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.217.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.243.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 124.254.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.7.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.31.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.57.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.60.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.61.0.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.128.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.176.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.208.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.208.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.209.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.240.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.248.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 125.252.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 128.134.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 129.254.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 134.75.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 137.68.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 141.223.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 143.248.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 147.43.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 147.46.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 150.150.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 150.183.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 150.197.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 152.99.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 152.149.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 154.10.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 155.230.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 156.147.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 157.197.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 158.44.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 161.122.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 163.152.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 163.180.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 163.239.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 164.124.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.132.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.141.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.186.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.194.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.213.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.229.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.243.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.244.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 165.246.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 166.79.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 166.103.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 166.104.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 166.125.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.78.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.115.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.126.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.131.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.154.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.188.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.219.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 168.248.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 169.140.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 169.211.2.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.5.90.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.100.2.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.104.15.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.132.15.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.132.247.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.132.248.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.195.39.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.195.40.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.203.138.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.203.140.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.203.144.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.203.146.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.245.249.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.245.250.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 192.249.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 198.178.187.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.6.95.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.14.103.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.14.165.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.20.82.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.20.84.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.20.86.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.20.99.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.20.119.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.20.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.21.0.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.22.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.30.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.43.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.47.143.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.68.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.73.132.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.86.8.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.89.248.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.93.6.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.126.112.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.133.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.136.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.136.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.150.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.158.144.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.163.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.165.56.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.167.208.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.171.248.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.174.88.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.179.176.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 202.189.128.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.17.226.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.77.176.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.80.57.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.81.8.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.81.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.82.219.0/24 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.82.220.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.82.240.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.83.128.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.84.240.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.90.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.100.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.109.0.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.123.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.128.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.128.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.128.236.0/22 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.129.6.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.130.64.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.130.176.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.131.24.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.132.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.133.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.142.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.142.216.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.149.112.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.152.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.153.144.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.166.208.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.169.4.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.170.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.171.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.173.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.175.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.190.26.0/23 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.207.16.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.210.16.0/30 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.210.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.212.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.212.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.215.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.216.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.217.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.223.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 203.224.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.0.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.2.32.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.4.88.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.4.216.0/21 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.16.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.57.224.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.80.96.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.87.192.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.89.160.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.90.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.92.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.96.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.178.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.180.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.192.64.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.204.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.210.192.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 210.216.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.32.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.104.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.112.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.168.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.176.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 211.192.0.0/10 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.36.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.48.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.101.128.0/17 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.144.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.209.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 218.232.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.240.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 219.248.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.64.0.0/11 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.103.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.116.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.120.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.149.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 220.230.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.132.64.0/19 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.133.48.0/20 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.133.128.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.138.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.140.0.0/14 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.144.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.160.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 221.168.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.96.0.0/12 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.112.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.120.0.0/15 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.122.0.0/16 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.231.0.0/18 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.232.0.0/13 --dport 25 -j logdrop
-A INPUT -p tcp -s 222.251.128.0/17 --dport 25 -j logdrop


# Public ports
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN --dport 22 -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN --dport 443 -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN --dport 2200 -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN --dport 1863 -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN --dport 5050 -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN --dport 5190 -j ACCEPT

# Accept good connections
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Drop the rest
-A INPUT -j logdrop

# Output filters
-A OUTPUT -o lo -j ACCEPT
-A OUTPUT -p tcp -m state --state NEW,ESTABLISHED -j ACCEPT
-A OUTPUT -p udp -m state --state NEW,ESTABLISHED -j ACCEPT
-A OUTPUT -p icmp -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
COMMIT
```


Also, to answer treefinger, I just started working with iptables and I learned it by looking at other scripts and reading the man page a little bit. I actually scrapped this script I was working on and have a better one as follows:

```
#!/bin/sh

#Define variables
#External_Interface='wlan0'	# $External_Interface
#Internal_Interface='wlan0'	# $Internal_Interface
NTP_Server='1.us.pool.ntp.org'	# $NTP_Server
DNS_Server='192.168.0.1'	# $DNS_Server
DHCP_Server='192.168.0.1'	# $DHCP_Server


echo "Resetting iptables to default state"

iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

echo "Applying rules..."

# Default Policy
sudo iptables -P INPUT DROP	# Drop INPUT packets without logging
sudo iptables -P OUTPUT DROP	# Drop OUTPUT packets without logging
sudo iptables -P FORWARD DROP	# Drop FORWARD packets without logging

# Create a LOGDROP chain to log and drop packets
sudo iptables -N LOGDROP
sudo iptables -A LOGDROP -j LOG
sudo iptables -A LOGDROP -j DROP

# Log invalid state traffic
sudo iptables -A INPUT -m state --state INVALID -m limit --limit 5/minute -j LOG --log-prefix "INVALID STATE:"

# Allow all input to loopback interface
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A OUTPUT -o lo -j ACCEPT

# DHCP
sudo iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -p udp -d $DHCP_Server --dport 67 -j ACCEPT
sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -p udp -s $DHCP_Server --sport 67 -j ACCEPT

# DNS
sudo iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -p udp -d $DNS_Server --dport 53 -j ACCEPT
sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -p udp -s $DNS_Server --sport 53 -j ACCEPT

# NTP
sudo iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -p udp -d $NTP_Server --dport 123 -j ACCEPT
sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -p udp -s $NTP_Server --sport 123 -j ACCEPT

# Outbound TCP
sudo iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -p tcp -m multiport --dports 21,22,80,443,1863,2200,5050,5190,6667,6697 -j ACCEPT

# Allow inbound TCP for established connections
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -p tcp -m multiport --sports 21,22,80,443,1863,2200,5050,5190,6667,6697 -j ACCEPT

# Allow streaming music
sudo iptables -A OUTPUT -m state --state NEW,ESTABLISHED,RELATED -p tcp -m multiport --dports 7254,8000 -j ACCEPT
sudo iptables -A INPUT -m state --state RELATEd,ESTABLISHED -p tcp -m multiport --sports 7254,8000 -j ACCEPT

# Log and drop all other traffic
sudo iptables -A INPUT -j LOGDROP
sudo iptables -A OUTPUT -j LOGDROP

echo "Finished!"
```

---

### Post by kevdog on 2008-07-05
isnt this line redundant??:

sudo iptables -A LOGDROP -j DROP

since the default stance on the 3 chains is DROP, if they have made it to the end of the LOGDROP chain, they will in the end be dropped anyway by reason on the default policy on the INPUT/OUTPUT chains.

I bet if you delete this line, everything will be the same.

---

### Post by g4m3cub3 on 2008-07-05
Yes, you're right. Thank you for pointing that out. With the default policy being set to DROP, all I need to do is log at the end.

---

