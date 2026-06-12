---
title: "Block countries IP addresses in iptables"
date: 2024-02-06
forum: Networking &amp; Wireless
---

### Post by sohrabp72 on 2024-02-06
I want to deny all countries' IP addresses in iptables except a specific one but seems if I only allow the one-country IP ranges it has less resource consumption. the question is, is it possible to block all incoming IP addresses in iptable except the one specified by ipset?
I want to drop any packet before processing except the one-country IP ranges. so the server won't get even ping and can't recognized in any manner.

---

### Post by TheFu on 2024-02-06
Yes. It is possible.

Place the total block list after the bypass list.

However, you should be aware that links, advertising, and tracking cross country boundaries all the time, so unless your country blocks this practice, allowing just 1 country in will definitely break many parts of the internet.

If you are running a server, then you have control over what external references are used ... er ... unless you also host things like analytics from 3rd parties or the webapps use 3rd party tools like jquery pulled from outside sources to work.

If course, you'll want to test this idea/method on a non-production system before deploying it.

IP addresses move around. They may seem tied to a specific country, but they really aren't.  /29 subnets right next to each other could be hosted in completely different countries.  It is common for content caching networks to place content servers near specific countries and have DNS requests from that region resolve to the content caches though the real servers are in a completely different part of the world. While there are free IP ---> Country lists, those are constantly out of date.  Even the paid versions with the most up to date information run 1-3 months behind.

That's for IPv4.  IPv6 makes blocking by subnet completely impractical.  You'll be better off working out a solution that recognizes attacks and adds the IP/subnet to a blocklist for a month or 6.

And just to be clear, I decided to attempt something similar to what you seem to wan about 15 yrs ago.  I started with a free country -to- subnet list and added to it.
```
$ wc -l /etc/ipset.up.rules
7135 /etc/ipset.up.rules

```
Now it is 7100+ subnets being blocked through an IPset list with a single firewall.  I use a different set for different services since emails from friends overseas need to be allowed, but not spam from certain countries.  1 IPtable rule applies to all those ipset subnets:
```
$ sudo iptables -L |grep countryblock
DROP       all  --  anywhere             anywhere             match-set countryblock src
```
I don't even bother logging them.

Oh ... and Let's Encrypt isn't happy about my blocks, so every 3 months, I have to flush it for 3 minutes to get new free TLS certs.

Is this for a desktop/laptop or a server?  The way to handle it is very different.

---

### Post by sohrabp72 on 2024-02-06
Thanks for replying.
There is no linked services to be worried about if they break.
Yes, it is a server and there is really no need of other countries IP ranges but one.
How can I achieve that using ufw or iptables?

---

### Post by TheFu on 2024-02-06
I don't know that ufw supports using ipset rules at all. It may. IDK.
I have a single rule that blocks "bad" subnets as an ipset.  I add more subnets to the ipset list both live and to the ipset file so they aren't lost after a reboot.  There are lots of guides to accomplish this on the internet.  I set it up about a decade ago and don't remember all the details. Sorry.
$ more /etc/iptables/rules.v4 
```
...
# The first rule after the automatic rules from other tools
-A INPUT --match set --match-set countryblock  src --jump DROP
...
```

I have a bunch of custom iptables INPUT rules for all sorts of web stuff like preventing abusers from eating all the bandwidth, 

The trick is to ensure the ipset is filled after boot, but before networking is up.  After networking comes up, iptable rules are applied which references the named ipset.  I'm block subnets. You want to block all, and allow specific subnets, it appears. That's the opposite of what I've done.

---

### Post by The Cog on 2024-02-06
> **TheFu said:**
> I don't know that ufw supports using ipset rules at all. It may. IDK.
nftables has **set** built in - not an add-on like **ipset**.
If you are using a recent Ubuntu then you are very probably using nftables anyway, through an iptables -> nftables translation utility. Try **sudo nft list ruleset** and see if it says anything.

---

### Post by TheFu on 2024-02-06
```
$ sudo nft list ruleset
sudo: nft: command not found
```

so not on 20.04.

22.04 seems to have nft. Nice.  I'd learn to use nft, if I were doing this today on a newer release than I'm currently running.

---

### Post by sohrabp72 on 2024-02-06
Yes I have nft on 22.04.
How can I do that using nft?

---

### Post by The Cog on 2024-02-07
> **sohrabp72 said:**
> Yes I have nft on 22.04.
How can I do that using nft?

It's the same concept as iptables. It's mainly the configuration syntax that has changed. So TheFu's comments still apply.
Here are some reference docs:
[https://wiki.nftables.org/wiki-nftables/index.php/Main_Page](https://wiki.nftables.org/wiki-nftables/index.php/Main_Page)
[https://www.netfilter.org/documentation/index.html](https://www.netfilter.org/documentation/index.html)
[https://wiki.nftables.org/wiki-nftables/index.php/Netfilter_hooks](https://wiki.nftables.org/wiki-nftables/index.php/Netfilter_hooks)
[https://netfilter.org/projects/nftables/manpage.html](https://netfilter.org/projects/nftables/manpage.html)

It is probably best if you start a new thread with more specific questions as we don't want to hijack this specific iptables question.

---

