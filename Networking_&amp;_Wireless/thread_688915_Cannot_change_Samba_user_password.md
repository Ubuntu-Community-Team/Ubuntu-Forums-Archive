---
title: "Cannot change Samba user password"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by nooozeguy on 2008-02-05
Hi,

I am trying to share files between a Vista laptop and a Ubuntu desktop using Samba.

The problem appears to be that the password for the user is incorrect.

This appears to be because each time I try to change the password in Samba, it does not take (the password I make is longer than the existing password, but when I got back to check, the shorter password is still present).

I have tried using these commands to no avail:

sudo smbpasswd -a yourusername
sudo smbpasswd -e yourusername

Then

smbpasswd

to set the password.

Any help would be dearly appreciated!

Thanks,
Josh

---

### Post by swerdna on 2008-02-06
> **nooozeguy said:**
> Hi,

I am trying to share files between a Vista laptop and a Ubuntu desktop using Samba.

The problem appears to be that the password for the user is incorrect.

This appears to be because each time I try to change the password in Samba, it does not take (the password I make is longer than the existing password, but when I got back to check, the shorter password is still present).

I have tried using these commands to no avail:

sudo smbpasswd -a yourusername
sudo smbpasswd -e yourusername

Then

smbpasswd

to set the password.

Any help would be dearly appreciated!

Thanks,
Josh

1:You're not LITERALLY using 'yourusername' are you?
2: You can only use names that are existing Ubuntu logon users.

Swerdna

---

