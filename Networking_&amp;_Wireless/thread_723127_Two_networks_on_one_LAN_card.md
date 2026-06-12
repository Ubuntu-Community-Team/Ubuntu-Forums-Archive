---
title: "Two networks on one LAN card"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by dusnoki on 2008-03-13
Here is my problem... i have two networks that i need to enable simultaneously on Kubuntu 7.10 64bit version...
they both have different ip adressess, different Gateways but i have only one dns adress...

1.st network
IP adress: 10.128.32.110
mask 255.255.255.0
gateway 10.128.32.1

2.nd network
ip adress: 192.168.1.3
mask:255.255.255.0
gateway:192.168.1.1
dns:192.168.1.1

i did the same thing in windows xp without problem... but here in Kubuntu i'm having some problems... can someone help me please!!!

---

### Post by Paris Heng on 2008-03-13
> **dusnoki said:**
> Here is my problem... i have two networks that i need to enable simultaneously on Kubuntu 7.10 64bit version...
they both have different ip adressess, different Gateways but i have only one dns adress...

1.st network
IP adress: 10.128.32.110
mask 255.255.255.0
gateway 10.128.32.1

2.nd network
ip adress: 192.168.1.3
mask:255.255.255.0
gateway:192.168.1.1
dns:192.168.1.1

i did the same thing in windows xp without problem... but here in Kubuntu i'm having some problems... can someone help me please!!!

It is Ok if one DNS for the outgoing interface, just use the **route add** to add the network into the linux routing table. Try man for route to look for the command. What you want to do actually with this two different IP subnet?

---

### Post by dusnoki on 2008-03-13
Well the first network is my local wireless network from my town... and the second network is my adsl modem... so on the first network i am able to download things in local and 2.nd from the internet... but my problem is how to enter these two adresses into network manager or how it is called... i know the route add procedure but i don't know where can i enter the second IP adress and gateway... that's my problem
now i can eighter use one or the second network... not both simultaneously!!!

---

### Post by SpaceTeddy on 2008-03-13
i don't understand the setup you are talking about. you have one network card which should hold both ip confgurations ? you have two network cards that should act as one ? can you please explain with a little more detail what exactly you are trying to do.

also, having more than one gateway does not work ! a gateway is a route of last resort, where anything that the computer cannot find attached to it's netwok cards will forward the requests to in the hope that the gateway knows where they are. Having more than one is having the internet offered twice to you.

so, please clarify what you want to do with your setup - what your goal is that you are trying to accomplish.

---

### Post by koenn on 2008-03-13
Two networks on one LAN card :
You can assign 2 IP addresses to 1 NIC by creating aliases, i.e instead of eth0, you configure eth0:0 and eth0:1 in /etc/network/interfaces.
[http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html](http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html)

but since you're talking about both wireless and wired networks, this is probably not what you're actually trying to do.
You'll have to be more precise in your explanations.

---

