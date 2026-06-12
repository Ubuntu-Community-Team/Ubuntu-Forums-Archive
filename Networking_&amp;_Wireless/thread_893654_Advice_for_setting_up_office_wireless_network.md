---
title: "Advice for setting up office wireless network"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by DigitalFudge on 2008-08-18
Hey Guys,

My budget for setting up a network for our new offices has been slashed so much that my boss has pretty much left me only with the option of running an entirely wireless office network.. (I know...).

I intend to have an ubuntu server running in the backend to provide some file and print server needs. 

I've set up many wireless networks before, but none with multiple access points. So I have a few questions:

[LIST=1]
[*]How can I configure the network so that clients can seamlessly switch between APs? Is it simply a matter of having the same SSID or is it a little more complicated?
[*]Is it possible to control at all who can access what on a wireless network? For instance normal desktops etc have full access to the network and everything, while guest laptops can only access certain sites or network resources?
[*]How does RADIUS fit into all this?
[/LIST]

Thanks very much
DF

---

### Post by jimv on 2008-08-18
1.  Here's a article for setting up several AP's for the same network:

[http://www.wi-fiplanet.com/tutorials/article.php/3628576](http://www.wi-fiplanet.com/tutorials/article.php/3628576)

2.  I can think of two way to do this.  You could use MAC address filtering or you could setup a domain to allow authenticated users access to network resources.

3.  A radius server essentially checks credentials when someone tries to join a network.  Here's a Wikipedia article.  DD-WRT firmware for wireless routers supports the use of radius.

[http://en.wikipedia.org/wiki/RADIUS](http://en.wikipedia.org/wiki/RADIUS)

---

