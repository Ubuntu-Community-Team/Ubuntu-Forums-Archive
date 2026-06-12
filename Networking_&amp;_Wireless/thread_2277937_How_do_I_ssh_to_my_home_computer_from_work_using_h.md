---
title: "How do I ssh to my home computer from work using https port?"
date: 2015-05-12
forum: Networking &amp; Wireless
---

### Post by twtduck.ii on 2015-05-12
Hello,

I'd like to be able to ssh to my home computer from my laptop at work, but I have never made an ssh tunnel before, and I'd have to do it over port 443 (my office blocks all but a few ports). Below is a diagram of what I would like to set up, could you guys help me and describe what exactly I need to do to get there?

Here are some details about my devices (If I give enough information to you guys, you can probably walk me through the whole ordeal step by step).

Router:
 - Runs dd-wrt
 - Is the only device on the network able to communicate with the modem (without rewiring or changing IP addresses)

Modem 
 - Runs default (Linksys) firmware
 - I never restart it, so I always have the same WAN IP address

My computer
 - Runs most of the day
 - Always has same IP

Laptop
 - At work, can't use most ports
 - Port 443 (https) works
 - IP address changes at work almost daily (I think that they reset the network each night)

Please guide me so that I can do this without too much trouble. Thanks!

Here's that diagram:

[IMG]http://i.imgur.com/nxPjjQC.png[/IMG]

---

### Post by ian-weisser on 2015-05-12
Beware.
Do not circumvent your employer's policies lightly.
Do NOT use an SSH tunnel to circumvent your employer's policies, proxies, or network protection measures. That may be grounds for ending your employment there.

---

### Post by twtduck.ii on 2015-05-13
I already read the policies and talked with the IT director. They are fine with it, just so long as I don't misuse the technology.

---

### Post by Lars Noodén on 2015-05-13
Your modem or router will have to forward port 443 on its own external IP to port 22 on your home computer's IP.  The details of port forwarding vary from brand to brand and router to router.  Install openssh-server on your home computer and verify that you can log in over the LAN using the local addresses.   Then set up port forwarding on your modem and see if you can log in from outside using port 443.  Once you have it working, it might be a good idea to turn off password authentication and use keys instead.  

If you want to use port 443 for both SSH and HTTPS then you could multiplex using [sslh](http://www.rutschle.net/tech/sslh.shtml).  That would still require forwarding but port 443 to port 443 (or whatever).

---

