---
title: "No internet with static ip?!"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by dvdhaar on 2009-05-03
Hi there,

I've two NIC's, one of the two if for my VirtualBox Windows machine. My interfaces file looks like this:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254

auto eth2
iface eth2 inet dhcp

```

But when using the static IP I don't have any internet!?

```

daniel@server:~$ ping www.ubuntu.com
PING www.ubuntu.com (91.189.94.199) 56(84) bytes of data.

```

When I do this, it works for some reason?!

```

sudo dhclient eth0

```

:confused:

By the way, how can I change the eth0 and eth2 names? I read I had to change the /etc/iftab file but I haven't got any?

---

### Post by JK3mp on 2009-05-03
try etc/ftab if that doesn't work...then idk. Do you have a devicde on network that forces use of DHCP?

---

### Post by dvdhaar on 2009-05-03
> **JK3mp said:**
> try etc/ftab if that doesn't work...then idk. Do you have a devicde on network that forces use of DHCP?

/etc/ftab doesn't exsists on my machine oO

Hmm not that I know of, I guess I can change the 192.168.1.100 to say 192.168.1.222 if that's what you mean? That no other device is using it?

---

### Post by Yashiro on 2009-05-03
> gateway 192.168.1.254
Are you sure that is the correct gateway?

---

### Post by dvdhaar on 2009-05-03
> **Yashiro said:**
> Are you sure that is the correct gateway?

Yes, this is on my workstation:

```

daniel@Daniel:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth1

```

---

### Post by cariboo on 2009-05-03
When using two network cards, they have to be on different subnets. If your router provides an ip address to eth2  of 192.168.1.10, then eth0 should have a static ip address of 192.168.0.10.

---

### Post by Iowan on 2009-05-03
> **dvdhaar said:**
> By the way, how can I change the eth0 and eth2 names? I read I had to change the /etc/iftab file but I haven't got any?My /etc/iftab file sez:> # This file is no longer used and has been automatically replaced.
# See /etc/udev/rules.d/70-persistent-net.rules for more information.


---

### Post by dvdhaar on 2009-05-03
> **cariboo907 said:**
> When using two network cards, they have to be on different subnets. If your router provides an ip address to eth2  of 192.168.1.10, then eth0 should have a static ip address of 192.168.0.10.

Why is that? Do you need to reconfigure your whole network just to get two nics going on one machine?! I want to have a XP box inside my Ubuntu server which runs some services linux is not able to run. How would I go about doing that?

> **Iowan said:**
> My /etc/iftab file sez:

That file doesn't exist on my machine either.. Weird..?!

---

### Post by DGortze380 on 2009-05-03
> **cariboo907 said:**
> When using two network cards, they have to be on different subnets. If your router provides an ip address to eth2  of 192.168.1.10, then eth0 should have a static ip address of 192.168.0.10.

no... that makes no sense. 

You certainly can have two cards on the same subnet.

> 
        gateway 192.168.1.254


I would check that gateway, it's odd. It should be the address of the first layer 3 device you need to hit to reach the internet, in most cases, the address of your home router.

I suggest you trouble shoot one card at a time. As you may need to add static routes to get everything working correctly, it can get confusing.

Lastly, you really don't need the second NIC for your VM, you could just do away with it, and set it up with Host-Interface Networking on your main NIC.

---

### Post by dvdhaar on 2009-05-03
This is what my interfaces file looks like at the moment. It's now working fine.

```
daniel@server:~$ cat /etc/nework/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254

#auto eth2
#iface eth2 inet dhcp

```

The only thing I noticed is I can't reach the machine trough its hostname anymore, I was always able to though..

I'm sure my gateway is 100% correct, 192.168.1.254 is my modem + router.

I haven't really dug into the networking thing in VirtualBox. I want to be able to reach the XP machine via another PC in my network. Will I be able to with Host-Interface Networking?

---

### Post by cariboo on 2009-05-03
It seems I was wrong, I've never needed two nics on the same subnet, as I've only used two nics in a router/gateway/firewall setup. After a bit of research, you can set things up the way you need using this script:

```

#/bin/sh
ifconfig eth0 down
route del default
route add default gw {ip of gateway} eth2
ifconfig eth1 up
```

Where eth0 has a static ip address and eth2 has a dynamic ip address.

I plan on giving this a try myself later on this week.

---

### Post by DGortze380 on 2009-05-03
> **dvdhaar said:**
> 
I haven't really dug into the networking thing in VirtualBox. I want to be able to reach the XP machine via another PC in my network. Will I be able to with Host-Interface Networking?

Yes, you will.

Host-Interface will allow your Virtual Machine's NIC to receive a DHCP Lease from your local subnet and be accessed as if it were a separate box on the network. Or you can, of course, set up a static address in the guest. Either way, Host-Interface and 1 NIC on the Host is the easiest way to go.


> **dvdhaar said:**
> 

This is what my interfaces file looks like at the moment. It's now working fine.

```
daniel@server:~$ cat /etc/nework/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254

#auto eth2
#iface eth2 inet dhcp

```



Just an FYI, with this config file, eth2 is not set up.

---

