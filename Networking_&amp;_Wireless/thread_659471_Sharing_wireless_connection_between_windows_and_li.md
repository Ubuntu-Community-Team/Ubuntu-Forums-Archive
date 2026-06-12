---
title: "Sharing wireless connection between windows and linux"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by 223511194173 on 2008-01-05
This is more of a learning exercise than a really serious problem, but:

My cable internet connection recently died when the whole neighborhood lost service after a storm.
There is a free wifi network that's easy to pick up in the area.

I have a laptop running windows XP and a desktop running Xubuntu 7.10. The laptop has a wireless card, but the desktop doesn't have one, and so currently it has no internet connection.

What I'd like to be able to do is share the laptop's connection with the desktop so that the desktop can surf. From what I've seen so far, this would supposedly be fairly easy if I had a crossover cable, but I don't have one handy.

I do have a router, a cable modem (not that it's much good right now), and a whole bunch of ethernet cables.  I'm pretty new to linux; I imagine that what I want to do is probably not that hard, I just don't really know my way around configuring my internet connection from the command line.

Realistically, I will probably just go out and get a cheap-ish usb wireless card for the linux box. In the meantime, it would be nice to learn how to share the connection.

Thanks in advance for any help.

---

### Post by Limpan on 2008-01-05
The first thing you should try is to use a normal ethernet cable, maybe one of the computers have auto mdi-x and can sense that the wrong cable is used and switch it over internally. If that works you would be done.

If that doesn't work you could try this. Make sure the laptop with wireless shares the connection with anything connected to the ethernet port. Then connect the laptop to the WAN port of the router and the Xubuntu machine to on of the LAN ports. Make sure the router uses DHCP to receive a IP-address on the WAN interface. Make sure that you do not use the same IP range on any two network segments (i.e. the wireless net, the net between the laptop and the router, between the xubuntu machine and the router).

---

### Post by 223511194173 on 2008-01-07
I'm sure this would be obvious if I wasn't such a noob, but:

For anyone who has a similar issue and finds this post later on, the solution was:

Set up the wireless connection to be shared on the windows machine. (Right-click it, properties, advanced, allow other computers to connect to the internet using this connection.)

Connect the windows machine, somewhat counter intuitively, to a LAN port on the router, not to the WAN/internet port. Ubuntu machine connects to a LAN port also.

get the windows host's IP and DNS servers from the windows command line with ipconfig /all.

On the Ubuntu client, edit the file /etc/network/interfaces so that the last part looks like this: (have to be root to edit it.)

# The primary network interface
auto eth0
iface eth0 inet static
 address 192.168.0.2 
 netmask 255.255.255.0
 broadcast 192.168.0.255
 gateway 192.168.0.1
 dns-nameservers [whatever two dns servers windows shows from ipconfig]

The gateway has to be the host, IP, which should automatically be 192.168.0.1. Each additional client should have an address one higher than this, so in my case the Ubuntu machine was 192.168.0.2, an additional client would have been 192.168.0.3, and so forth.

I don't know why the "broadcast" is 192.168.0.255, but it works, so hey. Don't think this will usually need to change. Ditto for the netmask.

I saw a lot of information that said to restart the interface with sudo /etc/init.d/networking restart, but this just gave errors that I didn't understand and did not work. Not sure what I was doing wrong here.

What did work was

sudo ifconfig [interface, in my case eth0] [Client IP address, in my case 192.168.0.2]
sudo route add default gw [host IP, in my case 192.168.0.1]

I'm not sure why I had to input the last two commands, when just editing the configuration file should have been enough. I assume that since the networking restart thing didn't work, I had to somehow get the system to notice that the configuration file had changed, and that did the trick. Regardless, it works perfectly now; both computers have internet access.

---

