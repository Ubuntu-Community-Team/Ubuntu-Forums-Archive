---
title: "Join an ubuntu workstation to a specific Active directory container"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by xxsludgexx on 2007-08-23
I can do:
[B]net ads join -U [email]admin@domain.inte[/email]rnal
[/B]
that works just fine, but it puts the computer object in "Root\Computers" and that doesn't work with our layout.

I've seen several sites mention that you can do this:

[B]net ads join "Computers\BusinessUnit\Department\Servers" -U [email]admin@domain.inte[/email]rnal
[/B]

but I get Bad option errors.

Any idea how I can get a workstation to join a domain, and place it's workstation object in a container I specify? I already got krb and samba and winbind all setup.

---

### Post by xxsludgexx on 2007-08-29
bump for great justice

---

### Post by DigitalWarrior on 2008-03-06
I am having the same problem, and I too would like to bump this question "for great justice".

---

