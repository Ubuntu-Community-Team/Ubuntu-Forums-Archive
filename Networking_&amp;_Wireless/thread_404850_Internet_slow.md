---
title: "Internet slow"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by Mr Greencastle on 2007-04-09
(Ubuntu Edgy 6.10, broadband)

I am new to Ubuntu, I had Vista but I didn't like it. The problem is my download speed is really slow when using synaptic, apt-get, aptitude or the update manager, usually between 12-40 kB/s. I recently did a fresh install and updating/synaptic etc. is getting annoying.


I use firefox my download speed is between 300-600 kB/s (tried on many websites), I've disabled ipv6, but don't think thats the problem, I am running XP on dual boot and download is fine aswell. (websites load fast)

It's a wired connection.

Can anyone give me easy instructions to help speed this process up?

Thanks in advance

---

### Post by rolando on 2007-04-09
You say its  only when using Syanptic, apt-get etc, what repositories are you using?  Are you using the ones nearest to you?

Here are mine, and as Im in the uk, great.

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) edgy main restricted

These were put in by default, not by me.

Not sure where you are, but see if the repositories you are using are close to you.

Its all I can think of.

---

### Post by stchman on 2007-04-11
> **Mr Greencastle said:**
> (Ubuntu Edgy 6.10, broadband)

I am new to Ubuntu, I had Vista but I didn't like it. The problem is my download speed is really slow when using synaptic, apt-get, aptitude or the update manager, usually between 12-40 kB/s. I recently did a fresh install and updating/synaptic etc. is getting annoying.


I use firefox my download speed is between 300-600 kB/s (tried on many websites), I've disabled ipv6, but don't think thats the problem, I am running XP on dual boot and download is fine aswell. (websites load fast)

It's a wired connection.

Can anyone give me easy instructions to help speed this process up?

Thanks in advance

Try using OpenDNS.  My Charter internet was really slow and using OpenDNS values my internet was then blazing fast.

[http://www.stchman.com/openDNS.html](http://www.stchman.com/openDNS.html)

Trust me it will help.

Also make sure your hosts and hostname file are one liners.

---

