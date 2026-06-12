---
title: "Xubuntu 16.04 openvpn and private internet access (PIA) not working"
date: 2016-11-23
forum: Networking &amp; Wireless
---

### Post by rob-from-canada on 2016-11-23
Hi, I tried troubleshooting the issue with PIA support the other night and was not able to get it working. I am able to connect to a PIA server, but can't reach any other destinations. 

My guesses at this point are firewall, or routing, or maybe openvpn config issue. 

PIA has me create and store ovpn files in my home directory. 
```
rob@galifrey:~/.ovpn$ ls
ca.rsa.2048.crt    CA Toronto.ovpn    crl.rsa.2048.pem
```

I'm trying to setup the Toronto connection... this is what the ovpn file looks like:
```
rob@galifrey:~/.ovpn$ cat CA\ Toronto.ovpn 
client
dev tun
proto udp
remote ca-toronto.privateinternetaccess.com 1198
resolv-retry infinite
nobind
persist-key
persist-tun
cipher aes-128-cbc
auth sha1
tls-client
remote-cert-tls server
auth-user-pass
comp-lzo
verb 1
reneg-sec 0
crl-verify crl.rsa.2048.pem
ca ca.rsa.2048.crt
disable-occ
```

When I'm connected to the VPN, this is what my routing looks like:
```
rob@galifrey:~/.ovpn$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.7.10.5       0.0.0.0         UG        0 0          0 tun0
0.0.0.0         192.168.100.254 0.0.0.0         UG        0 0          0 wlp2s0
10.7.10.1       10.7.10.5       255.255.255.255 UGH       0 0          0 tun0
10.7.10.5       0.0.0.0         255.255.255.255 UH        0 0          0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlp2s0
172.98.67.58    192.168.100.254 255.255.255.255 UGH       0 0          0 wlp2s0
192.168.100.0   0.0.0.0         255.255.255.0   U         0 0          0 wlp2s0

```

When I'm not connected, this is what it looks like: 
```
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.100.254 0.0.0.0         UG        0 0          0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlp2s0
192.168.100.0   0.0.0.0         255.255.255.0   U         0 0          0 wlp2s0
``` 

This is what my firewall rules look like:
```
rob@galifrey:~/.ovpn$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

Finallly, here is ifconfig on /dev/tun, first when off, then when connected to VPN:
```
rob@galifrey:~/.ovpn$ sudo ifconfig tun0
tun0: error fetching interface information: Device not found
```
```
rob@galifrey:~/.ovpn$ sudo ifconfig tun0
tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.79.10.6  P-t-P:10.79.10.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:2505 (2.5 KB)

```

I'm at a loss. Oh, and I can't use the client, because when I installed I chose to encrypt the disc. Last time I used Xubuntu, it was pretty simple to choose to just encrypt the home directory, but I couldn't figure out that option in the 16.04 installer. They have a workaround where if you just encrypt home, you can move everything to /opt where their client can use the setuid bit, which it can't do on encrypted volumes.

Thanks for reading,
Rob

---

### Post by rob-from-canada on 2016-11-24
Solved by PIA support. They gave me this link [https://www.privateinternetaccess.com/pages/client-support/ubuntu-openvpn](https://www.privateinternetaccess.com/pages/client-support/ubuntu-openvpn) and said it would work on 16.04... and it did.

---

