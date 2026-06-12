---
title: "Setting up Squid. What to configure ports?"
date: 2019-03-21
forum: Networking &amp; Wireless
---

### Post by mark236 on 2019-03-21
Hello.
I want to make **Wifi-hotspot with authorization by SMS**. I found an **[article]("https://habr.com/ru/post/307338/")** on the Internet in which I try to work, but which I do not understand in subtle details.
Available: old computer under the server; workstation with which I write; TP-Link TL-WR720N router. I thought another modem to take to receive SMS, which MTS sells.


I installed an old computer in my home network and installed Ubuntu Server 16.04.6 LTS 32-bit on it. By default, I also installed SSH, for access from my other computer.
I changed file /etc/network/interfaces:
```
employee@wifi-server:/etc/squid$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*
It changed only the addresses from 10.x.x.x to the addresses of my subnet 192.168.0.x. It is very possible that I made a mistake already at this step, since I do not understand which addresses here should be assigned.
Then I check ports sudo ss -lnptu | grep: 3128
# The loopback network interface
#auto lo
#iface lo inet loopback

# The primary network interface
#auto enp5s2
#iface enp5s2 inet dhcp


auto enp5s2
iface enp5s2 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        dns-nameservers 8.8.8.8
```

I installed the program as in the article:
```
apt-get install git fakeroot build-essential devscripts
apt-cache policy squid3
apt-get build-dep squid3
apt-get build-dep libecap2
apt-get install libssl-dev libgnutls28-dev
```

Next, I installed Squid from the repository version 3.6.12, because I did not want to suffer with the build of the source (I do not really understand this).
I did not correct the error as in the article (messages in the logs: SECURITY ALERT: Host header detected on local = ...: 443 remote = ...: *).

Output systemctl status -l squid:
```
employee@wifi-server:/etc/squid$ systemctl status -l squid
&#9679; squid.service - LSB: Squid HTTP Proxy version 3.x
   Loaded: loaded (/etc/init.d/squid; bad; vendor preset: enabled)
   Active: active (running) since &#1063;&#1090; 2019-03-21 20:24:11 +05; 1h 22min ago
     Docs: man:systemd-sysv-generator(8)
   CGroup: /system.slice/squid.service
           &#9500;&#9472;2938 /usr/sbin/squid -YC -f /etc/squid/squid.conf
           &#9500;&#9472;2944 (squid-1) -YC -f /etc/squid/squid.conf
           &#9492;&#9472;2945 (logfile-daemon) /var/log/squid/access.log

&#1084;&#1072;&#1088; 21 20:24:10 wifi-server systemd[1]: Starting LSB: Squid HTTP Proxy version 3.x...
&#1084;&#1072;&#1088; 21 20:24:10 wifi-server squid[2895]:  * Starting Squid HTTP Proxy squid
&#1084;&#1072;&#1088; 21 20:24:11 wifi-server squid[2895]:    ...done.
&#1084;&#1072;&#1088; 21 20:24:11 wifi-server systemd[1]: Started LSB: Squid HTTP Proxy version 3.x.
&#1084;&#1072;&#1088; 21 20:24:11 wifi-server squid[2938]: Squid Parent: will start 1 kids
&#1084;&#1072;&#1088; 21 20:24:11 wifi-server squid[2938]: Squid Parent: (squid-1) process 2944 started
&#1084;&#1072;&#1088; 21 20:24:34 wifi-server systemd[1]: Started LSB: Squid HTTP Proxy version 3.x.
&#1084;&#1072;&#1088; 21 20:43:11 wifi-server systemd[1]: Started LSB: Squid HTTP Proxy version 3.x.
&#1084;&#1072;&#1088; 21 21:21:33 wifi-server systemd[1]: Started LSB: Squid HTTP Proxy version 3.x.
```

Created the configuration file /etc/squid/squid.conf:
```
employee@wifi-server:/etc/squid$ cat squid.conf
acl localnet src 192.168.0.0/24
acl SSL_ports port 443
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl CONNECT method CONNECT

dns_nameservers 10.66.66.1
http_access deny !Safe_ports

http_access deny CONNECT !SSL_ports

http_access allow localhost manager
http_access deny manager

http_access allow localnet
http_access allow localhost
http_access deny all

#http_port 3128
#&#1087;&#1088;&#1086;&#1079;&#1088;&#1072;&#1095;&#1085;&#1099;&#1081; &#1087;&#1086;&#1088;&#1090; &#1091;&#1082;&#1072;&#1079;&#1099;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1086;&#1087;&#1094;&#1080;&#1077;&#1081; intercept
http_port 192.168.0.10:3128 intercept options=NO_SSLv3:NO_SSLv2

#&#1090;&#1072;&#1082;&#1078;&#1077; &#1085;&#1091;&#1078;&#1085;&#1086; &#1091;&#1082;&#1072;&#1079;&#1072;&#1090;&#1100; &#1085;&#1077;&#1087;&#1088;&#1086;&#1079;&#1088;&#1072;&#1095;&#1085;&#1099;&#1081; &#1087;&#1086;&#1088;&#1090;, &#1080;&#1073;&#1086; &#1077;&#1089;&#1083;&#1080; &#1079;&#1072;&#1093;&#1086;&#1090;&#1080;&#1090;&#1077; &#1074;&#1088;&#1091;&#1095;&#1085;&#1091;&#1102; &#1091;&#1082;&#1072;&#1079;&#1072;&#1090;&#1100; &#1072;&#1076;&#1088;&#1077;&#1089;
#&#1087;&#1088;&#1086;&#1082;&#1089;&#1080; &#1074; &#1073;&#1088;&#1072;&#1091;&#1079;&#1077;&#1088;&#1077;, &#1091;&#1082;&#1072;&#1079;&#1072;&#1074; &#1087;&#1088;&#1086;&#1079;&#1088;&#1072;&#1095;&#1085;&#1099;&#1081; &#1087;&#1086;&#1088;&#1090;, &#1074;&#1099; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1077; &#1086;&#1096;&#1080;&#1073;&#1082;&#1091; &#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1072;, &#1087;&#1086;&#1101;&#1090;&#1086;&#1084;&#1091; &#1085;&#1091;&#1078;&#1085;&#1086;
#&#1091;&#1082;&#1072;&#1079;&#1099;&#1074;&#1072;&#1090;&#1100; &#1085;&#1077;&#1087;&#1088;&#1086;&#1079;&#1088;&#1072;&#1095;&#1085;&#1099;&#1081; &#1087;&#1086;&#1088;&#1090; &#1074; &#1073;&#1088;&#1072;&#1091;&#1079;&#1077;&#1088;&#1077;, &#1077;&#1089;&#1083;&#1080; &#1082;&#1086;&#1085;&#1077;&#1095;&#1085;&#1086; &#1090;&#1072;&#1082;&#1086;&#1077; &#1078;&#1077;&#1083;&#1072;&#1085;&#1080;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090;, &#1082; &#1090;&#1086;&#1084;&#1091; &#1078;&#1077; &#1074; &#1083;&#1086;&#1075;&#1072;&#1093; #&#1089;&#1099;&#1087;&#1103;&#1090;&#1089;&#1103; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080; &#1086; &#1090;&#1086;&#1084;, &#1095;&#1090;&#1086; &#1085;&#1077;&#1087;&#1088;&#1086;&#1093;&#1088;&#1072;&#1095;&#1085;&#1099;&#1081; &#1087;&#1086;&#1088;&#1090; &#1085;&#1077; &#1091;&#1082;&#1072;&#1079;&#1072;&#1085;=)
http_port 192.168.0.10:3130 options=NO_SSLv3:NO_SSLv2

#&#1080; &#1085;&#1072;&#1082;&#1086;&#1085;&#1077;&#1094;, &#1091;&#1082;&#1072;&#1079;&#1099;&#1074;&#1072;&#1077;&#1084; HTTPS &#1087;&#1086;&#1088;&#1090; &#1089; &#1085;&#1091;&#1078;&#1085;&#1099;&#1084;&#1080; &#1086;&#1087;&#1094;&#1080;&#1103;&#1084;&#1080;
https_port 192.168.0.10:3129 intercept ssl-bump options=ALL:NO_SSLv3:NO_SSLv2 connection-auth=off cert=/etc/squid/squidCA.pem

always_direct allow all
sslproxy_cert_error allow all
sslproxy_flags DONT_VERIFY_PEER

#&#1091;&#1082;&#1072;&#1078;&#1077;&#1084; &#1087;&#1088;&#1072;&#1074;&#1080;&#1083;&#1086; &#1089;&#1086; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1084; &#1073;&#1083;&#1086;&#1082;&#1080;&#1088;&#1091;&#1077;&#1084;&#1099;&#1093; &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1086;&#1074; (&#1074; &#1092;&#1072;&#1081;&#1083;&#1077; &#1076;&#1086;&#1084;&#1077;&#1085;&#1099; &#1074;&#1080;&#1076;&#1072; .domain.com)
acl blocked ssl::server_name  "/etc/squid/blocked_https.txt"
acl step1 at_step SslBump1
ssl_bump peek step1

#&#1090;&#1077;&#1088;&#1084;&#1080;&#1085;&#1080;&#1088;&#1091;&#1077;&#1084; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077;, &#1077;&#1089;&#1083;&#1080; &#1082;&#1083;&#1080;&#1077;&#1085;&#1090; &#1079;&#1072;&#1093;&#1086;&#1076;&#1080;&#1090; &#1085;&#1072; &#1079;&#1072;&#1087;&#1088;&#1077;&#1097;&#1077;&#1085;&#1085;&#1099;&#1081; &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;
ssl_bump terminate blocked
ssl_bump splice all

sslcrtd_program /usr/lib/squid/ssl_crtd -s /var/lib/ssl_db -M 4MB

coredump_dir /var/spool/squid
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0     0%      0
refresh_pattern .               0       20%     4320
cache_dir aufs /var/spool/squid 2048 49 256
maximum_object_size 61440 KB
minimum_object_size 3 KB

cache_swap_low 90
cache_swap_high 95
maximum_object_size_in_memory 512 KB
memory_replacement_policy lru

#logfile_rotate 31
logfile_daemon /usr/lib/squid/log_db_daemon
access_log daemon:/127.0.0.1:3306/base/table/user/password squid
```

It changed only the addresses from 10.x.x.x to the addresses of my subnet 192.168.0.x. **It is very possible that I made a mistake already at this step**, since I do not understand which addresses here should be assigned.
Then I check ports sudo ss -lnptu | grep: 3128
The terminal does not output anything to the following commands:
```
sudo ss -lnptu | grep :3129
sudo ss -lnptu | grep :3130
```

[B]Do I understand correctly that these ports are not open? Should they be open?

Dear forum users, I ask your criticism of my mistakes and explanations of how to fix it, since I do not understand everything in this operating system.
Is this equipment enough? Have I assigned the correct ports? Why are some ports closed? Was it necessary to correct the error SECURITY ALERT?[/B]

Or, please forward me to another place to ask this question.
Thank.

---

