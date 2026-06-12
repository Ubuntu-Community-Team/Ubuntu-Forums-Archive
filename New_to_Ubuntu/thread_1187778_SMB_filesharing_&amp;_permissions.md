---
title: "SMB filesharing &amp; permissions"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by jadedcritic on 2009-06-15
OK, I'm getting a little punch-drunk stupid here, I'm hoping someone with more experience can share some insight. Quitting Microsoft for me is turning out to be like quitting smoking. This is my 3rd or 4th attempt, but I promise, I'm working on it!

The scenario:
My main PC is an IMAC running leopard 10.5.7. I'm sharing my home directory as both an AFP and an SMB share. I got one of my laptops (a Toshiba) working on Ubuntu exclusively, but when I try to connect to the share, I'm running into problems.  I pull up Nautilus and type smb://<ip addr>/<sharename>

And the share comes up just fine.  When I click on one of the nested directories, it fails. "You do not have the permissions necessary to view the contents of "directory". 

I'd be OK with that, *IF it was giving me a chance to enter the password for the share*. It's not, it's just failing (and telling me I don't have the right permissions. I know the share is read-write, because I can connect to it fine, with both OSX (Leopard), and various flavors of windows; so I can only assume that I'm doing something wrong in the linux sense.

So I guess my question, at it's most basic is this. How, in Ubuntu, does one specify, "Please use these different credentials, to connect to this SMB share" 

All suggestions are appreciated.

---

### Post by AboveTheLogic on 2009-06-15
try

smb://<username>@<ip addr>/<sharename>

---

### Post by jimv on 2009-06-15
which version of ubuntu?

---

### Post by jadedcritic on 2009-06-15
> **jimv said:**
> which version of ubuntu?

9.04 Freshly downloaded from friday.

The curious thing is, it's the same user account on the imac and the ubuntu laptop, it's just a different password.

---

### Post by AboveTheLogic on 2009-06-15
Same acct, different password... that might be your problem.

SMB is designed around Windows. With Windows sharing by default, it works best when the same user account with the same passwords exist on both the client and server machines, then it just uses windows authentication.

Try making the passwords match or using different accounts. There is likely a way to do it the way you are trying, though...

---

### Post by jadedcritic on 2009-06-15
> **AboveTheLogic said:**
> Same acct, different password... that might be your problem.

SMB is designed around Windows. With Windows sharing by default, it works best when the same user account with the same passwords exist on both the client and server machines, then it just uses windows authentication.

Try making the passwords match or using different accounts. There is likely a way to do it the way you are trying, though...

Didn't work!  DOH.  (Changed the password to match). Same error.
Nutty. :(

---

### Post by AboveTheLogic on 2009-06-15
how about another username?
can you get to this share from another machine on the network?

---

### Post by sandyd on 2009-06-15
> **jadedcritic said:**
> OK, I'm getting a little punch-drunk stupid here, I'm hoping someone with more experience can share some insight. Quitting Microsoft for me is turning out to be like quitting smoking. This is my 3rd or 4th attempt, but I promise, I'm working on it!

The scenario:
My main PC is an IMAC running leopard 10.5.7. I'm sharing my home directory as both an AFP and an SMB share. I got one of my laptops (a Toshiba) working on Ubuntu exclusively, but when I try to connect to the share, I'm running into problems.  I pull up Nautilus and type smb://<ip addr>/<sharename>

And the share comes up just fine.  When I click on one of the nested directories, it fails. "You do not have the permissions necessary to view the contents of "directory". 

I'd be OK with that, *IF it was giving me a chance to enter the password for the share*. It's not, it's just failing (and telling me I don't have the right permissions. I know the share is read-write, because I can connect to it fine, with both OSX (Leopard), and various flavors of windows; so I can only assume that I'm doing something wrong in the linux sense.

So I guess my question, at it's most basic is this. How, in Ubuntu, does one specify, "Please use these different credentials, to connect to this SMB share" 

All suggestions are appreciated.

what about
```

smb://<username>:<password>@<address>

```

---

### Post by jadedcritic on 2009-06-15
whoh, never mind, I knocked it loose.

Noticed there was one nested folder that didn't kick out the same error. Started poking at the folder permissions from terminal. Somehow "everyone" had gotten set to No Access, and the folder that worked was read/execute.

Thanks to all for suggestions. :popcorn:

---

