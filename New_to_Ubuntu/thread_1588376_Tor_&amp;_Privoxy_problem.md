---
title: "Tor &amp; Privoxy problem"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by 289531.EXE on 2010-10-04
The proxy server is refusing connections

Firefox is configured to use a proxy server that is refusing connections.

    *   Check the proxy settings to make sure that they are correct.

    *   Contact your network administrator to make sure the proxy server is
          working.

So, Tor was installed with Privoxy, it worked after the initial installation, then when I restarted my computer it gave me the message above.

Are there any simple step by step instructions on fixing this?

---

### Post by bodhi.zazen on 2010-10-04
My guess is you need to configure privoxy, change the listen line from "localhost:8118: to 127.0.0.1:8118"

See also :

[http://bodhizazen.net/Tutorials/tor/](http://bodhizazen.net/Tutorials/tor/)

---

