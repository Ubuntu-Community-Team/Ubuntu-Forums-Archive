---
title: "IP tables"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by frank002 on 2009-01-26
I thought ip tables was turned on by default, however, I just read that it isn't. If it isnt, how do you turn it on? Thanks.

---

### Post by BlakeM on 2009-01-26
Bit of a noob as well. But to my understanding:

[LIST=1]
[*]iptables is installed by default, but not enabled.
[*]The reason behind this is because a virgin installation of Ubuntu has no services listening.
[*]To turn it on, I'm pretty sure it's:
> sudo ufw enable
[/LIST]

As far as I know, ufw is a simplified interface to iptables that makes it easier for new people to learn.

See also: [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

---

### Post by frank002 on 2009-01-26
Thanks

---

