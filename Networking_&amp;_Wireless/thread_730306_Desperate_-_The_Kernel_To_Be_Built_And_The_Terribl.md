---
title: "Desperate - The Kernel To Be Built And The Terrible Drivers"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by webdreamer on 2008-03-20
The drivers are driving me insane! The modem is awful. It's an IceData500 which is something that doesn't seem to exist outside of Portugal; however the Bewan modems are similar in all ways, so installing both is equivalent. The problem is the Unicorn PCI Card, whose trademark is to be cheap, but not so much to be practical for linux users. I've got around this a long, long, long time, and I got to this: I have the driver for Unicorn PCI, but when I use the makefile a lot of errors come out. First it was because some folders weren't there at all, so I got another version that had all the files. But the problem remains.
I [then found a blog]("http://blog.moria.org.uk/2005/06/") stating that "even getting the driver compiled is a nightmare without your own kernel source tree to hand", which, well... it's basically what I'm experiencing.

So what is building the kernel?
How do I set
" Enable "Asynchronus Transfer Mode (ATM)", "Classical IP over ATM", "PPP (point to point protocol) support", "PPP over ATM", and "ATM over TCP" (and don't forget iptables, NAT, and everything else you will need to actually use the connection). "
as said on the blog?

I'm desperate. I need some help, some good help, asap, PLEASE!...
Oh and don't say go and buy a decent modem, or a proper router, for if that was a choice, I wouldn't post this thread. Thanks to everybody in advance.

---

### Post by dmizer on 2008-03-20
to install the sourcecode for the linux kernel:
```
sudo aptitude install linux-source
```
you'll probably also need the source code building tools (if you don't already have them):
```
sudo aptitude install build-essential
```

you may also need to install the linux-headers
```
sudo aptitude install linux-headers-generic
```
beyond that, i'm afraid i won't be much help.

---

### Post by www.rzr.online.fr on 2008-07-10
> **webdreamer said:**
> The drivers are driving me insane! 

same for me , but I managed to get it working on dapper :
[http://rzr.online.fr/q/unicorn](http://rzr.online.fr/q/unicorn)

good luck

---

