---
title: "ip6tables looses rules on next boot"
date: 2005-09-26
forum: Networking &amp; Wireless
---

### Post by monoworks on 2005-09-26
Hi!

I used mainly the rules from [http://www.tldp.org/HOWTO/Linux+IPv6-HOWTO/x2231.html](http://www.tldp.org/HOWTO/Linux+IPv6-HOWTO/x2231.html) to disable ip6 traffic completely for incoming connections. This works.

But for some strange reason on next boot the rules are lost as ip6tables -L tells me.
Does ip6tables not save it on his own?
Why is ruleset of iptables not lost? Because of Firewall Firestarter saving it in some config files I do not yet know?

Thank you in forward! :-)

---

### Post by GrumpySmurf on 2005-09-27
The official ubuntu wiki has a [Iptables howto]("https://wiki.ubuntu.com/IptablesHowTo") guide.

Basically, you'll need iptables-save to keep your settings after you've set your rules.

Ip6tables isn't specifically mentioned, so if iptables-save doesn't work (or ip6tables-save maybe), you'll need to create a [bootup script]("https://wiki.ubuntu.com/UbuntuBootupHowto").

---

### Post by monoworks on 2005-09-27
Thank you very much!

ip6tables-save did not work as already tried. Strangely it outputs the rules direkt to the screen with formatting for ip6tables conforming textfiles. It seems to be meant using it with a pipeline.

Well, I created a bootscript and this works. :-)

For others having same problem:
Read the link as mentioned before: [https://wiki.ubuntu.com/UbuntuBootupHowto](https://wiki.ubuntu.com/UbuntuBootupHowto)
And create as initscript a contentlike:
```

#! /bin/sh

ip6tables -I INPUT -i sit+ -p tcp --syn -j DROP &&
ip6tables -I INPUT -i eth+ -p tcp --syn -j DROP &&
ip6tables -I FORWARD -i sit+ -p tcp --syn -j DROP &&
ip6tables -I FORWARD -i eth+ -p tcp --syn -j DROP &&
ip6tables -I INPUT -i sit+ -p udp ! --dport 32768:60999 -j DROP &&
ip6tables -I INPUT -i eth+ -p udp ! --dport 32768:60999 -j DROP &&
ip6tables -I FORWARD -i sit+ -p udp ! --dport 32768:60999 -j DROP &&
ip6tables -I FORWARD -i eth+ -p udp ! --dport 32768:60999 -j DROP &&
ip6tables -A INPUT --protocol icmpv6 --icmpv6-type echo-request -j ACCEPT --match limit --limit 30/minute

```
(this example blocks all incoming ip6 traffic for example to protect your unsecured mysql and apache)

---

