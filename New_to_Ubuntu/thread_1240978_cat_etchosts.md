---
title: "cat /etc/hosts"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by colau on 2009-08-15
cat /etc/hosts
```


127.0.0.1	ubuntu-desktop	localhost.localdomain	localhost

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
Can I delete these lines below?Are they necessary?
```

::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
And is there any problem if I delete these(bold+red)?
```

127.0.0.1	ubuntu-desktop	**[COLOR="DarkRed"]localhost.localdomain	localhost[/COLOR]**

```

---

### Post by Bachstelze on 2009-08-15
They're here for a reson, so deleting thme would be a bad idea. Why would you want to do that anyway?

---

### Post by colau on 2009-08-15
> **HymnToLife said:**
> They're here for a reson, so deleting thme would be a bad idea. Why would you want to do that anyway?
What's the reason?
It's ip version 4 with my ip address.

---

### Post by Bachstelze on 2009-08-15
> **colau said:**
> What's the reason?
It's ip version 4 with my ip address.

And exactly how was I supposed to know? Anyway, yes, you can delete it then, but I really don't see the point.

---

### Post by shae on 2009-08-15
> **colau said:**
> cat /etc/hosts
```


127.0.0.1	ubuntu-desktop	localhost.localdomain	localhost

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
Can I delete these lines below?Are they necessary?
```

::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
And is there any problem if I delete these(bold+red)?
```

127.0.0.1	ubuntu-desktop	**[COLOR="DarkRed"]localhost.localdomain	localhost[/COLOR]**

```

Generally speaking You can remove the stuff for IP6 (Note, you also have to make sure the ip6 module does not load), but DO NOT remove localhost.localdomain or localhost.  Doing so can screw stuff up.

---

### Post by credobyte on 2009-08-15
You *can* delete them, however, I wouldn't do it without a backup copy.

---

