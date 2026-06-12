---
title: "[SOLVED] Home Network IP Assigning"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2007-08-18
[I]this might be a silly/simply-answered question, but i haven't seen a discussion about it any where.  on most routers for home networking, the default ip addresses are something like 192.168.1.#... is it advisable/possible to change these to something else?

for example... what if i change my router settings to have my home network reside on 324.546.789.444 and then set all my connections to that ip address?  would that cause any forseeable problems?

thanks, in advance for any suggestions...[/I]

---

### Post by 1/0 on 2007-08-18
The maximum number within a IP address is 255, i.e. you can set it to anything between 0.0.0.0 to 255.255.255.255. Due to that fact, setting an IP to 324.546.789.444 is impossible/not going to work. 

Some IP:s are reserved such as 127- (which is a sling address) and 0- (no destination). As far as I know there are only IP series that are reserved for private networks are 10-, 172- and 192-. If an IP from these series tries to go through a router, the router discards the traffic.

I suggest you to choose any numbers from those series (subnet mask 255.0.0.0). The thing is that these are private IP addresses. Setting them to anything else will mess up your router, i.e. it has no private IP to protect. Changing the IP address within these ranges is possible but will not really change the security much. Its much better to focus on a proper iptables scrip, secure the services, make sure the router is only acting as router/firewall and nothing else such as web server or desktop. Installing snort might be good as well. All of this is available in Smoothwall and M0n0wall. 

I hope it helps!

---

### Post by moore.bryan on 2007-08-18
[i]
thanks for the reply...

i was just using the suggested ip address for demonstration purposes, so it's good to know it wouldn't work... ;-)

what about setting the router to use 234.111.179.123 and then setting the computers in the network to work off that ip address?

i already run a hardware firewall, so that's not an issue...
[/i]

---

### Post by 1/0 on 2007-08-18
Isn't the router your firewall? 

The thing is if you set the IP to another range than 10-, 172- or 192- will mess with your router. For 1 the router will be outside your LAN since both ranges are internet ranges. 2 setting the IP to any other IP will mean that you might set your computers to use the same IP as someone else, for instance a company or a web site. That means you might get lots of traffic by mistake and probably lots of other problems.

Basically you have to set the ip range to one of the three above ranges. These are private, meaning no one else sees them outside your LAN. From the outside all your computers has the same IP; the IP given to you by your ISP via DHCP, PPP, PPPoE, static or similar.

---

### Post by moore.bryan on 2007-08-18
[I]ah, i see.  so i could use 192.234.123.222, but not 234.123.222.192?

thanks, again...[/I]

---

### Post by 1/0 on 2007-08-18
No problem. Just remember you need to set all other computers to connect via that IP.

---

### Post by moore.bryan on 2007-08-18
*got it; i think i understand now.  thanks!*

---

### Post by Synflux on 2007-08-19
The reserved ranges are:

10.0.0.0 - 10.255.255.255 /255.0.0.0
172.16.0.0 - 172.31.255.255 /255.255.0.0
192.168.0.0 - 192.168.255.255 /255.255.255.0

You should only use an address within one of the above ranges on your private network. You can change your subnet scheme however.

---

### Post by beejournal on 2007-08-22
Did this work out well for you?

I have 2 machines (one feisty server and one feisty desktop)  -> small dlink wireless router  -> cable modem.  btw i have wired connects to router.

I just installed openssh on both systems.  However when I try to ssh to server from client, it prompts me for the server login credentials but doesn't accept them.  Instead it accepts the local (client) password and makes the connection to itself.

made sure sshd was running on both ends.

What Have i done wrong here.  Tried to do the /etc/network/interfaces fix with a static ip.
Did the same on desktop system using the network gui (breaks my connection to the internet and router).  I even put the server ip and host alias in /etc/hosts.

please help!

i may post in beginners thread too.

---

