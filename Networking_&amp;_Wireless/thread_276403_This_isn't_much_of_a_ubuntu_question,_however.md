---
title: "This isn't much of a ubuntu question, however"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by c0rrupt3d_fate on 2006-10-12
plain and simple, I use windows machines at school, however at school you've guessed it, 99% of the world wide web is blocked, and its blocked at router level, and I can't use a proxy I've tried that already, what I can do contrarily is use a VPN to my house, to get to virtually any site I want, from school.... although the site that was providing the VPN service for me, which by the way was logmein.com is also now blocked, I've heard something about ssh tunneling as an alternative, I have putty on the computer at school, I just can't use it, because I have not the slightest clue on how to go about setting up a server at my house for it, also keep in mind, my only objective here is accessing blocked web pages


thank you in advance

---

### Post by kidders on 2006-10-12
Hi there,

> I have not the slightest clue on how to go about setting up a server at my house
The OpenSSH server works out of the box ... you won't have to jump through any hoops.

Having done things like this in the past, may I suggest installing Squid too. You would run a www proxy on your home PC, that only serves pages to localhost, and tunnel a connection to it over SSH from school.

Bear in mind that you would most probably be expelled for doing this (at least where I live!), so here's what I'm suggesting you should **_definitely not do_**:

[LIST=1]
[*]Serve your home PC with squid on, say, port 8080.
[*]Serve the world with an SSH server, on a port that's likely to be accessible from school ... say maybe 53.
[*]Go to school and log into your PC, redirecting remote (school) port 6969, say, to localhost:8080.
[*]Reconfigure your browser to use a proxy at localhost:6969.
[/LIST]

All being well, you can avoid having to run your SSH server on port 80. This would mean you'd have to persuade puTTY to use your school's proxy to tunnel your SSH connection over HTTP, and you'd end up with a completely ludicrous HTTP over SSH over HTTP configuration, that would cut out every so often, whenever your school's proxy got bored of keeping your connection alive.

Thankfully, the theory is fairly simple. The *real* trouble will start when you find it doesn't quite work, and you have to try to figure out where the problem might be!!

**Edit:** By the way, it's helpful if you don't double-post.

---

### Post by tturrisi on 2006-10-13
The school blocks www access for a reason:
**While in school, be a student!**
- *Your Principal*

---

### Post by kidders on 2006-10-13
Good point!

---

