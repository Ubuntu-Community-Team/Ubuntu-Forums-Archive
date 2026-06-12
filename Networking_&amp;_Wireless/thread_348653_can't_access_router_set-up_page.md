---
title: "can't access router set-up page"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by moon_dog on 2007-01-29
i can't seem to access the router page through my browser.  when i enter the router's address (192.168.100.100), i get a blank page with the message Busy on it.  i tried using telnet to talk to the router and this is what came out:

```
mo@mo-laptop:~$ telnet 192.168.100.100 80
Trying 192.168.100.100...
Connected to 192.168.100.100.
Escape character is '^]'.
HTTP/1.0 503 R
Content-Type: text/html

BusyConnection closed by foreign host.

```

is there a way to set up port forwarding through the command line?  that's all i really need to do.

---

### Post by coder928 on 2007-01-30
have you tried to ping the router via the command line to make sure its not a network issue?

---

### Post by moon_dog on 2007-01-30
yep, i can ping the router.  i can also access the net.  it's only the router's set up page that i can't access.

---

### Post by tturrisi on 2007-01-30
What brand-model router?

You must have changed the router ip address to 192.168.100.100, correct?
I have never seen a router use that ip address, most default router addresses are:
192.168.1.1 or 192.168.0.1.  Realize that 192.168.100.100 is not the same as 192.168.1.1.

As for telnet to router, I believe the router must have remote management enabled, which is usually set to disabled by default.

---

