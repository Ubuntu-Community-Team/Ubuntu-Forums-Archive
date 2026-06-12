---
title: "Multiple Vlan cannot ping the router"
date: 2015-03-24
forum: Networking &amp; Wireless
---

### Post by itec4u on 2015-03-24
Hi there
I hope you are well


Last few days I have been trying to fix my server to support multiple vlan , I searched everywhere and still couldn't fix it to ping other devices and the router. :(   
also I remove all the firewall . :(
Some Other devices can ping the router because  it has in the same subnet . 


Please help me guys, I would like to know my mistake.
 
This is my configuration :
I remove network manager 
I installed vlan
I add  modprobe 8021q to the kernel 
I edit my interfaces (see below)
restart my network 
Ip4 forward 


I have switch 2960 and Cisco router 2900 series
My configuration in the switch:
one port trunk connected to the server and other port divided to 3 vlan 


My configuration in the router:
1 access port have an ip (not trunk)   192.168.10.1


Thanks in advance I appreciate your help




```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
        auto lo
        iface lo inet loopback
#vlan 10
    auto eth0.10
    iface eth0.10 inet static
        address 192.168.10.2
        netmask 255.255.255.240
        vlan-raw-device eth0
#vlan 20
        auto eth0.20
    iface eth0.20 inet static
        address 192.168.20.1
        netmask 255.255.255.0
        vlan-raw-device eth0
#vlan 30
       auto eth0.30
       iface eth0.30 inet static
        address 172.17.116.1
        netmask 255.255.252.0
        vlan-raw-device eth0



```

---

### Post by itec4u on 2015-03-25
Please Help!!!

I need to know is my configuration for the server certainly right ..

---

