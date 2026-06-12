---
title: "networking issues and questions after fresh ubuntu server instalation"
date: 2017-12-03
forum: Networking &amp; Wireless
---

### Post by bern1 on 2017-12-03
Hi, 
I've just installed ubuntu server 17.10 + lubuntu-core GUI on my home computer/server and have couple of networking issues and questions I hope the community help me to resolve. 

Here is networking report of my system:
[http://paste.ubuntu.com/26105103/](http://paste.ubuntu.com/26105103/)

1. ALL 3 wired cards are displayed as 'device not managed' despite I changed 'managed=true' in the NetworkManager.conf. Wireless network is managed correctly by NM. How could I activate wires connection as managed?

2. I would like to use all four network interfaces. How could I activate all as UP on system boot?

3. I'm going to install (as a virtual machine -VM using VirtualBox) separate linux software (IPFire) as router/firewall and wanted to my ubuntu server to be secured through the IPfire VM firewall. IPfire would be the only system that connects to an "external" physical net. So I understand that Internet interface enp1s0 (before the bridge with VM) on ubuntu server side (=host) has to be unconfigured /  unmanaged, which means TCPv4 off, TCPv6 off, all off = no connection  directly. How could I configure enp1s0 interface to achieve this?

4. I'm planing to launch VM router/firewall in the headless mode (as a service in the background). It takes about 2 minutes for VM to start. How could I configure network interfaces to start instantly UP and not to waiting for network of VM?

Every advice would be appreciated:)
TIA,

---

### Post by powersj on 2017-12-04
Can you see if there is a file in /etc/netplan/ and if so if the renderer is set to NetworkManager or not?

---

### Post by bern1 on 2017-12-05
> **powersj said:**
> Can you see if there is a file in /etc/netplan/ and if so if the renderer is set to NetworkManager or not?

Hi, 
I've removed NetworkManager completely and switched to networkd. 
 Also I created netplan files in /etc/netplan/ each for network interface (4 in total).
This move let me to resolve 1, 2, 4 points from my first post. 

Point 3 remains...
e.g how to block internet traffic on 'enp1s0' for ubuntu  and the same time pass through the traffic to MV firewall/router ('enp1s0' is bridged with VM network interface)?
On ubuntu I tried:
```
sudo ip addr flush enp1s0
```
but traffic is not blocked. 
Although for few moments I can see:
```
enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 70:85:c2:3d:6b:ba  txqueuelen 1000  (Ethernet)
        RX packets 43560  bytes 14380626 (14.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 11251  bytes 1247052 (1.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
after minute or two I see 'inet' again:
```
enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.15.191  netmask 255.255.255.0  broadcast 192.168.15.255
        ether 70:85:c2:3d:6b:ba  txqueuelen 1000  (Ethernet)
        RX packets 43922  bytes 14449616 (14.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 11582  bytes 1332123 (1.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
please advise what to do. 
How to disable TCP/UDP for 'enp1s0' interface?
Is there any way to do that in the netplan configuration file?
Thanks,

---

### Post by powersj on 2017-12-05
> **bern1 said:**
> Hi, 
I've removed NetworkManager completely and switched to networkd. 
 Also I created netplan files in /etc/netplan/ each for network interface (4 in total).
This move let me to resolve 1, 2, 4 points from my first post. 


Awesome! Glad that worked for you.

> **bern1 said:**
> 
How to disable TCP/UDP for 'enp1s0' interface?
Is there any way to do that in the netplan configuration file?


Do you want to disable it or have the traffic from the host machine get routed through the VM with the firewall? A diagram with which physical ports and bridges are doing what would help.

---

### Post by bern1 on 2017-12-06
> **powersj said:**
> Do you want to disable it or have the traffic from the host machine get routed through the VM with the firewall? A diagram with which physical ports and bridges are doing what would help.
  Please find my clumsy diagram;)

[IMG]http://drive.google.com/uc?export=view&id=1SPsdLeLqOeRstF2PvQ9JIZpCjCdk7EQi[/IMG]

I would like to disable internet traffic for Ubuntu and pass it through to bridged VM. 
Can I do this by blocking ubuntu MAC address (IPTABLE on ubuntu) or mayby there is more simple way? I do not have experience with IPTables...
Regards,

---

### Post by powersj on 2017-12-06
I believe what you want to accomplish is done by having the default route of the host be through the bridge on 192.168.2.1 or at least something other than 192.168.15.28. The output of `ip r` will show you your routing table and running `
ip route change default via <ip>` will change the default route.

Does that help?

---

### Post by bern1 on 2017-12-07
> **powersj said:**
> I believe what you want to accomplish is done by having the default route of the host be through the bridge on 192.168.2.1 or at least something other than 192.168.15.28. The output of `ip r` will show you your routing table and running `
ip route change default via <ip>` will change the default route.

Does that help?

'ip r' gives me:
```
ela@akacja:~$ sudo ip r
default via 192.168.15.1 dev enp1s0 proto dhcp src 192.168.15.191 metric 100 
default via 192.168.2.1 dev enp3s0f1 proto dhcp src 192.168.2.10 metric 100 
192.168.2.0/24 dev enp3s0f1 proto kernel scope link src 192.168.2.10 
192.168.2.1 dev enp3s0f1 proto dhcp scope link src 192.168.2.10 metric 100 
192.168.15.0/24 dev enp1s0 proto kernel scope link src 192.168.15.191 
192.168.15.1 dev enp1s0 proto dhcp scope link src 192.168.15.191 metric 100 

```

I'm browsing the internet to find out how to block the internet access on ubuntu machine. 
I've tried iptables and block ubuntu's MAC:
```
sudo iptables -A INPUT -p all -m mac --mac-source 70:85:c2:3d:6b:ba -j DROP
sudo iptables -A FORWARD -p all -m mac --mac-source 70:85:c2:3d:6b:ba -j DROP
```
but this doesn't block and still can access the internet
The IPTABLES after the change:
```
ela@akacja:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere             MAC 70:85:C2:3D:6B:BA

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere             MAC 70:85:C2:3D:6B:BA

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
Why doesn't work? Or maybe there are other ways to block internet access for a particular MAC in ubuntu?
Regards,

---

### Post by photonxp on 2017-12-07
> **bern1 said:**
> I've tried iptables and block ubuntu's MAC


Doesn't sound like a good idea to me. 
According to your diagram, the IPfire VM will require the Ubuntu's MAC to redirect internet traffic. If ubuntu's MAC is really blocked, the pathway to internet for IPfire VM would also be blocked. 

As others have mentioned, manipulating the route tables seem to be a better idea if eventually you could figure out how to use it or someone helps you figure out.

---

### Post by bern1 on 2017-12-08
Hi guys, 
Problem solved :smile:
I've changed the content of netplan file for interface enp1s0 from:
```
network:
    version: 2
    renderer: networkd
    ethernets:
        enp1s0:
            dhcp4: true
```
to:
```
network:
    version: 2
    renderer: networkd
    ethernets:
        enp1s0:
            addresses:
                - 192.168.15.23/24
            dhcp4: no
```
and all works fine. 
I set static address on IPFire router (VM) but forget switch dhcp to static on Ubuntu server. 
Anyway after the change Ubuntu machine is now LAN host of VM and has not direct connection to the Internet
It is interesting because for this I do not need external ethernet switch...
I will investigate this in free time..
Thanks for your posts. :smile:

---

