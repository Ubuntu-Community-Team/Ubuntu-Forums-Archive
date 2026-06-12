---
title: "how to reset iptables?"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by evilkastel on 2009-06-19
Hello all. I have been temering with iptables in order to get RO to work well, but in the preocess i got 4 false Ips, so, the original ip the game was connecting to is redirected to other, that second one to a third one, and that way about 6 times.

I want to now how to reset the default iptables policies, also iptables --flush does not seem to be working.

---

### Post by wojox on 2009-06-19
try

iptables -F

that will flush current rules.

---

