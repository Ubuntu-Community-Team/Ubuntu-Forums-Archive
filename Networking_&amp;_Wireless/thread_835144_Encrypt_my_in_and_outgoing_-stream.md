---
title: "Encrypt my in and outgoing -stream?"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by pzhukke on 2008-06-20
Hi!

I've searched on the forums but havn't really found what I'm looking for:

What I want to do, is that I want to run a server (with ubuntu) and 
hook that up to my internet, then it's some software on this server that encrypts my traffic and sends it further through another networkcard to e.g a router with some computers.
The schedule would look something like this if you get me:

_Internet_ <-> _Server with software_ <-> _Encrypted traffic_ <-> _Router with computers_.

This would make all my traffic on the router encrypted, if you get me?
Instead of running some software on each computers that encrypts the in/outgoing stream, I think this is a better sollution, or?

I'm really looking forward for some answers!
Peace.

---

### Post by SpaceTeddy on 2008-06-20
if you want encrypted traffic, you will need a software running on both computers. Also, you will need to understand basic routing for what i am suggesting, as well as basic iptables. 

I've written a [[COLOR="Blue"]howto[/COLOR]]("http://ubuntuforums.org/showthread.php?t=752127") on... um... howto setup network bridging. This is, for you setup, probably overkill, but should show you the direction you should search in. 

Also, aside from vpn connections or tunnel through some application layer protocol, i cannot think of a practical solution to your question... all assuming that i understood it correct.

hope it helps :)

---

