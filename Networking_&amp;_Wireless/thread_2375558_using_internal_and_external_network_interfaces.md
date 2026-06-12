---
title: "using internal and external network interfaces"
date: 2017-10-25
forum: Networking &amp; Wireless
---

### Post by kunalv-shah on 2017-10-25
Hi All,

Just installed Ubuntu 17.10. I have two network interfaces, a. wifi and b. ethernet.

I connect wifi to one router - network 192.168.1.x and ethernet to another network 192.168.0.x. both 192.168.1.x and 192.168.0.x have internet access. I want to make sure when I browse internet, it uses 192.168.1.x and not 192.168.0.x. Basically, I want to use 192.168.1.x for internet access and 192.168.0.x for internal network use only (like connecting my ubuntu box from my laptop etc.)

Can you please suggest how do I achieve this? Sorry if this is a novice network question.  

Thanks
Kunal

```

kunalshah@kunalshah-desktop:~$ ip address
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 38:d5:47:1b:27:2d brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.16/24 brd 192.168.0.255 scope global enp3s0
       valid_lft forever preferred_lft forever
    inet6 fe80::91ff:c87b:ac4b:1be/64 scope link 
       valid_lft forever preferred_lft forever
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether ec:08:6b:fd:fe:25 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.102/24 brd 192.168.1.255 scope global dynamic wlp2s0
       valid_lft 27762sec preferred_lft 27762sec
    inet6 2405:204:9214:ed89:959d:2012:d27f:f9da/64 scope global temporary dynamic 
       valid_lft 3090sec preferred_lft 3090sec
    inet6 2405:204:9214:ed89:295:8c75:925b:6799/64 scope global mngtmpaddr noprefixroute dynamic 
       valid_lft 3090sec preferred_lft 3090sec
    inet6 fe80::cee2:40ca:30e5:d167/64 scope link 
       valid_lft forever preferred_lft forever
4: vmnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 1000
    link/ether 00:50:56:c0:00:01 brd ff:ff:ff:ff:ff:ff
    inet 192.168.10.1/24 brd 192.168.10.255 scope global vmnet1
       valid_lft forever preferred_lft forever
    inet6 fe80::250:56ff:fec0:1/64 scope link 
       valid_lft forever preferred_lft forever
5: vmnet8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 1000
    link/ether 00:50:56:c0:00:08 brd ff:ff:ff:ff:ff:ff
    inet 192.168.190.1/24 brd 192.168.190.255 scope global vmnet8
       valid_lft forever preferred_lft forever
    inet6 fe80::250:56ff:fec0:8/64 scope link 
       valid_lft forever preferred_lft forever
kunalshah@kunalshah-desktop:~$ 


kunalshah@kunalshah-desktop:~$ ip route
default via 192.168.0.1 dev enp3s0 proto static metric 100 
default via 192.168.1.1 dev wlp2s0 proto static metric 600 
169.254.0.0/16 dev wlp2s0 scope link metric 1000 
192.168.0.0/24 dev enp3s0 proto kernel scope link src 192.168.0.16 metric 100 
192.168.1.0/24 dev wlp2s0 proto kernel scope link src 192.168.1.102 metric 600 
192.168.10.0/24 dev vmnet1 proto kernel scope link src 192.168.10.1 
192.168.190.0/24 dev vmnet8 proto kernel scope link src 192.168.190.1 




```

---

### Post by TheFu on 2017-10-25
Set the "metric" to be lower for the 192.168.1.x subnet.  If you post the **route** cmd output, we can be more exact.

---

### Post by kunalv-shah on 2017-10-25
> **TheFu said:**
> Set the "metric" to be lower for the 192.168.1.x subnet.  If you post the **route** cmd output, we can be more exact.

Hi, here is the outout of route command

```


kunalshah@kunalshah-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         gateway         0.0.0.0         UG    100    0        0 enp3s0
default         gateway         0.0.0.0         UG    600    0        0 wlp2s0
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.190.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8


```

---

### Post by TheFu on 2017-10-26
You shouldn't have 2 default gateways.
The metric settings ought to handle the priorities.
The last 2 interfaces - are those local to the machine?  192.168.10.0 192.168.190.0

---

### Post by kunalv-shah on 2017-10-26
[QUOTE
The last 2 interfaces - are those local to the machine?  192.168.10.0 192.168.190.0[/QUOTE]

They are vmware virtual interfaces.

---

### Post by kunalv-shah on 2017-10-26
Hi,

based on route command output, can you please suggest what should be ideal setting (in terms of route command output) that I should configure accordingly?

---

### Post by TheFu on 2017-10-27
Remove the default route for the wifi adapter.

---

### Post by kunalv-shah on 2017-10-27
Thanks TheFu

```

[COLOR=#000000][FONT=Menlo]sudo route del default gw 192.168.0.1[/FONT][/COLOR]
``` fixed the issue.

the new routing looks like this

```


**kunalshah@kunalshah-desktop**:**~**$ route 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         gateway         0.0.0.0         UG    600    0        0 wlp2s0
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.190.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8


```

---

### Post by kunalv-shah on 2017-10-28
One final question, how do I make this change permanent? At reboot, all these changes go bye bye.

---

### Post by TheFu on 2017-10-28
From here, it appears that you removed the wrong default gateway (based on the route table). I thought you didn't want wifi to be used for internet.

To make it permanent, edit the /etc/network/interfaces file. A post-up entry should do it. Isn't that where all your settings are being made anyways?  If not, then I'd rework whatever you are doing so all of it is in that file.  I don't trust any GUI for non-trivial networking, which is what you have here.

---

### Post by kunalv-shah on 2017-10-28
Hi TheFu,

the route table is exactly how I wanted. So that is good. i checked and internet is routed through the interface I wanted. Now I want to make it permenent. My /etc/network/interface file looks like this. Do you suggest I add it at the bottom?

```

**kunalshah@kunalshah-desktop**:**~**$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
**kunalshah@kunalshah-desktop**:**~**$ 


```

---

### Post by TheFu on 2017-10-28
I cannot help if you use a GUI to control your network interfaces. Sorry.

BTW, bridging networks, like you are could be a huge security issue.  Just depends on the overall network architecture and company policies.  Where I've worked, people get fired for doing stuff like this without approval from corp-security.  Of course, it could be 100% fine at your location.  Generally, wifi needs a VPN to be secure enough to use on a corporate network.

---

### Post by kunalv-shah on 2017-10-28
Hi TheFu, I am using this at home so no worries about corporate guidelines. I think I found the solution through GUI. It was so easy but was not documented. Here is how it is done.

Login to ubuntu desktop. Go to settings->network. 

Open the connection you want only for internal resources. 

[IMG]https://ibb.co/efJh1R[/IMG]
[IMG]https://ibb.co/efJh1R[/IMG]
[ATTACH=CONFIG]277306[/ATTACH]

chose the option indicated below. "use this connection only for resources on its network"

[ATTACH=CONFIG]277307[/ATTACH]

this fixed the routing issue. Now my routing table looks like this.

```


**kunalshah@kunalshah-desktop**:**~**$ sudo route 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         gateway         0.0.0.0         UG    600    0        0 wlp2s0
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.190.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8

```
[IMG]https://ibb.co/icxEFm[/IMG]

[IMG]https://ibb.co/icxEFm[/IMG]

---

