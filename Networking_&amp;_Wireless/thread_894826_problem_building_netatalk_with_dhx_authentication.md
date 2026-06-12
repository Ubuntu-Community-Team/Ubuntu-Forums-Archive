---
title: "problem building netatalk with dhx authentication"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by stairwayoflight on 2008-08-19
Hi,

I am trying to build netatalk on ubuntu-server hardy because the binary only allows clear-text password authentication, which is disabled in Leopard by default.

I successfully built it before, but now on the 'dpkg-buildpackage' step I seem to be getting different output; I can't find the configuration summary at the tail of the output (which confirms if the dhx module was built) and I get a ton of lines giving warnings about "x shouldn't link to y because it doesn't use any of its symbols."

Any ideas for me?

PS -- I am following the howto here:
[http://blog.our-files.com/?p=5](http://blog.our-files.com/?p=5)

---

### Post by stairwayoflight on 2008-08-19
Ehh, for some reason I couldn't get it to build on my server, but it built and tested ok on the lappy so I copied the deb to the server and installed that. Problem solved.. sort of!

---

