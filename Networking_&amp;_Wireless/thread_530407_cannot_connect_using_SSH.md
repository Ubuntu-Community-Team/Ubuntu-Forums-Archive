---
title: "cannot connect using SSH"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by SVcoaster on 2007-08-20
I am trying to learn server setup and for a time thought I was getting better at it but I had to install a new copy of Ubuntu server because of a hard drive problem. Now when I try to use ssh to connect to the server I cannot. I ran ssh -v  and the first thing that seems strange is this:

debug1: An invalid name was supplied
Cannot determine realm for numeric host address

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: An invalid name was supplied
Cannot determine realm for numeric host address

debug1: An invalid name was supplied
A parameter was malformed
Validation error

the host information is in /etc/hosts right? I think it is correct. I have no idea where the invalid name might be. Anyway, it continues to load and I get:

The authenticity of host xxx.xxx.xxx. can't be established.

I say yes to continue to connect but my password is rejected. It says:

debug1: Authentications that can continue: publickey,password
Permission denied, please try again

I had just set up the password so I am sure it is correct. Can anyone tell me where I should be looking for the problem?

George

---

### Post by spd106 on 2007-08-20
The ssh client stores the ip address and fingerprint of a server so that it can authenticate it next time you want to connect. As the fingerprint has changed, it rejects the server. Try deleting the ~/.ssh/known_hosts file, then you should be able to get a connect again from scratch. I have run into this problem a few times.

---

### Post by SVcoaster on 2007-08-20
> **spd106 said:**
> The ssh client stores the ip address and fingerprint of a server so that it can authenticate it next time you want to connect. As the fingerprint has changed, it rejects the server. Try deleting the ~/.ssh/known_hosts file, then you should be able to get a connect again from scratch. I have run into this problem a few times.

I am still getting the same message:
's password: 
debug1: Authentications that can continue: publickey,password
debug1: No more authentication methods to try.
Permission denied (publickey,password).

I deleted the known_hosts and the pub key but still no go. I am still bothered by the invalid name and malformed parameter error which I am guessing is on the server side. It reads:

debug1: An invalid name was supplied
Cannot determine realm for numeric host address

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: An invalid name was supplied
Cannot determine realm for numeric host address

debug1: An invalid name was supplied
A parameter was malformed
Validation error

---

