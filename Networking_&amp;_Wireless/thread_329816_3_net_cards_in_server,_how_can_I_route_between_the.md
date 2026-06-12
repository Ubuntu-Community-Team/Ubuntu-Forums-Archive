---
title: "3 net cards in server, how can I route between them?"
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by kvonb on 2007-01-02
My server (Ubuntu 6.06) has 3 network devices:

eth0, eth2, wlan0.

The Internet connects through eth2 via PPPoE.

My LAN machines connect through the server via eth0 (wired).

All this works well.

I am adding an ad-hoc wireless network to run alongside the wired LAN, through wlan0.

The drivers are all installed and working, and I can ping each machine from the other (well, after stopping Firestarter, but that is another issue!).

I need to know how to "patch" wlan0 to eth0, ie allow Internet connections from the wireless network AS WELL AS from the wired LAN.

I have attached a listing of ifconfig from the server.

Thanks, Kev :)

---

### Post by bernied on 2007-01-02
Maybe either 
[iptables](http://www.linuxguruz.com/iptables/howto/)
or
[route](http://www.die.net/doc/linux/man/man8/route.8.html) - this one less powerful, but maybe easier

---

### Post by kvonb on 2007-01-02
Those are the tools, but what is the actual theory behind doing it?  A man page is fine if you know what you need to do, and I don't know what I need to do!

---

### Post by bernied on 2007-01-03
This is not something I have actually done, but as far as I understand it, you want to set up your computer to be a network router. Most of us home-network-admin wannabees use a hardware router, which does all this work for us.

So, the router takes network traffic and decides how to forward it on, based on a bunch of software that has a bunch of rules. You already have the software, you just have to give it the rules.

So you need rules in both directions. On the machines that are connected via the wireless access point, you need a rule that says 'everything should go via the wireless access point'. And on the router you need rules that say 'everything addressed to machines on the wireless network (192.168.1.*) should go via wlan0', 'everything going to your wired LAN should go via eth2' and 'anything else should go via eth0'. It's possibly that first one that is most missing, I suspect the other two are already there, else your wired stuff wouldn't be working.

I think you can do all this with the route command. There is lots of complexity in the man page, but have a look at the examples. And also just try 
```
route
```
to tell you what rules are already running.

I think that first rule for the router, might be achieved by something like:
```
route add -net 192.168.1.0 netmask 255.255.255.0 wlan0
```
this assumes that all your IP addresses on the wireless network are in the form 192.168.1.*

On a wireless machine, you could add the route (though it might already be there):
```
route add default 192.168.1.1 ethx
```
where ethx is the wireless interface on that machine.

My approach to stuff like this has always been to start with what I know, google it, look for the key ideas and look for stuff I don't understand, then google those, until I have built a picture of what I need to do. So much of this stuff is just about knowing what words to google.

Alternatively, you can google 'ubuntu router howto', which gets you [this](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html) link, which tells you how to do this stuff using yet another tool - webmin. Though it looks like webmin is accessing iptables. But when things don't work you still need the theory.

---

### Post by kvonb on 2007-01-03
Thanks Bernie, I'll give it a go tomorrow :).

The route line you gave looks like it might work.

Regards, KEv :)

---

