---
title: "local network server over Wi-Fi via ap hotspot"
date: 2017-01-13
forum: Networking &amp; Wireless
---

### Post by a.dusty.trail on 2017-01-13
I'm running ubuntu mate 16.04.1 and I would like to run a apache2 Web server for a local Wi-Fi network.
(There will be other servers services running later)
I can create a hotspot with the network manager but cannot connect to the web server running on the same device.

What an I missing.
(There is no connection to the internet this is a local network only)
(If it helps think of it as being a standalone local router with various server services )

---

### Post by geeksmith on 2017-01-13
So, you can't hit the web page from the server itself? If you can't get that far, I wouldn't bring a Wi-Fi hotspot into the mix yet. Get the web server working on the local server, then add to it from there.

Have you tried this walk-through? [https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html)

---

### Post by a.dusty.trail on 2017-01-13
Yes the server is working fine I can connect to a network router via Wi-Fi and log in and do everything remotely.
But I can't make it work as a hotspot.
I can't connect to the web server without using a router.

Here is a netstat if it helps
sudo netstat -ltnp 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      859/mysqld      
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN      1238/x11vnc     
tcp        0      0 10.42.0.1:53            0.0.0.0:*               LISTEN      1018/dnsmasq    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      839/sshd        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      679/cupsd       
tcp6       0      0 :::6600                 :::*                    LISTEN      1/init          
tcp6       0      0 :::5900                 :::*                    LISTEN      1238/x11vnc     
tcp6       0      0 :::80                   :::*                    LISTEN      1184/apache2    
tcp6       0      0 :::21                   :::*                    LISTEN      847/vsftpd      
tcp6       0      0 :::22                   :::*                    LISTEN      839/sshd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      679/cupsd

---

### Post by SeijiSensei on 2017-01-13
It might be a routing issue.  Does the hotspot give out addresses to its clients in the same subnet as the server?  Post the results of "ifconfig" and "route -n" on the server inside [noparse]```

```[/noparse] tags when the hotspot is running.  Run the same commands on a client machine connected to the hotspot.

---

### Post by a.dusty.trail on 2017-01-14
ifconfig
enxb827ebc51f38 Link encap:Ethernet  HWaddr b8:27:eb:c5:1f:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:47969 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11986 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2213454 (2.2 MB)  TX bytes:8465407 (8.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:91480 (91.4 KB)  TX bytes:91480 (91.4 KB)

wlan0     Link encap:Ethernet  HWaddr b8:27:eb:90:4a:6d  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ba27:ebff:fe90:4a6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:460 errors:0 dropped:318 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:79212 (79.2 KB)  TX bytes:23623 (23.6 KB)

 route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.0.0       0.0.0.0         255.255.255.0   U     600    0        0 wlan0

My client is restricted to a few Android devices and a Windows desktop do I can't run the commands there but I can verify that they are getting up a addresses from the hotspot correctly
Ie 10.42.0.194

The hot spot is the same system that is running the servers. The issue is defiantly routing but I have been unable to find out how to route the network services to the hotspot on the same machine.
(It might help to think of it as trying to use one machine to be a local lan router and hosting various network services at the same time all in one)

---

### Post by SeijiSensei on 2017-01-14
I take it the web server is running on the same machine as the hotspot?

What happens when you open a browser on a client and point it to [http://10.42.0.1/](http://10.42.0.1/) ?

In Windows, you can display the routing table by opening a terminal and typing the command "route print".

---

### Post by a.dusty.trail on 2017-01-14
I finally found out what was needed.
edit the file /etc/sysctl.conf and add the following line to the bottom of the file:

net.ipv4.ip_forward=1

Now it forwards some services running on the machine to the hotspot.
What's working
X11vnc, mod, ftp
What's not working
Apache2 (hosting owncloud,mediawiki)

Update
Now Windows cannot connect to anything
Android tablet connecting to everything but apache
(The only thing that occurred between Windows working or not, was the server was rebooted)
Update 2
Next reboot everything is working every where including apache2
I'm still stumped

---

