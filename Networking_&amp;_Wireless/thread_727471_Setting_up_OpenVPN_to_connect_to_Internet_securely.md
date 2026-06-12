---
title: "Setting up OpenVPN to connect to Internet securely"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by alexisbellido on 2008-03-17
Hello guys. I have a few computers running Ubuntu 7.10 at home in Peru as well as a Ubuntu 7.10 server colocated at New York, US.

I want to be able to connect to this server in the US from my clients in Peru using OpenVPN so that I can browse the Web and access online applications securely as well as using my server's IP.

I have setup OpenVPN using the [Quickstart guide]("http://openvpn.net/index.php/documentation/howto.html#quick") 

After setting up my server and one client I have these IP's:

Server: 10.8.0.1
Client: 10.8.0.6

I can start OpenVPN with the corresponding keys and config files in both machines and can ping between server and client using but I am unable to browse the Web or use any online application. I can even ssh from client to server using the new private IP's.

A friend told me to run this as root as well: 'echo 1 > /proc/sys/net/ipv4/ip_forward' , but that didn't help.

I think I'm missing something related to default gateway or DNS in my client.

I tried putting the server's VPN IP, 10.8.0.1, in the client's /etc/resolv.conf but that didn't help, I also tried using the OpenDNS servers but again no luck.

Then I tried:

sudo route add default gw 10.1.0.8 tun0

and:

sudo route del default gw 192.168.0.1 eth0_rename

in my client to avoid using my router at home (which is 192.168,0,1) as default gateway but I lost my Internet connection completely so I had to revert these steps.

A friend told me that maybe BIND at my server (I have BIND managing a few domains I have in my server) was not accepting requests from the IP of my VPN client but I don't see how that affects my setup because I even tried using a third party DNS (OpenDNS)

I know I'm close and maybe you can help me find where's my mistake. I will really appreciate your help. Thanks guys!

These are my current settings:

**Server (10.8.0.1):**

openvpn.conf:

dev tun
proto tcp
port 1194

ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/server.crt
key /etc/openvpn/easy-rsa/keys/server.key
dh /etc/openvpn/easy-rsa/keys/dh1024.pem
user nobody
group nogroup
server 10.8.0.0 255.255.255.0
comp-lzo
persist-key
persist-tun
status openvpn-status.log
verb 3
client-to-client
push "redirect-gateway def1"
log-append /var/log/openvpn

output from 'ifconfig' for tun0

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00 
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:17481 (17.0 KB)  TX bytes:11349 (11.0 KB)

output from 'route -n'

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.2        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
x.y.z.w   0.0.0.0         255.255.255.248 U     0      0        0 eth0
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
0.0.0.0         x.y.z.w   0.0.0.0         UG    100    0        0 eth0
0.0.0.0         x.y.z.w   0.0.0.0         UG    100    0        0 eth0
0.0.0.0         x.y.z.w   0.0.0.0         UG    100    0        0 eth0
0.0.0.0         x.y.z.w   0.0.0.0         UG    100    0        0 eth0
0.0.0.0         x.y.z.w   0.0.0.0         UG    100    0        0 eth0

(x.y.z.w is my server's public IP, I just noticed I have repeated entries in my route table, maybe because I have a few interfaces running in the server, aliases really, from x.y.z.1 to x.y.z.4)

**Client (10.8.0.6):**

openvpn.conf:

dev tun
client
proto tcp
remote x.y.z.w 1194
resolv-retry infinite
nobind
user nobody
group nogroup

# Try to preserve some state across restarts.
persist-key
persist-tun
ca ca.crt
cert client1.crt
key client1.key
comp-lzo

# Set log file verbosity.
verb 3


output 'ifconfig' for tun0

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00 
          inet addr:10.8.0.6  P-t-P:10.8.0.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 b)  TX bytes:60 (60.0 b)

output  'route -n'

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.5        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
x.y.z.w   192.168.0.1     255.255.255.255 UGH   0      0        0 eth0_rename
10.8.0.0        10.8.0.5        255.255.255.0   UG    0      0        0 tun0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0_rename
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0_rename
0.0.0.0         10.8.0.5        128.0.0.0       UG    0      0        0 tun0
128.0.0.0       10.8.0.5        128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0_rename

---

### Post by SpaceTeddy on 2008-03-19
firstly, to route everything through the openvpn server, only the directive
```
redirect-gateway
```
is needed in the config file of the client. there is no additional route adding needed.
only the locally attached lans and the vpn-server itself will then still be run over the real internet - everything else is tunneled through to the server...

as for your connection problem - yes, you do need to turn on ip_forwarding on the server (which can be done temporarily via 
> sudo su
echo 1 > /proc/sys/net/ipv4/ip_forward

or you edit the file /etc/sysctl.conf and set uncomment the following line, resulting in ip_forwarding always being enabled at boot time.
```
#net.ipv4.conf.default.forwarding=1
```

as for your connection problem, i think the problem is not sending to the internet - it is that the replies from the internet cannot find their way back to you. If you are not rewriting the pakets at the vpn server, they will still hold your vpn-address - which is unknown in the internet. So i think you need to enable IP-Masquerading to fix this problem

this command assumes that your internet device is eth0 (change it to whatever device the server connects to the internet to.)
```
sudo iptables -A POSTROUTING --table nat -o eth0 -j MASQUERADE
```
This will rewrite any paket comming from the vpn network to look to the rest of the world as if your server sent it. so the replies will be sent back to your server, which will then send them back to you via the vpn.

hope it works :)

---

### Post by alexisbellido on 2008-03-19
Hi, thanks a lot! It worked. I was missing the iptables part.

I've written a tutorial about [OpenVPN and Ubuntu in Spanish]("http://www.ventanazul.com/articulos/instalar-openvpn-ubuntu-y-usar-hulu") and will translate to English soon.

Cheers!

---

