---
title: "Firewall"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by gerowen on 2006-10-28
I've got a question.  I'm new to Ubuntu, but does 6.10 come with a firewall by default?  I can't seem to find any settings for one so I'm assuming not, but I have my printer and a folder shared as Windows shares and my Windows based laptop can't access them.  Is there a firewall that I just don't know about?

---

### Post by aoanla on 2006-10-28
Like most linux distributions, Ubuntu has control over port access (which is basically what a simple firewall does) via iptables.

I don't see that it should have closed ports to outbound traffic, though... (ah, I see you're having problems from outside - yes, it's possible the ports are closed. There's a graphical firewall configuration tool called fireflier that you might want to use, if you're not used to configuring iptables.)

---

### Post by madmetal on 2006-10-28
i think shamba will help you make printer and folders common with windows..

---

### Post by gerowen on 2006-10-28
Ok, I've installed the Firestarter UI frontend, which is pretty handy, and I found a walkthrough for editing samba users.

---

