---
title: "aMsn connection problem / Port Forwarding doesn't work"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by _Narcisse_ on 2008-08-07
Hi Everyone, 

I have a connection problem with amsn... I know what you're thinking ;), I already have port forwarded the ports 6890 to 6900 and 1863 but it keeps saying that I'm firewalled or behind a router, which is precisely the case, but ignoring the port forwarding settings. I think I forgot something evident but I can't figure what.

I recently bought a Linksys WAG200G DSL/Router that works perfectly. 
My Unbuntu computer have a static IP, the router is set as a gateway and port forwarding for both bittorrent and amsn are set. 
But I don't know why, amsn refuses even to connect.
Furthermore, Iptables is set to accept everything :

```

target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```   

Even stranger, the bittorrent port forwarding for Deluge works fine.

EDIT : Oh, and Pidgin connect without any problem...

Help would be very appreciated, I don't get it and I don't like it ](*,)

Thanks.

---

### Post by Claus7 on 2008-08-07
Hello,

I wouldn't advice you to mess with IPtables. Just firestarter would do the job. Now, are you sure that you haven't changed the default port of amsn program or that it belongs to those you have enabled? If all these are ok have you enabled via your modem the right ports with the right type? Do you check via your browser that the port forwarding is ok every time you open your pc? I had problems myself so check this out and see if anything helps you : 
[http://ubuntuforums.org/showthread.php?t=712425&highlight=amsn](http://ubuntuforums.org/showthread.php?t=712425&highlight=amsn)
[http://ubuntuforums.org/showthread.php?t=472123&highlight=kad](http://ubuntuforums.org/showthread.php?t=472123&highlight=kad)

Regards!

---

### Post by _Narcisse_ on 2008-08-07
Hello Claus7,

Thanks for your answer.
Yes, I already checked everything you said multiple times, the ports in aMsn are the default ones, the right ports are forwarded for both TCP and UDP and the router configuration saved...
I know a bit of Iptables but I've desactivated it because the router have an integrated firewall and I didn't want them to conflict with each other. 
Of course, I also uninstalled Firestarter.
I don't know but I think the problem is specific to the router...

Thanks anyway,

Regards

---

### Post by acardh on 2008-08-07
I have the same problem. I'm using Ubuntu Hardy on three different computers and in different networks. AMSN is not getting a connection in any of them, that appended at the same time. My guess is that it is a Microsoft blocking issue. It is not the first time that they do this kind of things.
I am not totally sure of this though. In the AMSN page says nothing about it (yet).:confused:

---

### Post by cariboo on 2008-08-08
Try turning of your firewall and see if you can connect. Eliminate the obvious first. If your router has a firewall, there is not really a need  to run a firewall on your computer.

Jim

---

### Post by _Narcisse_ on 2008-08-08
I'm not really convinced by the Microsoft issue, even if I know that's their style. aMsn was connecting without any problem with my ppp0 connection, the problem appeared when I installed the dsl/router. 

And as I said before, I already turned off Iptables, and de facto, Firestarter. The only firewall that's on is the one integrated to the Linksys. Obviously, it's working too much :-s

Thanks for your answers.

Regards

Narc'

---

### Post by Adri2000 on 2008-08-08
There was a change in the protocol a few days ago that made aMSN unable to connect. Fixed packages are available in the -proposed repositories. See [https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722](https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722)

---

### Post by acardh on 2008-08-08
I knew it. It was a microsoft issue.

== SRU ==
Microsoft changed the msn protocol so that amsn 0.97 is no longer able to login. This is fixed in >= 0.97.1. intrepid has 0.97.2.
At the beginning only a few servers were affected, now it seems a lot of users are encountering this bug.
Patch: [http://amsn.svn.sourceforge.net/viewvc/amsn/branches/0_97/amsn/protocol.tcl?r1=10215&r2=10261&view=patch](http://amsn.svn.sourceforge.net/viewvc/amsn/branches/0_97/amsn/protocol.tcl?r1=10215&r2=10261&view=patch)
==========

---

### Post by _Narcisse_ on 2008-08-08
**@Adri2000** : Thanks a lot ! 
Finally my new router was not the problem... Coincidences and Murphy law...
Thanks for the link, wise developer. The package in hardy-proposed works fine. 

*Merci ;)*

**@acardh** : Yes it was, my bad. Finally that's *really* their style. But that's probably an upgrade, a least in the Microsoft sense...

---

### Post by Ubulindy on 2009-11-17
Anyone having issues lately forwarding a port for aMSN 0.97.2? This only just started. Im on Hardy 8.04, no issues with anything else.

---

### Post by Ubulindy on 2009-11-30
> **acardh said:**
> I knew it. It was a microsoft issue.

== SRU ==
Microsoft changed the msn protocol so that amsn 0.97 is no longer able to login. This is fixed in >= 0.97.1. intrepid has 0.97.2.
At the beginning only a few servers were affected, now it seems a lot of users are encountering this bug.
Patch: [http://amsn.svn.sourceforge.net/viewvc/amsn/branches/0_97/amsn/protocol.tcl?r1=10215&r2=10261&view=patch](http://amsn.svn.sourceforge.net/viewvc/amsn/branches/0_97/amsn/protocol.tcl?r1=10215&r2=10261&view=patch)
==========

Ive found another work around, It seems that MSN ( official ) uses the protocol SSDP PORT 1900. When you launch aMSN, you'll notice that service comes up, but is blocked. Simply allow that service, and voila. Your port in connections will now test fine  :-D

---

