---
title: "Message &quot;Same is available in software channel&quot;???"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by brawd on 2009-06-26
Hi All,

I've spent this evening trying to install Ubuntu on a pendrive after getting much needed advice on the forum earlier and followed the links.
I did all the PPA thing and security codes and finally downloaded the package.

When I told it to install it came up with the message I wrote in the header.
I assume it is a cautionary message - so I treated it with caution and didn't run it.

So then I looked in my software channels (?) which I assume are Applications and System and found nothing like it.

So what do I need to do? Are there dark corners of my computer I have to rummage through to find some software or do I run the downloaded program.

Advice would be gratefully received.

regards,

brawd

---

### Post by WRDN on 2009-06-26
The message means the package is currently available somewhere on one or more servers listed in /etc/apt/sources.list

It is recommended you install it from here, as you can guarantee the package is safe (i.e. it contains no spyware etc), and you will automatically get updates for it when available.

To try and find the package, look in the Synaptic Package Manager (System > Administration > Synaptic Package Manager, or run "gksudo synaptic").

---

### Post by snakeman21 on 2009-06-26
Basically what it means is that the same package is available in the repositories.  You can find it via synaptic or the add/remove programs utility.  It warns you because downloading from the repos is more reliable.  You know you will get a complete package, and not a corrupted file.

---

