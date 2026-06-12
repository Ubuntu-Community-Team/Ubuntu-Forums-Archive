---
title: "apt-get proxy"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by wwoollff on 2007-12-28
Hi.I have a small problem.A few weeks I struggled to get my apt-get to work via a proxy.(my browser was running smoothly).Finally it worked, but now I'm home, and here I don't have a proxy.So, I tried all the possibilities to make bash work without a proxy.I verified also the file /etc/bash.bashrc, and it doesn't contain any information about it.Btw, I'm running a Kubuntu Gutsy.

thx alot.

edit: wget works fine.Only apt-get uses the old proxy.So bash si not the problem, apt-get is.

---

### Post by tech9 on 2007-12-28
> **wwoollff said:**
> Hi.I have a small problem.A few weeks I struggled to get my apt-get to work via a proxy.(my browser was running smoothly).Finally it worked, but now I'm home, and here I don't have a proxy.So, I tried all the possibilities to make bash work without a proxy.I verified also the file /etc/bash.bashrc, and it doesn't contain any information about it.Btw, I'm running a Kubuntu Gutsy.

thx alot.

make sure that the direct connection option is selected under

System>Preference>Network Proxy

&

your network proxy settings in synaptic

---

