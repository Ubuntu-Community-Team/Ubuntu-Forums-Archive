---
title: "[SOLVED] Mail server from desktop - possible?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by djbushido on 2008-12-11
Is it at all possible to set up my own mail server from a desktop computer such that emails sent to me would be like to [email]djbushido@djbushido.com[/email] or something?
I doubt it, but it would be pretty neat

---

### Post by Kareeser on 2008-12-11
The functionality you're looking for can be accomplished, yes, but there is one problem:

Even if you set your server up to listen for mail going to "djbushido@djbushido.com", AND

Even if someone sent an e-mail to "djbushido@djbushido.com".

The outgoing mail server (i.e. GMail, Windows Live Mail) won't know there "djbushido.com" is, and may ultimately return the mail as undeliverable after querying multiple DNS servers.

What you need to do requires registering a domain name (djbushido.com), and setting up the registrar to forward all mail requests to your machine's public IP address, which will be listening for those requests. That costs money =P

We can help you with that, if you'd like :)

===

If, on the other hand, you want to spoof your "from" header with something different, that's a tad easier to accomplish. We can help you there too.

So. What would you like?

---

### Post by djbushido on 2008-12-11
actually, i would like both, as long as i don't have to pay for anything (registration with DNS). Again though, i doubt that that is possible.

---

### Post by albinootje on 2008-12-11
If you really don't want to pay anything at all for a domain-name, 
then you can try a free-of-charge service as provided by for example [http://www.dyndns.com/](http://www.dyndns.com/)

But having your own domain-name is nowadays pretty cheap. 
Here in Holland i've seen offers at good quality webhosting-providers to have your own domain-name for about 7 euros a year.

The "dynamic" free-of-charge domain-name providers usually offer you only sub-domain names or domain-names where they choose the name.

Apart from that running your email from your desktop is possible.
You make sure that port 25 gets port-forwarded from your ADSL-router or cable-modem, and you set up your mailserver properly.
However, if you don't have some mx fall-back for your emails elsewhere,
and you're gonna turn off your desktop every night, then you might get into slight email delivery problems or delays.

---

### Post by djbushido on 2008-12-11
I'm not sure after all if this is what I really want to do. I just don't want to get into something this complicated just yet. Anyway, thank you though for answering my question.

---

