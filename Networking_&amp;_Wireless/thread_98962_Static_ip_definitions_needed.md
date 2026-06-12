---
title: "Static ip definitions needed"
date: 2005-12-04
forum: Networking &amp; Wireless
---

### Post by Sonique on 2005-12-04
Okay, some might sound so easy you'll laugh, but i need to check because I can ping my router but cant ping anything outside the network on static ip.

I need to know what the following really mean and any examples if know any:

What is the "IP address"? [its not the one from my ISP is it?]
What is the subnet mask? [ive seen 255.0.0.0 255.255.255.0 and 255.255.0.0 but what does it mean?]
What is the Gateway address? [is that the address of my router? how can i find it out?]
What is a nameserver?
Is there anything else I need to know to configure a static ip connection?

Cheers

---

### Post by Lambert on 2005-12-04
> What is the "IP address"? [its not the one from my ISP is it?] 
Just like you have a house address so the postoffice can deliver mail to you, your pc has an address so your requests for data have a path to come back to. There is a public ip and then your local ip. Your public ip gets the data from the net to your router then your router uses your local private ip to get it to the correct pc.

> What is the subnet mask? [ive seen 255.0.0.0 255.255.255.0 and 255.255.0.0 but what does it mean?] 
This doesn't mean much for a home user, mostly larger networks. A netmask is used to break down larger networks into smaller subnets. If you want to learn more you can start [here]("http://en.wikipedia.org/wiki/Subnetwork").

> What is the Gateway address? [is that the address of my router? how can i find it out?] 
Yes it is your router. You basically have to know this. If you're connected to it there are ways to find it through commands . Most home routers are 192.168.x.x (usually 0.1 or 1.1)

> What is a nameserver? 
nameserver actually takes [www.google.com]("http://www.google.com") and turns it into an ip address so it can send the data. 


You can ping your router but no internet. Two things to look at.

1. Your /etc/resolv.con file should look something like this.

search some.server.net
nameserver xxx.xxx.xxx.xxx (where the xs = ip address of name server)

You can call your isp provider to get this information or if you have a windows xp machine you can open up a command prompt and type ipconfig /all (you can find your routers ip here also)

2. check to make sure your router is in your routing table. type the command

route

you should have something like this.

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.0.0     U     0      0        0 ath0
default         192.168.1.1     0.0.0.0         UG    0      0        0 ath0

the line to note is default. This is your gatway to the internet (your router) if that's not there then use this command

router add default gw routers_ip

where routers_ip = your routers ip (192.168.x.x)

---

### Post by az on 2005-12-04
[QUOTE=Sonique]Okay, some might sound so easy you'll laugh, but i need to check because I can ping my router but cant ping anything outside the network on static ip.

I need to know what the following really mean and any examples if know any:

What is the "IP address"? [its not the one from my ISP is it?]
What is the subnet mask? [ive seen 255.0.0.0 255.255.255.0 and 255.255.0.0 but what does it mean?]
What is the Gateway address? [is that the address of my router? how can i find it out?]
What is a nameserver?
Is there anything else I need to know to configure a static ip connection?

Cheers[/QUOTE]


Why can't you use DHCP?


As for IP address definitions, here is a great article:
[http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm)

---

### Post by tonysathre on 2005-12-04
ya i would use DHCP, to set this up go to system administration networking and change your NIC to get a IP automatically, after that do a dhclient on your client machine, u will prolly have to set up a DHCP range on your router as well but im not exactly sure how to do that, also look at this for network troubleshooting.
 [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

### Post by Sonique on 2005-12-11
1. The reason why i don't use dhcp is because i go to system>administration>networkting>eth0>dchp and enable it, it does a bit of loading and seems like it has done it, but i find out it's not actually on the internet nor can i ping my network anymore.

2. I do have a xp computer and did " ipconfig /all" but there was nothing to do with "some.server.net" and no nameservers [ primary dns suffix was blank and connection-specific dns suffix was blank too ].

3. /etc/resolv.con and /etc/resolv.conf are blank perhaps thats is what is wrong? do i need to write this in myself or should this have been default on installation?
search some.server.net  -- what part of "ipconfig /all" on my xp computer is this.
nameserver xxx.xxx.xxx.xxx -- what part of "ipconfig /all" on my xp computer is this.

---

### Post by Lambert on 2005-12-11
after running ipconfig /all there should be a section "windows ip configuration" Under this section there is "DNS suffix search list" this is what goes after search.

A little further down you will see "DNS servers" this will be the ip address that goes after name server.

---

