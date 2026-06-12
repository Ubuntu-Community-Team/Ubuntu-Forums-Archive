---
title: "Compiling &amp; Postfix"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by Merrigan on 2007-10-15
Hi There,

I had a discussion this weekend with a fellow systems administrator that hates Ubuntu server for one reason, and that is that he is unable to compile anything on Ubuntu server? I have not yet tried this as for me it wasn't neccesary. How true is this?

Also, what would be the procedure to get postfis with ssl enabled n ubuntu server? This is apparently what he tried to compile but don't think that it would be neccesary...

Thanx a lot!

 -- Merrigan

---

### Post by kidders on 2007-10-18
> **Merrigan said:**
> I had a discussion this weekend with a fellow systems administrator that hates Ubuntu server for one reason, and that is that he is unable to compile anything on Ubuntu server? I have not yet tried this as for me it wasn't neccesary. How true is this?This is the *opposite* of the truth hehe. Having said that, compiling software one's self for use on a production server is not recommended on any distro, unless you know what you're doing.

> **Merrigan said:**
> Also, what would be the procedure to get postfis with ssl enabled n ubuntu server?On ubuntu, simply "apt-get install" it. You don't have to do anything special to make Postfix SSL-capable.

---

### Post by tkharris on 2007-10-18
On that same note, I would use Debian Stable ( etch ) for a production mail server over Ubuntu.

---

