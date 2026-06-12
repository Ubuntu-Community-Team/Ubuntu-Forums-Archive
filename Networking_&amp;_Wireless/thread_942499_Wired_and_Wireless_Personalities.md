---
title: "Wired and Wireless Personalities"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by xefialtis on 2008-10-09
I have need of setting up a machine in a special way. This laptop goes into 4 different environments...

I have 2 wired environments and 2 wireless environments.
With these environments, I also have VPN environments...

So it gets complicated.

I have it set with different connection "personalities" where I can start up wireless at home or at work : "sudo ifup wlan0=home" (or work)

I imagine I can do the same with eth0, so that really isn't an issue.
The big issue is, at work, we need a proxy. At home I do not need a proxy.
I have the system environment set to use a proxy, so at work, everything (pidgin, thunderbird, firefox, etc) works just fine, but at home, nothing works. So I have to go and "unset" the environment variable...etc...

And my need changes when I connect to work from home via VPN, I need to have the proxy again...

So, what I am wondering is, 
With a way to designate the wlan0=home or wlan0=work (and even doing the same with eth0, etc), is there a way to add the proxy configuration to turn the proxy on or off depending on the network I have connected to?
Can I put something in interfaces with pre-up or post-up, in some way?

---

