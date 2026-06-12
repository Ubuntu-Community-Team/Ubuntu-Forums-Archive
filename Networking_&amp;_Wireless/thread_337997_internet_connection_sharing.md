---
title: "internet connection sharing"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by TheOtherLinuxFreak on 2007-01-13
how do i do Internet connection sharing with window xp and xubuntu? i have them networked with samba.

thanks!

---

### Post by SuperMike on 2007-01-13
An easier and more secure route would be to visit Wal*Mart or some online site and pick yourself up a DSL/Cable Router. (I personally prefer US Robotics products over anything else.) By doing this, you get a NAT-router with all kinds of firewall possibilities and with a bit less hassle than trying to share an Internet connection on Xubuntu. The router then can be configured to connect to your ISP and then you have your two systems connect to that. And if you have dial-up Internet instead of DSL or cable, there are some DSL/Cable router products that you can purchase that have an additional serial port on them for adding a modem connection.

Then, turn on the firewall on XP and add a firewall script to your Xubuntu workstation (with the proper holes poked in it, of course). As for Ubuntu Linux firewall, see my signature line below for a link on how to do a firewall script.

Your workstations will get their IP address from the NAT router inside the DSL/Cable Router.

---

### Post by blundr on 2007-01-13
if you'd like to have your ubuntu box act as a router, then you need to have two network interface cards.

card 1 goes to your internet connection

card 2 goes to a switch where the rest of your devices plus into.

i use arno's iptables script.  it works very well for me.  there are gui versions available for iptables, you can search synaptic for other options.

```
apt-get install arno-iptables-firewall
```

there are alot of other things you should keep in mind, like whether or not you need to have your router be a dhcp server, dns server etc, but this should get you started.

---

### Post by SuperMike on 2007-01-14
If you want to go the software-only route, then Internet connection sharing can be setup with tinyproxy. See the link in my signature to set that up. One Ubuntu box has the Internet connection and the tinyproxy service running. The other workstations point to this IP address and proxy port in order to surf the Internet.

---

### Post by TheOtherLinuxFreak on 2007-01-15
the windoze box is the one with the internet connection. the xubuntu box is only a pentium 2.

---

### Post by TheOtherLinuxFreak on 2007-01-15
> **blundr said:**
> if you'd like to have your ubuntu box act as a router, then you need to have two network interface cards.

card 1 goes to your internet connection

card 2 goes to a switch where the rest of your devices plus into.

i use arno's iptables script.  it works very well for me.  there are gui versions available for iptables, you can search synaptic for other options.

```
apt-get install arno-iptables-firewall
```

there are alot of other things you should keep in mind, like whether or not you need to have your router be a dhcp server, dns server etc, but this should get you started.

this is how i have the winbox setup. what do i do to windoze so that it will share the connection? i thought of maby making the defualt gateaway the ip of the winbox.

---

### Post by TheOtherLinuxFreak on 2007-01-16
anyone?

---

### Post by TheOtherLinuxFreak on 2007-01-17
hasnt anyone ever done this before????

---

### Post by koenn on 2007-01-17
[http://www.practicallynetworked.com/sharing/xp_ics/](http://www.practicallynetworked.com/sharing/xp_ics/)
or
[http://www.google.com/search?hl=en&q=xp+internet+connection+sharing](http://www.google.com/search?hl=en&q=xp+internet+connection+sharing)

---

### Post by TheOtherLinuxFreak on 2007-01-17
what about windows xp to ubuntu?

---

### Post by carverj on 2007-01-17
> this is how i have the winbox setup. 

Do you mean that you have winbox with one card for ISP connection and one card for switch connection and the IP address of the Linux box in the arp table?
I am assuming that you can ping between the machines if the wire is plugged in.
Assuming you can access the net with winbox no probs., should be able to access net on private IP address I'd imagine.
Have you thought of replacing the switch with a router?
That's how my home network works
Hope you get it sorted!

---

### Post by TheOtherLinuxFreak on 2007-01-18
i have two network card in the winbox. they are pluged directly together with a crossover cable. i have them net worked and it works. i just need internet connection sharing. (dont have money for a router.) yes i can ping between them. they are networked with samba.

---

### Post by koenn on 2007-01-18
You're gonna have to be a bit more precise in your descriptions. When I read
> i have two network card in the winbox. they are pluged directly together with a crossover cable, I  picture a computer with 2 network cards, and a crossover cable from one network card to an other network card on the same computer. Obviously, that doesn't make sense, but I can then only *assume * your ubuntu box is connected to the winxp box with a crossover cable, and a 2nd network card on the xp machine is (in some way)  connected to the internet. 

Also, you said
>  	the windoze box is the one with the internet connection., and 
> what do i do to windoze so that it will share the connection?
so I found you some instructions on XP internet connection sharing. 
Now you say
>  	what about windows xp to ubuntu?
Does that mean you've changed your mind (and your network design) and want to use the ubuntu machine to share the internet connection ?  
That was explained in post #3 - although I can imagine you'd need some additional clarification, which will be hard to get if you don't manage to explain clearly what your network looks like so far.

---

### Post by TheOtherLinuxFreak on 2007-01-18
sorry about my typing. 

 > [QUOTE]i have two network card in the winbox. they are pluged directly together with a crossover cable
, I picture a computer with 2 network cards, and a crossover cable from one network card to an other network card on the same computer. Obviously, that doesn't make sense, but I can then only assume your ubuntu box is connected to the winxp box with a crossover cable, and a 2nd network card on the xp machine is (in some way) connected to the internet.[/QUOTE]

the winbox and th ubuntu box are connected together with a crossover cable. the win box has 2 network cards. it is also connected to the internet.

> Also, you said

[QUOTE]the windoze box is the one with the internet connection.
, and

> what do i do to windoze so that it will share the connection?
so I found you some instructions on XP internet connection sharing.
Now you say

> what about windows xp to ubuntu?
Does that mean you've changed your mind (and your network design) and want to use the ubuntu machine to share the internet connection ?
That was explained in post #3 - although I can imagine you'd need some additional clarification, which will be hard to get if you don't manage to explain clearly what your network looks like so far.[/QUOTE]

what i meant when i said > what about windows xp to ubuntu?  was what do i do to the ubuntu box now that i set up the winbox?  but i guess i didnt explain it clearly enough. sorry.

---

### Post by koenn on 2007-01-18
1- check that the winxp machine can get on the internet
2- find out what the IP addresses and subnet masks are for both network cards in the XP. One of them will probably be something like 192.168.0.1 and should be the one your ubuntu machine is connected to.
3 - use that address as "gateway" for your ubuntu machine. This means also you'll have to configure ubuntu to use a 'static' IP address (and network configuration). 
4- give the ubuntu machine an ip address in the same range as the 192.168.0.1 (or whatever IP address you found for the network card connected to the ubuntu machine). suggestion: 192.168.1.10
5-ping from ubuntu to xp and/or from xp to ubuntu
6-complete the ubuntu network config - you ptobably need to specify DNS servers: you can use the same values as on the XP machine
7- see if you can reach internet from the ubuntu machine

Do this step by step, solve each step before you try the next one. 
If you get stuck and don't know how to proceed, describe how far you got and provide details (IP addressed used, results of ping, ...)

---

### Post by TheOtherLinuxFreak on 2007-01-18
Thanks!!!:D  it worked. now i know what i was do ing wrong. i forgot to add a dns sever. 
now im now replying from my ubuntu box. thanks!
i have them networked but how do i access the windows shared folder?

---

### Post by koenn on 2007-01-18
> i have them networked but how do i access the windows shared folder?
That's a whole different question. Normally you should be able to access windows shared folders from your file browser (nautilus ?) - through Places -> Network Servers or Places -> Connect to Server : Windows share.

I've seen that question dealt with a number of times on these forums so maybe you can use the search (or start a new thread).

---

### Post by TheOtherLinuxFreak on 2007-01-18
my file browser is thunar.

---

### Post by koenn on 2007-01-18
I don't know thunar.

---

### Post by TheOtherLinuxFreak on 2007-01-18
what other file managers are there for xubuntu? thunar doesnt show networked folders

---

### Post by night-hawk on 2007-01-20
> **TheOtherLinuxFreak said:**
>  how do i access the windows shared folder?

> **TheOtherLinuxFreak said:**
> my file browser is thunar.

I just did what you are asking.  Thunar does not have that feature yet.  So you need to mount windows shares so they appear in your filesystem.

See post #3 on this thread: 
[ http://www.ubuntuforums.org/showthread.php?t=340675]("http://www.ubuntuforums.org/showthread.php?t=340675")

---

### Post by carverj on 2007-01-22
OK, so you had to specify the IP of the winbox as the DNS location manually?
Welcome to the outside of your network.

---

### Post by TheOtherLinuxFreak on 2007-01-22
> **carverj said:**
> OK, so you had to specify the IP of the winbox as the DNS location manually?
Welcome to the outside of your network.

yes i had to manually set the dns address.

---

### Post by carverj on 2007-01-22
Yeah I don't remember having to set that when I set up my network.
It must configure automatically when using DHCP!!

---

### Post by koenn on 2007-01-22
not really. 
You've implemented WIndows XP Internet Connection Sharing. Basically, that means the XP box works as a router with NAT (network address translation). Routers route. They don't do DHCP (or DNS, or make coffee, or do the dishes). You might think that "some routers do dhcp and dns" but that just means that the router, a dns forwarder  and a  dhcp daemon are all running on the same machine, the appliance which you call your "router" .

WinXP ICS does not include a dhcp service, and therefore you had to manually configure the ubuntu machine with static ip addres, network mask, dns servers, etc.  Why ? because that's how Microsoft designed its Internet Connection Sharing.

---

### Post by night-hawk on 2007-01-22
> **koenn said:**
> WinXP ICS does not include a dhcp service, and therefore you had to manually configure the ubuntu machine with static ip addres, network mask, dns servers, etc.

Setting the IP manually was personal preference, not a must.  WinXP ICS does have dhcp....but it only works for the 192.168.0.0/24 network.

---

### Post by carverj on 2007-01-22
> WinXP ICS does have dhcp....but it only works for the 192.168.0.0/24 network.

OK, so you can issue a pool of class C using DHCP, but unlike Ubuntu, Windows ICS requires manual DNS entries ?

---

### Post by night-hawk on 2007-01-23
The client machines' default gateway and DNS server is set to 192.168.0.1.

---

### Post by TheOtherLinuxFreak on 2007-01-23
> **night-hawk said:**
> The client machines' default gateway and DNS server is set to 192.168.0.1.
thats how mines set up

---

### Post by koenn on 2007-01-23
> **night-hawk said:**
> Setting the IP manually was personal preference, not a must.  WinXP ICS does have dhcp....but it only works for the 192.168.0.0/24 network.
Ah, ok, I could have been wrong there - I haven't looked at ICS since Windows 98.

Anyway, without dhcp you'd *always* need to manually set DNS servers. 
With a dhcp server, it depends on the dhcpserver. If it only gives out IP addresses and a default router, you would still have to manually add DNS servers. If it gives out a complete configuration, DNS servers would be included - and if I read night-hawk correctly, that is the case for ICS.

---

