---
title: "Apache2 not reachable from outside"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by BramuS on 2007-06-09
Hi everyone, i'm new to Ubuntu, i used to work with Gentoo but my whole kernel just collapsed :( I decided to try out Ubuntu cause i did read some nice things. 

I found on some wiki ubuntu page a tutorial to setup apache2 i just did follow it and set it up. I try to connect to it and it works just perfect also from other pc in lan i can connect to the page and see my new test page.

But now i asked some friends if they could reach it and they **can't**. I already did forward port 80 cause on Gentoo was also an webserver running and i did gave Ubuntu the same IP as the Gentoo box that was in the lan before.

Does anyone knows what the problem can be? some one said something about it is timing out? Hope some one will help me!

[http://81.204.121.38](http://81.204.121.38) = the page :)

---

### Post by BramuS on 2007-06-10
fixed 

Listen *:80 in the ports.conf file :)

---

