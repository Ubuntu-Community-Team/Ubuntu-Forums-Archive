---
title: "port forwarding nightmare...."
date: 2011-09-05
forum: New to Ubuntu
---

### Post by Dasien on 2011-09-05
Hello all who are out there... I have been trying to forward the port on my router a Lynksys 54g and I have not been able to figure it out and for some reason the upnp does not seem to work. I have followed the advice of the other threads and from portforward.com to no avail. I am confused because both places of advice express how I need to have a static IP without giving any useful advice on how to do this. Portforward does not support Linux and so without a step by step I seem to be stuck. I have googled it but the advice found did not seem to work. I use Ubuntu because it is challenging to find answers and problem solve on my own but when I am about to give up I turn to the fourm so any help would be appreciated.

---

### Post by YesWeCan on 2011-09-05
Would you elaborate on what you are trying to do? Whats the port forward for?

---

### Post by haqking on 2011-09-05
> **Dasien said:**
> Hello all who are out there... I have been trying to forward the port on my router a Lynksys 54g and I have not been able to figure it out and for some reason the upnp does not seem to work. I have followed the advice of the other threads and from portforward.com to no avail. I am confused because both places of advice express how I need to have a static IP without giving any useful advice on how to do this. Portforward does not support Linux and so without a step by step I seem to be stuck. I have googled it but the advice found did not seem to work. I use Ubuntu because it is challenging to find answers and problem solve on my own but when I am about to give up I turn to the fourm so any help would be appreciated.


Portforwarding is nothing to do with Linux so as for supporting it that is not true.

port forwarding is something you do on your Router (which is usually running some type of linux so it is supported ;-)

To give yourself a static IP is simple, there is a terminal method but i am assuming you are new to this so i will use GUI as a an example.  Go to network manager and for the connection you wish to change choose edit connections.

Then on the IP4 tab give yourself a static IP, making sure it is valid for your subnet.
So if your current DHCP IP is 192.168.0.2 then give yourself that as static then turn off DHCP on your router unless there are other DHCP clients in which case you need to give yourself an address outside of the DHCP scope or make a reservation.

Give yourself a gateway address (router address usually 192.168.0.1 or similar) and a subnet mask usually 255.255.255.0.

To see what your current address is if any on DHCP so you can assign it as static run 
[I]
ifconfig [/I]

from the terminal and look at your inet4 address.

Then you are done.

See here for an old but still valid example [http://www.addictivetips.com/ubuntu-linux-tips/how-to-assign-static-ip-address-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-assign-static-ip-address-in-ubuntu-linux/)

As for port forwarding that is simply making sure you router forwards all traffic on a given port to your IP address.

Example.  SSH is port 22 so you set up port 22 to forward to 192.168.0.2

The layout of menu and how to do this will be dependant on your router, if you are using bittorrent that is usually already listed as an application for port forwarding and defaults to the torrent port unless you change it in your client (good idea if your ISP are agasint torrenting)

Remember the addresses i use are examples, substistute for your setup, thought should be similar as 192.168.x.x is a private class C addressing scheme used by most home devices.

---

### Post by Old_Grey_Wolf on 2011-09-05
Link to the Linksys WRT54G router users manual [http://ec1.images-amazon.com/media/i3d/01/A/man-migrate/MANUAL000000300.pdf](http://ec1.images-amazon.com/media/i3d/01/A/man-migrate/MANUAL000000300.pdf).

---

### Post by Dangertux on 2011-09-05
This is the simplest way I can show you this : Thankfully I have an old Linksys 54g laying around :-P

In the below example.

192.168.1.25 : LAN IP of the machine you're forwarding the port to.


Simply go to Applications & Gaming > Port Range Forwarding in your router configuration then configure the ports you want connections forwarded for, make sure you choose the right protocol or both, then enable the port forward and save your settings. In this
 example I enabled 22 (tcp) , 25(tcp & udp), and 80 (tcp).

In this example I only forwarded 3 non-consecutive ports. However you can also forward ranges. Say you're running an IRC Server you could change the port range to something like 6667 to 6675. This would forward connections on ports 6667, 6668, 6669, 6670, 6671, 6672, 6673, 6674, 6675 on the protocol specified to the IP address specified.

---

### Post by haqking on 2011-09-05
> **Dangertux said:**
> This is the simplest way I can show you this : Thankfully I have an old Linksys 54g laying around :-P

In the below example.

192.168.1.25 : LAN IP of the machine you're forwarding the port to.


Simply go to Applications & Gaming > Port Forwarding in your router configuration then configure the ports you want forwarded, make sure you choose the right protocol or both, then enable the port forward and save your settings. In this
 example I enabled 22 (tcp) , 25(tcp & udp), and 80 (tcp).


ha ha awesome.

I was still contemplating whether to get in the attic and get my old one out to do exactly the same thing.

You saved me the dust and cobwebs..LOL

---

### Post by YesWeCan on 2011-09-05
Time to get the Hoover out, me thinks. :P


As for static IP addresses. I think you should do this in the router too. You just tell the router to always assign the same IP address to your linux box when it asks for one. Simpler than setting up a static IP address in the linux box.

---

