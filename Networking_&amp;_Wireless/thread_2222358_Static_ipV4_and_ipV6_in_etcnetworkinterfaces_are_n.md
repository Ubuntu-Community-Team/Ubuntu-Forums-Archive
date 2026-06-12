---
title: "Static ipV4 and ipV6 in /etc/network/interfaces are not working"
date: 2014-05-06
forum: Networking &amp; Wireless
---

### Post by ufe on 2014-05-06
Hi, 
I try to setup a ipv4 and Ipv6 routers for my home network.
I have no official ipv6 address and no ipv6 connection to my provider (Telekom Germany).
It's Ubuntu 14.04.

I'm running dnsmasq as Ipv4 dns and dhcp server as well as ipv6 dns and dhcp. I try to run statefull, so i have full dns coverage.

I did the /etc/network/interfaces as per some blogs and recommendations on the internet.

I'm facing the issue, that my self assigend static ipV6 2001::address is not set, I need to shut down the device on the command line with ifdown eth0 ; ifup eth0 to enable the 2001:: address.
The fe80:: addresses are all there.

In Dnsmasq I use the constructor statement to set the range for the 2001:: ipV6 addresses and this fails, as the interface has no 2001:: address.

What I'm doing wrong?

ufe

 
/etc/network/interfaces (truncated)                                                                                                                                                auto lo                                                                                                                                         
auto eth0                                                                                                                                       
auto eth0.10                                                                                                                                    
auto eth1                                                                                                                                       
auto eth2                                                                                                                                       
#auto eth3                                                                                                                                      
                                                                                                                                                
iface eth0 inet static                                                                                                                          
        address 192.168.16.2                                                                                                                    
        netmask 255.255.255.0                                                                                                                   
        broadcast 192.168.16.255                                                                                                                
        gateway 192.168.16.1                                                                                                                    
iface eth0 inet6 static                                                                                                                         
        address 2001:1234:5678:0000::2                                                                                                          
        netmask 64                                                                                                                              
        #gateway 2001:1234:5678::9ec7:a6ff:fe96:a045                                                                                            
up /sbin/ifconfig eth0 inet6 add 2001:1234:5678:0000::2/64                                                                                      
                                                                                                                                                
up /sbin/sysctl -w net.ipv6.conf.default.forwarding=1                                                                                           
up /sbin/sysctl -w net.ipv6.conf.all.forwarding=1                                                                                               
up /sbin/sysctl -w net.ipv4.conf.default.forwarding=1                                                                                           
up /sbin/sysctl -w net.ipv4.conf.all.forwarding=1                                                                                               
dns-nameservers 192.168.16.2 192.168.16.1                                                                                                       
dns-domain fritz.box                                                                                                                            
dns-search local fritz.box                                                                                                                      
                                                                                                                                                
accept_ra 1                                                                                                                                     
autoconf 1                                                                                                                                      
                                                                                                                                                
                                                                                                                                                
iface eth1 inet static                                                                                                                          
        address 192.168.1.2                                                                                                                     
        netmask 255.255.255.0                                                                                                                   
        broadcast 192.168.1.255                                                                                                                 
iface eth1 inet6 static                                                                                                                         
        address 2001:1234:5678:0001::2                                                                                                          
        netmask 64                                                                                                                              
up /sbin/ifconfig eth1 inet6 add 2001:1234:5678:0001::2/64                                                                                      
                                                                                                                                                
iface eth0.10 inet static                                                                                                                       
        address 10.0.0.2                                                                                                                        
        netmask 255.255.255.0                                                                                                                   
        network 10.0.0.0                                                                                                                        
        broadcast 10.0.0.255                                                                                                                    
        mtu 1500                                                                                                                                
        vlan_raw_device eth0                                                                                                                    
iface eth0.10 inet6 static                                                                                                                      
        address 2001:1234:5678:0010::2                                                                                                          
        netmask 64

---

