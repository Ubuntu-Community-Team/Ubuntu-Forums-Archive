---
title: "IP Config, multiple ip's for Co-location"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by Sir Jake on 2008-03-13
Hello there, I have a server just about ready to send out to a colocation.
The next thing I have to setup is my ip's I will be running a few CSS gaming servers off this one, and I'm not sure how to make my one connection use multiple connections.
Using Ubuntu server 7.10 with gnome installed.
I don't know how to setup the ip's they give me
Any help would be great,
Thanks Jake.

---

### Post by SpaceTeddy on 2008-03-13
just to clairy, you want mutliple ip addresses on one network card ? 
if that is the case, you need ti setup virtual network cards. You can either do that via webmin, or you can edit the config file directly. 

prerequiste is that your server has a static ip already ! 

i will only explain what you will have to do when you edit the config files directly. but for that i need to know if you are running cli only, or of you have a graphical system install aswell

---

### Post by Sir Jake on 2008-03-13
Yeah, I need it setup on one network card, I have ubuntu-desktop installed on here.
For the colocation I put in an order for 5 static ip's

---

### Post by SpaceTeddy on 2008-03-13
ok, what you want to edit is your /etc/network/interfaces
you can open that one with 
```
gksu gedit /etc/network/interfaces
```

you will (most likely) not find anything in there other than your loopback device (lo)

what you need to do first off, if definde your primary network card. This is the one that shows when you run
```
ifconfig
```
it should be something like eth0, eth1 or so... if you are in doubt, then just paste the output of the commands here.

now, to acctually assign something to an interface (primary) you will need to write a block for it. This could be such an example
```
auto eth0
iface eth0 inet static[INDENT]address 192.168.0.1
netmask 255.255.255.0
broadcast 192.168.0.255
network 192.168.0.0
[/INDENT]

```

this will assign your network interface eth0 the ip 192.168.0.1 and all the other stuff that it need to work properly. the first line will make sure the device is brought up at boot time

once you have that setup, youc an definde subdevices to be attached to the main device a subdevice is almost the same, it just differs a little in the device name. the first subdevice could be defined like this
```
auto eth0:1
iface eth0:1 inet static[INDENT]address 192.168.2.1
netmask 255.255.255.0
broadcast 192.168.2.255
network 192.168.2.0
[/INDENT]
```
this will define a network device called eth0:1, which is working on the same physical network card as eth0 does, but with a different ip (as you can see, they don't even need to be in the same subnet)... just define as many devices as you want.

so, the full file would be looking like this now (with two devices)
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
[INDENT]address 192.168.0.1
netmask 255.255.255.0
broadcast 192.168.0.255
network 192.168.0.0
[/INDENT]

auto eth0:1
iface eth0:1 inet static
[INDENT]address 192.168.2.1
netmask 255.255.255.0
broadcast 192.168.2.255
network 192.168.2.0
[/INDENT]
```

that is pretty much all there is to it... i think

---

