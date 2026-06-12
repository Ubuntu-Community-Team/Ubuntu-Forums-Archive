---
title: "This problem is doing my head in."
date: 2010-11-11
forum: New to Ubuntu
---

### Post by techno_ni on 2010-11-11
I have a server with esxi, I have created a virtual machine with ubuntu i have vmware tools installed I have added apache, php, mysql installed.

When I type in the ip address the page comes up saying it works.

When I type that ip address on a different computer on my network nothing is displayed.

On my esxi server the ip address is 192,168,1,4 and on ubuntu it is 192,168,1,69 does this have to be the same.  For every time I change it on the esxi server to 192,168,1,69 I can't get access to ubuntu when i run the virtual machine.

I have the address as static in ubuntu.

---

### Post by Dragonbite on 2010-11-11
So is it that the host (esxi) can view the Ubuntu site via IP, but outside of the host it cannot?  If so, looks like esxi is not transferring traffic to and from the Ubuntu image.

Can the ubuntu image see any of the other computers in your network?

---

### Post by techno_ni on 2010-11-12
Here is a better overall view of my system.  I have esxi on a dedicated machine I then use VMware vsphere client on my windows xp machine to set up my virtual machine which is Ubuntu 9.10 I have vmware tools installed. 

1) My ip address on my esxi dedicated machine is 192.168.1.4 and my ip address in Ubuntu is 192.168.1.69 does this have to be the same or can they be different ?

2) I can go to my XP machine and ping 192.168.1.69 but I can't ping my XP machine within Ubuntu is there a firewall preventing access?

3) I don't think my network connections are connected up right in ubuntu because it says ifupdown and I had to change from static to dhcp in etc/network/interfaces to get the internet working again and when I right click in the right hand corner and go to connection information it just says error displaying connection information.

When I go to network tools and do a port scan it says port 80 is open.

---

### Post by Dragonbite on 2010-11-12
> **techno_ni said:**
> Here is a better overall view of my system.  I have esxi on a dedicated machine I then use VMware vsphere client on my windows xp machine to set up my virtual machine which is Ubuntu 9.10 I have vmware tools installed. 

1) My ip address on my esxi dedicated machine is 192.168.1.4 and my ip address in Ubuntu is 192.168.1.69 does this have to be the same or can they be different ?

2) I can go to my XP machine and ping 192.168.1.69 but I can't ping my XP machine within Ubuntu is there a firewall preventing access?

3) I don't think my network connections are connected up right in ubuntu because it says ifupdown and I had to change from static to dhcp in etc/network/interfaces to get the internet working again and when I right click in the right hand corner and go to connection information it just says error displaying connection information.

When I go to network tools and do a port scan it says port 80 is open.

I would think the IP address of the client needs to be different than that of the host, otherwise it would get confusing.

So XP can ping Ubuntu, but Ubuntu cannot ping XP.  I wouldn't think Ubuntu's firewall would get in the way, but somehow it isn't passing its communication through the host outward.

So are you saying that Ubuntu can get external access (internet) when using DHCP, but not the static IP?  

When using DHCP, what is the IP address you get?  Also, when using DHCP can you ping the XP machine?

This is dusting off some memory of mine when I started with Ubuntu Server, but I can't remember the details yet, or how I solved it.  I'm starting to think, though, that it may be in your Ubuntu box like you said, and not so much the VM Client.

I'm hoping somebody with more VM/Server experience can pop in and wave their "magic wand", but I'll keep trying to remember and see if I can dig up any notes on when it happened to me and how I resolved it.

---

### Post by Skavenger0 on 2010-11-12
In vSphere configuration settings for that virtual machine make sure you have a network card and that it is set to VM network and Flexible. 

The ESXi must have a different IP to your guest as they are seperate entities.

Post the results of ifconfig please.

If you can ping from windows I dont think its an interface or vmware issue so it could be an issue with the ubuntu install. 
Either firewall or do you use a proxy?

---

### Post by techno_ni on 2010-11-16
> **Skavenger0 said:**
> In vSphere configuration settings for that virtual machine make sure you have a network card and that it is set to VM network and Flexible. 

The ESXi must have a different IP to your guest as they are seperate entities.

Post the results of ifconfig please.

If you can ping from windows I dont think its an interface or vmware issue so it could be an issue with the ubuntu install. 
Either firewall or do you use a proxy?
Here is the ifconfig details.

> 

eth0      Link encap:Ethernet  HWaddr 00:0c:29:77:86:92  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe77:8692/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1774 (1.7 KB)  TX bytes:4437 (4.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)



Oh and I don't use a proxy.

---

