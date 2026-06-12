---
title: "Multiple servers on a IP class from my ISP"
date: 2014-01-08
forum: Networking &amp; Wireless
---

### Post by avaserver on 2014-01-08
Hello there.
I have a dedicated server connected with a static IP Address and a PPPOE connection. On this server i have installed Ubuntu Server 12.04 (LAMP + a control panel).
Everything works fine (web, mail, ftp services , etc).

Meanwhile i have bought another dedicated server. I spoke with my ISP and i asked for an upgrade for my internet connection. 
They told me that they can give me a class with 8 static IP Addresses and this modification can be done from their servers without any modification of the physical equipments.
That means that i have to buy a router? And if so how should i make the ip allocation so that every server to have an unique IP from that class of 8 IP`s? This means that i have to make port forwarding from my router for pointing to that 2 servers and at the same time every server to have an unique IP from that class of 8 IP`s?

How can I technically do that? 
Thanks in advance !

---

### Post by avaserver on 2014-01-08
I fount some pictures to desribe my situation:
[IMG]http://ava-design.ro/ips_static1.jpg[/IMG]

[IMG]http://ava-design.ro/ips_static2.jpg[/IMG]

---

### Post by bab1 on 2014-01-08
> **avaserver said:**
> Hello there.
I have a dedicated server connected with a static IP Address and a PPPOE connection. On this server i have installed Ubuntu Server 12.04 (LAMP + a control panel).
Everything works fine (web, mail, ftp services , etc).

Meanwhile i have bought another dedicated server. I spoke with my ISP and i asked for an upgrade for my internet connection. 
They told me that they can give me a class with 8 static IP Addresses and this modification can be done from their servers without any modification of the physical equipments.
That means that i have to buy a router? And if so how should i make the ip allocation so that every server to have an unique IP from that class of 8 IP`s? This means that i have to make port forwarding from my router for pointing to that 2 servers and at the same time every server to have an unique IP from that class of 8 IP`s?

How can I technically do that? 
Thanks in advance !

Yes you need a a router to manage your network.  The network range you have provided is incorrect however.  With IPv4 addressing and CIDR,  you still have to be mindful of the subnet boundaries.  This means you can have a network of 88.34.223.16 /29 (.16 to .23) or 88.34.223.24 /29 (.24 to .31).  You can't have some from one subnet and some from another.

The ISP will supply the WAN side IP and you use your allocation on the LAN side (6 hosts + netID and broadcast address).  There is no need to use NAT in this setup.

---

### Post by avaserver on 2014-01-08
If i don`t need NAT, means that i cand use a switcher too?
The IP`s from the picture above are not real. I copyied them from a tplink router website.

Actually my ISP gave me a subnet [COLOR=#000000][FONT=Verdana]188.xx.xxx.208/29 (8 hosts...actually 6 hosts). That means that i can use: .209/.210/.211/.212/.213.
[/FONT][/COLOR]That means that i cand use a switcher. The main cable in switch came with .208 IP so i can configure Server1 with eth0 IP: [COLOR=#000000][FONT=Verdana]188.xx.xxx.209  and Server2 with eth0 IP:[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]188.xx.xxx.210. And both server with subnet 255.255.255.248 and gateway: [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]188.xx.xxx.208.
[/FONT][/COLOR]
That sould work?

---

### Post by bab1 on 2014-01-08
> **avaserver said:**
> If i don`t need NAT, means that i cand use a switcher too?

Not sure what you mean by switcher.  The network will need a router that will connect your LAN to the ISP.  The device can have just a WAN connection and a LAN connection.  Then you would need a switch that connects to the router.  The switch is what you connect the PC's to,
> 

The IP`s from the picture above are not real. I copyied them from a tplink router website.

Actually my ISP gave me a subnet [COLOR=#000000][FONT=Verdana]188.xx.xxx.208/29 (8 hosts...actually 6 hosts). That means that i can use: .209/.210/.211/.212/.213.


The range is .208 to .215 so you have usable .209 to .214
> 
[/FONT][/COLOR]That means that i cand use a switcher. The main cable in switch came with .208 IP so i can configure Server1 with eth0 IP: [COLOR=#000000][FONT=Verdana]188.xx.xxx.209  and Server2 with eth0 IP:[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]188.xx.xxx.210. And both server with subnet 255.255.255.248 and gateway: [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]188.xx.xxx.208.
[/FONT][/COLOR]
That sould work?
Not exactly correct.  The gateway should not be the Network ID (.208).  It is the LAN side address of the router (switcher???).  The subnet mask is correct at: 255.255.255.248.  All of the IP addresses left can be used for your PC's.  The gateway address can be any of these but it is usually the first (or last) in the available range.  Remember, the netID (.208) and the broadcast (.215) should not be assigned to a device (PC, Printer, etc).

---

### Post by avaserver on 2014-01-08
So it means that:
[COLOR=#000000][FONT=Verdana][I]188.xx.xxx.208 - Network IP
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][I]188.xx.xxx.209 - Server1
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][I]188.xx.xxx.210 - Server2
188.xx.xxx.211 - Server3
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Verdana]*188.xx.xxx.212 - *[/FONT][/COLOR][COLOR=#000000][FONT=Verdana][I]Server4
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][I]188.xx.xxx.213 - Server5
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][I]188.xx.xxx.214 - Server6
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][I]188.xx.xxx.215 - Broadcast IP

And the Gateway - any ip from [/I][/FONT][/COLOR][COLOR=#000000][FONT=Verdana].209 to .214
Subnet Mask: 255.255.255.248
And how should i configure exactly my rooter with the NAT disabled? 

I was wondering if i can use only a switch (or network hub) and not a router.
Because my ISP gave me statical IP`s it is not an DHCP connection.[/FONT][/COLOR]

---

### Post by bab1 on 2014-01-08
> **avaserver said:**
> So it means that:
[COLOR=#000000][FONT=Verdana][I]188.xx.xxx.208 - Network IP
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][I]188.xx.xxx.209 - Server1
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][I]188.xx.xxx.210 - Server2
188.xx.xxx.211 - Server3
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Verdana]*188.xx.xxx.212 - *[/FONT][/COLOR][COLOR=#000000][FONT=Verdana][I]Server4
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][I]188.xx.xxx.213 - Server5
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][I]188.xx.xxx.214 - Server6
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][I]188.xx.xxx.215 - Broadcast IP

And the Gateway - any ip from [/I][/FONT][/COLOR][COLOR=#000000][FONT=Verdana].209 to .214
Subnet Mask: 255.255.255.248
And how should i configure exactly my rooter with the NAT disabled? 

I was wondering if i can use only a switch (or network hub) and not a router.
Because my ISP gave me statical IP`s it is not an DHCP connection.[/FONT][/COLOR]
The gateway is one of those IP addresses.  The device has both a ISP address interface (WAN) and a LAN interface (eth0 or somesuch).  The router (gateway) routes the ISP network to the LAN network.  So if we take your setup we would have this```

188.xx.xxx.208 - Network ID # this is the ID number of this subnet)
[COLOR="#0000FF"]188.xx.xxx.209 - Gateway (router LAN side Ethernet IP address)[/COLOR]
188.xx.xxx.210 - Server1
188.xx.xxx.211 - Server2
188.xx.xxx.212 - Server3
188.xx.xxx.213 - Server4
188.xx.xxx.214 - Server5
188.xx.xxx.215 - Broadcast IP
```

Once again the ISP address is on the WAN side of the router.  Kind of like this ```

     WAN side
          |
          |   ISP controlled 
------------------------       [COLOR="#FF0000"]<- This is the router[/COLOR]
          |
          |
          |  [COLOR="#0000FF"]**188.xx.xxx.209 **[/COLOR] <-- The Gateway!
   LAN side (your network)

```

You need a router.  You can't use a hub or plain switch.  A hub or switch only understands Ethernet.  The WAN to LAN connection works with TCP/IP to route the packets.  This is not a connection like a  phone.  This is multi layered packet switched internetworking.

---

### Post by Doug S on 2014-01-08
In my opinion, a switch could be used and a router is not needed.
I have two static IP addresses (although my ISP still makes me use DHCP to fetch and lease those static IP addresses), and I use a switch between my DSL modem and whatever I have at static IP address 1 and static IP address 2.

---

### Post by SeijiSensei on 2014-01-08
If you have never tackled something like this before, I suggest you ask the ISP for help.  I'm surprised they aren't providing you with a router as part of the service package.   

Otherwise you could use an Ethernet switch to interconnect the Internet-facing machines, and use one of the Linux machines as a NAT router for any clients you might have.  In this case, you'd have at least the Ethernet line from the ISP going into the switch, along with the public-facing ports of any servers.  All these machines should use the gateway address your ISP provides.  If you equip one of these machines with a second Ethernet card, you can create a private network behind that machine and have it act as a masquerading router.

But again, unless you have some experience with networking, get help from the ISP.  They can probably ship you a pre-configured router that you just need to drop into your network.

You'll also need to think about how to firewall this configuration.  The public-facing machines, in particular, should only have ports open for the services they offer.

---

### Post by bab1 on 2014-01-08
> **Doug S said:**
> In my opinion, a switch could be used and a router is not needed.
I have two static IP addresses (although my ISP still makes me use DHCP to fetch and lease those static IP addresses), and I use a switch between my DSL modem and whatever I have at static IP address 1 and static IP address 2.

I would assume that if the ISP assigned me "a block of IP addresses" in the form of a subnet that I would control those IP addresses (in the inside of my LAN)  The ISP then would only have control of the WAN side interface.  

What you are describing is more like a block of IP addresses in a larger network that the ISP controls.  This sounds like how the cable companies in the USA handle it.  In that case a simple switch would work.  I have my doubts about this solution as the OP did not describe it as so.

We shall see.

---

### Post by Doug S on 2014-01-08
> **bab1 said:**
> I would assume that if the ISP assigned me "a block of IP addresses" in the form of a subnet that I would control those IP addresses (in the inside of my LAN)  The ISP then would only have control of the WAN side interface.  

What you are describing is more like a block of IP addresses in a larger network that the ISP controls.  This sounds like how the cable companies in the USA handle it.  In that case a simple switch would work.  I have my doubts about this solution as the OP did not describe it as so.

We shall see.Yes, fair comment. And yes, in my case the static IP addresses are part of a bigger sub-net

---

### Post by avaserver on 2014-01-08
As far as I understand I need  a router that have the posibility  to disable NAT. In WAN config of the router i should put the static ip address, gateway, subnet mask and the two dns's that my ISP gave it to me in the first place. Then in the LAN config i have to put the ip-s from the subnet, the .248 subnet mask, .109 gateway and disable NAT. The main cable pluged in the router and then from port 1 another cable that goes into switch. And from switch another 2 cables that goes into the 2 servers. Is that correct?

---

### Post by bab1 on 2014-01-08
> **avaserver said:**
> As far as I understand I need  a router that have the posibility  to disable NAT. In WAN config of the router i should put the static ip address, gateway, subnet mask and the two dns's that my ISP gave it to me in the first place. Then in the LAN config i have to put the ip-s from the subnet, the .248 subnet mask, .109 gateway and disable NAT. The main cable pluged in the router and then from port 1 another cable that goes into switch. And from switch another 2 cables that goes into the 2 servers. Is that correct?

I think both @Doug S and @ SeijiSensei bring up valid points.  Particularly 2 SeijiSensei's point about asking the ISP about how they see it.  The ISP's viewpoint has more validity that any of us.  We can't see the upstream ISP topology.

I also think that @ SeijiSensei's thoughts on the ISP providing you with a fully configured router is something to pursue.

The configuration you mention at the top IS NOT CORRECT.  I think that until you confirm from your ISP what topology they expect we are all just guessing.  Lets not guess.  Find out what we are really dealing with.  What router are you thinking of using?

---

