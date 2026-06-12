---
title: "passwordless ssh problem"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by troythered on 2006-12-20
Hey there, using edgy eft, I have done the following:

ssh-keygen -t rsa
default files
entered in a passphrase

cat id_rsa.pub > authorized_keys

copied the authorized_keys file over to the .ssh folder in the home of the account I wish to access.

made sure that /etc/ssh/sshd_config was set for RSAAuthentication = yes

and then

ssh-add
asked for my passphrase, which i entered

NOW

I am still being asked for my password.  Also upon reboot the ssh-add -l shows nothing, i must re-enter the passphrase.

What am I missing?

Troy

---

### Post by mitch.c on 2006-12-20
> **troythered said:**
> made sure that /etc/ssh/sshd_config was set for RSAAuthentication = yes
Did you set:
```
PubkeyAuthentication yes
```
Did you restart sshd?
> **troythered said:**
> I am still being asked for my password.
You'll be asked for your password until you set:
```
PasswordAuthentication no
```
But don't do that until you have pubkey auth working.
> **troythered said:**
> Also upon reboot the ssh-add -l shows nothing, i must re-enter the passphrase.
That's normal. ssh-add does not retain your key over sessions.

---

### Post by troythered on 2006-12-20
Ok found out what it was:

The file permissions on the .ssh folder and the authorized_keys weren't set right:
had to do a
chmod go-w .ssh
and
chmod 600 .ssh/authorized_keys

now its good, BUT

am I able to automate the ssh-add somehow? or would that undermine the security aspect?

Troy

---

