---
title: "openvpn ubuntu 12.04 cannot access port 1194"
date: 2014-07-09
forum: Networking &amp; Wireless
---

### Post by mantale1 on 2014-07-09
Hi All,

   Please bear with me, as I'm new to using the openvpn software and networking in general. I'm not quite understanding how to get certain ports open for listening. I have the latest version of openvpn installed and configured on my machine according to this guide : [http://madisonlinux.org/InstallingOpenVPNOnUbuntu10.04?action=AttachFile&do=get&target=install_open_vpn_on_ubuntu.pdf](http://madisonlinux.org/InstallingOpenVPNOnUbuntu10.04?action=AttachFile&do=get&target=install_open_vpn_on_ubuntu.pdf), which seems to be a fairly standard guide to setting up a bridging VPN server.

 When I try to check to see if certain ports are open from sites like [http://canyouseeme.org/](http://canyouseeme.org/) I get messages (for some ports) saying the ports are blocked. I have opened up the firewall on my router and forwarded several different ports to my machine's local IP. The ports I have forwarded, specifically, are 80, 443, 943 and 1194. For example, from canyouseeme.org, port 80, 443 and 1194 get timeout errors but port 943 (which is the port openvpn uses as a login page, either for admins or users) is open and not blocked.

 When I run the command ```
sudo netstat -antlp
``` this is the output : 
```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.0.36:53         0.0.0.0:*               LISTEN      1690/named      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1690/named      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1067/cupsd      
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1888/master     
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      1690/named      
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      20055/apache2   
tcp        0      0 0.0.0.0:1723            0.0.0.0:*               LISTEN      1903/pptpd      
tcp        0      0 127.0.0.1:904           0.0.0.0:*               LISTEN      2591/python     
tcp        0      0 127.0.0.1:905           0.0.0.0:*               LISTEN      2591/python     
tcp        0      0 0.0.0.0:1194            0.0.0.0:*               LISTEN      19961/openvpn   
tcp        0      0 127.0.0.1:906           0.0.0.0:*               LISTEN      2591/python     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1742/mysqld     
tcp        0      0 127.0.0.1:907           0.0.0.0:*               LISTEN      2591/python     
tcp        0      0 127.0.0.1:908           0.0.0.0:*               LISTEN      2591/python     
tcp        0      0 127.0.0.1:909           0.0.0.0:*               LISTEN      2591/python     
tcp        0      0 192.168.0.36:943        0.0.0.0:*               LISTEN      2591/python     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      20055/apache2   
tcp        1      0 192.168.0.36:44156      4.27.6.135:80           CLOSE_WAIT  3263/plugin-contain
tcp        0      0 192.168.0.36:34410      198.252.206.149:443     ESTABLISHED 3031/firefox    
tcp        0      0 192.168.0.36:52172      74.125.225.156:80       ESTABLISHED 3031/firefox    
tcp        0      0 192.168.0.36:39483      23.63.227.123:80        ESTABLISHED 3031/firefox    
tcp        0      0 192.168.0.36:39482      23.63.227.123:80        ESTABLISHED 3031/firefox    
tcp        0      0 192.168.0.36:42954      74.125.225.153:80       ESTABLISHED 3031/firefox    
tcp        1      0 192.168.0.36:59033      91.189.89.144:80        CLOSE_WAIT  2990/ubuntu-geoip-p
tcp        0      0 192.168.0.36:39284      172.226.23.198:80       ESTABLISHED 3031/firefox    
tcp        0      0 192.168.0.36:37469      198.252.206.149:443     ESTABLISHED 3031/firefox    
tcp        0      0 192.168.0.36:55957      74.125.225.143:443      ESTABLISHED 3031/firefox    
tcp        0      0 192.168.0.36:46766      172.226.23.198:443      ESTABLISHED 3031/firefox    
tcp        1      0 192.168.0.36:40295      4.27.6.252:80           CLOSE_WAIT  3263/plugin-contain
tcp        0      0 192.168.0.36:54724      173.252.113.2:443       ESTABLISHED 3031/firefox    
tcp        0      0 192.168.0.36:58580      108.168.151.6:80        ESTABLISHED 3031/firefox    
tcp        0      0 192.168.0.36:39481      23.63.227.123:80        ESTABLISHED 3031/firefox    
tcp        0      0 192.168.0.36:44623      199.16.156.201:443      ESTABLISHED 3031/firefox    
tcp        0      0 192.168.0.36:54741      23.74.9.73:80           ESTABLISHED 3031/firefox    
tcp        1      0 192.168.0.36:58041      4.23.55.147:80          CLOSE_WAIT  3263/plugin-contain
tcp        0      0 192.168.0.36:43615      91.189.94.12:80         TIME_WAIT   -               
tcp        0      0 192.168.0.36:33713      198.252.206.149:443     ESTABLISHED 3031/firefox    
tcp        0     77 192.168.0.36:37651      173.194.121.39:443      LAST_ACK    -               
tcp        0      0 192.168.0.36:39480      23.63.227.123:80        ESTABLISHED 3031/firefox    
tcp        0      0 192.168.0.36:41628      66.220.152.19:443       ESTABLISHED 3031/firefox    
tcp        0      0 192.168.0.36:39942      23.74.8.168:443         ESTABLISHED 3031/firefox    
tcp        0      0 192.168.0.36:33912      198.252.206.149:443     ESTABLISHED 3031/firefox    
tcp6       0      0 :::53                   :::*                    LISTEN      1690/named      
tcp6       0      0 ::1:631                 :::*                    LISTEN      1067/cupsd      
tcp6       0      0 :::25                   :::*                    LISTEN      1888/master     
tcp6       0      0 ::1:953                 :::*                    LISTEN      1690/named 


```

What I'm not sure about is the local IPs. As one can see, port 943 is listening from this socket (correct terminology?) 192.168.0.36:943, but 1194 is on 0.0.0.0:1194. On my router's set-up software I have port 1194 being forwarded to 192.168.0.36:1194. Is this why canyouseeme.org cannot ping (?) port 1194? If this is the problem, how would I change the openvpn software to listen to 192.168.0.36:1194?

Any help would be greatly appreciated.

---

### Post by The Cog on 2014-07-09
I haven't looked at that guide you linked, but OpenVPN normally talks UDP not TCP protocol. So I doubt if canyouseeme will find it. So see if your PC is even listening on a UDP port try the command
```
netstat -lnup
```
Equally, you need to forward UDP to the server with your router, not TCP.

---

### Post by mantale1 on 2014-07-09
Hey @The Cog, thanks for the response. After messing around and doing some reading I modified a few things.

First, I used ufw to open up firewall restrictions to those ports.

The other thing I did was in the openvpn configuration file (for me server.conf) I uncommmented 
proto tcp
and also left
proto udp 
uncommented as well.

When I execute ```
sudo netstat -anulp
``` I get
```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           800/avahi-daemon: r
udp        0      0 0.0.0.0:47325           0.0.0.0:*                           800/avahi-daemon: r
udp        0      0 192.168.0.36:53         0.0.0.0:*                           1719/named      
udp        0      0 127.0.0.1:53            0.0.0.0:*                           1719/named      
udp        0      0 192.168.0.36:1194       0.0.0.0:*                           6708/openvpn    
udp6       0      0 :::5353                 :::*                                800/avahi-daemon: r
udp6       0      0 :::46916                :::*                                800/avahi-daemon: r
udp6       0      0 :::53                   :::*                                1719/named   


```

Also from my router I have both UDP and TCP protocols forwarding to my server's local ip and the appropriate ports.

the problem now is that when I arrive at the web interface using the server's external ip address, I can log in, but then the software gets stuck on "locating new server" and never gives confirmation that is had connected.

---

### Post by The Cog on 2014-07-10
I would advice against using tcp for openvpn. The UDP performance is likely to be better. 

I don't know about a web interface for OpenVPN.

There is a log file in (normally in /etc/openvpn I think) that may give some indication what the problem is.

---

