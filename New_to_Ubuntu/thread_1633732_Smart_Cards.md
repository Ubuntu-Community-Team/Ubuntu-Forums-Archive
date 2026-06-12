---
title: "Smart Cards"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by ironic.demise on 2010-11-29
I have a smart card reader.
This is a pretty general question and it comes mainly from curiosity.

What smart cards do I need?
How can I implement them in Ubuntu for login (or other interesting things)?

The smart card reader is part of a DELL keyboard (RT7D60)

---

### Post by bodhi.zazen on 2010-11-29
> **ironic.demise said:**
> I have a smart card reader.
This is a pretty general question and it comes mainly from curiosity.

What smart cards do I need?
How can I implement them in Ubuntu for login (or other interesting things)?

The smart card reader is part of a DELL keyboard (RT7D60)

Any card that fits your reader should work with Ubuntu (linux).

---

### Post by ironic.demise on 2010-11-30
Any smartcard, I see a few on Ebay.
What about software?

---

### Post by bodhi.zazen on 2010-11-30
> **ironic.demise said:**
> What about software?

Should be build into the kernel, in other works it should "just work".

If you would like the technical details, see:

[http://www.faqs.org/docs/Linux-HOWTO/Smart-Card-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Smart-Card-HOWTO.html)

---

### Post by eriktheblu on 2010-11-30
CoolKey is what I use. I'm not sure if there are any others. Your reader might not be accessible in Ubuntu; I've had much better luck with SCM Microsystems than Dell devices.

I've not heard of anyone using it for login purposes (guess I haven't been reading up on it, details [here]("https://help.ubuntu.com/community/CommonAccessCard")). I use the one I was issued for web authentication on work related sites.

If you're trying to set it up for personal use, the other problem I see the card authoring. Not only am I unaware of any Linux software for this purpose, but your built in card reader is not capable of it.

---

### Post by ironic.demise on 2010-11-30
I knew I would need a smart-card reader, and a lot of cheap smart card reader-writers are available but it was mainly just a musing of mine, thanks for the links.

Edit, in one of the links there *is* a smart card writer.

---

### Post by martinpaljak on 2010-12-29
> **bodhi.zazen said:**
> Any card that fits your reader should work with Ubuntu (linux).
Contrary to your understanding, all smart cards share the same common size, but not all smart cards have the same functionality or work the same way on Linux.

---

### Post by martinpaljak on 2010-12-29
> **ironic.demise said:**
> I have a smart card reader.
This is a pretty general question and it comes mainly from curiosity.

What smart cards do I need?
How can I implement them in Ubuntu for login (or other interesting things)?

The smart card reader is part of a DELL keyboard (RT7D60)


Have a look at [http://www.opensc-project.org/opensc](http://www.opensc-project.org/opensc)

---

