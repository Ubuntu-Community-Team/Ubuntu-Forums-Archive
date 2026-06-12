---
title: "Sharing a internet connection between Mac OS X and Ubuntu 6.10"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by mrlinuxpt on 2006-11-01
I have a friend that has a MacBook and he wants to share the internet connection win the Mac with his Ubuntu 6.10 PC.

How can he do it?

---

### Post by kidders on 2006-11-01
Hi there,

There are too many answers to this question ... things very much depend on what kind of hardware is available. For instance, if your friend's modem has a router in it -- many do -- you don't need to do anything other than plug both machines into it. On the other hand, the Ubuntu box might be connecting to your ISP over PPP, in which case you'll probably wind up having to configure the computer *itself* as a router, and install a second network adapter.

If you can be a little more specific, there's bound to be a good solution for you :-)

---

### Post by mrlinuxpt on 2006-11-01
He wants to connect direcly to the ubuntu box. He has a USB modem because he broke the router yesterday.

---

### Post by kidders on 2006-11-01
Ohhhh... and hence the need to ask the question in the first place. Now I'm with you :-)

Here's one option:
[LIST]
[*]Install iptables, bind and dhcp on the Ubuntu box.
[*]Configure dhcp & bind.
[*]Plug the MacBook into the Ubuntu box's ethernet port, now that it's free.
[*]Ping the Ubuntu box from the Mac.
[*]Configure iptables and set up packet forwarding.
[*]Surf the web from the Mac.
[/LIST]

Basically, you would be setting up the Linux box to take the place of the router. Unfortunately, if you've never done it before, this procedure is fraught with irritating complications. If you like, I can talk you through it ... there are many, many HOWTOs around also.

---

### Post by cenourinha on 2006-11-01
Hi there, I'm the friend...
:) 

I have a router.
I have the macbook powered by wireless... and i have connect a network cable in the macbook to the pc (ubuntu).

I have configured it in the Network options.
I have put the ip, router address and the mask, i can send ping to the macbook but i cann't send ping's for the router.

There is no connection, how can i soulve this problem?
I have desactivate the macbook firewall and turned the internet connection by network.

---

### Post by kidders on 2006-11-01
Hiya,

I'm afraid I'm a little lost ... you *do* have a router? In that case, why not just plug both your computers into it?

If you want to connect your Mac to the internet via your Ubuntu box anyway, have you installed iptables, etc. & configured NAT/masquerading, et al?

---

### Post by cenourinha on 2006-11-01
I have router... but i'm a little nervous and i have cut the cable... and now it's smaller looool

The router have wireless soo i have internet on macbook.
Then i wanna have internet in ubuntu via macbook.

---

### Post by kidders on 2006-11-01
Lol you *cut* your cable?!

Well that's more of a question for an Apple forum, really. You'll be happy to know that most (if not all) of what you need should already be on your Mac though. Take a look in System Preferences -> Network to get started.

Ideally, you shouldn't need to do anything to your Ubuntu box, except configure it to use DHCP.

---

### Post by cenourinha on 2006-11-01
Yes, i cut my cable because my connection get down in 5 to 5 minutes for 6 mounths and my Internet Service Provider didn't do nothing.

:\

---

