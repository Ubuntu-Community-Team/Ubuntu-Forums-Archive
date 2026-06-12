---
title: "slow system boot with LDAP authentication"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by niobos on 2007-11-15
Hi,

I'm trying to get (K)ubuntu to work in my SOHO network. It stores all user accounts in an central LDAP database.

I was surprised that ubuntu came with a nice set of packages/scripts to automate this. It even works! Mostly....

When LDAP authentication is activated, the system is extremely slow to boot. Everything works and starts, but it takes AGES. Especially dbus and hald take a long time.

I'm not sure about this, but my guess is that the network connection isn't yet up when dbus starts. Therefor, every username lookup will have to wait for an LDAP timeout.

What can I do to get around this? If you need any config-files, just ask!

---

### Post by kesomir on 2007-11-18
try changing

```
bind_policy=hard
```

to

```
bind_policy=soft
```

in /etc/ldap.conf

---

### Post by niobos on 2007-11-18
Thank you, works like a charm!

---

