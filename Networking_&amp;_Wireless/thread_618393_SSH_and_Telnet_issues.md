---
title: "SSH and Telnet issues"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by joselin on 2007-11-20
I have a problem trying to connect to my network ssh or telnet server from Internet.

The issue is the following:
I have a couple of routers, first one have x.x.x.1 as ip address, and the second one have x.x.x.2. Well, ssh and telnet ports are forwarded in router one to x.x.x.2. And in router two to x.x.x.3 (a computer behind the routers).

But, with this configuration can't connect... seems that computer x.x.x.3 never receives a connect petition. Could someone point me on what could be the issue and how can I solve it?

Best regards

---

### Post by wolfger on 2007-11-20
> **joselin said:**
> But, with this configuration can't connect... seems that computer x.x.x.3 never receives a connect petition. Could someone point me on what could be the issue and how can I solve it?

I'm not a network guru, but it seems to me that setup ought to work.
Question: Why is the destination computer behind 2 routers?
Suggestion: Have you tried telling both routers that traffic on these ports should go to .3?

---

### Post by joselin on 2007-11-20
> **wolfger said:**
> I'm not a network guru, but it seems to me that setup ought to work.
Question: Why is the destination computer behind 2 routers?
Suggestion: Have you tried telling both routers that traffic on these ports should go to .3?


Because the router 1 must have connected the internet line (router 2 with same configuration doesn't works fine), and this router only have one free ethernet port (to this port I connect router 2).

And yes, if I forward all the ports to .3, doesn't work fine. Can't connect to neither ssh nor telnet.

---

### Post by wolfger on 2007-11-20
Have you ever had this working, or some other port number successfully forwarded, to this computer? Or to another computer on the network? I'm a bit concerned by the statement that router #2 can't connect directly to the internet. Perhaps I'm just not knowledgeable enough to help... but it sounds to me like something is wrong with router #2.

---

### Post by dmizer on 2007-11-20
if your routers are actually routers (not hubs), they each will need to be on different subnets.

so instead of:
router 1: x.x.x.1
router 2: x.x.x.2
computer: x.x.x.3

it will need to be:
router 1: x.x.1.x
router 2: x.x.2.x

and all computers on your network (behind router 3) will have addresses like so:
x.x.2.1
x.x.2.2
x.x.2.3

---

### Post by wolfger on 2007-11-20
So in this case:
Router 1: *.*.1.1 routing telnet and ssh to *.*.2.1
Router 2: *.*.2.1 routing telnet and ssh to *.*.2.2
Computer: *.*.2.2

but I'm confused about the "one router per subnet" rule. I mean... I've never seen a 255 port router, but 255.255.255.0 is a very common subnet mask. How would anybody utilize a large subnet?

---

### Post by dmizer on 2007-11-20
you need to put each router on a different subnet because each router needs dominion over the entire subnet range even if you restrict the router to a specific range inside the subnet.

for example, router 1 tries to offer DHCP to all addresses in the X.X.1.X range (including X.X.1.1, X.X.1.2, and X.X.1.3).  if you also have another router in the same subnet, it will also trying to supply ip addresses (or pass network traffic) to X.X.1.1, X.X.1.2, and X.X.1.3.  so both router 1, and router 2 are trying to supply addresses to eachother and you have a loop.

if you try to have communication between two routers in the same subnet but different ip address range (ex: router one = X.X.1.1-10 and router 2 = X.X.1.11-20), router 1 can't see router 2 because router 2 is outside router 1's range.

so it's not about how much of the subnet is being used, it's about how addresses are supplied to each device.  or in other words, different routing devices cannot supply or pass traffic along the same subnet.  so, each router should be configured (and thought of) as a separate network, and given it's own subnet.

exceptions to this would be for redundant ip routing stack architecture, which is far to complex for consumer level routers.

my understanding of network archetecture is not complete (is anyone's?), so i'm perfectly willing to admit that i'm wrong if you can show me proof.

---

### Post by wirelessmonkey on 2007-11-21
Except you could be using VLANs, in which case multiple routers would utilize the same subnet, and multiple subnets (by nature) can be routed from one router. (...) 

Dmizer is right though... you should have router 1 (x.x.x.1) connect to external interface for router 2 (x.x.x.2).  Internal interface of router 2 should be a different net (192.168.x.1) and the computer should have an address on that net (192.168.x.2)

---

### Post by joselin on 2007-11-21
In the attached image you can see how is the state of my network.

The issue is that router 1 have the internet connection plugged and I can't connect to ssh server from outside my network. But I can connect to internet without issues from all the computers behind router 2.

If I put router 2 on other subnet, X.X.2.1, I suppose that I must forward ports to my new computer ip address (X.X.2.2) from router 1. Will be work this configuration?

---

### Post by dmizer on 2007-11-21
almost got it.

router 1 must forward incomming ssh and telnet connections to router 2.  router 2 must be configured to forward router 1 ssh and telnet connections to your computers.

so all incoming ssh and telnet connections must be forwarded twice.

incomming ssh/telnet connection -> router 1 (forward) router 2 (forward) computers

ps.
as a side note, you'll probably have much less headache if you configure your second router as a hub.  so connections are passed directly from router 1 to your computers.  you will also notice a speed increase if configured in this way.

---

### Post by joselin on 2007-11-21
> **dmizer said:**
> almost got it.

router 1 must forward incomming ssh and telnet connections to router 2.  router 2 must be configured to forward router 1 ssh and telnet connections to your computers.

so all incoming ssh and telnet connections must be forwarded twice.

incomming ssh/telnet connection -> router 1 (forward) router 2 (forward) computers


Ok, will try this evening and let you know tomorrow.

Thanks a lot for your help.

Regards

---

### Post by joselin on 2007-11-21
Well, does not work. I forwarded port from router 1 to router2, and from router 2 to computer. One thing, as a gateway in computer I must have router 1 to have internet access, if I select router 2 I can't connect to internet. Seem that I'm doing something in a wrong way.

I tried to configure router 2 as you told me before too, in other subnet, but seems that can't connect to internet through computer attached to it.

I don't know how to configure router 2 to acts as a switch, but I think that this can be the better solution for me, can someone help me on it?

Regards

---

### Post by wolfger on 2007-11-21
> **joselin said:**
> as a gateway in computer I must have router 1 to have internet access, if I select router 2 I can't connect to internet. Seem that I'm doing something in a wrong way.

Something's wrong. If it's set up as above (with routers on different subnets, and the computer on router 2's subnet), then you would have to declare router 2 as the gateway, because the computer would not be able to even see router 1. The whole purpose of declaring a gateway is to tell traffic which device to go to in order to get off the subnet.

---

### Post by dmizer on 2007-11-21
> **joselin said:**
> I don't know how to configure router 2 to acts as a switch, but I think that this can be the better solution for me, can someone help me on it?

Regards

what brand, model, and version of router is your second router?  if you can't figure out how to configure your router as a hub, you may also consider simply purchasing a hub, as they are very inexpensive.

---

### Post by joselin on 2007-12-03
Sorry for my late answer, but I were out.

The router with the issue is a Linksys WAG345G-EU, and the firmware is untouched.

---

### Post by joselin on 2007-12-03
> **dmizer said:**
> what brand, model, and version of router is your second router?  if you can't figure out how to configure your router as a hub, you may also consider simply purchasing a hub, as they are very inexpensive.

Sure, buying a hub is no problem, but I wanted to understand why I have this issue first, and if I can solve it will be great.

---

