---
title: "Problems with ADSL"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by felipefcm on 2007-03-02
Hello everybody, I have a 500g D-Link working as router/bridge.
It's connected with a Kubuntu 6.06 in the Ethernet Card (Realtek)
Both the router and Ethernet card works nice in Windows XP

I've read a lot of things on the net about the problem, so I decided to write here.

Problem: can't connect with an adsl connection

/etc/network/interfaces - 

[all the Loopback configuration]

if-up /sbin/ifconfig eth0 up (but I think that using inet manual like below it's don't work)

auto eth0
iface eth0 inet manual 

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider


I don't know much about network and Linux, I started using it some weeks ago.

Note: pppoeconf don't find anything...it's reach it's timeout for the PADO packages...I guess that the Ethernet is not linked with the router. I want my IP Dinamic and the DHCP server is running on the router. Tell me if it's better configure the modem to work as a router or bridge and how can I do this...the command pon dsl-provider also not works. In fact, nothing works =P

Thank you very much!
Felipe

---

### Post by felipefcm on 2007-03-02
It's valid to remember that I can't acess the modem configuration page [http://10.1.1.1](http://10.1.1.1)
It say that's a Unreachble network

---

### Post by felipefcm on 2007-03-11
thank you all for the help...it's very nice to know that i can count with your help.

---

### Post by Mr. C. on 2007-03-11
Perhaps you'll get better response without the attitude, and with a little more clarity.  Your post is awfully confusing.

It's not clear to me if your Ubuntu system has a functional network connection to the router or not.

What is the ouptput of 
```

ifconfig -a
```

and for your LAN, what is the IP address, network mask, gateway and broadcast address configured on your router.

MrC

---

### Post by steveneddy on 2007-03-11
It seems that he is trying to use the computer as the pppoe connection when in reality the router does that job. Just type the ip address of the router, make sure that it is set to gateway and that your user name and password are correct. You shouldn't have to configure anything on the computer to connect to an always on internet connection.

---

### Post by Mr. C. on 2007-03-11
I was wondering the same thing, steveneddy; you are probably correct. 

MrC

---

