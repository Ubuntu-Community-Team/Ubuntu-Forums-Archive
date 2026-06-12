---
title: "OpenVPN - Joining Network"
date: 2017-02-04
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2017-02-04
Ubuntu 16:04 Laptop
Ubuntu 16:04 Raspberry Pi (Remote machine)
Normal connection via ssh with secure key

Folks,

I am having problems with what should be a simple connection.

My remote device is part of a 192.168.1.0 network with the router at 254

I have connected using openvpn using 192.168.2.27 as server (remote device) and 192.168.2.26 as client. Connects fine and able to ping. Network manager on my client shows the VPN IP address as 192.168.2.26  --  So far so good.

Am using tcp protocol (only as intention was to access web server) so openvpn has remote config file to include proto tcp-server and the client has proto tcp-client.

Reading up on openvpn I have enabled forwarding correctly and added  push "route 192.168.1.0 255.255.255.0" to server config file.

I have also added to the Linux route using the following;

```
route add -net 192.168.2.0/24 gw 192.168.1.254
```

and netstat -r shows as follows;

```
Kernel IP routing tableDestination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         dsldevice.lan   0.0.0.0         UG        0 0          0 wlx74da382e0a3f
link-local      *               255.255.0.0     U         0 0          0 wlx74da382e0a3f
192.168.1.0     *               255.255.255.0   U         0 0          0 wlx74da382e0a3f
192.168.2.0     dsldevice.lan   255.255.255.0   UG        0 0          0 wlx74da382e0a3f
```

Cannot ping anything in remote network and, if using my local machine I access an internet web page the connection shows via my normal connection and not via the VPN address as shown by network-manager.

traceroute seems to only return asterisks nowadays so is of little help.

Netstat -l doesn't even suggest the tcp connection is there;

```
netstat -lActive Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:8200                  *:*                     LISTEN     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 *:5901                  *:*                     LISTEN     
tcp        0      0 *:x11-1                 *:*                     LISTEN     
tcp        0      0 127.0.1.1:domain        *:*                     LISTEN     
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp6       0      0 [::]:netbios-ssn        [::]:*                  LISTEN     
tcp6       0      0 [::]:http               [::]:*                  LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
tcp6       0      0 [::]:3128               [::]:*                  LISTEN     
tcp6       0      0 [::]:https              [::]:*                  LISTEN     
tcp6       0      0 [::]:microsoft-ds       [::]:*                  LISTEN     
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:50757                 *:*                                
udp        0      0 PiggyPi.lan:51829       *:*                                
udp        0      0 *:ipp                   *:*                                
udp        0      0 192.168.2.27:ntp        *:*                                
udp        0      0 PiggyPi.lan:ntp         *:*                                
udp        0      0 localhost:ntp           *:*                                
udp        0      0 *:ntp                   *:*                                
udp        0      0 192.168.1.25:netbios-ns *:*                                
udp        0      0 PiggyPi.lan:netbios-ns  *:*                                
udp        0      0 *:netbios-ns            *:*                                
udp        0      0 192.168.1.2:netbios-dgm *:*                                
udp        0      0 PiggyPi.lan:netbios-dgm *:*                                
udp        0      0 *:netbios-dgm           *:*                                
udp        0      0 *:mdns                  *:*                                
udp        0      0 239.255.255.250:1900    *:*                                
udp        0      0 *:52102                 *:*                                
udp        0      0 192.168.2.27:54749      *:*                                
udp        0      0 127.0.1.1:domain        *:*                                
udp6       0      0 fe80::76da:38ff:fe2:ntp [::]:*                             
udp6       0      0 ip6-localhost:ntp       [::]:*                             
udp6       0      0 [::]:ntp                [::]:*                             
udp6       0      0 [::]:mdns               [::]:*                             
udp6       0      0 [::]:44878              [::]:*                             
udp6       0      0 [::]:36304              [::]:*                             
raw        0      0 *:icmp                  *:*                     7          
raw6       0      0 [::]:ipv6-icmp          [::]:*                  7          
raw6       0      0 [::]:ipv6-icmp          [::]:*
```



Any suggestions appreciated.

Geffers

---

