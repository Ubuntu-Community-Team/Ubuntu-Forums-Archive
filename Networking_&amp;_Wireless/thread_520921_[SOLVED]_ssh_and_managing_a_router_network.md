---
title: "[SOLVED] ssh and managing a router network"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by rbprogrammer on 2007-08-08
i have a small home network set up (like most of us) that i can ssh into when i am away at school.  the network is always on b/c there is always someone at home on the internet.  i then have a small server that i have set up.

my question is how to i get access to my router and do tasks within it?  i can ssh into the network, so immediately i thought of one of those text based web browsers.  so i tried lynx, links, links2, and elinks.  but none seem to work.

[LIST]
[*]lynx - i cant even connect to the router
[*]links - i can get to the routers home page, but cant log in
[*]links2 and elinks - i can log in, but the html links on the side never show up, so i can do any administering
[/LIST]

i was wondering if anyone knew of a better text based web browser, or maybe even a different way of accessing my router from outside the network??

---

### Post by noob12 on 2007-08-09
You can use a regular browser and an ssh tunnel.  All the comforts of home.  Here's the unix version.  If you use putty, it's possible but awkward to provide instructions.

This assumes you haven't disabled this functionality (AllowTcpForwarding) in your sshd_config.  It is on by default.

Let's say your home router is on your private net at 192.168.1.1, and your home sshd server is on mydesktop.myhome.org.  When you ssh into your home machine use the command
```

ssh -L8888:192.168.1.1:80  mydesktop.myhome.org

```

Then open a web browser, e.g. firefox, and enter the url  **[http://localhost:8888](http://localhost:8888)**.  This should reach your router.

**NOTE: You have to substitute the actual values of your router's internal ip address and your home's public hostname or ip.**

---

### Post by rbprogrammer on 2007-08-09
wow, that was way better than using a text based web browser..

thanks so much :guitar: ...

---

