---
title: "Require su to account"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by blacklr on 2009-01-06
Hi. I have disabled direct ssh logins for a shared account using /sbin/nologin, but I would like to allow a small set of users to login as themselves and then su to this account.  The only solution is have is 

```
su - -s /bin/bash shared_account
```

Anyone have a more elegant solution?  

Thanks.

---

### Post by Joeb454 on 2009-01-06
If there's no other elegant solution found you could make it into a bash script to have each user run to switch to that account?

---

### Post by handydan918 on 2009-01-06
> **blacklr said:**
> Hi. I have disabled direct ssh logins for a shared account using /sbin/nologin, but I would like to allow a small set of users to login as themselves and then su to this account.  The only solution is have is 

```
su - -s /bin/bash shared_account
```

Anyone have a more elegant solution?  

Thanks.

What about not disabling direct ssh logins at all, and just allowing access based on group membership?

---

### Post by blacklr on 2009-01-06
The problem is that my company's policy does not allow direct logins for shared accounts like this (or root, for that matter).  This 'user' is required by some software the developers are using, probably only 5-6 folks.  

This isn't a big deal, but I can just see their faces when they have to type

```
su - -s /bin/bash shared_account
```

I wish they could just type 

```
su - shared_account
```

I guess if it makes them mad, they can just set up their own alias! :P

Thanks for your help.

---

### Post by Shazaam on 2009-01-06
Make a desktop launcher that points to the script? No more long faces. :D

---

### Post by bodhi.zazen on 2009-01-06
You will need to configure sudo, but why not

```
sudo -u shared_account -i
```

You can also add as alias to each users .bashrc if you wish

alias share='sudo -u shared_account -i'

---

