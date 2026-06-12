---
title: "Web Cache and Bandwidth Controlling"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by cryptohash on 2007-08-04
I am having issues with my ISP and what I need to do is cut down my family's bandwidth usage.  Seems simple.  We can only push a certain amount per day (to be safely inside our fair access guidelines).  Let's say that's 500 MB per day.

1) A web cache seems like a darn good idea.  I've heard great things about Squid.  I personally don't have any experience with it so a setup tutorial online would be much appreciated.

2) Bandwidth capping, throttling, whatever you want to call it also seems like a great idea.  Here's my plan: User 1 is allocated 200 MB per day, User 2 is allocated 150 MB per day, User 3 is allocated 100 MB, User 4 is allocated 50 MB per day.  Here's the catch: Some users have more than one computer (like myself).  That poses a problem considering filtering cannot be achieved using only IP addresses or only MAC addresses.  Therefore, a login system would be best.

Rather than setting up some sort of: User 1 is throttled to 100 kbps, I want each user to have the full potential of the connection, but when they reach their limit (in MB), they are cut off completely (a polite notice from the server would be great).

Unfortunately, I have absolutely no idea how to set something like this up.  I believe that there is something like this in the Astaro Security Gateway, but at this point in time (and after many frustrated attempts at installing it and getting it running), I've given up on ASG.  If I can start with a base install of Ubuntu and work from there that would be great.  Any ideas?

---

### Post by kidders on 2007-08-06
Hi there,

If I were doing this, I'd try to avoid authentication, personally. Purely from a client-side perspective, my order of preference would be...
[LIST=1]
[*]Transparent proxying of some traffic ... eg HTTP only.
[*]Standard, unauthenticated proxying of most data.
[*]Authenticating proxies.
[/LIST]

That way, if all went to plan, no client-side configuration would be necessary. I think I'd go right back to basics, and ...
[LIST]
[*]Start with a list of the MAC addresses of authorised PCs on your network. (Hopefully, that's feasible!) DHCP-assign them all fixed IP addresses.
[*]Reserve an IP pool for visitors to your network. You could allocate it a small collective bandwidth allowance later (ie treat the pool as one PC).
[*]You could essentially use your pre-determined IP addresses to take the place of authentication, and create a set of pointless (ie functionless) iptables rules to count the packets arriving at your internet gateway from each source.
[*]Every ten minutes or so, you could do some sums with the byte counts, and decide whether to block anyone.
[/LIST]

The iptables "byte counter" rules would be quite complex, especially when you add proxying to the mix. I would suggest configuring squid as a transparent HTTP proxy, and allowing everything else to make direct internet connections. When a download limit is exceeded, you could then alter the iptables non-HTTP byte counting rules to have them drop all packets, and redirect all HTTP traffic to a polite message about daily limits.

> **cryptohash said:**
> Rather than setting up some sort of: User 1 is throttled to 100 kbps, I want each user to have the full potential of the connectionYep... the world of bandwidth throttling is a nasty one, mostly because it is very difficult to exercise any control over the rate at which a remote server chooses to send you data.

Your usage limit rules could be arbitrarily complex, and written in a scripting language of your choice ... eg perl, bash, php, python, etc. For instance, you might decide to impose standardised hostnames on your network clients. My computers might be called things like kidders-powerbook or kidders-amd, allowing your script to associate IP addresses with each other in a way that wouldn't require it to be constantly re-written, every time the composition of your network changed. You could perhaps allocate 50MiB to all (ie not *each*) of the computers in your visitors pool, and up to an additional 100MiB, subtracted proportionally from your other users' daily allocations.

Although (as I mentioned) I would prefer non-authenticating, partially proxied solutions where they're possible, they have two shortcomings that may or may not be tolerable...
[LIST]
[*]It would be hard to manage situations where a MAC address/operating system combination isn't enough to uniquely identify a user (ie two different people make habitual use of the same OS on the same machine).
[*]Administrative overrides would also be awkward. With an authenticating, fully proxied scheme, all you'd have to do is supply a special username & password.
[/LIST]

Having said that, something along the lines of what I've described has a number of strengths...
[LIST]
[*]Zero client-side configuration.
[*]No interference with protocols that don't always proxy well.
[*]No irritating login prompts in web browsers.
[/LIST]

What do you think?

---

