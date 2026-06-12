---
title: "[SOLVED] OpenVPN-client connects,cant see server's subnet"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by andb on 2007-10-29
Using OpenVPN as an ethernet bridge, I am able to successfully connect to the OpenVPN server, but then can't access machines on the server's subnet. I also cannot ping the client from machines on the subnet. So only the client and server are properly connected. I have tried to include everything that could be useful, I hope someone can find the flaw in my setup.

What is not configured correctly to properly bridge the client onto the subnet? By the way, my internal network is on 192.168.14.0/255.255.255/0 inside my dd-wrt router, Im testing using a computer on the WAN segment, which is 10.0.0.0/255.255.255.0, which is the default LAN setting of the Well ADSL router that I am using, which acts as the DHCP server only on this middle segment.

Internet <-> Well Router <-> lan segment with OpenVPN client <-> Linksys-DD-WRT <-> OpenVPN server and 192.168.14.0 subnet

I greatly appreciate any help fixing this problem!

On the server:
```
$ cat /proc/sys/net/ipv4/ip_forward
1
```

```
$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:0C:29:A1:ED:9F  
          inet addr:192.168.14.53  Bcast:192.168.14.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fea1:ed9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:329557 (321.8 KiB)  TX bytes:249962 (244.1 KiB)

eth0      Link encap:Ethernet  HWaddr 00:0C:29:A1:ED:9F  
          inet6 addr: fe80::20c:29ff:fea1:ed9f/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:3523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:361741 (353.2 KiB)  TX bytes:269437 (263.1 KiB)
          Interrupt:16 Base address:0x1400 

tap0      Link encap:Ethernet  HWaddr 02:10:73:EA:B1:70  
          inet6 addr: fe80::10:73ff:feea:b170/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:353 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:19391 (18.9 KiB)  TX bytes:60253 (58.8 KiB)


```
openvpn server routing:
```
$ route
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.14.0    *               255.255.255.0   U     0      0        0 br0
default         linksys         0.0.0.0         UG    0      0        0 br0
```


```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
```
$cat server.conf
local 192.168.14.53
port 1194
proto udp
dev tap0
ca /etc/openvpn/ca.crt
cert /etc/openvpn/server.crt
key /etc/openvpn/server.key
dh dh1024.pem
ifconfig-pool-persist ipp.txt
server-bridge 192.168.14.53 255.255.255.0 192.168.14.220 192.168.14.240
client-to-client
keepalive 10 120
comp-lzo
max-clients 100
user nobody
group nobody
persist-key
persist-tun
status openvpn-status.log
verb 3
mute 20
```

On the client:
```
$ cat client.conf
client
dev tap
proto udp
remote PUBLIC_IP_ADDRESS_IS_HERE 1194
resolv-retry infinite
nobind
ca CA_HERE
cert CERT_HERE
key KEY_HERE
ns-cert-type server
comp-lzo
verb 3
mute 20
```

client routing before:
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
default         mygateway1.ar7  0.0.0.0         UG    0      0        0  eth0
```
client routing after connecting to the server:
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
192.168.14.0    *               255.255.255.0   U     0      0        0           tap0
default         mygateway1.ar7  0.0.0.0         UG    0      0        0  eth0
```


And in case it might help, the init.d script I use to start the bridge on the server at boot:
```
$ cat /etc/init.d/bridge
#!/bin/bash  
# Create global variables   
# Define Bridge Interface 
br="br0" 
# Define list of TAP interfaces to be bridged, 
# for example tap="tap0 tap1 tap2". 
tap="tap0" 
# Define physical ethernet interface to be bridged 
# with TAP interface(s) above. 
eth="eth0" 
eth_ip="192.168.14.53" 
eth_netmask="255.255.255.0" 
eth_broadcast="192.168.14.255" 
gw="192.168.14.11"   

start_bridge () {   
#################################   
# Set up Ethernet bridge on Linux   
# Requires: bridge-utils   
#################################    
for t in $tap; do
     openvpn --mktun --dev $t   
done    
for t in $tap; do
     ifconfig $t 0.0.0.0 promisc up   
done

ifconfig $eth 0.0.0.0 promisc up

brctl addbr $br 
brctl addif $br $eth
for t in $tap; do
     brctl addif $br $t   
done    
ifconfig $br $eth_ip netmask $eth_netmask broadcast $eth_broadcast up   
route add default gw $gw $br
} 

stop_bridge () {   
####################################   
# Tear Down Ethernet bridge on Linux   
####################################    
ifconfig $br down
brctl delbr $br    
for t in $tap; do
     openvpn --rmtun --dev $t   
done   

ifconfig $eth $eth_ip netmask $eth_netmask broadcast $eth_broadcast up   
route add default gw $gw $eth
}  
case "$1" in 
start)   
echo -n "Starting Bridge"   
start_bridge   
;; 
stop)   
echo -n "Stopping Bridge"   
stop_bridge   
;; 
restart)   
stop_bridge   
sleep 2   
start_bridge   
;; 
*)   
echo "Usage: $0 {start|stop|restart}" >&2   
exit 1   
;; 
esac
```

---

### Post by bradleyd on 2007-11-02
did you ever find a answer? I am in the same boat. I have tried routing and bridging to no avail.

---

### Post by andb on 2007-11-07
No reply yet. I'll post to OpenVPN's mailing list and if I do ever figure it out I'll let you know. Its odd, because Ive seen quite a few howtos where the writer has had it "just work". I also tried on a debian etch machine, I expect it is not openvpn related but network related on the subnet...

---

### Post by bradleyd on 2007-11-07
I finally got routing to work. I gave up on bridged. Now the only problem is I cant ssh through the tunnel. It all works perfectly if I am coming in from a verizon or sprint mobile card. As soon as I try from home(which is behind a ipcop firewall, cable broadband) it connects fine but no ssh. I can ftp through the tunnel and telnet through the tunnel, when connecting from home. When I ssh it just hangs. I have tried this from other employees home machines with the same result..  It seems to be some NAT or MTU problem??? I cant find any docs on this particular problem. Thanks for the post back.

---

### Post by andb on 2007-11-07
So the OpenVPN server is at work? What kind of firewall or router is it behind? I would check the ListenAddress, try a different port ( I always more away from 22 as a simple precaution) I've been testing locally by putting a router in front of the OpenVPN box with a routed WAN port to which I connect my test client. That way, there is no "junk" in the middle to make problems.

Fortunately I dont need the VPN urgently right now, and my NAT forwarded ssh port is enough for my needs. 

Can you post you sshd_config file? If you run `netstat -al | grep tcp` on the openvpn machine after trying to open the ssh session, do you see anything there from this?

Just a few ideas, hope it helps...

---

### Post by bradleyd on 2007-11-07
My openvpn server is at work. It is a Ubuntu box behind a netscreen firewall. I have tried to ssh to the openvpn server and other machines on the same subnet. When i ssh into the box from outside. it asks for password and then just freezes. I put wireshark on it and it just seems the return packet from the ssh daemon just does not get there. Strange that if I use a mobile broadband card and connect to openvpn server that ssh and tunnel all perform correctly. The sshd conf on the machines that I am trying to ssh into are standard installs. They work fine behind the LAN. Another oddity is that when ssh does not work, that I am able to ftp to a ftp server in the same subnet as the vpn server. So the tunnel is working, just not relaying back the packet from the authorization of the sshd daemon.
Cant figure this one out.

---

### Post by andb on 2007-11-08
Got mine working. I left out an important piece of info, I was running the openvpn server in vmware. I set it up on a real box, and it worked right away. So later, if I do try to put it back in a virtual machine, Ill focus on the VMware server bridge, maybe use NAT instead.

If you would forward the ssh port from your firewall via NAT to your server, are you able to connect like that? If not, than its not a vpn issue, but somewhere else. The too low MTU idea on the router/firewall sounds plausible.

---

### Post by bradleyd on 2007-11-08
Yes I can connect using ssh from firewall no problem. I did run a mtu-test from openvpn client and it came back with fail. Said to try --fragment or -mssix

---

### Post by smile25 on 2007-12-24
> **andb said:**
> Got mine working. I left out an important piece of info, I was running the openvpn server in vmware. I set it up on a real box, and it worked right away. So later, if I do try to put it back in a virtual machine, Ill focus on the VMware server bridge, maybe use NAT instead.

The problem with vmware is that it needs to be able to set the network adapter to promiscuous mode, but does not have permissions to do so.  On the host run:

```
chmod a+rw /dev/vmnet0
```

Then restart the vmware server (or whatever you are using).

see [HTML]http://www.vmware.com/support/ws5/doc/ws_net_advanced_linux_vadapter_promiscuous.html[/HTML]

---

### Post by lonetree on 2008-01-15
Has anyone ever got OpenVPN work without a problem at all? My problem seems to be a bit similar just that I am not running VMware.

My OpenVPN client can get connected to the VPN server, and that's all, client can get files from the VPN server but not from any other LAN nodes, VPN clients are running Windows anyway, in Windows Explorer, the VPN client can only see the server machine and no other than that.

all terminals are connect to a Linksys router to access internet. I have enable IP forwarding in the VPN server and yet still to no avail. Does anyone of you got it working at all?

and one more thing, I am using the route method

thanks

regards,

---

### Post by oceanmonkey on 2008-04-04
Thanks for everyone keep inputting your information into this issue, that really helped me to get my vpn set up. 

i successfully setup my openvpn on one of my guest linux box on vmware server.

when i get connected with the host through openvpn, i can get the correct ip but can not ping or visit any other machine on the server's side. i found out that on the vmware host side your vmnet0(if you are using bridge) needs to be set in the Promiscuous mode.

i did the following to enable the Promiscuous mode on vmnet0
root@yourmachinname:~#  echo "PromiscuousAllowed yes" /dev/vmnet0  config

after doing this, without any restart, almost immediately the connect is up and running.
I can now connect from a remote widows openvpn gui in my office to a guest vm openvpn server at my home and able to visit all the machines on the server side.

if you have any question regarding this process, you can send me email i would love to offer my help.


hope that helps.:)

---

