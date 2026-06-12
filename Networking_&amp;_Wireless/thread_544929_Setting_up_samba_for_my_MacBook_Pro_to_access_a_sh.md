---
title: "Setting up samba for my MacBook Pro to access a share"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by thorlin on 2007-09-06
I have a MacBook Pro and Ubuntu Feisty Fawn.  I have a share on Ubuntu that I'm trying to access from my MBP via Samba.  I can see the machine and see the share, but when I attempt to authenticate I get a bad username/password message.

I've read that I need to setup a samba user so i'm doing the following.

I'm attempting to use the command:

sudo smbpasswd -a username

but i get a message

Failed to modify password entry for user share

It doesn't matter what I do for a login or password it always fails.

Help.

---

### Post by lisati on 2007-09-08
You might have to do the following:
```

sudo apt-get install ssh

```

---

