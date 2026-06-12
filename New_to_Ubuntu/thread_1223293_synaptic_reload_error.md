---
title: "synaptic reload error"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by ws.venkateswaran on 2009-07-26
i added the following sources

[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)
[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)

to my third party software sources. when i reload synaptic i get the following error messages

"*W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE*"

whats the problem..

---

### Post by QIII on 2009-07-26
Good instructions here.
 
 Look at the "Read about installing"
 
 [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by ws.venkateswaran on 2009-07-26
thanks..... it worked.... do those 2 lines automatically load updates of all the applications so that i can install the latest from synaptic or do i have to keeping changing those 2 lines periodically

---

### Post by Bucky Ball on 2009-07-26
> **ws.venkateswaran said:**
> 

"*W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the **public key is not available**: NO_PUBKEY EF4186FE247510BE*"

whats the problem..

That was your problem. Whatever you have done has installed the public key also. When adding a repo to your sources list you always need one. :)

---

