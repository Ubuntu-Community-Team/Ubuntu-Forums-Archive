---
title: "Run two PiHole as DNS server at home"
date: 2022-01-19
forum: Networking &amp; Wireless
---

### Post by cazz on 2022-01-19
Hi
Right now I use one PiHole to filter my browser traffic to make it easy to use internet :)

So right now I have 

```
Computer-PiHole-Router

```

But I do wonder if that is goode idea to have two PiHole as DNS server at home and then use Google 8.8.8.8/8.8.4.4 as DNS server

I wonder if that any very good idea to have your own DNS server at home with PiHole and unbound?
[https://docs.pi-hole.net/guides/dns/unbound/](https://docs.pi-hole.net/guides/dns/unbound/)

---

### Post by TheFu on 2022-01-19
I think it is a good idea to have 2 DNS servers at home.
I think is it a bad idea to use Google's DNS. Use the privacy-respecting Cloudflare DNS instead.  1.1.1.1 and 1.0.0.1

What's Computer-PiHole-Router?  hostnames should be all lower-case for a few reasons, though in theory, mixed-case names shouldn't matter for any hostname or DNS name ... sometimes it does.

I don't use unbound, though it is in my router as an available service.  I vaguely recall some issue, at least for my OPNSense router, with Unbound.

While you are worrying ... setup your pihole DNS to use DNSSec.

---

### Post by cazz on 2022-01-20
Thanks for the replay
That I mean with "computer-pihole-router" is that I have set routerns ipaddress as DNS server in Pihole.


To tell the truth that I'm not sure what unbound does, have not read so much about it yet but I going to look into DNSSec.

---

### Post by TheFu on 2022-01-20
No need for your router do know anything about DNS. I disable all DNS in my router to prevent human confusion. After all, things that work, even when not the desired configuration, will be used by someone accidentally.  The only DNS settings in a router might be in the DHCP server and it should point at the r-pi static IP address on the LAN.

The pihole should point directly at 1.1.1.1 and 1.0.0.1 external DNS.
BTW, on all your internal LAN machines, you don't want them running any local DNS caching - so disable resolvconf and systemd-resolved.  You want a simple, static, /etc/resolv.conf that points at YOUR pi-hole systems and is a normal file, not a symlink somewhere else.

---

### Post by cazz on 2022-01-21
I think I going to try this

DNS-Over-HTTPS

[https://docs.pi-hole.net/guides/dns/cloudflared/](https://docs.pi-hole.net/guides/dns/cloudflared/)

---

### Post by fragglebliss on 2022-01-21
Forgive my ignorance but why use Unbound when using Pi-Hole?

Why not just allow Pi-Hole to handle all of your DNS tasks and simply point all internal systems to the Pi-Hole server?

---

### Post by cazz on 2022-01-22
To be honest, I do not really know what all this is doing, I just try a little for fun
I still want to use Pi-hole to filter advertising and did not think to add some more to that.
But Yesterday I did see my internet provider support DoT so I did install stubby and got that to work with Pi-hole.

I did have to change port of stubby to 53000 but now it works I think :D

---

### Post by TheFu on 2022-01-22
Pi hole is a DNS server. It filters advertising using lists of known advertising DNS locations.  Only the Pi-hole should be used for DNS by any systems where you want filtering.  The Pihole needs to point to upstream DNS ... 1.1.1.1 is my recommendation with 1.0.0.1 as a failover. This is a privacy-centric DNS provider that is also very fast.

Your ISP's DNS is likely (99.99%) used for tracking. Using any encrypted channel to the ISP is worthless. They already see all your data unless it goes somewhere else.  The point of DNSSec and DNS-over-HTTPS is to keep DNS data away from anyone who doesn't actually need it - like your ISP!

No clue what "change port of stubby" means.

---

### Post by fragglebliss on 2022-01-22
> **cazz said:**
> To be honest, I do not really know what all this is doing, I just try a little for fun


That's ok.

I do a lot of that myself and is the only way to learn how stuff works and what configs work together best.

I have run Pi-Hole plenty of times (not currently) but have always found no additional components are necessary.

At least not if it's just ad-filtering that you want to achieve.

---

### Post by TheFu on 2022-01-23
Pi-hole has a simple DNS server inside it too. This can be used for your LAN systems and if you are running any internal-only websites or other internal servers (jellyfin, NFS, calibre, wallabag, nextcloud, whatever), it makes some systems able to find them easier - especially for Android devices that Google has decided should completely ignore /etc/hosts files AND system set mDNS or @netgroups (not many people use @netgroups anymore).

My pi-holes have a simple text table for DNS entries on my LAN.  Combined with static IPs and DHCP Reservations, all devices on the LAN have known IPs, except guest devices (those actually are all wifi and end up on a different, untrusted, LAN along with my IoT and IoSh devices).

---

