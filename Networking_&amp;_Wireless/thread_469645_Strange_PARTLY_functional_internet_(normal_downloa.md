---
title: "Strange PARTLY functional internet (normal downloads, barely usable browsing)"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by Eoghanalbar on 2007-06-10
I'm thinking it's got something to do with the way ubuntu interacts with my home network.

Downloading files is normal, but when browsing pages get stuck a lot. Sometimes the status is "waiting for [url]", sometimes "transferring data from", sometimes "/!\ Firefox could not find/connect" or similar failure, sometimes the address bar is just blank even though it displays the loading animation, sometimes the status is done but images are not completely loaded or even whole pages (google searches!) are chopped off halfway through.
And if I want to open an old session, ugh, it's hopeless. Only a few of the tabs ever load, and even those are not quite right.

I connect to the internet though a wired LAN. I used speedtest.net and got the same results using my laptop with ubuntu and an older windows XP desktop, and plugging the laptop in through a different wire.

So I saved a firefox session I was using on the laptop and tried it out on the XP desktop, and it loaded fine, even this one long blog archive full of graphs eventually loaded.

And the XP desktop has half the ram, a single processor, and has largely been taken over by my little brother who fills it up with viruses (they seem to hitch a ride on the masses of programs to cheat at computer games that he downloads).

I used to use an old laptop that ran windows ME before I replaced it with xubuntu, and I got the same problem. I was told it was because I should be running a lighter distro (I went to try and get DSL working, and had too much trouble with that to answer back). As I just explained, I don't think this is the case.

Disabling ipv6 or using different browsers seemed to be the generic solution to slow internet on the forums; they made no difference.

Hence the "my home network is being mean to ubuntu" hypothesis (although I can access the other computers just fine).

So I've been fiddling with the network settings in ubuntu, matching them to the XP desktop's, and even just trying ever option at random, and nothing seems to make a difference.

What can I do?

---

### Post by Pragmatist on 2007-06-10
What type of modem are you using (Make and Model)?
Are you using a router?  If so, what is its Make and Model?

Have you tried disconnecting all computers but the Ubuntu computer, and then try this:

1.) Turn everything off
2.) Reset the modem and wait until it finishes starting up.
3.) Boot the Ubuntu computer (which is the only one connected now).

---

### Post by Mr. C. on 2007-06-10
Check the DNS server you are using.  From a terminal window:

```
cat /etc/resolv.conf
```

If the DNS server listed is the IP address of your router, change it to your ISPs DNS server's.  Many forwarding DNS implementations in routers are faulty, and cause this trouble.

MrC

---

### Post by Eoghanalbar on 2007-06-11
Oh by the way, I tried your "shut down everything and restart with only the ubuntu laptop" thing, Pragmatic. Didn't help.

Mr. C.... What? I don't know how to tell which of the three strings of numbers each marked "nameserver" is the DNS, and whether it's my router or my ISP. Your bash code there didn't work for me without some modifications, either.

---

### Post by Mr. C. on 2007-06-11
nameserver is the NS in DNS (domain name server).  If you have three nameserver lines, each is tried in order.

The command I listed is correct, and works just fine.  Show the output of your entering the command and its output.

MrC

---

### Post by 444 on 2007-06-11
Do

route -n

too

If they're three nameservers then I'm pretty sure those are the ISP DNS servers. You don't have three routers...

---

### Post by Mr. C. on 2007-06-11
> **444 said:**
> Do

route -n

too

If they're three nameservers then I'm pretty sure those are the ISP DNS servers. You don't have three routers...

One could easily be the router's caching DNS server, while the other two are the ISP's name servers.   There is no reason to guess, when data is easily available.

I can't imagine why you think the routing table has anything to do with this issue.

MrC

---

### Post by 444 on 2007-06-11
More than one default route slows things...

---

### Post by corbouk on 2007-06-11
I had a similear problem with a PC a while back and no software settings would fix it.  In the end I limited my gigabit nic to 100mbps and everything started working at full speed, very odd but you never know, it might help you!

---

### Post by Mr. C. on 2007-06-11
> **444 said:**
> More than one default route slows things...

This is false.  Two default routes will cause consistent failure, not random slowness.  The kernel does not guess or randomly pick the default route.

MrC

---

### Post by 444 on 2007-06-11
> **Mr. C. said:**
> This is false.  Two default routes will cause consistent failure, not random slowness.  The kernel does not guess or randomly pick the default route.

MrC

Browsin internet right now...
```

192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ath0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth2

```

---

### Post by Pragmatist on 2007-06-11
> **444 said:**
> Browsin internet right now...
```

192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ath0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth2

```
I really think this is an inappropriate place for this debate.  Assume that one of you is right, and help the OP.  If that doesn't work, then try the other's approach.  This back-and-forth is just confusing.

---

### Post by cspence on 2007-06-11
I had a similar problem. Try setting the MTU size smaller, 1492 seems like a good guess. If I remember correctly, from what I very recently read, the largest ethernet packet is 1500 bytes. PPPoE is commonly used by DSL modems and uses 8 of those 1500 bytes. So your computer shouldn't try to send more than 1492 bytes in a packet. I set mine to this and it fixed things.

I'm not 100% sure how you should do this. I don't remember which interface you were using, but try
[INDENT]ifconfig eth0[/INDENT]
or whatever your interface is if not eth0. Somewhere in the output should be a line like
[INDENT]UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/INDENT]
You want to reduce the 1500. Then try
[INDENT]sudo ifconfig eth0 mtu 1492[/INDENT]
and see if things are better. I can imagine that some interfaces might not like this being changed while they are up, but I don't know.

You may need to fiddle with the exact value. Try
[INDENT]ping [www.google.com](www.google.com) -c 1 -s 1472[/INDENT]
and see if the packet is received back. If not, reduce 1472 to 1462 and try again. Hunt around until you find the largest working value. 1464 works for me but not 1465. Add 28 to the largest value that works, and set MTU to that.

To have it set at boot time, I had to make my wireless card's entry in /etc/network/interfaces look like
[INDENT]
auto ath0
iface ath0 inet dhcp
wireless-essid xxxx
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx
post-up ifconfig ath0 mtu 1492
[/INDENT]
I think for most interfaces, a line saying simply "mtu 1492" is sufficient, but it didn't work for me.

I hope something there is helpful,
Clay

---

