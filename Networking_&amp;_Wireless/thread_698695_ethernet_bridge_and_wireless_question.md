---
title: "ethernet bridge and wireless question"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by xls on 2008-02-16
Here is my situation.  I have an established network of mixed wired/wireless ubuntu/windows clients.  Everything works as it should.  I have moved one of my wired computers out of the office and into my bedroom.  while not essential it would be nice to reconnect it to the network.  however, it's too far for any ethernet cables i have and i do not want to purchase a new wireless adapter.  it's simply not that important.

so i began to ponder.  despite being mobile, my laptop almost never leaves the bedroom.  said laptop has an unused ethernet jack on it.  it is also running ubuntu 7.10 (gutsy) 64 bit.  it should be a snap to just hook it up and get it going.  linux is nice like that.

the catch is that this isn't your usual case of "internet connection sharing."  I want the new bedroom computer back on the same network i have now.  I've setup openvpn with a bridged connection before. (once, and it was awhile ago so i forget the details and didn't learn much)  I've also used VMWare with a bridged interface and it worked without any fuss.  But that was under Windows and VMWare kinda did everything for me.  Anyway, I wanted to try bridging.

I've gotten bridge-utils on the laptop and tried setting that up but that didn't work.  I'm missing something and all "howtos" point to the same documentation ( [http://www.linux-foundation.org/en/Net:Bridge](http://www.linux-foundation.org/en/Net:Bridge) ) which I've read over and over but only makes me more and more confused.

Now I'm really starting to wonder... Is it even possible to bridge a ethernet jack to a wireless connection?  I do have an Atheros chipset wireless NIC for my laptop.  I'm guessing if this is at all possible, it should be with that NIC.  i'm not using madwifi.  from what i understand, it's included in Gutsy.

proposed network:
[IMG]http://i28.tinypic.com/2nlvm.png[/IMG]

maybe bridging isn't the solution i'm looking for.  if i can do it with routing, i'll do it that way.
I just want Computer 3 back on the network such that it receives broadcast packets from computers 1 and 2 and the wireless laptop.  if it could DHCP it's on ip as well, that would be great but not required.  And the laptop cannot sacrifice it's network connection for this.  i don't want to dedicate it to bridging.  so, is this a lost cause?

cheers

---

### Post by 444 on 2008-02-16
It's definitely possible. I use NAT for this, which may not be ideal for you (the broadcasts won't reach). I haven't bothered figuring out the bridging way.

Very simple way of doing it:
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -A POSTROUTING -t nat -o eth1 -j MASQUERADE

Then you'd just configure some manual ip addresses that don't conflict with the wireless adapter. You could set up DHCPD for automatic addresses.

---

### Post by xls on 2008-02-17
i wanted to avoid routing.. i could just use openvpn to hop onto my original network.  this just seems so heavy handed.  I know routing is possible and it's NOT what I want.  I could careless about Internet.  I want to access servers and files on my own and current network.

---

### Post by xls on 2008-02-19
bump

---

### Post by raiXer on 2008-02-20
Sorry but bridging is the only way to receive broadcasts from your current network.
I am too looking for some info on how to do bridging under ubuntu.

Btw it is possible to bridge a wireless card with a ethernet card. Windows does it.

---

### Post by SpaceTeddy on 2008-02-20
briding under ubuntu works as well as it does on any other debian based system. and you can bridge anything you want, really, as long as it is a device that has network capabilities.

install the brigde-utils (sudo apt-get install bridge-utils) and then use brctl to bind the two working network-cards together as one. 

don't have much time at the moment, but i can explain in more detail later.

this howto should get you started, tho. you don't need all the install, just jump in at the basic setup... that should work :)
[http://www.faqs.org/docs/Linux-HOWTO/BRIDGE-STP-HOWTO.html#BASIC-SETUP]("http://www.faqs.org/docs/Linux-HOWTO/BRIDGE-STP-HOWTO.html#BASIC-SETUP")

---

### Post by xls on 2008-02-21
thanks for the replies.  i've sorta made this my a little project of my own now.

the bridge stuff is easy enough to link two network devices together.
then for the bridging computer to get an ip, you have the BRIDGE get one via DHCP.

where does my wireless network configuration fit into all this?
when do i tell it which wireless network to use and what the password is for WPA2?

I'm going to read more about manually configuring my wireless and see how far that gets me.

cheers

---

### Post by SpaceTeddy on 2008-02-21
> **xls said:**
> thanks for the replies.  i've sorta made this my a little project of my own now.

the bridge stuff is easy enough to link two network devices together.
then for the bridging computer to get an ip, you have the BRIDGE get one via DHCP.

well, that is easy enough on the command line... "sudo dhclient br0" and you should have one.
[EDIT]
you should consider putting your bridged network cards in promisc mode so they will really forward ANYTHING. (do this with "sudo ifconfig eth0 promisc" and for eth1 likewise)
> **xls said:**
> 

where does my wireless network configuration fit into all this?
when do i tell it which wireless network to use and what the password is for WPA2?

you need to configure the underlaying wireless card to be an adhoc network. Also, the wifi card is part of the bridge. therefore, the adhoc network becomes part of the bridge and get put into the local network via the bridge.

for configuring your wifi card manually, i'd suggest you start with iwconfig. i know it is possible to connect to an access point with that... i don't know if you can also put the card into adhoc mode with it..
> **xls said:**
> 
I'm going to read more about manually configuring my wireless and see how far that gets me.

good luck on your quest :)

---

