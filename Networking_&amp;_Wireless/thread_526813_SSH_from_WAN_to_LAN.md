---
title: "SSH from WAN to LAN"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by tobyarnett on 2007-08-15
OK so I am very new to Linux but I am learning. I have a Linux box at the house (Ubuntu) and I have installed openssh-server on it. I can ssh to my Linux Laptop from my Windows Laptop while I am local on my LAN. I am using SecureCRT on one laptop and Putty on another laptop. When I type in the public WAN IP <i.e. 144.91.10.8 - not real> I get the error message: 

"The remote system refused the connection. This probably means that the service you are attempting to access, or that the service is being provided on a different port."

Is that meaning that my ISP is blocking the port or maybe an issue with my Linksys Wireless router???  Again locally I can SSH, from outside my network I can not get in via my public. I have made a dyndns.com account and that isn't working but maybe I am doing it wrong.


eth0      Link encap:Ethernet  HWaddr 00:90:F5:21:B5:A7  
          inet addr:10.10.11.2  Bcast:10.10.11.255 Mask:255.255.254.0
          inet6 addr: ab03::137:e3a0:c3aa:b5a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15323 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6013913 (5.7 MiB)  TX bytes:1616119 (1.5 MiB)
          Interrupt:11 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

<note I did change my critical info but those are my interfaces> 

What am I missing. Please keep it simple, if the answer involves scripts or programs please link a how to. I am pretty quick but again very new. Thanks for any help.

---

### Post by kevdog on 2007-08-16
If your running your ssh server on port 22 (the standard port) you need to change the settings on your linksys router to port forward all incoming connection on port 22 to your machine 10.10.11.2.  Dynamic DNS helps your name resolution, so that rather than typing ssh <WAN IP address> you can type ssh <xxxx.dyndns.com> or something like that.

You also on your server need to open up port 22 to outside connections, either by modifying the iptables manually, or using a GUI such as Firestarter or Guarddog.

---

### Post by noob12 on 2007-08-16
You'll need to setup a static internal ip address on the laptop that is hosting the ssh server to which you want to connect.  Then you'll need to setup the linksys router to forward port 22 to that address.   Not generally done with laptops.

To configure a static internal ip on your laptop, you use the System | Administration | Network menu item. Pick the interface.  Setup the address, netmask, gateway and dns servers.  The static address should be one that is on the same subnet, but is **not** in the pool of DHCP addresses that your linksys router assigns.

EDIT:  kevdog beat me to it.  I think we're consistent.

---

### Post by kevdog on 2007-08-16
Listen to noob12 -- He explains it better than me:)

---

### Post by netztier on 2007-08-16
> **noob12 said:**
> You'll need to setup a static internal ip address on the laptop that is hosting the ssh server to which you want to connect.  Then you'll need to setup the linksys router to forward port 22 to that address.   Not generally done with laptops.

To configure a static internal ip on your laptop, you use the System | Administration | Network menu item. Pick the interface.  Setup the address, netmask, gateway and dns servers.  The static address should be one that is on the same subnet, but is **not** in the pool of DHCP addresses that your linksys router assigns.



Nice and short :-)

Two more things I'd like to add:

[LIST]
[*]to test this, your SSH client has to connect *from the WAN side*! Most routers won't allow "U-turn-connections" from the LAN to the WAN IP address (and that's quite OK like that).
[*]don't use port 22 for this. On the server, edit **/etc/ssh/sshd_config** and add another "Port .." line, for example 22222. On the router, configure port-forwarding accordingly for port 22222 to the SSH server's (static) LAN IP address.
[/LIST]

Reason for not using port 22: your SSH server will soon get flooded in brute-force password cracking attempts by kids playing with nmap and nessus or viruses/worms that are scanning the IP ranges of the large broadband ISPs and are looking for unpatched or poorly configured UNIX systems.

I had my SSHd running on port 22 only for 2 days when I noticed strange activity in /var/log/auth.log. Ever since I moved it to another port, there's silence. If someone absolutely *wants* to break into *your* system, they'll find the alternative port anyway and try their tricks there. Yet, there's no need to expose it to every port scanning tool on the market, is there?

best regards

Marc

---

### Post by tobyarnett on 2007-08-16
Cool thanks for the advice. I brought both of my laptops to work with me to day so I will try to configure this for a higher level port for my ssh. I believe I saw on my linksys how to forward to a port but I will have to look at that a bit further. As for the IP's, I have already made it static. I assigned 50 of my uppers IP's to be DHCP and the lower 50 to be static (why 100 you ask - I don't know I will never have 100 IP devices in my house but oh well)

So Summary of the Steps to Complete today:

1) Edit **/etc/ssh/sshd_config** and add another "Port .." line <we'll just say 3055 for now>
[LIST]
[*]port 3055
[/LIST]
2) Open up port 3055 to outside connections, either by modifying the iptables manually, or using a GUI such as Firestarter or Guarddog.
[LIST]
[*]Haven't used these programs, I will download and figure them out but to cover my basis is there simple commands I can reference to modify the iptables for this step?
[/LIST]
3) Then testing from a WAN side IP I should be able to connect..... (which I wasn't doing last night and figured that may have been half my problem)



Am I missing anything? Thanks for the help guys much appriciated.

---

### Post by netztier on 2007-08-16
> **tobyarnett said:**
> 

2) Open up port 3055 to outside connections, either by modifying the iptables manually, or using a GUI such as Firestarter or Guarddog.
[LIST]
[*]Haven't used these programs, I will download and figure them out but to cover my basis is there simple commands I can reference to modify the iptables for this step?[/list]


Well if the system running the SSH server does not run a firewall (netfilter/iptables with firestarter or another configuration frontend) - which Ubuntu does not run by default - then you can leave this step out. 

In my personal opinion, running a client-based firewall on Ubuntu is asking for more trouble that it actually aims to prevent or solve. The amount of brainpower and time to configure, maintain and troubleshoot a local firewall is better invested in keeping a close eye on which services are actually running on the host and restricting them in a proper way - instead of "running them all" and closing/restricting them afterwards with a firewall. What isn't open doesn't have to be firewalled, after all.

As long as you are behind a NAT-Router (as every common broadband router is), half of the firewalling job is handled by that device anyway. So there might be no need to install any of these programs.

best regards

Marc

---

### Post by tobyarnett on 2007-08-16
OK I guess I hadn't even realized either of those programs were Firewall programs till just now. Typically I run my Linksys router with firewall capabilities, but I also have internal software on my computers that have firewall as well. But I guess that leads me back to the issue of needing to identify the script to be used.

So I guess now I am back to just needing to implement some scripting to allow the outbound connections and changing my port to a new desired port <such as 3055 to keep with the thread>. I grabbed this from other sites can you verify for me if this will do what I am needing?

Currently my iptables look as follows: 

```

root@generic-name:~#iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Default I suppose since I have not done anything yet.

1) Changes SSH port to 3055 and restricts sessions to 8 at a max to prevent brute force attacks
```

sudo iptables -A INPUT -i eth0 -p tcp --dport 3055 -m state --state NEW -m recent --set --name SSH
sudo iptables -A INPUT -i eth0 -p tcp --dport 3055 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP
```


2) Accepts SSH traffic on port 3055
```

sudo iptables -A INPUT -p tcp -i eth0 --dport 3055 -j ACCEPT

```


I am not sure but of the two sets of commands it seems the second is redundant? Would this work to set up my ssh for outbound connections?


Thanks,
Toby

---

### Post by tobyarnett on 2007-08-30
Aight so I ended up getting this to work a while ago, sorry but ya'll weren't too much help. 

**Simple answers was all that was required:**

after the two keys were made:

I changed the .pub to the auth...key file like the tutorial said. 
I then took the private key (id_dsa) and then used WinSCP (free program you can download by typing that in google) to copy to my windows machine (which is very common in work and school environments) 

Used Putty Key Generator and the "**Conversions**" option at the top to** Import Key** my **ppk**, and convert it to a useable WINDOWS private key. 

That was the biggest issue right there and it took forever to find. Such a simple answer!!! I am not sure why everyone on here has to be so cryptic about things. 


Anyways on putty go to the **SSH **on the left select **Auth **then "browse" for the place I stored the ppk file at. 


Oh one more thing I did have to use port forwarding on my Linksys router, that was the other stopping point.

Thank guys for the big help!?!

---

### Post by netztier on 2007-08-30
> **tobyarnett said:**
> Aight so I ended up getting this to work a while ago, sorry but ya'll weren't too much help. 


Well. you could've told us that you had been using public/private key authentication from the start...

In 9 cases out of 10, when someone describes a problem the way you did, the culprit is indeed with port-forwarding - just the way you suspected it, too.

Plus you said that within your LAN, all was well - so there was no reason to suspect SSH or its authentication mechanisms as the cause for the problem.

best regards

Marc

---

