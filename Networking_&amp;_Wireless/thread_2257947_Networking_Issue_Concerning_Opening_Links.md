---
title: "Networking Issue Concerning Opening Links"
date: 2014-12-23
forum: Networking &amp; Wireless
---

### Post by uRock on 2014-12-23
This problem is occurring in Chrome beta and stable, as well as Firefox. I am running Ubuntu 14.04 64

When I go to Twitter and click on a link that has been tweeted the browser won't load the t.co link. Since I have both wired and wireless connections I can click disconnect in Network Manager on the wired connection right after clicking on a link and it will sometimes open the page, but that doesn't always work. It doesn't matter what site the link is going to.

This has been an ongoing issue for several months.

This also seems to be causing Facebook to intermittently have issues loading.

If I try to ping one of the links, it fails.```
******@****:~$ ping http://t.co/ejZpdGL6h9
ping: unknown host http://t.co/ejZpdGL6h9
******@****:~$ traceroute http://t.co/ejZpdGL6h9
http://t.co/ejZpdGL6h9: Name or service not known
Cannot handle "host" cmdline arg `http://t.co/ejZpdGL6h9' on position 1 (argc 1)
******@****:~$ ping http://ubm.io/1E8EI9T
ping: unknown host http://ubm.io/1E8EI9T
```

Things I have tried which hasn't fixed the problem,

1. Swapping out routers, even though none of the other systems on my network are having this issue.
2. Changed the DNS address on the router and in Network Manager to 8.8.8.8.
3. Uninstalled Network Manager and installed wicd.
4. Deleting Network Manager profiles.
5. Physically disconnecting the wired connection.
6. Disabling ufw.

I am at a loss at figuring out what to try next.

Cheers & Beers,
uRock

---

### Post by Doug S on 2014-12-23
I don't know about your browser problems, but I think your ping problem is because it should be a dns resolvable destination. I.E.:```
doug@doug-64:~$ [COLOR=#ff0000]ping t.co[/COLOR]
PING t.co (199.59.148.12) 56(84) bytes of data.
64 bytes from r-199-59-148-12.twttr.com (199.59.148.12): icmp_req=1 ttl=59 time=95.0 ms
64 bytes from r-199-59-148-12.twttr.com (199.59.148.12): icmp_req=2 ttl=59 time=94.6 ms
64 bytes from r-199-59-148-12.twttr.com (199.59.148.12): icmp_req=3 ttl=59 time=94.9 ms
64 bytes from r-199-59-148-12.twttr.com (199.59.148.12): icmp_req=4 ttl=59 time=94.3 ms
...
```

---

### Post by SeijiSensei on 2014-12-23
You can't ping URIs, only the servers themselves.  As Doug points out, pings for t.co itself work fine.

Are your wired and wireless connections both in the same subnet, e.g, 192.168.1.28 and 192.168.1.29?  That's never a good idea unless you're very careful with routing.  Just use one or the other connection.  If you want to use both to improve throughput, you should look into [bonding]("https://help.ubuntu.com/community/UbuntuBonding") interfaces.

---

### Post by uRock on 2014-12-23
> **Doug S said:**
> I don't know about your browser problems, but I think your ping problem is because it should be a dns resolvable destination. I.E.:```
doug@doug-64:~$ [COLOR=#ff0000]ping t.co[/COLOR]
PING t.co (199.59.148.12) 56(84) bytes of data.
64 bytes from r-199-59-148-12.twttr.com (199.59.148.12): icmp_req=1 ttl=59 time=95.0 ms
64 bytes from r-199-59-148-12.twttr.com (199.59.148.12): icmp_req=2 ttl=59 time=94.6 ms
64 bytes from r-199-59-148-12.twttr.com (199.59.148.12): icmp_req=3 ttl=59 time=94.9 ms
64 bytes from r-199-59-148-12.twttr.com (199.59.148.12): icmp_req=4 ttl=59 time=94.3 ms
...
```
Thanks for pointing that out. I can ping t.co
> **SeijiSensei said:**
> You can't ping URIs, only the servers themselves.  As Doug points out, pings for t.co itself work fine.

Are your wired and wireless connections both in the same subnet, e.g, 192.168.1.28 and 192.168.1.29?  That's never a good idea unless you're very careful with routing.  Just use one or the other connection.  If you want to use both to improve throughput, you should look into [bonding]("https://help.ubuntu.com/community/UbuntuBonding") interfaces.

I've tried in the past using just one interface with the same results.  Is there a command I can run to get Network Manager to dump everything it has stored about the connections to start anew? I've tried deleting the connections via NM and it didn't help any after restarting and not allowing wireless to connect.

---

### Post by uRock on 2014-12-23
I just threw in an ubuntu Live DVD and found that these problem persist there as well. I'm going to give 14.10 a try and see if the problem is there as well.

---

### Post by uRock on 2014-12-26
It appears the problem was the USB wired NIC. The problems with clicking links seems to went away after removing it from the system.

Facebook is still being screwy, but other people with different OSes seem to be having the same issue with that.

---

