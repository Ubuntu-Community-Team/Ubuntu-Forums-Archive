---
title: "IP restrictions until user pays Internet Cafe idea"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by sgtsquatlow on 2008-07-17
Hey, ive looked around and havnt noticed anything like what im looking for but i would assume it exists. I am looking for some software to install on a server that when someone connects their computer to the network it will restrict all access to the network until they visit a page and pay a fee and get the conformation code. If you could give me ideas of stuff that already work or even a maybe whether i could configure dhcp or something else to work like that. Any help would be great, thanks.

---

### Post by kidders on 2008-07-19
Hi there,

I'd use iptables, personally. You could split your idea into three tasks ...

**1: Configure iptables**
Set iptables up to block all traffic destined for external addresses, except your own PC, and the iptables router itself. I would suggest filtering by MAC address, to make circumventing payment that little bit less than trivial.

**2: Get internet access authorisation working (without payment)**
That should be a matter of writing a script to allow a particular IP address to route packets to the internet for a limited time (eg an hour).[LIST]
[*]You'll need to alter your /etc/sudoers (carefully!!) to allow a web server running on your router to modify your iptables rules.
[*]I'd suggest having the web server create a temporary file (eg /tmp/cafe/192.168.5.6), so you can use its timestamp to determine when to remove the corresponding rule.
[*]A cron task running every few minutes could check /tmp/cafe for iptables rules to remove.
[/LIST]

**3: Have your payment gateway execute your authorisation script**
How to do that depends on what you're using to verify payment, but it typically involves having the gateway use your authorisation script as a callback.


Alternatively, you could do something similar involving an authenticating proxy. That would make configuring your router more straightforward, but your users would have to suffer all the down-sides of using a proxied internet connection.

I hope that gives you some ideas.

---

