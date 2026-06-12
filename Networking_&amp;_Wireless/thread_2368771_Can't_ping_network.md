---
title: "Can't ping network"
date: 2017-08-14
forum: Networking &amp; Wireless
---

### Post by stephenisa on 2017-08-14
Hi Guys

I'm new to Ubuntu and getting a hang of it! I'm trying to understand how to talk to the 10.0.0.0/24 network from 10.10.1.0/24. Below is what I'm trying to acheiev

1) Ping the 10.0.0.0/24 Network from 10.10.1.0/24 and 10.10.3.0/24 Networks

On a computer using the 10.10.1.0 network I opened the command prompt and ran tracert 10.0.0.1, the results are below

1 <1 ms <1 ms <1ms  10.10.1.1
2   4 ms   4 ms    5 ms 172.17.0.6
3   *        *         *       Request Timed Out

Our Ubuntu is hosted in AWS and it's IP Address is 172.17.0.6. 

Now here is what I can do, I can ping the 10.0.0.0 network from 10.10.2.0 network! How do I make the other 2 networks reachable? 

Happy to provide as much information as possible

---

### Post by wildmanne39 on 2017-08-14
*Thread moved to **Networking & Wireless**.*

---

### Post by Andreyshel on 2017-08-15
[COLOR=#000000]What devices does your network have?[/COLOR]
Do you have a router between [COLOR=#000000]10.10.1.0/24 and [/COLOR][COLOR=#000000]10.0.0.0/24?

[/COLOR]

---

### Post by stephenisa on 2017-08-15
Meraki MX84 as the router in each network, I was pinging the 10.0.0.0 network from a computer that is connected to the 10.10.1.0 network. I'm assuming you are referring to route instead of router? If route and since we are using Ubuntu 14.04.02 LTS what command do I run to show routes?

Thanks for your help!

---

### Post by Andreyshel on 2017-08-15
> I`[COLOR=#000000]m assuming you are referring to route instead of router?[/COLOR]
I asked if 10.10.1.0 and 10.0.0.0   were directly connected or there is another network in between?

> [COLOR=#000000]If route and since we are using Ubuntu 14.04.02 LTS what command do I run to show routes?[/COLOR]

Routes you can see with route -n command

---

### Post by SeijiSensei on 2017-08-15
A common reason for this problem is that the remote computer doesn't have a route that directs packets back to the originating server.  Let's see the results of "route -n" inside of [noparse]```

```[/noparse] tags.

---

### Post by stephenisa on 2017-08-15
Hi Guys

See below, I ran route -n after running sudo su. I had to seperate the code tags into two

```

Destination     Gateway        Genmask          Flags     Metric    Ref     Use   Iface
0.0.0.0           172.17.0.1    0.0.0.0              UG        0           0        0      eth0

```

```

Destination     Gateway        Genmask          Flags     Metric    Ref     Use   Iface
172.17.0.0      0.0.0.0         255.255.255.0   U          0           0        0       eth0

```

Thanks again for your help!

---

### Post by Andreyshel on 2017-08-16
> [COLOR=#000000]See below, I ran route -n after running sudo su. I had to seperate the code tags into two[/COLOR]
So. You have a default route to 172.17.0.1 and no other routes in your table .
That means that all traffic, will  go to 172.17.0.1.
So, if you want traffic to go via 172.17.0.1 you should see if this device is turned on and have a route either to 10.0.0.0/24[COLOR=#000000] or another intermediate network.
Hard to say something more , because you do not tell how 10.0.0.0/24 and [/COLOR]10.10.1.0/24 is physically connected.

---

### Post by shridhar-kapshikar on 2017-08-16
You will have to add the route from 10.0.0.0/24 to 10.10.1.0/24 and 10.10.3.0/24 Networks.

Please refer to below link how to add the static routes in ubuntu
[https://askubuntu.com/questions/168033/how-to-set-static-routes-in-ubuntu-server](https://askubuntu.com/questions/168033/how-to-set-static-routes-in-ubuntu-server)

---

### Post by stephenisa on 2017-08-17
Hi Guys

Thanks again for your help! 

Here is what I uncovered, the 172.17.0.0 network sits in AWS under VPC, this VPC uses IPv4 CIDR which shows 172.17.0.0/16. Now within AWS EC2 instances there are instances that run on the 172.17.0.0 network however given in Ubuntu or I should say OpenSwan traffic is routed to 172.17.0.1 but no where in AWS or anywhere else I can find this IP, I cannot ping it from a computer that sits on 10.10.1.0 or 10.10.3.0 networks.

I can ping 172.17.0.1 within Ubuntu.

As for where the devices are physically connected, with the 10.10.1.0 it sits in South Western Sydney (Australia), call this A whereas 10.10.3.0 sits in Western Australia, call this B. Each location has a server that is connected to the internet via Meraki MX84. Each Meraki has Site to Site VPN which go back to the 172.17.0.0 network via public IP, which corresponds to the Ubuntu box and uses a pre-shared key.

I can ping and access the AD on both 10.10.1.0 and 10.10.3.0 networks, the AD IP is 172.17.1.10. 

With the 10.0.0.0 network, which is what I'm trying to access from 10.10.1.0 and 10.10.3.0 network it sits in the City, call this C. It is not using a Meraki MX84 but a CISCO (I will try and find the model). The CISCO uses Site to Site VPN and connects to Ubuntu, the same design as how the Meraki MX84 are set. I added a permit in CISCO for 10.10.1.0 and 10.10.3.0 networks but should I add a route into CISCO for those two networks? 

Again thanks for your help!

---

### Post by SeijiSensei on 2017-08-17
If 172.17.0.1 doesn't have routes to the various 10/8 networks, then you probably need to add the routes there.  At the moment it appears all your traffic goes through that router.

---

