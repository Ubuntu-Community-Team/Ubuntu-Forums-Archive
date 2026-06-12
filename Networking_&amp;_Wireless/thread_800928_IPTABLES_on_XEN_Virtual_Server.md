---
title: "IPTABLES on XEN Virtual Server"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by Pete89 on 2008-05-20
Hello,

I am trying to get a very simple IPTABLES config to work on XEN server that has two virtual machines. I am NATing between the XEN server and the guest machines. Here is an ifconfig on the XEN server:

eth0      Link encap:Ethernet  HWaddr 00:18:F3:FB:44:7C  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
             
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
 
         
vif3.0    Link encap:Ethernet  HWaddr FE:FF:FF:FF:FF:FF  
          inet addr:10.0.0.128  Bcast:0.0.0.0  Mask:255.255.255.255
          
         
And here is one guest machines ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:16:3E:BD:BC:97  
          inet addr:10.0.0.1  Bcast:10.255.255.255  Mask:255.0.0.0

So you can see that we are using the 10.0.0.x network for the virtual stuff.

So back to the host server and the iptables config. What I want to do is forward all port 80 traffic reaching the host server's eth0 interface to 10.0.0.1 and not forward anything else. I would like 10.0.0.1 to be invisible on the 192.168.1.x network. This config kinda works:

### Default Deny ####
iptables -P INPUT DROP

### Default Output ####
iptables -P OUTPUT ACCEPT

### Port Forwarding ###
iptables -A PREROUTING -t nat -p tcp -i eth0 --dport 80 -j DNAT --to 10.0.0.1:80

### Allow SSH connections to HOST Server ####
iptables -A INPUT -p tcp -s 192.168.1.0/24 --dport 22 -j ACCEPT


This config does the port forwarding just fine. It also only allows SSH connections on the host server. However, the guest server at 10.0.0.1 is hardly invisible. If I have routes created for the 10.0.0.x network locally  on my machine looky here:

elvis:/home/pete# nmap -sS 10.0.0.1
Interesting ports on 10.0.0.1:
Not shown: 1709 closed ports
PORT   STATE    SERVICE
21/tcp open     ftp
22/tcp open     ssh
25/tcp filtered smtp
68/tcp filtered dhcpc
80/tcp open     http

And can I connect to those ports? You bettcha.

I have tried this config with no success:

### Default Deny ####
iptables -P INPUT DROP

### Default Output ####
iptables -P OUTPUT ACCEPT

### Default Forward ###
iptables -P FORWARD DROP

### Port Forwarding Exceptions ###
iptables -A PREROUTING -t nat -p tcp -i eth0 --dport 80 -j DNAT --to 10.0.0.1:80

### Let port 80 get forwarded after PREROUTING ###
iptables -A FORWARD -p tcp -i eth0 -o vif3.0 -s 0/0 -d 0/0 --dport 80 -j  ACCEPT

### Allow SSH connections to Master Server ####
iptables -A INPUT -p tcp -s 192.168.1.0/24 --dport 22 -j ACCEPT

This config breaks forwarding. Nothing gets forwarded. I know this must be something simple but this is my first try with IPTABLES in many years. I found a good tutorial over at [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables")
And it is very well done but I am still sratching my head.

Thanks for any advice or help,

Pete

---

### Post by negustafson on 2008-06-28
As far as I can tell, IPTABLES support is missing from the Ubuntu repository version of Xen Server kernel. I, however cannot find anything more specific. You might want to try compiling your own kernel and making sure IPTABLES support is included. That process can be complicated, however. Please post if you find anything more about this.

---

