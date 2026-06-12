---
title: "Vmware Wlan"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by Bloedkopf on 2008-05-15
Hi guys, 
here is my Problem : 

I installed VMWare Server Edition on my Ubuntu 8.04. My Guest System is Win XP Prof.

I installed two Ethernet Devices on my Virtual machine;
                              1.) Bridged
                              2.) Using network /dev/vmnet2

My Bridges are:
                  vmnet0 is bridged to eth1
                  vmnet2 is bridged to wlan0; 

How can I connect to the Internet now with my XP??? The Network Connections are always show as not connected :( Does the Connection get a static or dynamic IP? What do I have to adjust? I really have no idea... 


Hope someone can help me :)
dave

---

### Post by superprash2003 on 2008-05-15
normally selecting bridged would work.. cause the router would directly assign an ip to the vmnet device.. in ubuntu could you post the output of ifconfig .. also ensure in system->administration->network , DHCP is selected under vmnet properties

---

### Post by tribaal on 2008-05-15
Usually what you want to do with virtual machines is to have a *single* virtual network card per machine, and then bridge or NAT it to whatever physical interface you use at the moment you boot the virtual machine.

Exposing two virtual network interfaces is only useful if you use your virtual machine as a router, firewall or other network-oriented task.

When you "Bridge" the interface, it means the VM will get a new IP address as if it was sitting on the network you're connecting to (so you need to have a DHCP on the physical network, or know the IP configuration for a static setup). 
One drawback is that if you have no network available (physically), then your VM will not be given an ip address. Not so handy when you're on the go :)

Some networks (like some universities or offices) will refuse to allow two IP addresses for a single physical interface. In this case you should use "NAT" instead: NAT gives a private IP address to your VM (one in the 127.0.0.0 network - your machine's local network), and VMware server will take care of forwarding the requests to the outer world.

My personal setup: I use "NAT" interfaces for my VMs on my laptop, so I'm independent from networks I connect to, and switch the virtual interface from eth0 to wlan0 when I change from wired to wireless networks.

Hope this helps :)

- Trib'

---

### Post by Bloedkopf on 2008-05-15
ok first step is done :) 
I can connect now to Internet with Cable...therefore i deleted the /dev/vmnet2 Device and only used the Bridge Device. 
But if I try to delete the Bridge Device and only use the /dev/vmnet2, I get no Connection again. 
 Here is my ifconfig: 

> 
wlan0     Link encap:Ethernet  Hardware Adresse 00:18:XX:XX:XX:XX  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:48045 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37797 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:56191254 (53.5 MB)  TX bytes:5248131 (5.0 MB)


Dont know where is the Problem now :(

dave

---

