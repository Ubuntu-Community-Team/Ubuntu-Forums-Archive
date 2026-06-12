---
title: "openvpn client setup in terminal"
date: 2017-08-28
forum: Networking &amp; Wireless
---

### Post by p0p2 on 2017-08-28
The task that i'm trying to accomplish is simple: configure my ubuntu  client  so that i can connect to internet via openvpn file by wifi.

  The connection with openvpn server is established, after "sudo openvpn file.ovpn", i get in output "Initialization Sequence Completed"
  But the internet connection isn't functioning. I can't access the web via GUI(firefox), nor ping.

```

user@computer:~$ ifconfig     
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:b2:bb:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:16057 (16.0 KB)  TX bytes:16057 (16.0 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.34  P-t-P:10.8.0.33  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1191 (1.1 KB)  TX bytes:4540 (4.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:4d:70:68:26  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:4dff:fe70:6826/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30520 (30.5 KB)  TX bytes:47304 (47.3 KB)
          Interrupt:21 Memory:ff5e0000-ff5f0000 

user@computer:~$
```

Here is what i tried,but after each command i still couldn't access internet:

```

sudo sysctl -w net.ipv4.ip_forward=1 

sudo route add -net 192.168.0.0 netmask 255.255.255.0 gw 10.8.0.34

sudo iptables -t nat -A POSTROUTING ! -o lo -j MASQUERADE 

sudo iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o tun0 -j MASQUERADE                                                           

sudo route add -net 192.168.0.0 netmask 255.255.255.255 gw 10.8.0.34
```

Also i removed ufw firewall.

---

### Post by SeijiSensei on 2017-08-29
You need to have a route that connects to the public IP of the server at the other end of the connection.  If you push all outbound traffic through the tunnel, then your machine cannot see the server.

Suppose the server is at 172.16.1.1 and your local router is 192.168.0.1.  Then you need this route:
```
sudo ip route add 172.16.1.1 via 192.168.0.1
```

---

### Post by p0p2 on 2017-08-29
Thanks for your reply Seiji-kun,here is what i tried,inspired from your command. I may not have chosen the right ip so i give the complete output:
```

user@computer:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:b2:bb:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1399825 (1.3 MB)  TX bytes:1399825 (1.3 MB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.106  P-t-P:10.8.0.105  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:15784 (15.7 KB)  TX bytes:1016 (1.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:4d:70:68:26  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:4dff:fe70:6826/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11783 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8581903 (8.5 MB)  TX bytes:1913342 (1.9 MB)
          Interrupt:21 Memory:ff5e0000-ff5f0000 

user@computer:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.8.0.105      128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 wlan0
10.8.0.1        10.8.0.105      255.255.255.255 UGH   0      0        0 tun0
10.8.0.105      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
128.0.0.0       10.8.0.105      128.0.0.0       UG    0      0        0 tun0
142.4.206.228   192.168.0.254   255.255.255.255 UGH   0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
user@computer:~$ sudo ip route add 10.8.0.106 via 192.168.0.12
[sudo] password for user: 
user@computer:~$ ping -c 1 google.com
ping: unknown host google.com
user@computer:~$ sudo ip route add 10.8.0.105 via 192.168.0.12
RTNETLINK answers: File exists
user@computer:~$ ping -c 1 google.com
ping: unknown host google.com
user@computer:~$ sudo ip route add 128.0.0.0 via 192.168.0.12
user@computer:~$ ping -c 1 google.com
ping: unknown host google.com
user@computer:~$ 


```

---

### Post by SeijiSensei on 2017-08-30
You have two default routes.

```
0.0.0.0         10.8.0.105      128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 wlan0

```

Delete the second one so all the traffic goes out tun0.  Also the first route should have 0.0.0.0 as its netmask like the second one does.

I'm guessing 142.4.206.228 is the address of the upstream VPN server?

---

### Post by p0p2 on 2017-08-31
Thanks for your patience.

What you are suggesting me to do doesn't look good i think,because:

The network come from wlan0 so if i delete wlan0, tun0 which is a virtual network created by openvpn is then disconnected, theorically.

Plus,i don't know how to proceed according to your method,which command(s) should i enter?

Also, i don't know if 142.4.206.228 is the address of the upstream VPN server.

---

