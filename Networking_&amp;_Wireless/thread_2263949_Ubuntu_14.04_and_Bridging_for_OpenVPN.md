---
title: "Ubuntu 14.04 and Bridging for OpenVPN"
date: 2015-02-04
forum: Networking &amp; Wireless
---

### Post by greatlakes09 on 2015-02-04
I am trying to set up bridging for OpenVPN.  I have searched high and low for a solutions, but keep finding conflicting solutions. 


Any help setting up a new interfaces file is appreciated!  Thanks in advance!


Suppose /etc/network/interfaces contains:


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo


And ifconfig returns:


eth0      Link encap:Ethernet  HWaddr 09:00:12:90:e3:e5  
          inet addr:192.168.1.29 Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe70:e3f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54071 errors:1 dropped:0 overruns:0 frame:0
          TX packets:48515 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22009423 (20.9 MiB)  TX bytes:25690847 (24.5 MiB)
          Interrupt:10 Base address:0xd020 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7766 (7.5 KiB)  TX bytes:7766 (7.5 KiB)




Then what should the new /etc/network/interfaces contain?

---

### Post by greatlakes09 on 2015-02-05
Think I figured this out.. still trying to figured out how to set vpn connection from client, but both the server and client see each other in the syslog. So far so good.  Not sure if I can use the network manager gui to connect, but that is what I am working on next.

================================
New Interfaces
================================

auto lo br0


iface lo inet loopback


iface br0 inet static 
  address 192.168.1.29 
  netmask 255.255.255.0
  gateway 192.168.1.254
  bridge_ports eth0


iface eth0 inet manual
  up ip link set $IFACE up promisc on
  down ip link set $IFACE down promisc off

---

### Post by greatlakes09 on 2015-02-23
to solve this, I used the existing interfaces file which contained:

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo

I then used a helper script that I found to set the interfaces:

#################################
# Set up Ethernet bridge on Linux
# Requires: bridge-utils
#################################


# Define Bridge Interface
br="br0"


tap="tap0"


# Define physical ethernet interface to be bridged
# with TAP interface(s) above.
eth="eth0"
eth_ip="192.168.1.107"
eth_netmask="255.255.255.0"
eth_broadcast="192.168.1.255"
gw="192.168.1.254"


openvpn --mktun --dev $tap


brctl addbr $br
brctl addif $br $eth


brctl addif $br $tap


ifconfig $tap 0.0.0.0 promisc up


ifconfig $eth 0.0.0.0 promisc up


ifconfig $br $eth_ip netmask $eth_netmask broadcast $eth_broadcast
route add default gw $gw


sudo /etc/init.d/openvpn start


## For remote debugging (added this in case you lose connection when remote debugging)
## server will reboot in 5 minutes with default interfaces file.
#sleep 5m
#sudo reboot

---

