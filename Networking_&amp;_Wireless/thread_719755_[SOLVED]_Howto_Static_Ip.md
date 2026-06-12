---
title: "[SOLVED] Howto Static Ip"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by perito on 2008-03-09
I did search google but all I found was using the terminal.. isnt there a faster way to change to static ip?
in windows its so easy 
i tried to Manual Configuration but it tells me invalid gateway?
I only want to change my IP to 192.168.0.4 for example to be able to play on a network.........

what is a valid gateway ?
I need a P2P wireless connection between 2 PCs... how should I know what is the valid gateway?
please help ..

---

### Post by TheWizzard on 2008-03-09
> **perito said:**
> I did search google but all I found was using the terminal.. isnt there a faster way to change to static ip?
in windows its so easy 


depends on your definition of easy. using the command line you just have to copy something like 
```
auto eth1
iface eth1 inet static
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1
```
into /etc/network/interfaces

it can't be easier than this with a gui.

---

### Post by TheWizzard on 2008-03-09
> **perito said:**
> 
what is a valid gateway ?
I need a P2P wireless connection between 2 PCs... how should I know what is the valid gateway?
please help ..

the gateway is the ip of your router

---

### Post by koenn on 2008-03-09
not if he's trying point to point to a computer on the same subnet.

in that case, gateway can be left blank, since you don't need routing. 

You probably get "bad gateway" because the new address is in a different subnet than the old address/gateway address - that can't work so the program complains.

---

### Post by perito on 2008-03-10
what im trying to do is a p2p connection, no router...
so I cant do this except by terminal?

lets say I want to make my ip 192.168.0.3
I'd have to do this:
auto eth1
iface eth1 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway ???????????

help... thx

---

### Post by perito on 2008-03-10
help plz?

---

### Post by kevdog on 2008-03-10
Before you make a static IP address (which would be static only to the LAN - not the outside world -- which means you usually have to sit behind a NAT or router) can you tell me the IP address that you were issued automatically?

---

### Post by perito on 2008-03-10
yes yes, when I make a static IP address I only want a LAN connection P2P between laptops to be able to play a computer game! I dont want to be connected to the internet.
why is it so hard on linux?
on windows, u right click on Wireless Network Connection >> Properties >> Internet Protocol (TCP/IP) >> Use the following IP address >> Insert the IP address...

there must be an easy way to do it... i dont care if its through the terminal or by clicking.. but can someone please tell me how to make my IP 192.168.0.3 for example ...

---

### Post by kevdog on 2008-03-10
See this thread -- may need to combine things if you need wep or wpa -- the static IP portion is at the bottom.
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by perito on 2008-03-10
> **kevdog said:**
> See this thread -- may need to combine things if you need wep or wpa -- the static IP portion is at the bottom.

what thread?

---

### Post by koenn on 2008-03-10
what's with the attitude ?
If you like Windows, use windows. If you want easy, get a Mac. 
You basically got a solution in post #4 but apparently you didn't read it, or didn't get it. 

You fill in exactly the same things you would in Windows : ip address, netmask (when in doubt, use 255.255.255.0). No gateway. 
You do that in Network Manager or by editing /etc/network/interfaces. You need root (sudo) to do this :
I don't use GUI for simple stuff like this so here's how you do it in a terminal

```

sudo nano /etc/network/interfaces

## then put in something like 
auto eth1
iface eth1 inet static
address 192.168.0.3
netmask 255.255.255.0


```
to save and exit : 
Ctrl+C, Y, [Enter]  - as shown on the screen. 



Then restart networking : ```
 sudo /etc/init.d/networking restart 
```


That's all, except that 'eth1' maybe isn't the correct name for your wireless card. I don't do wireless so I can't check.

---

### Post by perito on 2008-03-10
sorry alot if I sounded offending... I was really stressed as Ive been searching alot and can get the right solution.
thx for replying
Ill check it out and reply
thanks

---

