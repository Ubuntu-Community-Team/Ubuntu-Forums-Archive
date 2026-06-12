---
title: "How to configure Internet sharing distributed from quad ethernet card in PC ?"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by jreinis on 2008-07-23
First, I have such scheme : 
DSL modem/router with One LAN and WAN ports connected to 
PC biult-in LAN port having 
One built-in (autonegotion) LAN port and 
Quad (4) LAN ports PCI ethernet card :: 
(Sun X1034A Quad 4-Port Ethernet Network Card 501-4366) lspci [Sun Microsystems Computer Corp. Happy Meal 10/100 Ethernet [hme] (rev 01)]

I have connected by over-crossed cable PC from Quad NIC and a laptop.

In PC I have internet. In laptop I do not have internet and I can not ping from within laptop IP addressess of PC or DSl/modem.

Scheme: 
DSL modem 192.168.1.254 /gateway and DNS 192.168.1.254, NO DHCP/
-> PC (eth0-eth4 192.168.1.15-19)
DSL connected to eth0 (built-in LAN port)
When I connect laptop to any rest (eth1-4) => no ping, no internet.

eth1-4 on Quad NIC have 4 MAC addressess.

How to configure /etc/network/.... files to get Internet sharing?



laptop 192.168.1.65

---

### Post by jreinis on 2008-07-24
> **jreinis said:**
> First, I have such scheme : 
DSL modem/router with One LAN and WAN ports connected to 
PC biult-in LAN port having 
One built-in (autonegotion) LAN port and 
Quad (4) LAN ports PCI ethernet card :: 
(Sun X1034A Quad 4-Port Ethernet Network Card 501-4366) lspci [Sun Microsystems Computer Corp. Happy Meal 10/100 Ethernet [hme] (rev 01)]

I have connected by over-crossed cable PC from Quad NIC and a laptop.

In PC I have internet. In laptop I do not have internet and I can not ping from within laptop IP addressess of PC or DSl/modem.

Scheme: 
DSL modem 192.168.1.254 /gateway and DNS 192.168.1.254, NO DHCP/
-> PC (eth0-eth4 192.168.1.15-19)
DSL connected to eth0 (built-in LAN port)
When I connect laptop to any rest (eth1-4) => no ping, no internet.

eth1-4 on Quad NIC have 4 MAC addressess.

How to configure /etc/network/.... files to get Internet sharing?



laptop 192.168.1.65

Firestarter does not help because I need at least 2 port for Internet sharing. Firestarter allows to define only One [internal] port.

---

### Post by dmizer on 2008-07-24
first, the laptop cannot be on the same subnet as the dsl gateway.  you indicated that the dsl gateway is handing out an ip in the 192.168.1.x subnet.  so your laptop and each of the other (eth1-4) adapters on your quad nic will have to be on a different subnet.  for example, like this:

pc =
- eth0 192.168.1.x
- eth1 192.168.2.x
- eth2 192.168.3.x
- eth3 192.168.4.x
- eth4 192.168.5.x

the laptop, when connected to eth1 on the PC can only have an ip address of 192.168.2.1-254.

this also means that your laptop will not be able to communicate directly with computers on the 192.168.1.x, 192.168.3.x, 192.168.4.x, or 192.168.5.x subnets (at least not without tricky configuration).

keeping the above information in mind, you should be able to follow this howto: [https://help.ubuntu.com/community/Internet/ConnectionSharing?](https://help.ubuntu.com/community/Internet/ConnectionSharing?)

---

### Post by jreinis on 2008-07-24
> **jreinis said:**
> Firestarter does not help because I need at least 2 port for Internet sharing. Firestarter allows to define only One [internal] port.

Thanks for the tip about IP addressing!!!!!!!!!

Unfortunately, second tip does not work (link to some help from Ubuntu).

Their Configuring NAT concludes some mess (mistakes) with -i eth0(1) -o eth0(1) 
It is a for sure!!!!

---

### Post by dmizer on 2008-07-24
> **jreinis said:**
> Their Configuring NAT concludes some mess (mistakes) with -i eth0(1) -o eth0(1) 
It is a for sure!!!!

humm ... the NAT configuration in the howto says:
```
sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
```
not eth0(1) -o eth0(1).  not sure why that happened, but i know that the howto works correctly because i've used it several times.

---

### Post by jreinis on 2008-07-24
> **dmizer said:**
> humm ... the NAT configuration in the howto says:
```
sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
```
not eth0(1) -o eth0(1).  not sure why that happened, but i know that the howto works correctly because i've used it several times.

The problem is each person understands meaning of the eth0,eth1 , external, outbound by itslef.
My problem is I don't understand these definition.
For me eth0 is a port connected by cable to DSl modem/router. That's it, no any ex- in etc.
Ports eth1-4 (on another NIC) connected by cables to laptops. That's it. So for me laptops (should ) be connected in subnet (thanks again):
Which one eth0 or eth1 takes which one side in commands -i -o -d -s?

DSL Modem/Router
2XX.2xx.2xx.2xx     [WAN::::::::::::::::::::LAN] 192.168.1.254
                      |phone cable           | <- ethernet cable
Phone(High-Speed Internet)[plug]             |
						| 
Computer                                     |       
                              [motherboard-[eth0] 192.168.1.1
   
QUAD NIC [eth1,          eth2, eth3,  eth4] 192.168.~ -1.1 -2.1 -3.1 -4.1 
           |              |     |      |
 laptops  192.168.~1.100  1.101 1.102  1.104         

So, from within my scheme how change help forums commands?
I don't understand, really.

---

### Post by jreinis on 2008-07-24
> **dmizer said:**
> humm ... the NAT configuration in the howto says:
```
sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
```
not eth0(1) -o eth0(1).  not sure why that happened, but i know that the howto works correctly because i've used it several times.

Another problem is I can ping but with mistake.
ip address of dsl modem/router I can not ping and more important there is no internet.

---

### Post by Endwin on 2008-07-24
Hello, from what you have said you just want the laptops to use the computer to get to the DSL router. Pretty much turning your computer into a switch/hub. For this you don't need ANY iptables stuff. Just bridge the ports (essentially make it so all the ports look like they are all on the same network) I do s simular thing to this at home. I have 1 4 port nic and a wireless card. I have eth0 go to the net I then bridge eth1, eth2, eth3, and ath0 (wireless card) together to the same network. From there someone can just put a cross over cable into my home router and get net.


Make sure you have the extra repos enabled and install

```
sudo aptitude install bridge-utils
```

Once installed just edit **/etc/network/interfaces** as root

For the setup you described since you are not using DHCP

```
auto br0
iface br0 inet static
    address 192.168.1.15
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    bridge_ports eth0 eth1 eth2 eth3 eth4

```

Once done restart the networking with...

```
sudo /etc/init.d/networking restart
```

Now just give a laptop an IP of **192.168.1.65** it should now work. Give a different IP for your other laptops.

---

### Post by jreinis on 2008-07-25
> **Endwin said:**
> Hello, from what you have said you just want the laptops to use the computer to get to the DSL router. Pretty much turning your computer into a switch/hub. For this you don't need ANY iptables stuff. Just bridge the ports (essentially make it so all the ports look like they are all on the same network) I do s simular thing to this at home. I have 1 4 port nic and a wireless card. I have eth0 go to the net I then bridge eth1, eth2, eth3, and ath0 (wireless card) together to the same network. From there someone can just put a cross over cable into my home router and get net.


Make sure you have the extra repos enabled and install

```
sudo aptitude install bridge-utils
```

Once installed just edit **/etc/network/interfaces** as root

For the setup you described since you are not using DHCP

```
auto br0
iface br0 inet static
    address 192.168.1.15
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    bridge_ports eth0 eth1 eth2 eth3 eth4

```

Once done restart the networking with...

```
sudo /etc/init.d/networking restart
```

Now just give a laptop an IP of **192.168.1.65** it should now work. Give a different IP for your other laptops.

Now I can conncet but on main PC I can get internet added
route default gw 192.168.1.1254

But on connected laptops there is not internet still...
What I do wrong?

---

### Post by Endwin on 2008-07-25
Ok so I am clear on what is going on you can ping all the computers on your network. You can ping the other laptops, the main computer, and the router. You can get on-line with the main computer but not the laptops.

If that is the case then the problem now is probably DNS setup on your laptops. For example if you ping [www.google.com](www.google.com) on your main computer you will see an IP address. If you try and ping that address from the laptops you should be able to. If not then you need to check the config of the laptops and make sure all the gateway information, subnet mask, and broadcast is all correct.

A lot of this would be simpler if you used DHCP as all the relivent information is provided via the DHCP server. Many modem/routers have this built in and since you mentioned a 192.168.1.254 as the modem/router that makes me think you have DSL, with a 2wire modem/router. 

We are assuming here that the main computer is running Ubuntu what OS are the laptops running?

---

