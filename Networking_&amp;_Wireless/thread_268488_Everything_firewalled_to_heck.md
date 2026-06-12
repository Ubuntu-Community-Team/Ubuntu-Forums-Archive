---
title: "Everything firewalled to heck?"
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by jago25_98 on 2006-09-30
I've just started trying to use an install I did a couple of months ago.

It's as if there's a firewall getting in the way of everything I try to do,

cups doesn't work 
sshd doesn't work
nmap dooesn't work

I'm only trying to use 127.0.0.1 for these things.

and I'm reading about zero ports open policy coming in?

How do I open those ports? Yes I know I could use iptables to flush it all but where are the config files for this now? This was a fresh install.

---

### Post by kidders on 2006-09-30
Afaik there is no firewalling on a fresh install.

> cups doesn't work 
sshd doesn't work
nmap dooesn't work

Are cupsd and sshd running & configured to bind to 127.0.0.1? You can use netstat to get more detailed information about what services you're exposing, and where.

Just to be sure, check **iptables -L** to make sure nothing odd is in there.

---

### Post by JGuru on 2006-09-30
Looks like your network Admin has blocked all that's possible -ports, cups,
 ssh etc.,!!!

---

