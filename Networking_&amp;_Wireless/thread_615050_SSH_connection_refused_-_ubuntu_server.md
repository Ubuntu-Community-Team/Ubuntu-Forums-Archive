---
title: "SSH connection refused - ubuntu server"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by Yob on 2007-11-16
hi,

So, i figured i'd go an make myself a neat ubuntu server for storing my media files on, my back ups etc. (Had an old computer in the basement).

I went ahead and installed Ubuntu Server version and opted for LAMP and OpenSSH server.

When the installation process was done i tried to SSH to the machine from my regular ubuntu desktop and got:

```
ssh: connect to host 192.168.1.3 port 22: Connection refused
```

(I have a Netgear router and the above IP is where the server is).

I've been reading the forum for a while and tried some of the suggestions (forwarded the router on port 22, reinstalled the openssh-server from the repo) but i'm still getting the same error mess.

I'm not sure this is relevant, but my server is connected to the router via wire - the desktop wireless.

I've tried installing openssh-server on my desktop and access it from a laptop (via wireless) - works like a charm.

What am I missing?

---

### Post by dasunst3r on 2007-11-16
Did you type in your password incorrectly a few too many times?  DreamHost did that to me one time, and I had to get my host off the bad list.

---

### Post by Yob on 2007-11-16
Hi,

Nope, got this error the first time i tried to connect. I don't even get to the password part - it simply will not allow me to connect.

---

