---
title: "Using eth0 as a management interface and wlan0 for other traffic [iptables]"
date: 2015-06-27
forum: Networking &amp; Wireless
---

### Post by mudisoft on 2015-06-27
I've been playing with Ubuntu Mate on my RPi2, but I want to make eth0 the management interface and use WiFi for standard traffic.

I would like to use iptables (or something else?) to:

Allow port 22 on eth0
Allow port 3389 on eth0
Disallow everything else on eth0

Allow all traffic on wlan0 (web browsing, etc.)

I was able to add my ports with
```
iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
```
and block everything else with
```
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP
```
but I don't know how to make traffic (like web browsing) pass through the WiFi. I have a feeling that using the DROP statements I've blocked all traffic incl. wlan0, but I'm not sure how to isolate the interface. Any help is greatly appreciated.

---

### Post by TheFu on 2015-06-28
Normally, each interface controls the data going over that interface based on routing tables, metric setting and subnets.  If the wifi and wired interfaces are connected to different subnets, then this can happen automatically.   Otherwise, if it is possible, it is a fairly complex thing to accomplish and I think the only way is by using different userids - check out the -m owner option.

However, if you are doing this for security reasons - then you really need to use different subnets, IMHO.

My first question is how long have you been using Unix/Linux?

---

### Post by mudisoft on 2015-06-29
Thanks for the reply @TheFu

The two devices are on different subnets:
eth0: 192.168.0.0/24
wlan0: 192.168.1.0/24

What I'm not sure about is how to set up iptables so it can distinguish between the two and not block all traffic when I say "iptables -P INPUT DROP"

Is "iptables -P INPUT DROP **-i eth0**" going to block traffic only on eth0 - I might try that?

P.S. I am confident with using Linux, but I don't have a good understanding of it's inner workings e.g. firewalls.

---

### Post by ian-weisser on 2015-06-30
> **mudisoft said:**
> The two devices are on different subnets:
eth0: 192.168.0.0/24
wlan0: 192.168.1.0/24

Good.
Your router (not your Ubuntu system) should be routing .1 subnet traffic over the internet, and keeping .0 subnet traffic local.
One assumes you don't want to expose your admin interfaces to the dirty, dirty internet.

Example:
Let's say your rpi eth is plugged into a laptop eth. 
The Laptop functions as a router, and the Laptop's settings determine if that subnet can see the internet. Not the rpi's settings.
Meanwhile, the rpi's wi-fi dongle sees your router.
The router settings determine if wifi traffic can see the internet. Again, not the rpi's settings.

When rpi connects to the two subnets, the *routing table *(unrelated to iptables) tells the system which interface to send internet-related packets to.
The routing table logic figures which connection to use from clues in the upstream connections. ('Hey, that's a router and gateway. I will use it')
After the system has a *route* for traffic, you're ready to send actual traffic.
iptables filters and modifies that actual traffic based upon the rules (accept, drop, masquerade, mangle, etc) that you give it.

One of the clever things you can do with iptables is to change (mangle) packet data as it passes through, and that can be used for routing those packets. But I think it's a rather hacky solution for a non-router; better to simply set the routing table properly by ensuring your upstream connections have the proper settings.

---

