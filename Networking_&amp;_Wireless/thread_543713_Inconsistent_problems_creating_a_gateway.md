---
title: "Inconsistent problems creating a gateway"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by mcaycedo on 2007-09-05
Hi,

I have inconsistent problems when I try to assign a gateway to one of the machines in my network.  Here are the details of what I am trying to accomplish:

- I have a network of 9 Dell E521 pc with Ubuntu 7.04 desktop installed in each machine.
- They are all connected via 1GB switch and each machine has 1GB cards (Intel pro 82540EM)
- All machines are set up with fixed ip address with 10.6.25.2xx as range.
- In one of the machines I enabled the 100mb built-in network card and plug the incoming ethernet from ISP in it.  The other card (Intel pro 1GB) is connected to the switch.  The one connected to the ISP has an address 10.6.25.212 as eth0 and the one to my internal network has an address 10.6.25.213 as eth1.
- I followed the instructions in [http://www.debian-administration.org/articles/23](http://www.debian-administration.org/articles/23) describing how to create a gateway in debian but I get inconsistent results.
- I modified the script he describes to create the firewall and placed it in the /etc/network/if-up.d directory to run but that does not seem to work.  The way I sometimes get it to work is by not having the 00-firewall in the suggested directory and just when the system is up I just run it manually with sudo control.
- What I am trying to get is a proxy server, such Squid, installed but if I understand correctly I must have it running as gateway first.  Can someone help me out on this?

---

### Post by guardsman85 on 2007-09-05
> **mcaycedo said:**
> 
- All machines are set up with fixed ip address with 10.6.25.2xx as range.
What subnet mask are you using?  You'll not want to use two addresses on the same subnet for your internal and external cards.

> **mcaycedo said:**
> - In one of the machines I enabled the 100mb built-in network card and plug the incoming ethernet from ISP in it.  The other card (Intel pro 1GB) is connected to the switch.  The one connected to the ISP has an address 10.6.25.212 as eth0 and the one to my internal network has an address 10.6.25.213 as eth1.
- I followed the instructions in [http://www.debian-administration.org/articles/23](http://www.debian-administration.org/articles/23) describing how to create a gateway in debian but I get inconsistent results.

The Debian tutorial has eth1 as the external card and eth0 as the internal.  

> **mcaycedo said:**
>  - What I am trying to get is a proxy server, such Squid, installed but if I understand correctly I must have it running as gateway first.  Can someone help me out on this?
OK, what all do you want your proxy server to do?  If you want a basic NAT box, then we can probably simplify this without using Squid.  If you want to cache pages, then we may need it.

---

### Post by KCPokes on 2007-09-05
Additionally, if you are creating a gateway, you do NOT want to be running the desktop install.  There are far too many packages installed, by default, to expose that machine to constant internet traffic.  To run a gateway, you should start with a basic server install and add only the necessary packages as you proceed.  At the very least it is a matter of routing; internal IP on the gateway will be the default gateway for all other machines.  Then it is a matter of setting your routing table on your gateway to handle the traffic accordingly. 

Now since you do not have a router in front of your gateway, be aware that without the proper packages,you do not have a firewall solution in place.  I'd recommend getting basic routing done first, secure your network from external traffic, at which time you can start to introduce additional services, such as Squid, Snort, etc...

---

### Post by mcaycedo on 2007-09-05
Hi,

Thanks for your responses.  I do have the two network cards with the same subnet, 255.0.0.0. Which one should I change and what value do you recommend?
I reversed the values used in the debian tutorial, eth0 for external (100MB) and eth1 for internal (1gb going to my network sw).
All I am trying to do is used one of the machines for internet traffic and do caching since our ISP is not a fast one and would like to speed up the traffic.
Could I get away with the desktop since that machine needs to be used, I do not have a dedicated machine for that.

I also just got the following message in the /var/log/messages

NETDEV WATCHDOG: eth0: transmit timeout
b44: eth0: link is down
b44: eth0: link is up at 100Mbps, full duplex
b44: eth0: flow control is off for TX and off for RX

I also got the following message in a os window I had opened:
baycom12-desktop Kernel: (2739.238717) disabling IRQ #7

In the ifconfig, IRQ7 happens to be the one assigned to eth0 (external card)

This error came up after I went out for lunch and came back, aprox 1 hour.

Please advise.

---

### Post by KCPokes on 2007-09-05
255.0.0.0 is your netmask, not subnet, so that is causing a bit of confusion.  For a class C network, which is what you are running internally, you are going to have a netmask of 255.255.255.0.  That is really only important if you are assigning your machines static IPs, which at the gateway you'll have at least one.  There needs to be a difference between your internal network and external, thus both of your NICs cannot be on the same subnet, in this case 10.6.25.XXX.  

You have decided to use 10.6.25.XXX as your subnet, which means that your ETH0 (internal) should have an IP of 10.6.25.1, as it'll be your default gateway for your internal network.  ETH1 (external), if it is hooked up directly to your modem, should have a public IP assigned by your ISP.  This is all assuming your configuration as I don't know whether there is other hardware between your gateway and your modem.  The IP cannot be on the 10.XXX.XXX.XXX range because these are private IPs that will not resolve on the internet.  ETH1 should be set up as DHCP unless you have a static IP assigned to you, which means you will not need to set the netmask.  

Once you've set up your two interfaces your last task is to ensure routing rules are in place.  Essentially you'll set up a default route to use your ETH1 interface, while setting a route to direct all 10.6.25.* traffic to use the ETH0 interface (could really just say 10.*.*.* since all 10-dot addresses would have to be internal).  For example, if your ISP assigned you 66.33.62.171:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.6.25.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
66.33.0.0       0.0.0.0         255.255.240.0   U         0 0          0 eth1
0.0.0.0         66.33.0.1       0.0.0.0         UG        0 0          0 eth1

```

This is just an example, thus yours may, or may not, need some tuning to make it work correctly.

---

### Post by mcaycedo on 2007-09-05
I must thank you first for your time and understanding.  Here is the description of what I have.  The ISP has given me and IP address of 10.6.25.1 and told me to use it as my gateway.  In my initial setting I assigned fixed ip addresses to each of the machines such as 10.6.25.201/212 and everything worked fine, they were able to access the internet.  Since my ISP is actually satelite (I am located in an Island in the Caribbean) I wanted to speed up the browsing and was told to use a proxy such as Squid.  Researching the net I came accross the debian article in how to set a gateway to set up a proxy and followed it.  So far I have only tried to do the Gateway.
In the pc with a network address of 10.6.25.212 (eth0 external) I added another network card as 10.6.25.213 and used it as internal (eth1).
I am using a net mask of 255.0.0.0 in all of them.  With this actual numbers what do you suggest that I do to fix my problem?

eth0 (10.6.25.212 is configured as external with a gateway as 10.6.25.1 from my ISP
eth1 (10.6.25.213) is configured to go into the router ans the gateway is 10.6.25.213

As you can see I am not an expert and need guidence since I do not have local help that I can find.

Thanks a lot with all your help.

---

### Post by KCPokes on 2007-09-05
> **mcaycedo said:**
> I must thank you first for your time and understanding.  Here is the description of what I have.  The ISP has given me and IP address of 10.6.25.1 and told me to use it as my gateway.  In my initial setting I assigned fixed ip addresses to each of the machines such as 10.6.25.201/212 and everything worked fine, they were able to access the internet.  Since my ISP is actually satelite (I am located in an Island in the Caribbean) I wanted to speed up the browsing and was told to use a proxy such as Squid.  Researching the net I came accross the debian article in how to set a gateway to set up a proxy and followed it.  So far I have only tried to do the Gateway.
In the pc with a network address of 10.6.25.212 (eth0 external) I added another network card as 10.6.25.213 and used it as internal (eth1).
I am using a net mask of 255.0.0.0 in all of them.  With this actual numbers what do you suggest that I do to fix my problem?

eth0 (10.6.25.212 is configured as external with a gateway as 10.6.25.1 from my ISP
eth1 (10.6.25.213) is configured to go into the router ans the gateway is 10.6.25.213

As you can see I am not an expert and need guidence since I do not have local help that I can find.

Thanks a lot with all your help.

I'm still a bit confused, not by the description but more as to how/why your ISP would be set up this way.  The glaring change you need to make is that your internal machines need to move to a different network subnet; routing is going to be impossible since they are going to try to ARP locations, bypassing the routing rules.  If you left ETH0 alone and set ETH1 to 192.168.1.1, with all the other machines set to something on the 192.168.1.xxx subnet, adjusted your routing rules, as I've shown you above, you should be able to get out. 

Couple things that you need to keep in mind though.  You need to set up your network config, on your gateway machine, to point to the DNS servers from your ISP.  To speed up the process you should be able to point your other machines DNS lookup to 192.168.1.1, although you could also point them to your ISPs DNS servers, if you are so inclined.  

Your internal machines will have a gateway of 192.168.1.1 and a subnet of 255.255.255.0 (class C network).  

So to summarize, your external card will stay the same, with a gateway of 10.6.25.1, while your internal card needs to move to a different subnet, preferably 192.168.1.xxx.  Configure your routing rules and you should be ready to start shaking out the bugs.

---

### Post by mcaycedo on 2007-09-05
Great!  I am going to make the changes according to your solution and I will let you know how it goes.  I just have one more question regarding the routing rules.
How do I create or modify the routing rules? where is that kernel ID routing table?

Thanks a lot!

---

### Post by mcaycedo on 2007-09-05
I also forgot to ask you about the script is defined in the debian page.  Should I use it? if yes, where should I place it to run.

Thanks,

---

### Post by KCPokes on 2007-09-05
> **mcaycedo said:**
> I also forgot to ask you about the script is defined in the debian page.  Should I use it? if yes, where should I place it to run.

Thanks,

Absolutely use it.  It is the core of your system as its going to provide you 1) a level of protection from incoming packets, and 2) is going to put in place the ability for your internal card to forward the internal traffic to your external card.  Would have helped if I would have read that previously!  :oops:

With the script you will not need any routing rules as it will take care of it.  Essentially what I was trying to accomplishing with a bunch of routing the script is providing "out of the box".  Follow the explanation on the page and install the script in your /etc/network/if-up.d/ directory.  

Let me know how it goes.

---

### Post by mcaycedo on 2007-09-06
KCPokes,

Thanks for your help.  I followed the instructions and placed the script in the /etc/network/if-up.d directory and worked good.  I have another problem, it seems that my eth0 card times out as I can see in the messages file.  Please review my reply #4 as I explained the actual message I got.  When that happens, the whole access goes down.  Any suggestions?

---

### Post by guardsman85 on 2007-09-06
OK, I found [another forum]("http://tinyurl.com/2vypwr") which may be able to help.  It seems that some people have problems with Advanced Configuration and Power Interface (ACPI) settings causing the NIC to be killed.  You could try booting with the apci=off setting.

When your system boots and you see the grub menu hit the *Esc* key.
At the menu, hit *e* to edit your boot options.
At the next menu, arrow down to the *kernel* line.
Hit *e* again.
Arrow right to the end of the line and type [I]acpi=off
[/I]Hit *Enter*
Hit *b* to boot

We'll see if that works and then make it permanent if we need.

---

### Post by mcaycedo on 2007-09-10
KCPokes,

I wanted to tell you that I ended up bringing a person with knowledge in networks and found a problem with my Intel pro card.  He was also able to configure the gateway and installed Squid for me.  Things are running smooth and I wanted to thank you for your help and prompt responses.

---

