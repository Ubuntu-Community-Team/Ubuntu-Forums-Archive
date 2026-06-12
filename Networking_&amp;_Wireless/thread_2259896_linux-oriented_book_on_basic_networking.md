---
title: "linux-oriented book on basic networking?"
date: 2015-01-07
forum: Networking &amp; Wireless
---

### Post by haplorrhine on 2015-01-07
I only have a very basic understanding of things such as ARP requests, MAC addresses, and protocols.  I neither understand programming nor computing, although both sounds intersting and I may learn the former when it suits me.
Any recommendations of books that would give me a foundation in networking and security while having a bent toward linux users?  A bland textbook is fine, but I'll probably only read a few hundred pages.

---

### Post by TheFu on 2015-01-08
Do you podcast?
Security Now! episode 25 - 35 is a series on "how the internet works". [https://www.grc.com/sn/past/2006.htm](https://www.grc.com/sn/past/2006.htm)
Strangely, the audio was enough to solidify existing knowledge and fill in missing knowledge.  Excellent primer.  I could see it in my mind's eye based purely on the audio.

---

### Post by haplorrhine on 2015-01-09
Thanks, but I really prefer a book.

---

### Post by TheFu on 2015-01-09
> **haplorrhine said:**
> Thanks, but I really prefer a book.

Understand completely.

All the network folks I know neared as part of their CCNA training. Books for that are everywhere. IP networking is OS agnostic, so the basic texts are not UNIX/Linux specific.  The [Linux Documentation Project]("http://www.tldp.org/LDP/nag2/") put out information in HTML which can be printed, if you like.

The amazon reviews for [this book]("http://www.amazon.com/Networking-Beginners-Guide-Sixth-Edition/dp/0071812245") seem good. There's a *Networking for Dummies* book in the related products section.

Networking is like an onion with thousands of layers. Nobody understands them all.  Gaining enough knowledge to setup a home network that runs well isn't that hard.  If you want to setup a small business, then training is necessary, since network architecture is the backbone of computer security. It is the first line of defense.

---

### Post by SeijiSensei on 2015-01-09
My favorite when I began learning this stuff was Craig Hunt's [TCP/IP Network Administration](http://shop.oreilly.com/product/9780596002978.do).  This book looks a bit dated now, but none of the fundamental features of TCP/IP have changed in decades.

---

### Post by slickymaster on 2015-01-09
It's from 2002, but the basic principles still apply: [http://www.openna.com/pdfs/Securing-Optimizing-Linux-The-Hacking-Solution-v3.0.pdf](http://www.openna.com/pdfs/Securing-Optimizing-Linux-The-Hacking-Solution-v3.0.pdf)

---

### Post by haplorrhine on 2015-01-13
> **slickymaster said:**
> It's from 2002, but the basic principles still apply: [http://www.openna.com/pdfs/Securing-Optimizing-Linux-The-Hacking-Solution-v3.0.pdf](http://www.openna.com/pdfs/Securing-Optimizing-Linux-The-Hacking-Solution-v3.0.pdf)

That's perfect!  I'll see what I can get out of it before posting again.

---

### Post by haplorrhine on 2015-02-23
I wouldn't have printed pages 147-189 if I had known.  Should I even bother with all those kernel configuration options, considering that it's for 2002 Red Hat?

/usr/src/linux/config isn't even a file in Ubuntu 14.04

---

### Post by SeijiSensei on 2015-02-23
Just scanning the chapter titles of that PDF document tells me there a lot of pretty irrelevant stuff in there.  No, you shouldn't ever need to compile a kernel or anything else really these days.  And RedHat/CentOS does things differently from Debian/Ubuntu so files may not be in the same locations on both systems.  For instance, the configuration for the Apache webserver on RH-flavored systems resides in /etc/httpd; on Ubuntu it's in /etc/apache2, and the configuration files are structured very differently.

---

### Post by haplorrhine on 2015-02-23
I'm not necessarily sticking with Ubuntu anyway.  I realized what you're saying at the outset.  If it's saying something that doesn't describe my Ubuntu system, I more or less just leave it and move on.  It has clued me in on things I didn't know about before such as chattr, shredding, tripwire, .bash_history, .rhosts files, SETUID and SETGID bits, mounting directories on partitions, mount flags, PAM, why you can't always trust GUIs, and the list goes on.  In contrast, I ignored all the stuff on RPM package installation.

It's so old that it doesn't mention AppArmor, nor browser addons like NoScript, but I was already aware of such things from the [Ubuntu Basic Security]("https://wiki.ubuntu.com/BasicSecurity") guide.  In fact, I can already make my own custom changes to an AppArmor file thanks to opensuse.org ["Chapter 19. Profile Components and Syntax"]("https://doc.opensuse.org/documentation/html/openSUSE_122/opensuse-security/cha.apparmor.profiles.html"), most of which does apply in Ubuntu.

I still have to get to all of the TCP/IP routing stuff though!  Up to now, I've relied on encrpytion and MAC filtering.  I plan to install Kali Linux for penetration testing.

---

### Post by him610 on 2015-02-23
Linux Networking Cookbook by Carla Schroeder
O'Reilly
ISBN-13: 978-0596-10248-7
One can order it from Amazon.

---

