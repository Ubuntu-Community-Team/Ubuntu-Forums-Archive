---
title: "Net View"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by maxman_449 on 2008-11-10
Hi Guys,

Just a quick one from a new Linux user, how do you do a net view in Ubuntu. I need to see which machines are logged onto a Window network. Cheers :guitar:

---

### Post by kdcoetzee on 2008-11-10
You can install nmap

```

sudo apt-get install nmap

```

then just...

```

nmap -sP range.0/24

```

read the man page aswell

```

man nmap

```

---

### Post by kdcoetzee on 2008-11-10
> **maxman_449 said:**
> Hi Guys,

Just a quick one from a new Linux user, how do you do a net view in Ubuntu. I need to see which machines are logged onto a Window network. Cheers :guitar:

But I don't know about checking the Window network.

there may be a samba command that does that.

---

### Post by ilogak on 2010-10-14
You can try this one 
smbtree

---

