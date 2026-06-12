---
title: "cannot connect to localhost lamp server installed on ubuntu desktop on lan"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by rooster_fruit on 2008-08-19
I'm very new to the apache setup and linux in general. I've set up a lamp server on ubuntu desktop 8.04 (via synaptic; php5, php5-mysql, etc) and ive set it up so there's a folder in my documents folder that holds my server files, and i can look at my server via [http://green/](http://green/) (host is 127.0.0.1 set to localhost and green).

my problem is, i can't seem to view the server from other computers on my lan network. ive searched these forums, and all the topics ive found, people can see their sites locally.

and if it matters, im trying to connect through a mac (10.4 and 10.5)

---

### Post by jimv on 2008-08-19
Are you typing http://<ip address of the server>?

So it will look like [http://192.168.x.x](http://192.168.x.x) 

You can get the ip by typing 'ifconfig' in a terminal on the server.

---

### Post by rooster_fruit on 2008-08-20
yeah, i found my internal ip, and i was typing that in. the error i get on the mac is 'server not responding'

---

### Post by cariboo on 2008-08-20
Can you ping your server? To find out what the ip address of your server in a terminal type:

```
ifconfig
```

and note the address for eth0

Then try connecting using the ip address eg:

```
http://ip address
```

Jim

---

### Post by rooster_fruit on 2008-08-20
in my ifconfig, there's no ip adress under eth0, there's eth0:avahi, which has an inet address (169.254.x.x), and the wlan0 has the 192.168.0.x ip address. both get a timeout when i try to view them.

and if it matters, both work when i try it on my server machine

---

### Post by rooster_fruit on 2008-08-23
bump

---

### Post by eggdeng on 2008-08-23
This should be simple to sort out but you need to clear up a few points.
1) When you run ifconfig on the server, what is the IP for the interface which is connected to the local network? (The two IPs you posted are on different networks.)
2) What is the IP of the box (Mac) you are trying to access the server from? (System preferences -> Network -> TCP/IP)
If you can, post all the output, including gateway addresses and subnet mask(s).

---

### Post by bab1 on 2008-08-23
I understand you are new to Linux.  You should learn how to configure Ubuntu (LAMP) host manually.  I highly suggest you configure the host to a static address.  It is the simplest and in the long run the best for you.  All servers should have static addresses for consistency.

The term "localhost' is by definition local to the host!  Localhost (127.0.0.1) should not be resolved from a domain name.

To set up your Ubuntu host, see [[COLOR="Red"]**here**[/COLOR]]("http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html").

---

### Post by Iowan on 2008-08-23
The avahi address suggests the server isn't communicating with a DHCP server.  As bab1 mentioned, **127.0.0.1** should probably be left as **localhost** - you can set up **127.0.1.1** as **green**.  My LAMP server currently gets a DHCP address - that means I must look up the address (ifconfig) before I can address it from another machine on the network.

---

### Post by redmk2 on 2008-08-23
Guy's -- 127.0.0.1 is localhost.  This should **not** be assigned a hostname other than [COLOR="Red"]*localhost*[/COLOR] (by convention).

---

### Post by rooster_fruit on 2008-08-23
> **eggdeng said:**
> This should be simple to sort out but you need to clear up a few points.
1) When you run ifconfig on the server, what is the IP for the interface which is connected to the local network? (The two IPs you posted are on different networks.)
2) What is the IP of the box (Mac) you are trying to access the server from? (System preferences -> Network -> TCP/IP)
If you can, post all the output, including gateway addresses and subnet mask(s).the ip from the eth0 section is 169.254.x.x and the one from the wlan section is 192.168.x.x, they both appear at the same time. it may be worth noting that the wlan ip address keeps changing on me

> **bab1 said:**
> I understand you are new to Linux.  You should learn how to configure Ubuntu (LAMP) host manually.  I highly suggest you configure the host to a static address.  It is the simplest and in the long run the best for you.  All servers should have static addresses for consistency.

The term "localhost' is by definition local to the host!  Localhost (127.0.0.1) should not be resolved from a domain name.

To set up your Ubuntu host, see [[COLOR="Red"]**here**[/COLOR]]("http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html").i think my problem is that my internal ip address (the one that starts with 192.168.x.x) always changes because i'm using a laptop, the link you sent is for setting it up based on an ethernet connection, right? not a wireless one?

> **redmk2 said:**
> Guy's -- 127.0.0.1 is localhost.  This should **not** be assigned a hostname other than [COLOR="Red"]*localhost*[/COLOR] (by convention).i have it set to both, but if it really matters, ill change it back

---

### Post by bab1 on 2008-08-23
Actually, the part you need is the TCP/IP part.  192.168.x.x is IP part.  The hardware address is the Ethernet part.

Help me with my confusion.  The Apache server on the Laptop; right?  Is the laptop using wireless or the wired connection?  What do you mean by "internal"?

All of the interfaces use TCP/IP addresses.  The 169.254.x.x IP address is handed out when there is no attempt to configure the interface.  It's for the "it just works people"  Not a good thing for you.  

All of the computers must be on the same network ie; 192.168.0.0/255.255.255.0.  The addresses range from 1 to 254.  Think of it as the [COLOR="Sienna"]**192.168.0**[/COLOR] part as the street, and the [COLOR="DarkOrange"]**1 to 254**[/COLOR] as the house address.  Everyone needs to be on the same street to communicate locally.  On your local network you can have both wired and wireless talk to each other.  Internetworking is another matter.

I believe that what redmk2 meant was that 127.0.0.1 is normally only known as localhost.  Is okay to use 127.0.0.1 with another name?  Sure, but it will not work when trying it from any other computer in the local network.  Why, because ultimately the computers talk to the IP address, of which 127.0.0.1 is --- the localhost ie: itself!

I know this is long winded, but you are just starting out and these are the things you need to know when administrating  a network.

What I need to know to help:
[LIST]
[*]Which interface are you using to talk to the Mac's?
[*]Where are you getting the 192.168.x.x addresses from? (DHCP ??)
[*]What is the eth0 interface connected to?
[*]What are the IP addresses of the Mac's?
[*]How are the Mac's connected to the local network?
[/LIST]

---

### Post by rooster_fruit on 2008-08-24
> **bab1 said:**
> What I need to know to help:
[LIST]
[*]Which interface are you using to talk to the Mac's?
[*]Where are you getting the 192.168.x.x addresses from? (DHCP ??)
[*]What is the eth0 interface connected to?
[*]What are the IP addresses of the Mac's?
[*]How are the Mac's connected to the local network?
[/LIST]
im not sure what you mean by 'interface', but im just typing in the linux box's ip into firefox/safari/camino

one of my computer friends used the term 'internal ip' to describe the ip's starting with 192.168.x.x, and i'm getting tem from typein ifconfig (in the wlan section)

the only connection i have is from my wireless card, to my home router, i think that's what the eth0 is

i know that 192.168.x.x address of my mac, (192.168.0.100), im not sure about any others

the mac is connect directly to the router via ethernet cable


and yes this setup is a lamp server on my laptop computer thats connected to the internet via a wireless router

thanks for the help

---

### Post by bab1 on 2008-08-24
> im not sure what you mean by 'interface'

The interface I am referring to is the IP address of the NIC.  The NIC (network interface card) is represented by wlan0 (wireless) or eth0 (wired).  When you type the address in the browser it tries to communicate with your NIC.  The browser does not know the ip address is located on the same computer.

> the only connection i have is from my wireless card, to my home router, i think that's what the eth0 is
Nope, wlan0 is your wireless (see above).  And the router is giving it it's IP address.

> know that 192.168.x.x address of my mac, (192.168.0.100), im not sure about any others.  the mac is connect directly to the router via Ethernet cable


If you connect your laptop via a cable, I'll bet you will get an IP address in the same network as the mac.  Then the mac will be able to talk to the laptop.  See if the laptop and the mac have the same 192.168.0.x range when both are connected to the router by wires.  Reboot both machines when you connect them.

You really need to read some basic Linux and networking literature to understand this.  I can give you parts, but you have no real reference to what I am saying.  You need a little more background.  I'm advising you gently.  Read more...

It can be on the web.  No need to spend any money.  Google the terms "ethernet", "tcp/ip" and networking.

---

### Post by rooster_fruit on 2008-08-27
i connected via ethernet cable, and used the ip from ifconfig, and it works like a charm. thanks a ton! ill read up on networking

---

