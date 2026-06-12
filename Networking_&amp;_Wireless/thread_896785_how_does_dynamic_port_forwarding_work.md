---
title: "how does dynamic port forwarding work?"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by geekpie on 2008-08-21
Hi
I've set up dynamic port forwarding through the ssh server on our ubuntu box (using putty).   

It works, but I don't understand how:  as far as the remote website is concerned, the request comes from the box with the ssh server (the ubuntu box).  How then does the ubuntu box know, when it receives the HTTP response, that it should forward that response through the tunnel?  Does it "remember" that the port it used to make the request is associated with the ssh tunnel?

---

### Post by nixscripter on 2008-08-22
In a word, yes.

When the ssh box makes an outgoing connection in proxy, it remembers the port number it used. When data comes in on that port, it forwards it to the original box.

---

### Post by geekpie on 2008-08-22
thanks.

---

