---
title: "SSH Problem: Password Getting Rejected"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by groberts1980 on 2006-08-30
So I installed openssh-client today, and I'm trying to log into a machine in the unix lab at my school. I have an account and password that I've been using for awhile using SSH in Windows.

I am running the command:
 
```
ssh myusername@hostname
```

It is connecting, but it is rejecting my password. This same password works when I connect using SSH in Windows. 

When it connects, it comes back with:

```
username@hosname's password:
```

I type in my password and get:
 
```
Permission denied, please try again.
```

Replace username with my actual username and hostname with the machine I'm connecting to.

It looks like its connecting just fine, but it also appears my password is not being sent across the wire. Any ideas?

---

### Post by whizbaby on 2006-08-30
Spontaneous ideas
-encoding problem
-ssh-certificate problem because windohs certainly used another    (can lead to your IP being blocked)
-mistyped your password once (may get you blocked, too)

If your IP was blocked you have to get it freed by the school's admin (IP blocking is a protection against brute-force-try-to-login-scripts and man-in-the-middle-like-attack)

somebody thinking about more helpful stuff?

---

