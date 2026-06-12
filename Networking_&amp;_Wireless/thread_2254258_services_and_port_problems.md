---
title: "services and port problems"
date: 2014-11-25
forum: Networking &amp; Wireless
---

### Post by Forbees on 2014-11-25
recently had to reconfigure my media server to VNC through SSH since my log files were going crazy with a botnet trying to log in...

after getting SSH set up, and successfully tunneling in, i removed port 5900 from my routers forwarding list and rebooted. (there were a few updates asking me to reboot for)

since rebooting, i can't get plex media server to reach outside the computer on port 32400, i can't get to my transmission webui on port 9091, mumble server on port 64738, and i can't get in my terraria server on port 7777

the computer is in another city, but i'm being told that plex can't be accessed on the local network there too....

i can still SSH in, and tunnel VNC in.... and through VNC i can confirm that the transmission and plex webui are working fine on the localhost...... so why won't these services connect outside the local host anymore?

i can also confirm through VNC that the port forwarding is all correct on the router there too
```
sudo netstat -tulpn                          Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:9091            0.0.0.0:*               LISTEN      1940/transmission-g
tcp        0      0 127.0.0.1:6502          0.0.0.0:*               LISTEN      2926/murmurd
tcp        0      0 0.0.0.0:36809           0.0.0.0:*               LISTEN      2265/Plex Plug-in [
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN      1936/vino-server
tcp        0      0 0.0.0.0:32400           0.0.0.0:*               LISTEN      2250/Plex Media Ser
tcp        0      0 0.0.0.0:32401           0.0.0.0:*               LISTEN      2250/Plex Media Ser
tcp        0      0 0.0.0.0:32469           0.0.0.0:*               LISTEN      2317/Plex DLNA Serv
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      2107/dnsmasq
tcp        0      0 0.0.0.0:51413           0.0.0.0:*               LISTEN      1940/transmission-g
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1143/sshd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      569/cupsd
tcp        0      0 0.0.0.0:48445           0.0.0.0:*               LISTEN      2342/Plex Plug-in [
tcp        0      0 0.0.0.0:1855            0.0.0.0:*               LISTEN      2317/Plex DLNA Serv
tcp6       0      0 :::5800                 :::*                    LISTEN      1936/vino-server
tcp6       0      0 :::5900                 :::*                    LISTEN      1936/vino-server
tcp6       0      0 :::51413                :::*                    LISTEN      1940/transmission-g
tcp6       0      0 :::22                   :::*                    LISTEN      1143/sshd
tcp6       0      0 :::64738                :::*                    LISTEN      2926/murmurd
udp        0      0 192.168.1.4:47483       0.0.0.0:*                           2250/Plex Media Ser
udp        0      0 0.0.0.0:35945           0.0.0.0:*                           1940/transmission-g
udp        0      0 0.0.0.0:52569           0.0.0.0:*                           1940/transmission-g
udp        0      0 0.0.0.0:32410           0.0.0.0:*                           2250/Plex Media Ser
udp        0      0 0.0.0.0:32413           0.0.0.0:*                           2250/Plex Media Ser
udp        0      0 0.0.0.0:32414           0.0.0.0:*                           2250/Plex Media Ser
udp        0      0 0.0.0.0:40946           0.0.0.0:*                           575/avahi-daemon: r
udp        0      0 127.0.1.1:53            0.0.0.0:*                           2107/dnsmasq
udp        0      0 0.0.0.0:68              0.0.0.0:*                           2071/dhclient
udp        0      0 0.0.0.0:45426           0.0.0.0:*                           2317/Plex DLNA Serv
udp        0      0 0.0.0.0:631             0.0.0.0:*                           1050/cups-browsed
udp        0      0 0.0.0.0:58175           0.0.0.0:*                           2071/dhclient
udp        0      0 0.0.0.0:58266           0.0.0.0:*                           2317/Plex DLNA Serv
udp        0      0 192.168.1.4:37930       0.0.0.0:*                           2250/Plex Media Ser
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           2658/manage
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           575/avahi-daemon: r
udp        0      0 127.0.0.1:38225         0.0.0.0:*                           2250/Plex Media Ser
udp        0      0 0.0.0.0:50845           0.0.0.0:*                           2317/Plex DLNA Serv
udp        0      0 0.0.0.0:1900            0.0.0.0:*                           2317/Plex DLNA Serv
udp        0      0 0.0.0.0:2015            0.0.0.0:*                           2317/Plex DLNA Serv
udp        0      0 0.0.0.0:51413           0.0.0.0:*                           1940/transmission-g
udp        0      0 127.0.0.1:47373         0.0.0.0:*                           2250/Plex Media Ser
udp6       0      0 :::64738                :::*                                2926/murmurd
udp6       0      0 :::57849                :::*                                575/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                575/avahi-daemon: r
udp6       0      0 :::34560                :::*                                2071/dhclient

```

you'll see the ports i'm trying to access these services through are set to listen.... so i'm at a loss here

---

### Post by Forbees on 2014-11-25
actually..... it's probably related to UFW....... so how do i tell UFW to allow these services?

---

### Post by Forbees on 2014-11-25
sigh.... i'm an R-Tard. it was UFW. fixed it

---

