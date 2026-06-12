---
title: "network not working, SIOCADDRT: Network is unreachable"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by matt91 on 2007-01-11
i am trying to configure my static network under ubuntu. i am using the same configuration of that on my ms system which it works with. when i start the network with /etc/init.d/networking restart i get:
> 
matt@LINUX2:~$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                         
SIOCADDRT: Network is unreachable

Failed to bring up eth0.


my /etc/network file is:
> 
auto eth0
iface eth0 inet static
address 10.0.0.2
gateway 192.168.1.254
netmask 255.255.255.0


and /etc/resolv.conf is:
> 
search MSHOME
nameserver 62.6.40.178
nameserver 194.72.0.98
nameserver 192.168.1.254


the problem seems to be DNS related as i can still access ip addresses on my network. the first two DNS servers are my isp's, and the third is my router.
i can use DHCP but i like to specify everything manually.

---

### Post by spd106 on 2007-01-11
Your static IP address is rather unconventional. Try specifying an address in the 192.168.1.x range or consider a different gateway or subnet mask.

---

### Post by matt91 on 2007-01-11
i have changed the ip and it now does work. i dont understand however that a similar setup on my windows os works and that the ip's assigned by DHCP are basicly the same as what i am setting static.

---

### Post by anotherbigal on 2007-02-06
Hi,
I am getting the same problem while trying to install 6.10 server. All very confusing to someone who has never done anything like this before (vi is a challange quite apart from anything else).
 My file reads: (the #s are mine and only in this post)

auto eth0
iface eth0 inet static
address 192.168.0.10         # this should be the machine ip I think
netmask 255.255.255.255
network 192.168.0.1           # My router ip
broadcast 192.168.0.255    # is that correct?
gateway 192.168.1.254      # my gateway to the world

I cannot ping into or out of this machine, but the router (Netgear DG834) correctly lists it as an attached device
 Any help to this very green newbie will be appreciated

---

### Post by spd106 on 2007-02-06
Try these changes
```
auto eth0
iface eth0 inet static
address 192.168.0.10 # this should be the machine ip I think
netmask 255.255.255.[COLOR="Red"]0[/COLOR]
[COLOR="Red"]# [/COLOR]network 192.168.0.1 # My router ip
[COLOR="Red"]# [/COLOR]broadcast 192.168.0.255 # is that correct? 
gateway 192.168.[COLOR="Red"]0.1[/COLOR] # my gateway to the world
```

This assumes that the router will forward all outbound packets/DNS requests to the gateway.

Surely you have nano installed? It's far simpler to use for those new to terminal based text editors, though obviously not as powerful as the mighty vi (or emacs).

---

### Post by anotherbigal on 2007-02-07
Hi again, and thank you for your help.
I tried the alterations you suggested but no luck. The same error messages comes up:

*Reconfiguring network interfaces...
SIOCADDRT: Network is unreachable
Failed to bring up eth0

I tried making the two alterations you suggested as a pair, then individually, but always the same result.

I believe The gateway, 217.32.86.142 is what the router uses to access to outside world, but I am probably wrong. There is quite a learning curve going on here. The router also shows 255.255.255.255 as the subnet mask. Additionally, there is also a listing that says "ip address 86.128.77.52"

Any suggestions as to where else I should look to change other settings if need be please? I have got a small Windows peer to peer network going on here with 4 machines and a couple of printers running on it. I wanted to set up the new box as a server so I could host my own MySql database and lean PHP. As well as possibly hosting a small website and internal email to us all.

---

### Post by spd106 on 2007-02-07
The 217.32.86.142 address is of BT's router which you are connected to for the broadband access. Your router has an internet viewable (external) address 86.x.x.x. This is useful information that you really shouldn't give out unless you want DoS attacks.

However none of the above should have any bearing on the internal network. You should have two network interfaces on the router. One connects to the broadband (external) and the other connects to the internal network. You will have NAT running on your router which changes the addresses to the 192.168.0.0 network. 

The address of the router's internal interface is 192.168.0.1 with a subnet mask of 255.255.255.0 and all of the other machines will have an address of 192.168.0.x with the same subnet mask.
You don't need the network or broadcast line in the interfaces file, as you will be using the defaults, unless you really know what you are doing. However if you must specify them put the network address as 192.168.0.0.


If you have DHCP running then you must be sure to set static addresses outside of the DHCP address pool. eg if you have an address pool of 192.168.0.1 - 192.168.0.9, then set the server to a static address of 192.168.0.10. This way you won't get any address conflicts.

---

### Post by anotherbigal on 2007-02-07
Hey it worked!

I took out the two network and broadcast lines the reset the gateway to the router ip and bingo.

Thank you

---

### Post by skeeler on 2007-08-23
Hello.

I am having a very similar problem, and I'm hoping you can help me.

I have an wired/wireless network running in my home using a WRT54G router.
The router is configured thus:
Internal IP address:  144.144.144.144 <- This is much easier to remember than the default.
Netmask 255.255.255.248 <- This allows me to limit the number of computers on the network.
Starting DHCP address 144.144.144.147 <- This leaves room for a couple of static addresses.
DNS servers:  68.87.73.242 and 68.87.71.226 <- From Comcast.

One Wndows laptop is assigned an address by DHCP.  That works fine.
Another Windows laptop has the static address 144.144.144.146.  That also seems to work.

On my Linux desktop, I've installed Ubuntu 7.04 server edition, which means I don't have the GUI running.  It is NOT a dual-boot machine.  My plan is to set this up as a web server (and eventually, a remote dog-talking-to and dog-feeding machine).  The machine has both a wireless card and an integrated (Realtek) wired ethernet adaptor.  I'm wired into the router and planning to use that connection. 

I'm trying to follow this guide to setting up a web server:

[http://www.ubuntugeek.com/ubuntu-704-feisty-fawn-lamp-server-setup.html]("http://www.ubuntugeek.com/ubuntu-704-feisty-fawn-lamp-server-setup.html")

During installation, it complained that it could not reach the network, so I set up the IP info manually.  

I edited my /etc/networkk/interfaces file to look like this:

```

auto eth0
iface eth0 inet static
    address 144.144.144.145 <- This should be in the static range of my router. 
    netmask 255.255.255.248 <- Same as the router's and every other computer on the net.
    gateway 144.144.144.144 <- Router address.

```

As was suggested to anotherbigal---Hmph, I just now bothered to parse that name---I cut out the broadcast and network lines.

When I tried to restart my network, I got this, just like the OP:
```

# /etc/init.d/networking restart

* Reconfiguring network interfaces...
SIOCADDRT: Network is unreachable
Failed to bring up eth0.

```

FYI,I've edited my /etc/resolv.conf file to look like this:

```

nameserver 68.87.73.242
nameserver 68.87.71.226
nameserver 144.144.144.144

```

Here's the relevant (I think) excerpt from the output of ifconfig.  (Having no internet on that machine makes it hard to past it to you.)

```

...
eth0   Link encap: Ethernet Haddr 00:0E:A6:C4:60:C0
          inet addr:  144.144.144.145 Bcast 144.144.144.151 Mask 255.255.255.255.248
...

```

That all seems right to me.

Here's  snippet from the output of iwconfig:

```

lo        wireless extensions.
eth0   no wireless exensions.  <- This has me worreied.
ra0    <a bunch of stuff> 

```

Here's (I think) the important part of the output of lspci:

```

...
02:05.0 Ethernet controller:  Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
...

```

I actually looked at the Realtek site, and the only driver I could find for Linux seems to be unavailable.

I'm really frustrated with this problem, and I would greatly appreciate any guidance you could lend me.

---

### Post by spd106 on 2007-08-24
The problem with the netmask you have chosen is that it is only allows for five usable addresses. The first and last addresses are reserved for network and broadcast, so you cannot use 144.144.144.144 or 144.144.144.151. This is indicated in the ifconfig output too.

The fact this you are not using a reserved address range does make this a little odd, but as your not connecting to the Internet it shouldn't be a problem.

The Realtek card is standard wired Ethernet, so it shouldn't have wireless extensions working. This card is quite common and should just work. 

The wireless card is the RaLink one and is called ra0, which is normal. See [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500) for more information.

---

### Post by skeeler on 2007-08-24
spd106,

Yes, I've chosen that netmask specifically so that I only have 5 usable addresses.

What do you mean when you say I'm not using a reserved address range?  I am trying to connect to the internet, so if this is a problem, I need to know.

---

### Post by spd106 on 2007-08-24
Yes, well, that means you can't use 144.144.144.144 as a device's address. You will have to shift the gateway to .145 instead.

The problem with the 144.144.144.144/29 range you are using is that it can cause routing problems. If you are using a NAT device, then you should be using a private address range instead. [http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)

They're not all that hard to remember once you get used to them and once it's up and running you can forget about it.

---

### Post by skeeler on 2007-08-24
spd106,

Ah, I think I see what you mean now.  I'll try renumbering tonight and see if that works.

Thanks for your help.

---

### Post by skeeler on 2007-08-25
I followed spd106's suggestion and changed my network to more conventional settings.  My /etc/networkk/interfaces file now looks like this:


auto eth0
iface eth0 inet static
    address 192.168.0.2
    netmask 255.255.255.0
    network  192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.1

Now, everything seems to be working.  I'm downloading the GUI files as I write this.

Thanks!

---

