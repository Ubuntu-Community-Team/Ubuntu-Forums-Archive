---
title: "Dyndns with Netgear Router"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by tonycm1 on 2010-12-26
I've set up an account with Dyndns, set up dynamic DNS on my Netgear Router, and installed LAMP on Ubuntu 10.04.

Unfortunately, when I enter my dyndns address (ie. [http://insertnamehere.dyndns.org](http://insertnamehere.dyndns.org)), I can't seem to get it to load my test html file... instead, it loads my Router Configuration Page (ie. what you normally get when you type 192.168.1.1).

I've tried adding port forwarding on the router to forward port 80 to 192.168.1.8 (my computer) but it still only shows up with the router configuration page.

If I try [http://localhost](http://localhost) or [http://192.168.1.8](http://192.168.1.8), then the site loads perfectly though....

ideas? I'm just starting to learn LAMP and would appreciate a nudge in the right direction :)

---

### Post by sandyd on 2010-12-26
> **tonycm1 said:**
> I've set up an account with Dyndns, set up dynamic DNS on my Netgear Router, and installed LAMP on Ubuntu 10.04.

Unfortunately, when I enter my dyndns address (ie. [http://insertnamehere.dyndns.org](http://insertnamehere.dyndns.org)), I can't seem to get it to load my test html file... instead, it loads my Router Configuration Page (ie. what you normally get when you type 192.168.1.1).

I've tried adding port forwarding on the router to forward port 80 to 192.168.1.8 (my computer) but it still only shows up with the router configuration page.

If I try [http://localhost](http://localhost) or [http://192.168.1.8](http://192.168.1.8), then the site loads perfectly though....

ideas? I'm just starting to learn LAMP and would appreciate a nudge in the right direction :)
whats the router model?

---

### Post by tonycm1 on 2010-12-26
> **sandyd said:**
> whats the router model?

Netgear WPN824v3.

---

### Post by sandyd on 2010-12-26
> **tonycm1 said:**
> Netgear WPN824v3.
did you
a) disable remote access to router
b) update firmware

If that still doesn't work, then your router is suffering from
[http://www.dyndns.com/support/kb/loopback_connections.html](http://www.dyndns.com/support/kb/loopback_connections.html)

its been discussed for your particular router on the DynDNS forums, I just want make sure the issue still exists.

---

### Post by tonycm1 on 2010-12-26
> **sandyd said:**
> did you
a) disable remote access to router
b) update firmware

If that still doesn't work, then your router is suffering from
[http://www.dyndns.com/support/kb/loopback_connections.html](http://www.dyndns.com/support/kb/loopback_connections.html)

its been discussed for your particular router on the DynDNS forums, I just want make sure the issue still exists.

Yep! Firmware was updated last week to the newest.

And I originally though the problem was remote management of the router but it's disabled in the router configuration... 

Also tested port 80 and it's open! :S

---

### Post by bodhi.zazen on 2010-12-26
> **tonycm1 said:**
> I've set up an account with Dyndns, set up dynamic DNS on my Netgear Router, and installed LAMP on Ubuntu 10.04.

Unfortunately, when I enter my dyndns address (ie. [http://insertnamehere.dyndns.org](http://insertnamehere.dyndns.org)), I can't seem to get it to load my test html file... instead, it loads my Router Configuration Page (ie. what you normally get when you type 192.168.1.1).

I've tried adding port forwarding on the router to forward port 80 to 192.168.1.8 (my computer) but it still only shows up with the router configuration page.

If I try [http://localhost](http://localhost) or [http://192.168.1.8](http://192.168.1.8), then the site loads perfectly though....

ideas? I'm just starting to learn LAMP and would appreciate a nudge in the right direction :)

It can take up to 24 hours for your domain name to propagate.

Can you see your web page when you enter your public IP address ?

Also, it is a public server, you registered a domain name, so there is no need to post:

secret.domain.name.dyndns

Just post your host name and public ip address, lol.

If you want it to be "private", firewall it after it is debugged.

---

### Post by tonycm1 on 2010-12-26
I just tried accessing my public ip through an online proxy ([https://vtunnel.com](https://vtunnel.com)) and the site loaded!

Odd that when I type it in my browser, I get the router configuration page, but if I type it on a proxy, it loads :S

This can be a pain when it comes to testing if I have to load the site through a proxy all the time... why would the router config page load up if remote management is disabled?

---

### Post by bodhi.zazen on 2010-12-27
> **tonycm1 said:**
> I just tried accessing my public ip through an online proxy ([https://vtunnel.com](https://vtunnel.com)) and the site loaded!

Odd that when I type it in my browser, I get the router configuration page, but if I type it on a proxy, it loads :S

This can be a pain when it comes to testing if I have to load the site through a proxy all the time... why would the router config page load up if remote management is disabled?

Well this is happening because it takes up to 24 hours for your domain name to propagate through DNS.

Nothing to do now but wait, post back it is unresolved after 24 hours.

---

