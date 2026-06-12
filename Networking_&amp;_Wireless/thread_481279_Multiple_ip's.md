---
title: "Multiple ip's"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by didijeeeke on 2007-06-22
Hey,

In windows 2000/xp i am able to set more then 1 ip per NIC.
Is there a way to do this in ubuntu.

---

### Post by spd106 on 2007-06-22
Sure. 

The old way to do this was by creating a kind of virtual interface called an alias. For example if your main interface is eth0, then you would create eth0:0, eth0:1 etc. each with their own IP address. The normal use for this would be for the host to be connected to multiple networks.

The ifconfig man page goes into detail about how to create and manage these interfaces, you can automatically bring them up in the /etc/netowork/interfaces file just as any other interface. 

One word of warning as far a naming goes, I have read about problems in some cases when bizarre names are used, so I suggest that you stick to simple numerics as described above.

As the ifconfig tool supposed to be deprecated in favour of [iproute2]("http://linux-net.osdl.org/index.php/Iproute2"), you might want to use the ip command instead. The problem with this is that ifconfig can only show one address configuration, so it can be confusing. So if you start with iproute2, then stick with it. Ubuntu includes both and will continue to do so for some time yet.

---

### Post by didijeeeke on 2007-06-23
> **spd106 said:**
> Sure. 

The old way to do this was by creating a kind of virtual interface called an alias. For example if your main interface is eth0, then you would create eth0:0, eth0:1 etc. each with their own IP address. The normal use for this would be for the host to be connected to multiple networks.

The ifconfig man page goes into detail about how to create and manage these interfaces, you can automatically bring them up in the /etc/netowork/interfaces file just as any other interface. 

One word of warning as far a naming goes, I have read about problems in some cases when bizarre names are used, so I suggest that you stick to simple numerics as described above.

As the ifconfig tool supposed to be deprecated in favour of [iproute2]("http://linux-net.osdl.org/index.php/Iproute2"), you might want to use the ip command instead. The problem with this is that ifconfig can only show one address configuration, so it can be confusing. So if you start with iproute2, then stick with it. Ubuntu includes both and will continue to do so for some time yet.

Wath do you mean normal use is for the host to be connected to multiple networks ?
Do you mean a seperated layer 1 networks. 
Or do you mean the host is connected on 2 layer 3 networks like i want to do ?

Anyway I wil try this vitrual ip's.

---

### Post by kenweill on 2007-06-23
> **didijeeeke said:**
> Hey,

In windows 2000/xp i am able to set more then 1 ip per NIC.
Is there a way to do this in ubuntu.

I didn't know that... How did you do that in Windows XP?

---

### Post by didijeeeke on 2007-06-23
Quite easy. 
You got to the properties of the network nic you want to configure.
Then you select the tcp/ip protocol.
You wil see under your currented ip settings a advaced settings button.
Then you will have the option to add a ip adress. 

I did this out of my head so i might have mistaken me.

Wel anyway most poeple think for some weird reason that your network card assings the ip to the network.
This is not correct the only thing your nic does is working on layer 2 and 1. 
(ok some high end may also have a layer 3 part to save the main cpu but i mean basic cards)
So in other words the operating system listens for the network adress
(again don't schoot me i mean basic cards)

example a host sends a packet adressed to your host. 
This package contains your mac adress.
Your ip.
And some upd data.

Your network card who is reading the network for packages non stop.
Detects a package with it's mac adress in it.
So it says to the operating system: hey stop i got a package.
Next thing the operating system wil do is have a look at that package and see wath ip it contains.
So this is the part (layer 3) why the operating system is able to listen on more then one ip.

---

### Post by spd106 on 2007-06-23
[QUOTE=didijeeeke]Wath do you mean normal use is for the host to be connected to multiple networks ?
Do you mean a seperated layer 1 networks.
Or do you mean the host is connected on 2 layer 3 networks like i want to do ?

Anyway I wil try this vitrual ip's.[/QUOTE]

Sorry, I wasn't very clear. I meant in the logical sense, so the host will accept packets on say 192.168.0.0/24 and 10.0.0.0/8 at the same time if the NIC is on a physical network where both logical networks exist.

At home my DHCP server can be temperamental so I have my proxy on the normal 192.168.0.0 network and on 169.254.0.0 (link-local) network so that I can always connect through it. I'm sure there are many other uses, this is just an example.

I have read that a popular use is for hosting multiple virtual web servers on the same host PC. So that you can give a different IP address to separate users and shape bandwidth/utilisation etc.

---

