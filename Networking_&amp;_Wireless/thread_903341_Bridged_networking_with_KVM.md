---
title: "Bridged networking with KVM"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by Pkleingu on 2008-08-28
explanation situation: 

I want too test on ubuntu 8.4 desktop with KVM several ghost images
I have two network cards in the PC. 
KVM runs fine 
Restoring a ghost images in the virtual environment is now fine through Hawkpe 
I only wish that the virtual environment receives through dhcp an ip adres and that only that ip number is visible on the network. The same goes for the other NIC.  Only the ipadres obtained by DHCP of the virtual environment may be visible on the network.  The Internet on the host PC is still working, so this one is still with his ip address the on the network with is not my intention. I want too now how the virtual invirement should obtains a dhcp ipadres through specified networkcard. 
 I think I'm already pretty on the road, What do I need to adjust, and what boot options (for the launch of the virtual environment) should I use to the use the correct NIC to work? 
Who has intelligence of these network techniques?


pkleingu@pkleingu-desktop:/etc/network$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:21:70:15:a6:82  
          inet addr: xxx.xxx.43.195  Bcast: xxx.xxx.127.255  Mask:255.255.128.0
          inet6 addr: 2002:8f79:6585:5:221:70ff:fe15:a682/64 Scope:Global
          inet6 addr: fec0::5:221:70ff:fe15:a682/64 Scope:Site
          inet6 addr: fe80::221:70ff:fe15:a682/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77504 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9510595 (9.0 MB)  TX bytes:727497 (710.4 KB)

br1       Link encap:Ethernet  HWaddr 00:15:17:24:8c:a7  
          inet addr: xxx.xxx.43.197  Bcast: xxx.xxx.127.255  Mask:255.255.128.0
          inet6 addr: 2002:8f79:6585:5:215:17ff:fe24:8ca7/64 Scope:Global
          inet6 addr: fec0::5:215:17ff:fe24:8ca7/64 Scope:Site
          inet6 addr: fe80::215:17ff:fe24:8ca7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23598 (23.0 KB)  TX bytes:4856 (4.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:21:70:15:a6:82  
          inet6 addr: fe80::221:70ff:fe15:a682/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20252697 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2124927483 (1.9 GB)  TX bytes:16600070 (15.8 MB)
          Memory:fe9e0000-fea00000 

eth1      Link encap:Ethernet  HWaddr 00:15:17:24:8c:a7  
          inet6 addr: 2002:8f79:6585:5:215:17ff:fe24:8ca7/64 Scope:Global
          inet6 addr: fec0::5:215:17ff:fe24:8ca7/64 Scope:Site
          inet6 addr: fe80::215:17ff:fe24:8ca7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:872019 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:82280126 (78.4 MB)  TX bytes:213437 (208.4 KB)
          Base address:0xdce0 Memory:fe7c0000-fe7e0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2454 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2454 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:946568 (924.3 KB)  TX bytes:946568 (924.3 KB)

tap0      Link encap:Ethernet  HWaddr 00:ff:98:aa:32:16  
          inet6 addr: fe80::2ff:98ff:feaa:3216/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:14450996 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap1      Link encap:Ethernet  HWaddr 00:ff:fa:d3:45:07  
          inet6 addr: fe80::2ff:faff:fed3:4507/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:1845656 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vnet0     Link encap:Ethernet  HWaddr 4a:2b:8a:2d:4b:83  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::482b:8aff:fe2d:4b83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:7890 (7.7 KB)


desktop:~$ brctl show

bridge name    bridge id        STP enabled    interfaces
br0        8000.00217015a682    no        eth0
                            tap0
vnet0        8000.000000000000    yes        

vi interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address xxx.xxx.43.195
        network xxx.xxx.0.0
        netmask 255.255.128.0
        broadcast xxx.xxx.127.255
        gateway xxx.xxx.2.235
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off


auto eth1
iface eth1 inet manual

iface br1 inet static
        address xxx.xxx.43.197
        network xxx.xxx.0.0
        netmask 255.255.128.0
        broadcast xxx.xxx.127.255
        gateway xxx.xxx.2.235
        bridge_ports eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

---

### Post by gerni on 2008-08-30
i've the same problem than you - i've running ipcop (firewall) on my host and want to isolate my host from direct access to net internet (only through ipcop).
I've still not found a solution to this problem.
I would be very happy if anybody can help us :)
thank you!

---

### Post by Michael Longval on 2009-02-09
I'm not sure if this is going to work with anybody else's setup.

My system setup is as follows:

3.0 Ghz Core2-duo running Ubuntu 8.04LTS with KVM kernel module.
4 Gig ram
1 ethernet connection - connected to router/internet.

I had some trouble at first setting up the bridged interfaces to get KVM up and running.

Here is what I finally put in /etc/network/interfaces (I know it's just about the simplest definition you can have... but I had a lot of trouble getting it to work. ;-) (NB: I wanted to use static addresses ... if you use DHCP, then you'll have to adjust to taste)

==== begin config file ====

auto lo
iface lo inet loopback

## eth0
auto eth0
iface eth0 inet static
address 192.168.0.24
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

## br0
auto br0
iface br0 inet static
address 192.168.0.24
netmask 255.255.255.0
gateway 192.168.0.1
bridge_ports eth0 
bridge_maxwait 0

==== end config file ====

I then restarted the system with this network configuration.	

I then downloaded Ubuntu's JeOS 8.04.

I then setup my new VMs using Virtual Machine Manager.  

I added myself to a few groups via Users and Groups... (if I remember) : uml-net , libvirtd , netdev and kvm .  

I might have forgot some... sorry. 

Now using Virtual Machine Manager I created a new machine in the "System" domain. (I wasted a lot of time trying to configure a VM in the "Session" domain, but after much pain and suffering.... switched to the "System" domain and deleted the "Session" domain.)

I pointed the wizard to the JeOS .iso image, and selected "bridged" networking and gave a new unique  MAC address to the virtual card (VERY IMPORTANT STEP).  

Setup proceeded and built a perfectly functioning Virtual Machine.  By default the VM comes up using DHCP, which I changed in it's /etc/network/interfaces file.

Now I know that all this seems simple, but beleive me, with the state of the documentation about bridged networking on KVM, it took me more than a few hours to understand and set the stuff up the right way..... I spent I don't know how long trying to configure tap0 interfaces.... which are not necessary here.

Anyway now it works.  Just wanted to write this in case it might help someone.

Michael Longval

---

