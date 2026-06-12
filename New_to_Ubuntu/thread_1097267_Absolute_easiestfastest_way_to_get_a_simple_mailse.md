---
title: "Absolute easiest/fastest way to get a simple mailserver going for personal use"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by trillex on 2009-03-15
I've been scouring google the entire weekend to find a proper guide to get a mail server going for personal use, i.e. not just a server that can send and receive mails but also one that actually "hosts" the emails themselves (x@y.z) which can be used through a standard mail client like Thunderbird.

I really only need 1 domain going so every guide I find, that describes several domains just seems to be overkill and I just think there must be an easier way to get a simple, standard mailserver without any bells or whistles. 

Thanks in advance. :)

---

### Post by martrn on 2009-03-15
A absolutely easiest / fastest way to get a "simple" mailserver going, err lets think, you mean one that listens on ports 25 and relays any mail it receives to that to which it was addressed to routed via a few other STMP servers you have or something else ?

To get a mail srever for a domain, or multiple domains is the same insn't it ?

There is a guide called [http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/")  if you search google there is a book called (without a front cover) sendmail.  [http://www.google.co.uk/search?hl=en&q=sendmail%2C+th++Edition+%2B%22.pdf%22]("http://www.google.co.uk/search?hl=en&q=sendmail%2C+th++Edition+%2B%22.pdf%22").

---

### Post by mvalviar on 2009-03-16
```
sudo apt-get install postfix
```
Simple enough. Configure to fit.

---

### Post by hyper_ch on 2009-03-16
[http://www.howtoforge.com](http://www.howtoforge.com) --> many tutorialy simple to follow

---

### Post by trillex on 2009-03-16
I got it sorted out. I just had to read between the lines of the standard guide in ubuntu server. Thanks for the links, though.

---

