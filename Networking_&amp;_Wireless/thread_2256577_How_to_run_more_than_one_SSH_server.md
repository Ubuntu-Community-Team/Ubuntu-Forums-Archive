---
title: "How to run more than one SSH server"
date: 2014-12-13
forum: Networking &amp; Wireless
---

### Post by dani-valverde on 2014-12-13
Hello,
I have a NAS server and a Hummingboard, both of them set up as SSH servers. I'd like to be able to log into both from outside my LAN using SSH, so using port 22. Then, how should I forward the ports? I use to run only just the NAS, so I don't know how to make the forwarding so I can use the Humingboard as well.
Thanks,

Dani

---

### Post by ian-weisser on 2014-12-13
Example:
111.111.111.111:3333 --> 192.168.1.5:22 (NAS)   Forward port 3333 to NAS, port 22
111.111.111.111:4444 --> 192.168.1.8:22 (Hummingboard)  Forward port 4444 to Hummingboard, port 22

When you want to login from outside:
ssh me@mydomain -p 3333  (NAS)

Reminder: All SSH servers exposed to the internet, including port-fowarded, should use keys instead of passwords.

---

### Post by dani-valverde on 2014-12-14
Thanks! It works like a charm.
Cheers!

Dani

---

