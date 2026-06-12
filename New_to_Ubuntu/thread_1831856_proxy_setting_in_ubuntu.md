---
title: "proxy setting in ubuntu"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by amitpokhrel on 2011-08-23
HI I am using Ubuntu 10.10 and the internet I use has a proxy setting due to which I am not able to update my system or use software centre. Can anyone tell what can I do to make it work. (The proxy setting requires username and password authencation)

---

### Post by llamabr on 2011-08-23
maybe tell us more about the proxy server, how it works, and what you want to do.  Do you type a password for everything you do on the net?  apt-get should not be any different.

---

### Post by amitpokhrel on 2011-08-23
the proxy setting I use while browsing internet is:
ip- 172.16.1.1
port- 3128

I have to give my username and password when i start a session in any browser.
I am able to browse internet in Ubuntu but i am not able to update or use software center or synaptic

---

### Post by bodhi.zazen on 2011-08-24
> **amitpokhrel said:**
> the proxy setting I use while browsing internet is:
ip- 172.16.1.1
port- 3128

I have to give my username and password when i start a session in any browser.
I am able to browse internet in Ubuntu but i am not able to update or use software center or synaptic

See: [https://help.ubuntu.com/community/AptGet/Howto#Setting%20up%20apt-get%20to%20use%20a%20http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting%20up%20apt-get%20to%20use%20a%20http-proxy)

[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

---

### Post by Wim Sturkenboom on 2011-08-24
If you want to use GUI tools, you can configure synaptic (somewhere under preferences); this will take care of the update manager as well (and possibly the software center, not sure).

And bodhi.zazen's links covered the command line (for e.g. apt-get).

---

