---
title: "New 6.10 Ubuntu install - Firefox not working"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by symmonrj on 2007-02-09
I have done a new install, and DNS is resolving, and I can ping to web site name, but Firefox not loading. (Tried a few sites - Yahoo loaded one small frame then stopped - nothing else appears to load). I can ping the web sites I am trying. Firefox is set to connect direct (no proxy). Is there a "firewall" function in standard install blocking? Firefox in MS Windows works fine.

---

### Post by ola on 2007-02-09
Hi! Could you try to install another web browser (Opera, Links..) and see if that works?

Your problem sounds very strange and I have no good idea at the moment.. Sorry..

---

### Post by grmbrand on 2007-02-09
I think I'm actually seeing the same problem. My Xubuntu-based laptop is sitting on my office LAN, and I have no trouble getting pages from web servers within the LAN. However, if I point my browser at external sites (Google or Yahoo, for instance), the browser doesn't seem to get any pages back.

Curiously, I can telnet to port 80 at google.com and ping it from the laptop. Traceroutes (using 'tracepath') to hosts outside of the LAN work as well.

This problem is very recent. Last week my laptop didn't have this problem. I suspect that after my last package updates my laptop start fumbling incoming HTTP traffic.

Any ideas?

---

### Post by grmbrand on 2007-02-09
Following up on my own post--I tried to get lynx through synaptic, but all of the http-based repositories aren't working. That answers one question--the problem is not firefox.

Very mysterious...

---

### Post by noslenac on 2007-02-11
I had all the same symptoms on a Pentium 3 running Edgy 6.10. I followed the directions on this page and it fix my problems. If it does not help, just edit the .conf file again and delete the added line and save. Hope this helps.

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by symmonrj on 2007-02-11
Thank you for you responses. While I am not able to test right now (It's my daughters PC 1000 miles away), I am thinking it is the IPV6 thing.

Again, thanks.

---

