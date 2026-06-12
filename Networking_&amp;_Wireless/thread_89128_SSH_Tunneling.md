---
title: "SSH Tunneling"
date: 2005-11-11
forum: Networking &amp; Wireless
---

### Post by etc on 2005-11-11
Basically I'm going to be using my laptop on other networks than my own such as public wifi areas and airports(for example, I'd like to do something like [this]("http://www.linquist.net/geek/proxy/") except that I'm using linux and I want to use squid too).  I set up one of my desktops running Breezy, SSH, and squid.
What I'd like to know is how I could use SSH to tunnel all my traffic (web, email, etc) through the machine.  I have no idea how to secure SSH either.
I googled around but most of the guides were a little to confusing and not straightforward.
So what I'd like to know is what I'd have to do to secure SSH if I'm going to access it remotely out of my network.  Secondly, I'd like to know how to basically setup SSH tunneling and being able to use my squid cache with it (if thats possible).
Thanks

---

### Post by mgor on 2005-11-12
take a look at IPSec. found this guide[1], seems pretty straightforward.

[1] [http://www.smallworks.com/~jim/SISO/www.cybcon.com/~coert/linux/siso/ipsec.html](http://www.smallworks.com/~jim/SISO/www.cybcon.com/~coert/linux/siso/ipsec.html)

---

