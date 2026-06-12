---
title: "Which one is the PCs unique IP address?"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by carvacrol on 2009-11-27
**[SIZE=3]In Ubuntu-Linux, when I type "ifconfig" at terminal, which one is the PC's unique ip adress?[/SIZE]**

                   I have two PCs connected to the net through a router, but I want to know the unique IP addresses of each individual PC, not my router's or DSL modem's IP address, which is the information I get at the top of the page when I visit [www.whatismyipaddress.com(this]("http://www.whatismyipaddress.com%28this") is what routers are supposed to do, get 2 or more PCs to share the same IP address, among other things). So which one is the unique IP address of the PC when I type ifconfig?

Is it the numbers after "inet addr"? Or Bcast? Or Mask? Or inet6 addr?

Now that I am looking at the ifconfig info in terminal on both PC screens, I notice that the numbers after Bcast and Mask are exactly the same. However, the inet addr is almost the same for both PCs except for one number at the end. Is this the IP address for the PC? Is there also a site or tutorial that can tell me what all those other numbers and characters mean in ifconfig? So much info comes out when I type ifconfig...

---

### Post by Arlanthir on 2009-11-27
> **carvacrol said:**
> **[SIZE=3]In Ubuntu-Linux, when I type "ifconfig" at terminal, which one is the PC's unique ip adress?[/SIZE]**

                   I have two PCs connected to the net through a router, but I want to know the unique IP addresses of each individual PC, not my router's or DSL modem's IP address, which is the information I get at the top of the page when I visit [www.whatismyipaddress.com(this]("http://www.whatismyipaddress.com%28this") is what routers are supposed to do, get 2 or more PCs to share the same IP address, among other things). So which one is the unique IP address of the PC when I type ifconfig?

Is it the numbers after "inet addr"? Or Bcast? Or Mask? Or inet6 addr?

Now that I am looking at the ifconfig info in terminal on both PC screens, I notice that the numbers after Bcast and Mask are exactly the same. However, the inet addr is almost the same for both PCs except for one number at the end. Is this the IP address for the PC? Is there also a site or tutorial that can tell me what all those other numbers and characters mean in ifconfig? So much info comes out when I type ifconfig...


Yes, it's the inet addr as you correctly deduced :)
It should be almost the same for all the computers in the network, typically with only the last group of digits changed (after the last dot).

E.g.

192.168.2.2
192.168.2.3
192.168.2.4, etc

Your router configuration should live on xxx.xxx.xxx.1, but that's a rule of thumb more than an actual rule, I think.

I can't tell you much more because I'm no expert, but I hope I cleared some doubts.

---

### Post by SteveHillier on 2009-11-27
Hi carvacrol

I am not an expert but in any range of IP addresses such as 192.168.1.x there are 256 possible combinations.  Numbers ending in 0 and 255 are reserved.  255 is reserved for broadcasting to ALL addresses in the range, I forget what 0 is reserved for.  So in effect you get to choose numbers between 1 and 254.
As Arlanthir says most routers default to the number 1 (eg 192.168.1.1) but that is a convention.  You can use anything you like within the range.
Most routers will also act as dhcp servers so you don't have to set each machine with a known address, you let the router do it for you, but if you are using network printers or running domain servers it is probably good to have then on a fixed address but if you set them put them out of the way of dhcp allocated low numbers.  (most routers can be configured to allocate dhcp addresses in a given range of numbers only.)
Finally the mask (or netmask).  Normally you will use 255.255.255.0 for your local network, but if you get fixed IP addresses from your ISP you might see other numbers at the end.  The netmask is a bit pattern with all 1's to the left and all 0's to the right so you will only see a limited range of numbers in any one block so 128, 192, 224, 240, 248, 252, 254.  With a 0 in the last block your netmask can support 256 devices, if it is 128 then there can be 128 supported devices, if it is 192 then there can be 64 devices etc.
The mystery of 192.168.x.y network is that these numbers are reserved for private networks and convention uses this range, however you might see private networks (LANS) set up with numbers starting with 10 eg 10.1.1.x or with 172 eg 172.16.1.x but these are not commonly found except in installations that might just have a resident network engineer.  Your router then acts as a gateway between your private network (LAN) and the public network (WWW) and uses NAT to work out which local machine to send messages to.
I cannot help with IP6 addresses but I hope my words give you some assistance.

---

### Post by teward on 2009-11-27
What you're seeing is the internal network IP.  This is what only your network sees, and not what the Internet sees.  So, as was stated by Arlanthir, these IPs are assigned by your router.

If you're looking for what the Internet sees (your external network IP), then go to [http://whatismyip.com/](http://whatismyip.com/) and it will tell you what your IP address is (as the Internet sees it)

If I may ask, why do you need to know your IP address, and which IP address are you looking for?  The one your Router assigns, or the one the Internet sees?

---

### Post by carvacrol on 2009-11-27
> **SteveHillier said:**
> Hi carvacrol


The mystery of 192.168.x.y network is that these numbers are reserved for private networks and convention uses this range, however you might see private networks (LANS) set up with numbers starting with 10 eg 10.1.1.x or with 172 eg 172.16.1.x but these are not commonly found except in installations that might just have a resident network engineer.  Your router then acts as a gateway between your private network (LAN) and the public network (WWW) and uses NAT to work out which local machine to send messages to.
I cannot help with IP6 addresses but I hope my words give you some assistance.

Both of my inet addr's are 10.10.10 numbers, which differ only in the last number for both PCs. A lot of people I talk to about this, experts and non-experts alike, assume I am dealing with 192.168...  but I had these issues that prevented me from using the router for getting both PCs on the internet, and so I called Linksys and they told me to change the IP address or whatever to 10.10.10. That is how I finally got online through my Linksys DSL router. Your words have been most helpful, thanks.

---

### Post by lisati on 2009-11-27
AFAIK, when you connect to a site like [www.whatismyipaddress](www.whatismyipaddress) it will see one IP address, regardless of which computer you are using. Are you asking for help figuring out how to access a particular computer on your home network from somewhere outside your home network?

---

### Post by teward on 2009-11-27
Of course, my question goes unanswered.

SO...

I think he's just curious.  But NONE of the addresses you're seeing under ifconfig are your external network IP, the IP needed to access your computer(s) from outside your local network, for example, from a work computer.

But if you want that, you've got to configure your router for port-forwarding, not exactly the easiest thing in the world.


Otherwise, you've found your internal networks.  The numbers 10.10.10.*, where * denotes the end numbers, which are between 0 and 255 don't matter, at least the 10s don't, really.  My router's configured for 192.153.82.*, a personal configuration, where the *s are any number between 1 and 255 (for me).  However, that's the **internal network IP**, the IP that is ONLY within your network/router.

So, I ask you again as I did earlier, and **answer me please**.

*_**Which IP are you trying to find, the one for within your network, or the one that is your external network (internet) IP?**_*

---

### Post by carvacrol on 2009-11-28
> **TrekCaptainUSA said:**
> What you're seeing is the internal network IP.  This is what only your network sees, and not what the Internet sees.  So, as was stated by Arlanthir, these IPs are assigned by your router.

If you're looking for what the Internet sees (your external network IP), then go to [http://whatismyip.com/](http://whatismyip.com/) and it will tell you what your IP address is (as the Internet sees it)

If I may ask, why do you need to know your IP address, and which IP address are you looking for?  The one your Router assigns, or the one the Internet sees?

Sorry for the delay in answering, I was just experimenting a little. The reason I want to know the IP addresses of my PCs(the ones my router sees, not the one the internet sees) is so I can set up a LAN between them(they both have internet access though), both of my computers are running on Ubuntu. It seems that knowing the IP addresses of these PCs is vital for doing this. I just need to know both IP addresses and maybe some other things. I've never done this before, because I've never had more than one computer at the same time, although I've been going on the internet for over a decade now. I also have another computer that I borrowed from a friend that has Windows 7 that I also want to add to the network, but I figure that would be more challenging than connecting two Ubuntu PCs. The Windows addition will just be temporary, as an "experiment". I'd like to be able to set up FTP file-sharing, and turn one PC into a server. We'll see...

I ultimately want to know how to set up a LAN so I can be better educated and hopefully pass on this information while telling everyone how great Ubuntu is. I would also love to help make Ubuntu better when I become more knowledgeable(I already have some programming experience, but forget most of it). I've been using Ubuntu for only a few weeks now and it has exceeded my expectations. Thanks.

---

### Post by zaphod777 on 2009-11-28
on the computer go to the terminal and type ifconfig 

You can see I haave 3 interfaces 

1. eth0 - Ethernet
2. lo - loopback (used for operating system stuff)
3. wlan0 - wireless interface


I am using wireless so you can see I have an ip of 192.168.11.100

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:35:48:1d  
          inet addr:192.168.11.100  Bcast:192.168.11.255  

if you are setting up somme hosted apps you should go in your router and make sure you setup a DHCP reservation otherwise your computers IP might change because the address are dynamic.

```
nvilppu@zaphod:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:82:50:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1294637 (1.2 MB)  TX bytes:1294637 (1.2 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:35:48:1d  
          inet addr:192.168.11.100  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe35:481d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79836854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114735997 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39142786835 (39.1 GB)  TX bytes:132981213392 (132.9 GB)

nvilppu@zaphod:~$ 

```

---

### Post by Captain_tux on 2009-11-28
> **SteveHillier said:**
> Hi carvacrol

I am not an expert but in any range of IP addresses such as 192.168.1.x there are 256 possible combinations.  Numbers ending in 0 and 255 are reserved.  255 is reserved for broadcasting to ALL addresses in the range, I forget what 0 is reserved for.  So in effect you get to choose numbers between 1 and 254.
As Arlanthir says most routers default to the number 1 (eg 192.168.1.1) but that is a convention.  You can use anything you like within the range.
Most routers will also act as dhcp servers so you don't have to set each machine with a known address, you let the router do it for you, but if you are using network printers or running domain servers it is probably good to have then on a fixed address but if you set them put them out of the way of dhcp allocated low numbers.  (most routers can be configured to allocate dhcp addresses in a given range of numbers only.)
Finally the mask (or netmask).  Normally you will use 255.255.255.0 for your local network, but if you get fixed IP addresses from your ISP you might see other numbers at the end.  The netmask is a bit pattern with all 1's to the left and all 0's to the right so you will only see a limited range of numbers in any one block so 128, 192, 224, 240, 248, 252, 254.  With a 0 in the last block your netmask can support 256 devices, if it is 128 then there can be 128 supported devices, if it is 192 then there can be 64 devices etc.
The mystery of 192.168.x.y network is that these numbers are reserved for private networks and convention uses this range, however you might see private networks (LANS) set up with numbers starting with 10 eg 10.1.1.x or with 172 eg 172.16.1.x but these are not commonly found except in installations that might just have a resident network engineer.  Your router then acts as a gateway between your private network (LAN) and the public network (WWW) and uses NAT to work out which local machine to send messages to.
I cannot help with IP6 addresses but I hope my words give you some assistance.

Steve -

You may not be an expert, but you provide very good analysis here... good job!

The 0 in 192.168.1.0 is reserved for the network... so, 192.168.1.1 is the first IP in the 192.168.1.0 network (a Class C network). Thus, 127.0.0.1 indicates the first IP in the 127.0.0.0 network (and remember, there's no place like 127.0.0.1!).

---

### Post by SteveHillier on 2009-11-28
> **carvacrol said:**
> Both of my inet addr's are 10.10.10 numbers, which differ only in the last number for both PCs. A lot of people I talk to about this, experts and non-experts alike, assume I am dealing with 192.168...  but I had these issues that prevented me from using the router for getting both PCs on the internet, and so I called Linksys and they told me to change the IP address or whatever to 10.10.10. That is how I finally got online through my Linksys DSL router. Your words have been most helpful, thanks.

In this case the addresses 10.10.10.x will be your LAN addresses.
To see your external (WAN or WWW) address most routers I come across give this information on the status page.
In most cases the external IP is going to be dynamically set by your ISP and is likely to change every time you reboot your router.  If you have a fixed WAN IP you will probably be paying for it thus these are rarely seen with home users.

---

### Post by SteveHillier on 2009-11-28
> **carvacrol said:**
> I ultimately want to know how to set up a LAN so I can be better educated and hopefully pass on this information while telling everyone how great Ubuntu is. I would also love to help make Ubuntu better when I become more knowledgeable(I already have some programming experience, but forget most of it). I've been using Ubuntu for only a few weeks now and it has exceeded my expectations. Thanks.

carvacrol, if you have a router and two computers plugged into it then you have created your LAN.  Your computers will be aware of each other at the network level.
If you now want to share data between your computers then you have to set up the directories (folders) you want to share and give users appropriate access rights.  Then your machines will be aware of each other at the application level.

---

### Post by arapa on 2009-11-28
The PC's unique IP address is listed as 'inet addr:' when you run ifconfig -a

It will probably be listed under eth0 if you are plugged in using a cable. If you are using wireless it most likely is listed as wlan0

The program I use to get all IP addresses from my LAN is nmap.

```
sudo apt-get install nmap
``` 

then in your case run 

```
nmap -sP 10.10.10.0/24
```

(or what ever your LAN is - mine is 192.168.1.0/24) 

the '-sP' just pings everything in the requested block and tells you what addresses are alive and responding to ping. The /24 after your network (10.10.10.0) designates how many bits are being used for the network itself (also know as a subnet mask) 8+8+8 = 24 (11111111.11111111.11111111.00000000 is shorthanded as 255.255.255.0). The last 8 bits are used for your hosts on the network. 

Nmap can do a lot of other interesting stuff like tell you what ports are open on your various machines.

---

