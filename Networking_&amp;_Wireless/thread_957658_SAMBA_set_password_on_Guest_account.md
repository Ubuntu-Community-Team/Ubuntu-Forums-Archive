---
title: "SAMBA set password on Guest account"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by hammad1337 on 2008-10-24
How can I put a password on the Guest account in Samba (the account used for anonymous access). I don't want to create a new passworded user account, but rather, to put a password on the Guest account. Can anyone help me with that?


Thanks.

---

### Post by Iowan on 2008-10-24
I'm probably mistaken again, but the guest "account" is not an account - it is the "lack of an account"... so probably also has "lack of a password"... but I'll keep watching to see if a better answer comes along.

---

### Post by hammad1337 on 2008-10-24
But, can't we somehow force creation of an account named "Guest", with a pass associated with it?

I have tried this:

```

hammad@1337-mash33n ~ $ sudo smbpasswd -a Guest
[sudo] password for hammad: 
New SMB password:
Retype new SMB password:
Failed to modify password entry for user Guest
hammad@1337-mash33n ~ $ 

```

---

### Post by hammad1337 on 2008-10-24
Hey, I found the solution to the problem.
Here's what I did:

1. Create a user.
```

$ sudo adduser guest

```
DON'T, enter the password, even if it prompts you repeatedly. Just keep pressing enter, until it stops asking.

2. Add user to samba.
```

$ sudo smbpasswd guest

```
This time, enter the password.

Thats all. Done.

---

### Post by Iowan on 2008-10-24
Looks like what you did was "to create a new passworded user account" named "guest".

---

