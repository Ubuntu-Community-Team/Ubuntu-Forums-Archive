---
title: "Routing on the same network"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by Pconfig on 2007-06-19
Hey all,

kind of a strange title i now. But couldn't think of a better one. I've been searching around abit about setting up a computer as router. Now, i've got a normal router at home but it limits access to internet to 4 computers. I can't change it. It's baked into the firmware for my ISP specific router. So i actually want to let my ubuntu server tap of the internet from the router and distributed it over then network. I can only find manuals with 2 different netwok cards.
I think this should be possible.

Basicly it's something like this:

```

Modem
    ||
Switch  == Client 1 
    ||     == Client 2
Server

```

And both of the clients connect to the internet threw the server. Is something like this possible? If so, some hints would be welcome.

Thanks

Now i've got a ubuntu server running in the basement.

---

### Post by Pconfig on 2007-06-19
Could some kind of proxy server fix the problem maybe?

---

### Post by dannyboy79 on 2007-06-19
> **Pconfig said:**
> Hey all,

kind of a strange title i now. But couldn't think of a better one. I've been searching around abit about setting up a computer as router. Now, i've got a normal router at home but it limits access to internet to 4 computers. I can't change it. It's baked into the firmware for my ISP specific router. So i actually want to let my ubuntu server tap of the internet from the router and distributed it over then network. I can only find manuals with 2 different netwok cards.
I think this should be possible.

Basicly it's something like this:

```

Modem
    ||
Switch  == Client 1 
    ||     == Client 2
Server

```

And both of the clients connect to the internet threw the server. Is something like this possible? If so, some hints would be welcome.

Thanks

Now i've got a ubuntu server running in the basement.
not sure exactly what you're trying to accomplish as I have never ever heard of any router restricting the internet access to only 4 computers. Are you saying that you have tried to put an additional switch hooked to one of the ports on the router, then hooked computers to each 1 of those ports and then you're saying that only 4 of the computers could hae internet access? How many ports does your router have? My setup at home is like this

Modem > 5 port Router/Switch Combo 
                (1 port is obviously the modem in)---|>Computer
                                                                          |>Computer
                                                                          |>Computer
                                                                          |>5 port switch > 5 Additional Computers

So as you can see, I can have a total of 8 internet connected computers. If in fact what you say is true with your ISP provided Router and you don't want to use it all, than what you can do is get  a distro that specifically designed to be a router (monowall, smoothwall and many others, check them out here: [http://www.neowin.net/forum/lofiversion/index.php/t425156.html](http://www.neowin.net/forum/lofiversion/index.php/t425156.html)), then you will only have to have 2 NIC cards, and the switch will be connected to 1 of the nic cards and the modem will be plugged into the other one. So what would happen is basically your "server" would now be a router and it would protect your inside network from the nasty internet. 

but as I said I don't think all this is neccessary. if you currently have a switch, hook it up to one of the ports on your ISP provided router and hook all your computers from there and this should work. If it doesn't, then most likely you need to modify the DHCP server settings within the ISP provided router. If this is what you're saying you can't change, then that's totally stupid!!! And you'll have to either buy another router which has a built in dhcp server OR you have to set up a linux distro to act as a DHCP server BUT you can still always use the ISP provided Router to protect you from the nasty internet. good luck

---

### Post by Pconfig on 2007-06-19
Hey

first of all thanks for the reply.

The wan bridge really is limited to 4 users only. 1 computer gets obsoleted when all 5 try to connect to the internet. Firefox shows me the message then.

And i didn't connect a switch to the router, i was just trying to sketch the situation. It's basically a 4 port router with wireless abilities. So i have 4 wired computers and 1 wireless computers.

Would be a shame if i had to buy a new router just because of this. I think it can be fixed softwaremagically only :) I've got the proxy server up and running on my server now. It needs a little more configuring and i think i'm settled.

Unless anyone has a better suggestion of course.

---

### Post by dbott67 on 2007-06-19
What's the make & model of the router?  Perhaps the firmware can be updated/modified/hacked to "unlock" it.

-Dave

---

### Post by dannyboy79 on 2007-06-19
ok, so you're saying that your wireless router/switch has 4 ports on it and that when you try to use the internet with 4 wired ports and 1 wireless you;re saying that 1 doesn't work with the internet, is this because it's not getting an IP address? what does 
ifconfig
of the computer that doesn't work show? So I am guessing that your dhcp server of your ISP router is only able to hand out so many IP's which can be fixed by changing the settings IF you can. If you can't then like I said, you have a few choices. I don't know what a Proxy server is going to do for you?? Are you aware of what a Proxy Server does?

---

### Post by Pconfig on 2007-06-19
> **dannyboy79 said:**
> ok, so you're saying that your wireless router/switch has 4 ports on it and that when you try to use the internet with 4 wired ports and 1 wireless you;re saying that 1 doesn't work with the internet, is this because it's not getting an IP address? what does 
ifconfig
of the computer that doesn't work show? So I am guessing that your dhcp server of your ISP router is only able to hand out so many IP's which can be fixed by changing the settings IF you can. If you can't then like I said, you have a few choices. I don't know what a Proxy server is going to do for you?? Are you aware of what a Proxy Server does?

It's not that it doesn't get an IP. The network works fine on the computer. I can access other computers in the network, it's just my internet connection that taken away.

When i go to a page, it automatically get redirected to:
[http://192.168.1.1/Redirect/WANUsersOverLimit](http://192.168.1.1/Redirect/WANUsersOverLimit)

That pages tells me:
```

Configured WAN/Internet User Limit Exceeded

Your Gateway is currently configured as a 4 WAN/Internet User Version.

Please contact your Service Provider if you require additional concurrent WAN/Internet users.

```

Hacking the firmware might work (and probably will) but i've got no clue on how to do that.

If i check the firmware page, it says:

To update your software from a file on your PC, you must first download the software from:

[http://www.netopia.com/belgacom/](http://www.netopia.com/belgacom/)

Belgacom is my provider, so it seems that they created this model of router only for my ISP. There are some other firmware versions on the netopia site that are made for bulk routers but i'm not sure if i'll break my router when i flash one of those on it. Any ideas?

Thanks

Edit:
Ok, seems like my router has a telnet client. I'm currently going threw the options as they are undocumented.

Already got the output

show wan-users

Number of allowed concurrent WAN users: 4
Number of WAN connections currently in use:  2

Might get there afterall :)

Edit2:
Ok, after some more searching i found this page:
[http://www.netopia.com/equipment/purchase/fmw_update_intl.html](http://www.netopia.com/equipment/purchase/fmw_update_intl.html)

I've got a 3357 WEU-BC ADSL router. Now, if i flash the firmware on it from another provider, would it still let me connect to the internet? Or could i flash a bulk version of 3347 on the router?

---

### Post by Dudeman02379 on 2007-06-19
It sounds to me like the router they gave you has traffic filters to limit only 4 connections at a time to port 80.  They probably do that to limit the amount of bandwidth that you use.  You may want to try logging into your router through a web browser and see if there is any configuration that you can do.  I'm sure you could just throw on a new router and solve the problem.  Also maybe use a proxy that does NAT to mask your local network addresses.

---

### Post by Mr. C. on 2007-06-19
A NAT-ing router behind the ISPs router will solve the problem.  You can setup your server to perform a similar function.

Your broadband router limits based upon the MAC addresses it sees.

MrC

---

### Post by airtonix on 2007-06-20
1. connect your "basement-ubuntu"(BU) via its ethernet card 1(eth0) to the routers ethernet port.

2. connect a multiport switch via one of its ports to the ethernet car 2 of BU (eth1) 

3. plugin your extra computers into the switch...the IP you can use for any computer connecte don this switch will be between 10.1.1.10-10.1.1.50.

4. the Bu ethernet port that connects to the switch will be 10.1.1.1, and this ip will be the gateway address for each computer on the switch.

5. the IP of BU that connects to the router(internet)...will be 192.168.0.2

6. the router IP will be 192.168.0.1

7. install and open firestarter on BU

8. open main preferences,....select network-settings...then select eth1 as your local network card and eth0 as your internet-connected-device or wide-area-network.

9 dont bother with dhcp for now (ignorance is only bliss if you have cash.)

10. the gateway address of the eth1card will be the ip address of the eth0 card.

---

### Post by dbott67 on 2007-06-20
> **Pconfig said:**
> I've got a 3357 WEU-BC ADSL router. Now, if i flash the firmware on it from another provider, would it still let me connect to the internet? Or could i flash a bulk version of 3347 on the router?

I did a little reading up on the Netopia website about that router.  It appears one of the features of the router is the capability of "Automatic Provisioning":
> **Automatic Provisioning.** Upon initial power-up, Netopia 3300 Series gateways can be configured to "phone home" by contacting a pre-designated auto-configuration server (ACS), such as the [Motorola Netopia Broadband Server (NBBS)]("http://www.netopia.com/software/products/nbbs/index.html") service management platform or another TR-069 ACS. Without subscriber intervention, services are provisioned, gateway software configured, and the correct services activated. This real-time provisioning also helps streamline inventory management by leveraging a common hardware platform that can be customized upon activation.

In essence, they can remotely configure the router to meet the level of service that you are paying for.  Flashing the BIOS may be breaching your TOS and it's quite likely that they would know right away.

I recommend Mr.C.'s advice --- another NAT router connected to one of the 4 ports should do the trick.  Most NAT routers like D-Link, Linksys & Netgear can handle up to 253 devices without any restrictions.

-Dave

---

### Post by dannyboy79 on 2007-06-20
> **dbott67 said:**
> I did a little reading up on the Netopia website about that router.  It appears one of the features of the router is the capability of "Automatic Provisioning":


In essence, they can remotely configure the router to meet the level of service that you are paying for.  Flashing the BIOS may be breaching your TOS and it's quite likely that they would know right away.

I recommend Mr.C.'s advice --- another NAT router connected to one of the 4 ports should do the trick.  Most NAT routers like D-Link, Linksys & Netgear can handle up to 253 devices without any restrictions.

-Dave
couldn't he just make his ubuntu box a NAT router using iptables?

---

### Post by dbott67 on 2007-06-20
> **dannyboy79 said:**
> couldn't he just make his ubuntu box a NAT router using iptables?

Absolutely.  Although he would need a switch or hub of some sort; dual NICs in the Ubuntu box; etc.  When you figure out the cost of a cheap NIC and 4-port hub/switch it may be better to just spend a few extra bucks and get wifi, a nice web-based, easy-to-use interface, and a few other features.

-Dave

---

