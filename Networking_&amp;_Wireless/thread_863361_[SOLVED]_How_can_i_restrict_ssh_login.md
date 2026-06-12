---
title: "[SOLVED] How can i restrict ssh login?"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by dgrafix on 2008-07-18
I want to be able to dissalow all ssh logins except for one. For example lets call it vnclogin.

I want to do this because i want an insanely long password on just the one limited account that only has access to invoke vnc for the default screen.

No other local users are to be allowed in.


Ps: what is the difference between sshd and ssh? (ie.. sshd_config and ssh_config)

---

### Post by nemin on 2008-07-18
> **dgrafix said:**
> I want to be able to dissalow all ssh logins except for one. For example lets call it vnclogin.

I want to do this because i want an insanely long password on just the one limited account that only has access to invoke vnc for the default screen.

No other local users are to be allowed in.
Is this what you mean? [http://www.linuxquestions.org/questions/linux-security-4/ssh-deny-all-users-except-one-277288/](http://www.linuxquestions.org/questions/linux-security-4/ssh-deny-all-users-except-one-277288/)
I guess the first posts will help you, or google for the 'AllowUsers' and 'DenyUsers' function of sshd.

> **dgrafix said:**
> 
Ps: what is the difference between sshd and ssh? (ie.. sshd_config and ssh_config)
sshd is the daemon, so that program makes it possible for people to login to your system using a client-program like ssh. Makes sens?

---

### Post by dgrafix on 2008-07-18
Thanks :)

I had just figured it out, its easier than i thought!!

You just add:

AllowUsers username

at the end of sshd_config and it excludes everyone else :)


Its a bit more secure this way as my normal logins have relatively weak passwords for convenience. 
I did not want to have any weak pws on ssh though.

---

