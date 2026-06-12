---
title: "Ubuntu unreliable with two network cards, Help!"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by elperrillo on 2008-08-07
I have a Ubuntu server in which i'm trying to run SQUID however my my routes change every time I reboot a computer. The server has two network cards (eth0 and eth1) sometimes I have a specific route using eth1 but when I reboot the server the same route could be using eth0. This is making the use of squid practically imposible. it might work for minutes and then all of a sudden stop working because of that changing route. 
I have the same exact network configuration on another squid server running on FEDORA and its been running flawlessly for years, also this configuration is VERY SIMPLE. I bought a new server since Fedora is running on an old PIII machine and intalled Ubuntu on the new server (Dell 860 rackmounted), but so far I have not been able to get it to work reliably. Whe this happens Ubuntu becomes invisible to toher vlans on the network. Its hard for me to belive that Ubuntu can't run reliably with two network cards. 
Here is what i've done so far:

-Disabled ICMP redirects... did not work.
-Remove gateway from eth0 and left only a gateway for eth1... did not work.
-disconnected the Server from the network and plugged it on an isolated switch for testing ... did not work, routes kept changing anyways.

I do not know what else to do and I do not want to go Back to fedora since I have done a lot of work on this server. Do I have to change my network manager? Can anybody help?

---

### Post by SpaceTeddy on 2008-08-07
mhm - strange.

First things first - Network manager is not able to cope with two network cards (at least as far as i know). If you need more than one network card active you will have to do the configuration of the cards manually. 

Now, for my thought what i think might be happening - i think that both network cards are getting dhcp leases from somehwere, or that there is something that reconfigures the network cards manually. As you are running a server, i would suspect that you want to have static ip's anyway-

So, check you /etc/network/interfaces for any entries and manual config of the network cards, and make sure you disable the network manager. As soon as you want to use more than one network cards it is a real pain.

If in doubt, please post the content of you /etc/network/interfaces.

hope we can figure this out :)

---

### Post by elperrillo on 2008-08-07
Hi, thanks for your response. When I talk about "network Manager", I am not talking about the wireless one, I am talking about the regular ubuntu/gnome network config. I do have static IPs on the two network cards... here is my interfaces file.... as you can see it is really simple (I changed the ips for security purposes but the follow the same structure)...

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 49.30.133.10
netmask 255.255.255.240

auto eth1
iface eth1 inet static
address 192.168.1.112
netmask 255.255.0.0
gateway 192.168.254.254


Now these are two examples of what I get when I run "netstat -rn" 

Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt Iface
49.30.133.9 0.0.0.0 255.255.255.240 U 0 0 0 eth0
192.168.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth1
50.254.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth1
0.0.0.0 192.168.254.254 0.0.0.0 UG 0 0 0 eth1

Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt Iface
49.30.133.9 0.0.0.0 255.255.255.240 U 0 0 0 eth0
192.168.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth1
50.254.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth0
0.0.0.0 192.168.254.254 0.0.0.0 UG 0 0 0 eth1

Notice how the third line got changed again from eth1 to eth0... Even if I connect the server to an isolated switch this happens. So it is something with Ubuntu and not external.

---

### Post by SpaceTeddy on 2008-08-07
i have absolutely no idea what that would happen. seriously,i don't even know why that route is loaded. It is not an automated configuration that is done when the network interfaces come up... it is just there. Where is it coming from in the first place - do you know that ?

I am as stuck as you are - seriously sorry :(

---

### Post by elperrillo on 2008-08-07
Man I have not idea either were that route comes from because if you take a look at it, its ip structure does not follow the one on either of the two cards. and the funny thing is that, that route is comming out on my old fedora server too! (but it stays allways on eth1) I am testing the server now since I eliminated the extra gateway that I had in there, somehow Fedora performs well with two gateways since somehow it chooses one over the other, but Ubuntu gest confused... so far I have not had the problem, on my vlan but I sill need to check if other people on the vlan can reach the server.... That changing route might not be the cause of the problem after all, I just have to do some heavy testing before, I will post my findings here when I am done.

Thanks for your help anyways.

---

