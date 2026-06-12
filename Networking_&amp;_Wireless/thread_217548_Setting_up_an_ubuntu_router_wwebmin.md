---
title: "Setting up an ubuntu router w/webmin"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by Brunellus on 2006-07-17
Here's the story.

host 'funes' has two network interfaces--one wired (eth0) and one wireless (ath0).  ath0 is up and connects to a wireless router at 192.168.2.1 (netmask 255.255.255.0).

I want to share this connection within a small LAN, and then use 'funes' to route traffic from this lesser LAN to the wider network.  The catch--I also want this lesser LAN to be wireless.

I've followed this [this howto]("http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html").  I've been able to get webmin up and running.  The DHCP server is up, but I can't seem to get it to serve IPs in the range that I would like (192.168.1.0 rather than 192.168.0.1).  Also, How do I set it to route traffic from eth0 to ath0 and thus to the wider network?

---

### Post by Brunellus on 2006-07-17
just to clarify:  My setup is

internet----|router 1 (192.168.2.1)|----{wireless link}---funes ath0---funes eth0---router 2 (192.168.0.1)----wirelessly to other hosts.

---

### Post by Liam on 2006-07-17
Here's how you do the routing bit from the command line:

Tell the kernel to route the packets...

# iptables -t filter -A FORWARD -p all -s 192.168.1.0/24 -i eth0 -d 0.0.0.0 -o ath0 -j ACCEPT

Turn on routing...

# cat 1 > /proc/sys/net/ipv4/ip_forward

Make sure the outside router is the default gateway...

# route add default gw 192.168.2.1

I'll have to dig in to the DHCP stuff when I've got more time.

---

### Post by Liam on 2006-07-17
> **Brunellus said:**
> just to clarify:  My setup is

internet----|router 1 (192.168.2.1)|----{wireless link}---funes ath0---funes eth0---router 2 (192.168.0.1)----wirelessly to other hosts.

Wait... I missed the bit where you've got another AP in between your box and the new LAN.

My above instructions should still work if you set router 2 up to be an AP-only, ie, to not do any routing by itself.

---

### Post by Brunellus on 2006-07-17
> **Liam said:**
> Wait... I missed the bit where you've got another AP in between your box and the new LAN.

My above instructions should still work if you set router 2 up to be an AP-only, ie, to not do any routing by itself.
so wait--that would make router 2 effectively just an AP/switch, and funes the DHCP server...right?

How would that work?  

I was thinking that things would work (working backwards now)

new host >> router 2 (192.168.0.1)>>>>funes eth0 (192.168.3.1)>>>funes ath0 (192.168.2.100)>>>router 1 (192.168.2.1)>>Internet

---

### Post by Liam on 2006-07-17
> **Brunellus said:**
> so wait--that would make router 2 effectively just an AP/switch, and funes the DHCP server...right?


Yup.

Unless you're going to be hanging some more hosts off of that .3 subnet, there's really no need for it. It's also probably the reason funes isn't seeing the DHCP requests - router2 won't relay the broadcast traffic, since that's ethernet.

---

### Post by Brunellus on 2006-07-17
OK, now I am *thoroughly* confused.

I've turned off dhcp for router 2.  

But instead of serving up addresses in the 192.168.3.1 range, funes is serving up dhcp addresses like

192.168.0.247  (for router 2)

and 

192.168.0.101  (for a remote host connecting wirelessly to router 2).

This is not good, since router 2's web-configuration interface sits at 192.168.0.1.

What's going on?!

Also, I can't seem to get funes to route traffic from eth0 to ath0.

So the situation:  

1) the remote host (call it 'max') gets an IP from funes on DHCP, but not within the range I've tried to specify

2) funes can't/isn't routing traffic from the router 2 subnet to the rest of my network.

Help?

---

### Post by Brunellus on 2006-07-18
update:  I've been able to get DHCP to serve up IPs in the range that I wanted.  Now all I need is help on the routing end of things.  

Again, the goal is to route from eth0 to ath0 and thus out to the general internet.

---

### Post by mips on 2006-07-18
Have a look at the link below, might have to adapt a bit to your situation.

[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

---

### Post by Liam on 2006-07-18
I'm using .3.0 to mean your innermost net. I'm not certain at this point whether you've switched it to .2.0 or not.

So router2 is still in 192.168.3.1? Can you direct connect to that and change it to something else within the desired subnet, like .3.2?

Then, make funes eth0 .3.1, and make sure ath0 is set up with a static IP in .1.0.


Oh, wait: do all that, and then make sure router1 has a static route to .3.0 via ath0's IP - otherwise, your requests will get out, but the responses won't be able to find their way back.

---

### Post by Brunellus on 2006-07-18
I've been very unclear.

I've decided, for simplicity's sake, to go ahead and make my innermost subnet the 192.168.0.xxx net.  .2.0 is the next hop outwards. (router 1).  funes eth0 now sits fixed at 192.168.0.254 (because 192.168.0.1 is reserved for the web admin interface of router 2).  

Direct connecting to the router and changing it to anything else means...well..I lose it.  I have to hard-reset the sucker. So I accepted defeat and am trying to run on the 0.1 net.

I have no idea what I'm doing.

---

### Post by Liam on 2006-07-18
:)

Oookay. I'm gonna assume you're not going to NAT 192.168.0.0/24 to 192.168.2.100.

router1 should have a static route pointing to funes/ath0 (192.168.2.100) for 192.168.0.0/24.

funes eth0 is 192.168.0.254. It's serving DHCP for 192.168.0.0/24. You should set up iptables and routing like so:

To set up iptables and turn on routing:
# iptables -t filter -A FORWARD -p all -s 192.168.0.0/24 -i eth0 -d 0.0.0.0 -o ath0 -j ACCEPT

# cat 1 > /proc/sys/net/ipv4/ip_forward

Add router1 as the default gateway for funes:
# route add default gw 192.168.2.1

DHCP should be serving addresses in the range of .2-253, or something smaller.

Now, router2 is at 192.168.0.1. But he's not really a router, since you've turned off routing - he's just an AP, basically a switch. The only reason he should have in IP address is for the config interface.

Once you've got an internal host up (and everybody's interfaces are connected correctly), here's how to troubleshoot from it:
[list]
[*]If you can ping router2, but not funes, router2 is probably doing routing (and dhcp).
[*]If you can ping funes, but not router1, router1 probably doesn't have the static route set up.
[*]If you can ping router1, but nothing outside of it, then funes probably doesn't have the default gateway set up.
[/list]

---

### Post by Brunellus on 2006-07-18
wait wait wait.  Router1 sits at 192.168.2.1.  funes gets its IP (presntly 192.168.2.111) from Router1 via DHCP.  What's this about static routes and static IPs?  Is this whole thing simply NOT possible where that hop uses DHCP?

---

### Post by Liam on 2006-07-18
It *should* work, if you NAT the internal hosts at funes. Here's what you'd put in iptables:

# iptables -t nat -A POSTROUTING -o ath0 -j MASQUERADE
# iptables -t filter -A FORWARD -i eth0 -j ACCEPT

You won't, however, be able to access any hosts on the inside from the outside, just in case you care about that.

---

