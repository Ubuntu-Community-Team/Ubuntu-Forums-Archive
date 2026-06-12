---
title: "VNC, Static Ip, port forwarding Help needed."
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by yogo on 2008-05-23
After reading through many post and threads here and elsewhere, I am confused and not sure what I need to do to get this working.

This post is very close to exactly what I am trying to do.

[B]static ip and port forwarding bitorrent ubuntu
[http://ubuntuforums.org/showthread.php?t=800603](http://ubuntuforums.org/showthread.php?t=800603)

[/B][SIZE=1]I have assigned a static ip address for Ubuntu as seen here.
sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

iface eth0 inet static
address 192.168.11.100
netmask 255.255.255.0
gateway 192.168.11.1

auto eth0


However my router will not let me set a static as well. I have a Buffalo WHR-HP- G54

I have read all the tutorials at port forward.com  It would seem that it (port 5900) is still being blocked by something, Firestarter?, my router, am not sure, but when I use the VNC test page, it always fails a connection.

I probed port 5900 and it is in stealth mode.

and last but not least, I found this page which hav many cli commands, I have tried everything on [this page.]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html")
[/SIZE]**[SIZE=2][COLOR=Black][Howto: Ubuntu Linux convert DHCP network configuration to static IP configuration]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html")[/COLOR][/SIZE]**



Need a lot of help, Thanks

---

### Post by yogo on 2008-05-23
netstat -nat
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 192.168.11.2:54322      74.125.47.18:80         ESTABLISHED
tcp        0      0 192.168.11.2:54317      74.125.47.18:80         ESTABLISHED
tcp        1      0 192.168.11.2:54321      74.125.47.18:80         CLOSE_WAIT 
tcp        0      0 192.168.11.2:54320      74.125.47.18:80         ESTABLISHED
tcp        0      0 192.168.11.2:37825      74.125.45.104:80        ESTABLISHED
tcp        0      0 192.168.11.2:54323      74.125.47.18:80         ESTABLISHED
tcp        1      0 192.168.11.2:54319      74.125.47.18:80         CLOSE_WAIT 
tcp        0      0 192.168.11.2:54326      74.125.47.18:80         ESTABLISHED
tcp        1      0 192.168.11.2:54318      74.125.47.18:80         CLOSE_WAIT 
tcp        1      0 192.168.11.2:50111      74.125.47.189:80        CLOSE_WAIT 
tcp6       0      0 :::5900                 :::*                    LISTEN 

Now I would assume the last line means port 5900 is open?

---

### Post by yogo on 2008-05-23
Ok I got it so I can see another computer in my household, will it be hard to connect to my mothers pc if she is behind a router? In other words will she also have to port forward on their router?

TIA

---

